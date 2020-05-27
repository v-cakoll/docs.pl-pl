---
title: CorNotificationForTokenMovement — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: e8065a5492884a4b7f5d662737e4beddc6fca5b3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007601"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="eb2b6-102">CorNotificationForTokenMovement — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eb2b6-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="eb2b6-103">Określa powiadomienia, które będą wysyłane do klienta API metadanych, gdy następuje ponowne mapowanie tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb2b6-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="eb2b6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="eb2b6-105">Members</span></span>  
  
|<span data-ttu-id="eb2b6-106">Członek</span><span class="sxs-lookup"><span data-stu-id="eb2b6-106">Member</span></span>|<span data-ttu-id="eb2b6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eb2b6-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="eb2b6-108">Powiadamiaj `mdTypeRef` o `mdMethodDef` `mdMemberRef` `mdFieldDef` przeniesieniu tokenów,, lub.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="eb2b6-109">Powiadamiaj po przeniesieniu dowolnego tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="eb2b6-110">Nie powiadamiaj, gdy tokeny są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="eb2b6-111">Powiadamiaj o `mdMethodDef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="eb2b6-112">Powiadamiaj o `mdMemberRef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="eb2b6-113">Powiadamiaj o `mdFieldDef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="eb2b6-114">Powiadamiaj o `mdTypeRef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="eb2b6-115">Powiadamiaj o `mdTypeDef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="eb2b6-116">Powiadamiaj o `mdParamDef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="eb2b6-117">Powiadamiaj o `mdInterfaceImpl` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="eb2b6-118">Powiadamiaj o `mdProperty` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="eb2b6-119">Powiadamiaj o `mdEvent` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="eb2b6-120">Powiadamiaj o `mdSignature` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="eb2b6-121">Powiadamiaj o `mdTypeSpec` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="eb2b6-122">Powiadamiaj o `mdCustomAttribute` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="eb2b6-123">Powiadamiaj o `mdSecurityValue` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="eb2b6-124">Powiadamiaj o `mdPermission` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="eb2b6-125">Powiadamiaj o `mdModuleRef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="eb2b6-126">Powiadamiaj o `mdNameSpace` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="eb2b6-127">Powiadamiaj o `mdAssemblyRef` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="eb2b6-128">Powiadamiaj o `mdFile` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="eb2b6-129">Powiadamiaj o `mdExportedType` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="eb2b6-130">Powiadamiaj o `mdManifestResource` przeniesieniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb2b6-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb2b6-131">Remarks</span></span>  
 <span data-ttu-id="eb2b6-132">Token może być ponownie mapowany (czyli przeniesiony) podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2b6-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb2b6-133">Requirements</span></span>  
 <span data-ttu-id="eb2b6-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb2b6-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2b6-135">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="eb2b6-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eb2b6-136">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2b6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2b6-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb2b6-137">See also</span></span>

- [<span data-ttu-id="eb2b6-138">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="eb2b6-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
