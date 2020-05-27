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
ms.openlocfilehash: 629e18b6cd2fd7910804ecc608a45d2406dddea1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007497"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="4fcd4-102">CorTokenType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4fcd4-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="4fcd4-103">Wskazuje typ tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcd4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fcd4-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4fcd4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4fcd4-105">Members</span></span>  
  
|<span data-ttu-id="4fcd4-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4fcd4-106">Member</span></span>|<span data-ttu-id="4fcd4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4fcd4-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="4fcd4-108">`mdModule`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="4fcd4-109">`mdTypeRef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="4fcd4-110">`mdTypeDef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="4fcd4-111">`mdFieldDef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="4fcd4-112">`mdMethodDef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="4fcd4-113">`mdParamDef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="4fcd4-114">`mdInterfaceImpl`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="4fcd4-115">`mdMemberRef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="4fcd4-116">`mdCustomAttribute`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="4fcd4-117">`mdPermission`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="4fcd4-118">`mdSignature`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="4fcd4-119">`mdEvent`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="4fcd4-120">`mdProperty`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="4fcd4-121">`mdModuleRef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="4fcd4-122">`mdTypeSpec`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="4fcd4-123">`mdAssembly`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="4fcd4-124">`mdAssemblyRef`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="4fcd4-125">`mdFile`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="4fcd4-126">`mdExportedType`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="4fcd4-127">`mdManifestResource`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="4fcd4-128">`mdGenericParam`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="4fcd4-129">`mdMethodSpec`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="4fcd4-130">`mdGenericParamConstraint`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="4fcd4-131">`mdString`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="4fcd4-132">`mdName`Token.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="4fcd4-133">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fcd4-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fcd4-134">Remarks</span></span>  
 <span data-ttu-id="4fcd4-135">Każda wartość jest równa wartości górnego bajtu w odpowiednim tokenie metadanych.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fcd4-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fcd4-136">Requirements</span></span>  
 <span data-ttu-id="4fcd4-137">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fcd4-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fcd4-138">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="4fcd4-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4fcd4-139">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fcd4-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fcd4-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fcd4-140">See also</span></span>

- [<span data-ttu-id="4fcd4-141">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="4fcd4-141">Metadata Enumerations</span></span>](metadata-enumerations.md)
