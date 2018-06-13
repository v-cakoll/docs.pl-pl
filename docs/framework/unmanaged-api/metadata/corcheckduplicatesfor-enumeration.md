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
ms.openlocfilehash: 9cdb1570b682088e92ff7c7a78d84259d02d8512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444506"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="48f06-102">CorCheckDuplicatesFor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="48f06-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="48f06-103">Określa tokenów metadanych, które zostaną sprawdzone duplikatów.</span><span class="sxs-lookup"><span data-stu-id="48f06-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48f06-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="48f06-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="48f06-105">Members</span></span>  
  
|<span data-ttu-id="48f06-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="48f06-106">Member</span></span>|<span data-ttu-id="48f06-107">Opis</span><span class="sxs-lookup"><span data-stu-id="48f06-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="48f06-108">Sprawdź wszystkie tokeny metadanych duplikatów.</span><span class="sxs-lookup"><span data-stu-id="48f06-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="48f06-109">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="48f06-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="48f06-110">Nie sprawdzaj tokenów metadanych duplikatów.</span><span class="sxs-lookup"><span data-stu-id="48f06-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="48f06-111">Sprawdź, czy duplikaty `mdTypeDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="48f06-112">Sprawdź, czy duplikaty `mdInterfaceImpl` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="48f06-113">Sprawdź, czy duplikaty `mdMethodDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="48f06-114">Sprawdź, czy duplikaty `mdTypeRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="48f06-115">Sprawdź, czy duplikaty `mdMemberRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="48f06-116">Sprawdź, czy duplikaty `mdCustomAttribute` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="48f06-117">Sprawdź, czy duplikaty `mdParamDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="48f06-118">Sprawdź, czy duplikaty `mdPermission` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="48f06-119">Sprawdź, czy duplikaty `mdProperty` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="48f06-120">Sprawdź, czy duplikaty `mdEvent` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="48f06-121">Sprawdź, czy duplikaty `mdFieldDef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="48f06-122">Sprawdź, czy duplikaty `mdSignature` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="48f06-123">Sprawdź, czy duplikaty `mdModuleRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="48f06-124">Sprawdź, czy duplikaty `mdTypeSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="48f06-125">Sprawdź, czy duplikaty `mdImplMap` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="48f06-126">Sprawdź, czy duplikaty `mdAssemblyRef` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="48f06-127">Sprawdź, czy duplikaty `mdFile` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="48f06-128">Sprawdź, czy duplikaty `mdExportedType` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="48f06-129">Sprawdź, czy duplikaty `mdManifestResource` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="48f06-130">Sprawdź, czy duplikaty `mdGenericParam` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="48f06-131">Sprawdź, czy duplikaty `mdMethodSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="48f06-132">Sprawdź, czy duplikaty `mdGenericParamConstraint` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="48f06-133">Sprawdź, czy duplikaty `mdAssembly` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="48f06-134">Sprawdź, czy duplikaty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, i `mdMethodSpec` tokenów.</span><span class="sxs-lookup"><span data-stu-id="48f06-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48f06-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48f06-135">Requirements</span></span>  
 <span data-ttu-id="48f06-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48f06-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f06-137">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="48f06-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="48f06-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48f06-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f06-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48f06-139">See Also</span></span>  
 [<span data-ttu-id="48f06-140">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="48f06-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
