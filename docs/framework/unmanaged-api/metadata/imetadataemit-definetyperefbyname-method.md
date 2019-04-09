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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156172"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="6b633-102">IMetaDataEmit::DefineTypeRefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b633-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="6b633-103">Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie, który znajduje się poza bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6b633-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b633-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b633-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b633-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b633-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="6b633-106">[in] Token, określając zakres rozwiązywania.</span><span class="sxs-lookup"><span data-stu-id="6b633-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="6b633-107">Następujące typy tokenów są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="6b633-107">The following token types are valid:</span></span>  
  
-   `mdModuleRef`<span data-ttu-id="6b633-108">, jeśli typ jest zdefiniowany w tym samym zestawie, w którym zdefiniowano element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="6b633-108">, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   `mdAssemblyRef`<span data-ttu-id="6b633-109">, jeśli typ jest zdefiniowany w zestawie innym niż ten, w którym zdefiniowano element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="6b633-109">, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   `mdTypeRef`<span data-ttu-id="6b633-110">, jeśli typ jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="6b633-110">, if the type is a nested type.</span></span>  
  
-   `mdModule`<span data-ttu-id="6b633-111">, jeśli typ jest zdefiniowany w tym samym module, w którym zdefiniowano element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="6b633-111">, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="6b633-112">Wartość null, jeśli typ jest zdefiniowany jako globalnie.</span><span class="sxs-lookup"><span data-stu-id="6b633-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="6b633-113">[in] Nazwa typu docelowego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="6b633-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="6b633-114">[out] Wskaźnik do `mdTypeRef` token, który jest przypisany do typu.</span><span class="sxs-lookup"><span data-stu-id="6b633-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b633-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b633-115">Requirements</span></span>  
 <span data-ttu-id="6b633-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b633-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b633-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6b633-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b633-118">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b633-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6b633-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6b633-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b633-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b633-120">See also</span></span>

- [<span data-ttu-id="6b633-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6b633-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6b633-122">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6b633-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
