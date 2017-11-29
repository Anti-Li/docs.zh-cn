---
title: "BeginMethodEnumeration 函数 （非托管 API 参考）"
description: "BeginMethodEnumeration 函数开始对象的方法的枚举"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="479ad-103">BeginEnumeration 函数</span><span class="sxs-lookup"><span data-stu-id="479ad-103">BeginEnumeration function</span></span>
<span data-ttu-id="479ad-104">开始为对象提供的方法的枚举。</span><span class="sxs-lookup"><span data-stu-id="479ad-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="479ad-105">语法</span><span class="sxs-lookup"><span data-stu-id="479ad-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="479ad-106">参数</span><span class="sxs-lookup"><span data-stu-id="479ad-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="479ad-107">[in]未使用此参数。</span><span class="sxs-lookup"><span data-stu-id="479ad-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="479ad-108">[in]指向的指针[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)实例。</span><span class="sxs-lookup"><span data-stu-id="479ad-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="479ad-109">[in]零 (0) 的所有方法，或用于指定枚举的作用域的标志。</span><span class="sxs-lookup"><span data-stu-id="479ad-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="479ad-110">在中定义的以下标志*WbemCli.h*标头文件，或者你可以定义它们常量作为在代码中：</span><span class="sxs-lookup"><span data-stu-id="479ad-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="479ad-111">返回的常量</span><span class="sxs-lookup"><span data-stu-id="479ad-111">Constant</span></span>  |<span data-ttu-id="479ad-112">值</span><span class="sxs-lookup"><span data-stu-id="479ad-112">Value</span></span>  |<span data-ttu-id="479ad-113">描述</span><span class="sxs-lookup"><span data-stu-id="479ad-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="479ad-114">0x10</span><span class="sxs-lookup"><span data-stu-id="479ad-114">0x10</span></span> | <span data-ttu-id="479ad-115">限制到的类本身中定义的方法枚举。</span><span class="sxs-lookup"><span data-stu-id="479ad-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="479ad-116">0x20</span><span class="sxs-lookup"><span data-stu-id="479ad-116">0x20</span></span> | <span data-ttu-id="479ad-117">限制从基类继承的属性对枚举。</span><span class="sxs-lookup"><span data-stu-id="479ad-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="479ad-118">返回值</span><span class="sxs-lookup"><span data-stu-id="479ad-118">Return value</span></span>

<span data-ttu-id="479ad-119">此函数返回以下值中定义*WbemCli.h*标头文件，或者你可以定义它们常量作为在代码中：</span><span class="sxs-lookup"><span data-stu-id="479ad-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="479ad-120">返回的常量</span><span class="sxs-lookup"><span data-stu-id="479ad-120">Constant</span></span>  |<span data-ttu-id="479ad-121">值</span><span class="sxs-lookup"><span data-stu-id="479ad-121">Value</span></span>  |<span data-ttu-id="479ad-122">描述</span><span class="sxs-lookup"><span data-stu-id="479ad-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="479ad-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="479ad-123">0x80041008</span></span> | <span data-ttu-id="479ad-124">`lEnnumFlags`为非零，并且不是一个指定的标志。</span><span class="sxs-lookup"><span data-stu-id="479ad-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="479ad-125">0</span><span class="sxs-lookup"><span data-stu-id="479ad-125">0</span></span> | <span data-ttu-id="479ad-126">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="479ad-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="479ad-127">备注</span><span class="sxs-lookup"><span data-stu-id="479ad-127">Remarks</span></span>

<span data-ttu-id="479ad-128">此函数包装对的调用[IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="479ad-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="479ad-129">如果当前对象的类定义，则仅支持此方法调用。</span><span class="sxs-lookup"><span data-stu-id="479ad-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="479ad-130">方法操作不能从[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)指向实例的指针。</span><span class="sxs-lookup"><span data-stu-id="479ad-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="479ad-131">确保在其中枚举方法的顺序是固定的给定实例[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="479ad-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="479ad-132">要求</span><span class="sxs-lookup"><span data-stu-id="479ad-132">Requirements</span></span>  
 <span data-ttu-id="479ad-133">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="479ad-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="479ad-134">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="479ad-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="479ad-135">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="479ad-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479ad-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="479ad-136">See also</span></span>  
[<span data-ttu-id="479ad-137">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="479ad-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)