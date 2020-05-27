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
ms.openlocfilehash: ae30140e69926be32570960a32524a74b850bda4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009356"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="757cb-102">IMetaDataEmit::DefineTypeRefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="757cb-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="757cb-103">Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie, który znajduje się poza bieżącym zakresem.</span><span class="sxs-lookup"><span data-stu-id="757cb-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="757cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="757cb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="757cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="757cb-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="757cb-106">podczas Token określający zakres rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="757cb-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="757cb-107">Następujące typy tokenów są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="757cb-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="757cb-108">`mdModuleRef`, jeśli typ jest zdefiniowany w tym samym zestawie, w którym jest zdefiniowany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="757cb-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="757cb-109">`mdAssemblyRef`, jeśli typ jest zdefiniowany w zestawie innym niż ten, w którym jest zdefiniowany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="757cb-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="757cb-110">`mdTypeRef`, jeśli typ jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="757cb-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="757cb-111">`mdModule`, jeśli typ jest zdefiniowany w tym samym module, w którym jest zdefiniowany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="757cb-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="757cb-112">Wartość null, jeśli typ jest zdefiniowany globalnie.</span><span class="sxs-lookup"><span data-stu-id="757cb-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="757cb-113">podczas Nazwa typu docelowego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="757cb-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="757cb-114">określoną Wskaźnik do `mdTypeRef` tokenu, który jest przypisany do typu.</span><span class="sxs-lookup"><span data-stu-id="757cb-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="757cb-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="757cb-115">Requirements</span></span>  
 <span data-ttu-id="757cb-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="757cb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="757cb-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="757cb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="757cb-118">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="757cb-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="757cb-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="757cb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757cb-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="757cb-120">See also</span></span>

- [<span data-ttu-id="757cb-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="757cb-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="757cb-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="757cb-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
