---
title: CorCheckDuplicatesFor — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176191"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="f4733-102">CorCheckDuplicatesFor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f4733-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="f4733-103">Określa tokeny metadanych, które będą sprawdzane pod kątem duplikatów.</span><span class="sxs-lookup"><span data-stu-id="f4733-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4733-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4733-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="f4733-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f4733-105">Members</span></span>  
  
|<span data-ttu-id="f4733-106">Członek</span><span class="sxs-lookup"><span data-stu-id="f4733-106">Member</span></span>|<span data-ttu-id="f4733-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f4733-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="f4733-108">Sprawdź wszystkie tokeny metadanych pod kątem duplikatów.</span><span class="sxs-lookup"><span data-stu-id="f4733-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="f4733-109">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f4733-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="f4733-110">Nie należy sprawdzać tokenów metadanych pod kątem duplikatów.</span><span class="sxs-lookup"><span data-stu-id="f4733-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="f4733-111">Sprawdź, czy `mdTypeDef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="f4733-112">Sprawdź, czy `mdInterfaceImpl` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="f4733-113">Sprawdź, czy `mdMethodDef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="f4733-114">Sprawdź, czy `mdTypeRef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="f4733-115">Sprawdź, czy `mdMemberRef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="f4733-116">Sprawdź, czy `mdCustomAttribute` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="f4733-117">Sprawdź, czy `mdParamDef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="f4733-118">Sprawdź, czy `mdPermission` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="f4733-119">Sprawdź, czy `mdProperty` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="f4733-120">Sprawdź, czy `mdEvent` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="f4733-121">Sprawdź, czy `mdFieldDef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="f4733-122">Sprawdź, czy `mdSignature` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="f4733-123">Sprawdź, czy `mdModuleRef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="f4733-124">Sprawdź, czy `mdTypeSpec` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="f4733-125">Sprawdź, czy `mdImplMap` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="f4733-126">Sprawdź, czy `mdAssemblyRef` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="f4733-127">Sprawdź, czy `mdFile` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="f4733-128">Sprawdź, czy `mdExportedType` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="f4733-129">Sprawdź, czy `mdManifestResource` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="f4733-130">Sprawdź, czy `mdGenericParam` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="f4733-131">Sprawdź, czy `mdMethodSpec` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="f4733-132">Sprawdź, czy `mdGenericParamConstraint` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="f4733-133">Sprawdź, czy `mdAssembly` nie ma duplikatów tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="f4733-134">`mdMemberRef`Sprawdź, czy `mdTypeRef` `mdSignature`nie ma `mdTypeSpec`duplikatów , , i `mdMethodSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4733-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4733-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4733-135">Requirements</span></span>  
 <span data-ttu-id="f4733-136">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4733-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4733-137">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f4733-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f4733-138">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4733-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4733-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4733-139">See also</span></span>

- [<span data-ttu-id="f4733-140">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="f4733-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
