---
title: "IMetaDataEmit::DefineTypeRefByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ce04733fa9f149f155d850c53b65b263943cf8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="dd85e-102">IMetaDataEmit::DefineTypeRefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd85e-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="dd85e-103">Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie znajduje się poza bieżącym zakresem.</span><span class="sxs-lookup"><span data-stu-id="dd85e-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd85e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd85e-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd85e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd85e-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="dd85e-106">[in] Token określający zakres rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="dd85e-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="dd85e-107">Następujące typy tokenów są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="dd85e-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="dd85e-108">`mdModuleRef`, jeśli typ jest zdefiniowany w tym samym zestawie, w którym jest zdefiniowany element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="dd85e-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="dd85e-109">`mdAssemblyRef`, jeśli typ jest zdefiniowany w zestawie innego niż ten, w którym jest zdefiniowany element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="dd85e-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="dd85e-110">`mdTypeRef`, jeśli typ jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="dd85e-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="dd85e-111">`mdModule`, jeśli typ jest zdefiniowany w tym samym module, w którym jest zdefiniowany element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="dd85e-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="dd85e-112">Wartość null, jeśli typ jest zdefiniowany globalnie.</span><span class="sxs-lookup"><span data-stu-id="dd85e-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="dd85e-113">[in] Nazwa typu docelowego w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="dd85e-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="dd85e-114">[out] Wskaźnik do `mdTypeRef` token, który jest przypisany do typu.</span><span class="sxs-lookup"><span data-stu-id="dd85e-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd85e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd85e-115">Requirements</span></span>  
 <span data-ttu-id="dd85e-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd85e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd85e-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd85e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd85e-118">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd85e-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd85e-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd85e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd85e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd85e-120">See Also</span></span>  
 [<span data-ttu-id="dd85e-121">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="dd85e-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dd85e-122">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="dd85e-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
