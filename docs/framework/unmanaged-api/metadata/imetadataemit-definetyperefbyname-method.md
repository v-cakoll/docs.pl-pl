---
title: IMetaDataEmit::DefineTypeRefByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93c55cec3d35fd4208a4a8a7c9b235dd10fb9ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156172"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="879d2-102">IMetaDataEmit::DefineTypeRefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="879d2-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="879d2-103">Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie, który znajduje się poza bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="879d2-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="879d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="879d2-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="879d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="879d2-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="879d2-106">[in] Token, określając zakres rozwiązywania.</span><span class="sxs-lookup"><span data-stu-id="879d2-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="879d2-107">Następujące typy tokenów są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="879d2-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="879d2-108">`mdModuleRef`, jeśli typ jest zdefiniowany w tym samym zestawie, w którym zdefiniowano element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="879d2-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="879d2-109">`mdAssemblyRef`, jeśli typ jest zdefiniowany w zestawie innym niż ten, w którym zdefiniowano element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="879d2-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="879d2-110">`mdTypeRef`, jeśli typ jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="879d2-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="879d2-111">`mdModule`, jeśli typ jest zdefiniowany w tym samym module, w którym zdefiniowano element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="879d2-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="879d2-112">Wartość null, jeśli typ jest zdefiniowany jako globalnie.</span><span class="sxs-lookup"><span data-stu-id="879d2-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="879d2-113">[in] Nazwa typu docelowego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="879d2-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="879d2-114">[out] Wskaźnik do `mdTypeRef` token, który jest przypisany do typu.</span><span class="sxs-lookup"><span data-stu-id="879d2-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="879d2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="879d2-115">Requirements</span></span>  
 <span data-ttu-id="879d2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="879d2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="879d2-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="879d2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="879d2-118">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="879d2-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="879d2-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="879d2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879d2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="879d2-120">See also</span></span>

- [<span data-ttu-id="879d2-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="879d2-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="879d2-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="879d2-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
