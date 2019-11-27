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
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450148"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="230bd-102">CorNotificationForTokenMovement — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="230bd-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="230bd-103">Określa powiadomienia, które będą wysyłane do klienta API metadanych, gdy następuje ponowne mapowanie tokenu.</span><span class="sxs-lookup"><span data-stu-id="230bd-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="230bd-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="230bd-105">Members</span><span class="sxs-lookup"><span data-stu-id="230bd-105">Members</span></span>  
  
|<span data-ttu-id="230bd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="230bd-106">Member</span></span>|<span data-ttu-id="230bd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="230bd-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="230bd-108">Powiadamiaj po przeniesieniu tokenów `mdTypeRef`, `mdMethodDef`, `mdMemberRef`lub `mdFieldDef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="230bd-109">Powiadamiaj po przeniesieniu dowolnego tokenu.</span><span class="sxs-lookup"><span data-stu-id="230bd-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="230bd-110">Nie powiadamiaj, gdy tokeny są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="230bd-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="230bd-111">Powiadamiaj po przeniesieniu tokenu `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="230bd-112">Powiadamiaj po przeniesieniu tokenu `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="230bd-113">Powiadamiaj po przeniesieniu tokenu `mdFieldDef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="230bd-114">Powiadamiaj po przeniesieniu tokenu `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="230bd-115">Powiadamiaj po przeniesieniu tokenu `mdTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="230bd-116">Powiadamiaj po przeniesieniu tokenu `mdParamDef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="230bd-117">Powiadamiaj po przeniesieniu tokenu `mdInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="230bd-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="230bd-118">Powiadamiaj po przeniesieniu tokenu `mdProperty`.</span><span class="sxs-lookup"><span data-stu-id="230bd-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="230bd-119">Powiadamiaj po przeniesieniu tokenu `mdEvent`.</span><span class="sxs-lookup"><span data-stu-id="230bd-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="230bd-120">Powiadamiaj po przeniesieniu tokenu `mdSignature`.</span><span class="sxs-lookup"><span data-stu-id="230bd-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="230bd-121">Powiadamiaj po przeniesieniu tokenu `mdTypeSpec`.</span><span class="sxs-lookup"><span data-stu-id="230bd-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="230bd-122">Powiadamiaj po przeniesieniu tokenu `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="230bd-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="230bd-123">Powiadamiaj po przeniesieniu tokenu `mdSecurityValue`.</span><span class="sxs-lookup"><span data-stu-id="230bd-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="230bd-124">Powiadamiaj po przeniesieniu tokenu `mdPermission`.</span><span class="sxs-lookup"><span data-stu-id="230bd-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="230bd-125">Powiadamiaj po przeniesieniu tokenu `mdModuleRef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="230bd-126">Powiadamiaj po przeniesieniu tokenu `mdNameSpace`.</span><span class="sxs-lookup"><span data-stu-id="230bd-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="230bd-127">Powiadamiaj po przeniesieniu tokenu `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="230bd-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="230bd-128">Powiadamiaj po przeniesieniu tokenu `mdFile`.</span><span class="sxs-lookup"><span data-stu-id="230bd-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="230bd-129">Powiadamiaj po przeniesieniu tokenu `mdExportedType`.</span><span class="sxs-lookup"><span data-stu-id="230bd-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="230bd-130">Powiadamiaj po przeniesieniu tokenu `mdManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="230bd-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230bd-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="230bd-131">Remarks</span></span>  
 <span data-ttu-id="230bd-132">Token może być ponownie mapowany (czyli przeniesiony) podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="230bd-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="230bd-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="230bd-133">Requirements</span></span>  
 <span data-ttu-id="230bd-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="230bd-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="230bd-135">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="230bd-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="230bd-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="230bd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230bd-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="230bd-137">See also</span></span>

- [<span data-ttu-id="230bd-138">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="230bd-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
