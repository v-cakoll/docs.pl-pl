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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046049"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="80303-102">CorCheckDuplicatesFor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="80303-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="80303-103">Określa tokeny metadanych, które będą sprawdzane duplikatów.</span><span class="sxs-lookup"><span data-stu-id="80303-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80303-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80303-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="80303-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="80303-105">Members</span></span>  
  
|<span data-ttu-id="80303-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="80303-106">Member</span></span>|<span data-ttu-id="80303-107">Opis</span><span class="sxs-lookup"><span data-stu-id="80303-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="80303-108">Sprawdź wszystkie tokeny metadanych dla duplikatów.</span><span class="sxs-lookup"><span data-stu-id="80303-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="80303-109">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="80303-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="80303-110">Nie zaznaczaj tokeny metadanych dla duplikatów.</span><span class="sxs-lookup"><span data-stu-id="80303-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="80303-111">Sprawdź duplikaty z `mdTypeDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="80303-112">Sprawdź duplikaty z `mdInterfaceImpl` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="80303-113">Sprawdź duplikaty z `mdMethodDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="80303-114">Sprawdź duplikaty z `mdTypeRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="80303-115">Sprawdź duplikaty z `mdMemberRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="80303-116">Sprawdź duplikaty z `mdCustomAttribute` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="80303-117">Sprawdź duplikaty z `mdParamDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="80303-118">Sprawdź duplikaty z `mdPermission` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="80303-119">Sprawdź duplikaty z `mdProperty` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="80303-120">Sprawdź duplikaty z `mdEvent` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="80303-121">Sprawdź duplikaty z `mdFieldDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="80303-122">Sprawdź duplikaty z `mdSignature` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="80303-123">Sprawdź duplikaty z `mdModuleRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="80303-124">Sprawdź duplikaty z `mdTypeSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="80303-125">Sprawdź duplikaty z `mdImplMap` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="80303-126">Sprawdź duplikaty z `mdAssemblyRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="80303-127">Sprawdź duplikaty z `mdFile` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="80303-128">Sprawdź duplikaty z `mdExportedType` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="80303-129">Sprawdź duplikaty z `mdManifestResource` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="80303-130">Sprawdź duplikaty z `mdGenericParam` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="80303-131">Sprawdź duplikaty z `mdMethodSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="80303-132">Sprawdź duplikaty z `mdGenericParamConstraint` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="80303-133">Sprawdź duplikaty z `mdAssembly` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="80303-134">Sprawdź duplikaty z `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, i `mdMethodSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="80303-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80303-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80303-135">Requirements</span></span>  
 <span data-ttu-id="80303-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80303-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80303-137">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="80303-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="80303-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80303-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80303-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80303-139">See also</span></span>

- [<span data-ttu-id="80303-140">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="80303-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
