---
title: "CorNotificationForTokenMovement 枚举"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60d6c56394952fca84b45ba042f7d45a1dec6b1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="d6f03-102">CorNotificationForTokenMovement 枚举</span><span class="sxs-lookup"><span data-stu-id="d6f03-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="d6f03-103">指定令牌重新映射发生时将发送到元数据 API 客户端的通知。</span><span class="sxs-lookup"><span data-stu-id="d6f03-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f03-104">语法</span><span class="sxs-lookup"><span data-stu-id="d6f03-104">Syntax</span></span>  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="d6f03-105">成员</span><span class="sxs-lookup"><span data-stu-id="d6f03-105">Members</span></span>  
  
|<span data-ttu-id="d6f03-106">成员</span><span class="sxs-lookup"><span data-stu-id="d6f03-106">Member</span></span>|<span data-ttu-id="d6f03-107">描述</span><span class="sxs-lookup"><span data-stu-id="d6f03-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="d6f03-108">通知时`mdTypeRef`， `mdMethodDef`， `mdMemberRef`，或`mdFieldDef`令牌移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="d6f03-109">在任何标记移动时通知。</span><span class="sxs-lookup"><span data-stu-id="d6f03-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="d6f03-110">不会通知标记移动时。</span><span class="sxs-lookup"><span data-stu-id="d6f03-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="d6f03-111">通知时`mdMethodDef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="d6f03-112">通知时`mdMemberRef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="d6f03-113">通知时`mdFieldDef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="d6f03-114">通知时`mdTypeRef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="d6f03-115">通知时`mdTypeDef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="d6f03-116">通知时`mdParamDef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="d6f03-117">通知时`mdInterfaceImpl`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="d6f03-118">通知时`mdProperty`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="d6f03-119">通知时`mdEvent`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="d6f03-120">通知时`mdSignature`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="d6f03-121">通知时`mdTypeSpec`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="d6f03-122">通知时`mdCustomAttribute`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="d6f03-123">通知时`mdSecurityValue`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="d6f03-124">通知时`mdPermission`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="d6f03-125">通知时`mdModuleRef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="d6f03-126">通知时`mdNameSpace`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="d6f03-127">通知时`mdAssemblyRef`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="d6f03-128">通知时`mdFile`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="d6f03-129">通知时`mdExportedType`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="d6f03-130">通知时`mdManifestResource`标记移动。</span><span class="sxs-lookup"><span data-stu-id="d6f03-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6f03-131">备注</span><span class="sxs-lookup"><span data-stu-id="d6f03-131">Remarks</span></span>  
 <span data-ttu-id="d6f03-132">令牌可能会重新映射 （即移动） 期间的元数据合并。</span><span class="sxs-lookup"><span data-stu-id="d6f03-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6f03-133">要求</span><span class="sxs-lookup"><span data-stu-id="d6f03-133">Requirements</span></span>  
 <span data-ttu-id="d6f03-134">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6f03-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6f03-135">**标头：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d6f03-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d6f03-136">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6f03-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f03-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6f03-137">See Also</span></span>  
 [<span data-ttu-id="d6f03-138">元数据枚举</span><span class="sxs-lookup"><span data-stu-id="d6f03-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)