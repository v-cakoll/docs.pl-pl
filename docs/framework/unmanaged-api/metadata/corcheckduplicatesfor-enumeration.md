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
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007907"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="60c4e-102">CorCheckDuplicatesFor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="60c4e-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="60c4e-103">Określa tokeny metadanych, które będą sprawdzane pod kątem duplikatów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60c4e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="60c4e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="60c4e-105">Members</span></span>  
  
|<span data-ttu-id="60c4e-106">Członek</span><span class="sxs-lookup"><span data-stu-id="60c4e-106">Member</span></span>|<span data-ttu-id="60c4e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="60c4e-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="60c4e-108">Sprawdź wszystkie tokeny metadanych dla duplikatów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="60c4e-109">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="60c4e-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="60c4e-110">Nie sprawdzaj tokenów metadanych dla duplikatów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="60c4e-111">Sprawdź duplikaty `mdTypeDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="60c4e-112">Sprawdź duplikaty `mdInterfaceImpl` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="60c4e-113">Sprawdź duplikaty `mdMethodDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="60c4e-114">Sprawdź duplikaty `mdTypeRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="60c4e-115">Sprawdź duplikaty `mdMemberRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="60c4e-116">Sprawdź duplikaty `mdCustomAttribute` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="60c4e-117">Sprawdź duplikaty `mdParamDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="60c4e-118">Sprawdź duplikaty `mdPermission` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="60c4e-119">Sprawdź duplikaty `mdProperty` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="60c4e-120">Sprawdź duplikaty `mdEvent` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="60c4e-121">Sprawdź duplikaty `mdFieldDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="60c4e-122">Sprawdź duplikaty `mdSignature` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="60c4e-123">Sprawdź duplikaty `mdModuleRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="60c4e-124">Sprawdź duplikaty `mdTypeSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="60c4e-125">Sprawdź duplikaty `mdImplMap` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="60c4e-126">Sprawdź duplikaty `mdAssemblyRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="60c4e-127">Sprawdź duplikaty `mdFile` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="60c4e-128">Sprawdź duplikaty `mdExportedType` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="60c4e-129">Sprawdź duplikaty `mdManifestResource` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="60c4e-130">Sprawdź duplikaty `mdGenericParam` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="60c4e-131">Sprawdź duplikaty `mdMethodSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="60c4e-132">Sprawdź duplikaty `mdGenericParamConstraint` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="60c4e-133">Sprawdź duplikaty `mdAssembly` tokenów.</span><span class="sxs-lookup"><span data-stu-id="60c4e-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="60c4e-134">Sprawdź duplikaty `mdMemberRef` `mdTypeRef` tokenów,, `mdSignature` , `mdTypeSpec` i `mdMethodSpec` .</span><span class="sxs-lookup"><span data-stu-id="60c4e-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60c4e-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60c4e-135">Requirements</span></span>  
 <span data-ttu-id="60c4e-136">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60c4e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c4e-137">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="60c4e-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="60c4e-138">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c4e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c4e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60c4e-139">See also</span></span>

- [<span data-ttu-id="60c4e-140">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="60c4e-140">Metadata Enumerations</span></span>](metadata-enumerations.md)
