---
title: CorTokenType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b33b50e53c454f2b62253d12943ea044240d8cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230515"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="e346a-102">CorTokenType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e346a-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="e346a-103">Wskazuje typ tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="e346a-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e346a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e346a-104">Syntax</span></span>  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="e346a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e346a-105">Members</span></span>  
  
|<span data-ttu-id="e346a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e346a-106">Member</span></span>|<span data-ttu-id="e346a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e346a-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="e346a-108">`mdModule` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="e346a-109">`mdTypeRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="e346a-110">`mdTypeDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="e346a-111">`mdFieldDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="e346a-112">`mdMethodDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="e346a-113">`mdParamDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="e346a-114">`mdInterfaceImpl` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="e346a-115">`mdMemberRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="e346a-116">`mdCustomAttribute` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="e346a-117">`mdPermission` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="e346a-118">`mdSignature` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="e346a-119">`mdEvent` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="e346a-120">`mdProperty` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="e346a-121">`mdModuleRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="e346a-122">`mdTypeSpec` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="e346a-123">`mdAssembly` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="e346a-124">`mdAssemblyRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="e346a-125">`mdFile` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="e346a-126">`mdExportedType` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="e346a-127">`mdManifestResource` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="e346a-128">`mdGenericParam` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="e346a-129">`mdMethodSpec` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="e346a-130">`mdGenericParamConstraint` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="e346a-131">`mdString` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="e346a-132">`mdName` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="e346a-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="e346a-133">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="e346a-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e346a-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e346a-134">Remarks</span></span>  
 <span data-ttu-id="e346a-135">Każda wartość jest równa wartości pierwszy bajt odpowiedni token metadanych.</span><span class="sxs-lookup"><span data-stu-id="e346a-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e346a-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e346a-136">Requirements</span></span>  
 <span data-ttu-id="e346a-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e346a-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e346a-138">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e346a-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e346a-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e346a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e346a-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e346a-140">See also</span></span>

- [<span data-ttu-id="e346a-141">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="e346a-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
