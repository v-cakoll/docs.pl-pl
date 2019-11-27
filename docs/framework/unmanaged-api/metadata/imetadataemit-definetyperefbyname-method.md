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
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434385"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="ed261-102">IMetaDataEmit::DefineTypeRefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed261-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="ed261-103">Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie, który znajduje się poza bieżącym zakresem.</span><span class="sxs-lookup"><span data-stu-id="ed261-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed261-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed261-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed261-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed261-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="ed261-106">podczas Token określający zakres rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ed261-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="ed261-107">Następujące typy tokenów są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="ed261-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="ed261-108">`mdModuleRef`, jeśli typ jest zdefiniowany w tym samym zestawie, w którym jest zdefiniowany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="ed261-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="ed261-109">`mdAssemblyRef`, jeśli typ jest zdefiniowany w zestawie innym niż ten, w którym jest zdefiniowany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="ed261-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="ed261-110">`mdTypeRef`, jeśli typ jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="ed261-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="ed261-111">`mdModule`, jeśli typ jest zdefiniowany w tym samym module, w którym jest zdefiniowany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="ed261-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="ed261-112">Wartość null, jeśli typ jest zdefiniowany globalnie.</span><span class="sxs-lookup"><span data-stu-id="ed261-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="ed261-113">podczas Nazwa typu docelowego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="ed261-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ed261-114">określoną Wskaźnik do tokenu `mdTypeRef`, który jest przypisany do typu.</span><span class="sxs-lookup"><span data-stu-id="ed261-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed261-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed261-115">Requirements</span></span>  
 <span data-ttu-id="ed261-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed261-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed261-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ed261-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed261-118">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed261-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed261-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed261-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed261-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed261-120">See also</span></span>

- [<span data-ttu-id="ed261-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed261-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ed261-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed261-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
