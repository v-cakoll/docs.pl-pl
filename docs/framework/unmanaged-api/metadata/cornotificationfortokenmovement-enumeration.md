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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a7859bd890a2ecc10b5117f697ff8b06ad569f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781697"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="a564d-102">CorNotificationForTokenMovement — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a564d-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="a564d-103">Określa powiadomień, które będą wysyłane do klienta metadanych interfejsu API, gdy wystąpi tokenu ponowne mapowanie.</span><span class="sxs-lookup"><span data-stu-id="a564d-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a564d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a564d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a564d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a564d-105">Members</span></span>  
  
|<span data-ttu-id="a564d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a564d-106">Member</span></span>|<span data-ttu-id="a564d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a564d-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="a564d-108">Powiadom mnie, kiedy `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, lub `mdFieldDef` przenoszenia tokenów.</span><span class="sxs-lookup"><span data-stu-id="a564d-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="a564d-109">Powiadomienie, gdy dowolny token.</span><span class="sxs-lookup"><span data-stu-id="a564d-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="a564d-110">Nie powiadamiaj podczas przenoszenia tokenów.</span><span class="sxs-lookup"><span data-stu-id="a564d-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="a564d-111">Powiadom mnie, kiedy `mdMethodDef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="a564d-112">Powiadom mnie, kiedy `mdMemberRef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="a564d-113">Powiadom mnie, kiedy `mdFieldDef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="a564d-114">Powiadom mnie, kiedy `mdTypeRef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="a564d-115">Powiadom mnie, kiedy `mdTypeDef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="a564d-116">Powiadom mnie, kiedy `mdParamDef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="a564d-117">Powiadom mnie, kiedy `mdInterfaceImpl` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="a564d-118">Powiadom mnie, kiedy `mdProperty` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="a564d-119">Powiadom mnie, kiedy `mdEvent` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="a564d-120">Powiadom mnie, kiedy `mdSignature` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="a564d-121">Powiadom mnie, kiedy `mdTypeSpec` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="a564d-122">Powiadom mnie, kiedy `mdCustomAttribute` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="a564d-123">Powiadom mnie, kiedy `mdSecurityValue` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="a564d-124">Powiadom mnie, kiedy `mdPermission` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="a564d-125">Powiadom mnie, kiedy `mdModuleRef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="a564d-126">Powiadom mnie, kiedy `mdNameSpace` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="a564d-127">Powiadom mnie, kiedy `mdAssemblyRef` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="a564d-128">Powiadom mnie, kiedy `mdFile` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="a564d-129">Powiadom mnie, kiedy `mdExportedType` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="a564d-130">Powiadom mnie, kiedy `mdManifestResource` przenosi tokenu.</span><span class="sxs-lookup"><span data-stu-id="a564d-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a564d-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a564d-131">Remarks</span></span>  
 <span data-ttu-id="a564d-132">Tokenu można ponownie zamapować (który poruszyły) podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="a564d-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a564d-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a564d-133">Requirements</span></span>  
 <span data-ttu-id="a564d-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a564d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a564d-135">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a564d-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a564d-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a564d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a564d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a564d-137">See also</span></span>

- [<span data-ttu-id="a564d-138">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a564d-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
