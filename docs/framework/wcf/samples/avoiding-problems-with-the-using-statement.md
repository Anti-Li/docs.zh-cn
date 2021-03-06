---
title: 避免出现与 Using 语句有关的问题
ms.date: 03/30/2017
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 14a0649c9996158f1503581c906d8dfd1a95ebc8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503893"
---
# <a name="avoiding-problems-with-the-using-statement"></a>避免出现与 Using 语句有关的问题
本示例演示在使用类型化客户端时，不应使用 C# 的“using”语句自动清除资源。 此示例基于[入门](../../../../docs/framework/wcf/samples/getting-started-sample.md)实现计算器服务。 在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 本示例演示对类型化客户端使用 C# 的“using”语句时发生的两个常见问题以及发生异常后用于正确清除的代码。  
  
 C# 的“using”语句会导致调用 `Dispose`()。 它等效于 `Close`()，当发生网络错误时可能会引发异常。 由于对 `Dispose`() 的调用是在“using”块的右大括号处隐式发生的，因此导致异常的根源往往会被编写代码和阅读代码的人所忽略。 这是应用程序错误的潜在根源。  
  
 `DemonstrateProblemUsingCanThrow` 方法中演示的第一个问题是，右大括号引发异常，不执行右大括号后面的代码：  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 即使 using 块中的内容不会引发异常或可以捕获 using 块中的所有异常，`Console.Writeline` 也不会发生，因为右大括号处的隐式 `Dispose`() 调用可能会引发异常。  
  
 `DemonstrateProblemUsingCanThrowAndMask` 方法中演示的第二个问题是右大括号引发异常的另一种隐含情况：  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 因为 `Dispose`() 发生在“finally”块内，因此在 `ApplicationException`() 失败的情况下，`Dispose` 不会发生在 using 块外。 如果外面的代码必须要知道 `ApplicationException` 发生的时间，则“using”构造可能会因为屏蔽此异常而导致问题。  
  
 最后，示例演示 `DemonstrateCleanupWithExceptions` 中发生异常时如何正确清除异常。 本示例使用 try/catch 块报告错误并调用 `Abort`。 请参阅[预期异常](../../../../docs/framework/wcf/samples/expected-exceptions.md)示例有关捕获从客户端调用的异常详细信息。  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  using 语句和 ServiceHost：许多自承载的应用程序主要用于承载服务，并且 ServiceHost.Close 很少引发异常，因此这样的应用程序可以安全地一起使用 using 语句和 ServiceHost。 但请注意，ServiceHost.Close 可能引发 `CommunicationException`，因此，如果关闭 ServiceHost 以后应用程序继续执行，则应避免使用 using 语句并遵循前面提供的模式。  
  
 运行示例时，在客户端控制台窗口中显示操作响应和异常。  
  
 客户端进程运行三个方案，每个方案都会尝试调用 `Divide`。 第一个方案演示由于 `Dispose`() 中发生异常而跳过代码。 第二个方案演示由于 `Dispose`() 中发生异常而屏蔽重要异常。 第三个方案演示如何正确清除。  
  
 客户端进程的预期输出为：  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  确保已执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
3.  若要在单或跨计算机配置上运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和针对.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](http://go.microsoft.com/fwlink/?LinkId=150780)下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>请参阅
