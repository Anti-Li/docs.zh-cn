---
title: "ICorDebugThread2::GetVolatileOSThreadID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetVolatileOSThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ef0df7caad2e903e9325eb692fd318bec0c2c78
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="b431e-102">ICorDebugThread2::GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="b431e-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="b431e-103">获取此 ICorDebugThread2 操作系统线程标识符。</span><span class="sxs-lookup"><span data-stu-id="b431e-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b431e-104">语法</span><span class="sxs-lookup"><span data-stu-id="b431e-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b431e-105">参数</span><span class="sxs-lookup"><span data-stu-id="b431e-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="b431e-106">[out]此线程的的操作系统线程的标识符。</span><span class="sxs-lookup"><span data-stu-id="b431e-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b431e-107">要求</span><span class="sxs-lookup"><span data-stu-id="b431e-107">Requirements</span></span>  
 <span data-ttu-id="b431e-108">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b431e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b431e-109">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b431e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b431e-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b431e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b431e-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b431e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>