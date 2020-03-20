---
title: IMetaDataEmit::DefineNestedType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175814"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="86d64-102">IMetaDataEmit::DefineNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="86d64-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="86d64-103">Tworzy podpis metadanych definicji typu, zwraca `mdTypeDef` token dla tego typu i określa, że zdefiniowany `tdEncloser` typ jest członkiem typu, do którego odwołuje się parametr.</span><span class="sxs-lookup"><span data-stu-id="86d64-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86d64-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86d64-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="86d64-106">[w] Nazwa typu w Unicode.</span><span class="sxs-lookup"><span data-stu-id="86d64-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="86d64-107">[w] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="86d64-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="86d64-108">Jest to maska `CorTypeAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="86d64-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="86d64-109">[w] Token klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="86d64-109">[in] The token of the base class.</span></span> <span data-ttu-id="86d64-110">Jest to token `mdTypeDef` lub `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="86d64-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="86d64-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="86d64-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="86d64-112">[w] Tablica tokenów, które określają interfejsy, które implementuje ta klasa lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="86d64-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="86d64-113">[w] Token otaczającego typu.</span><span class="sxs-lookup"><span data-stu-id="86d64-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="86d64-114">Ostatnim elementem tablicy `mdTokenNil`musi być .</span><span class="sxs-lookup"><span data-stu-id="86d64-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="86d64-115">[na zewnątrz] Token `mdTypeDef` przypisany.</span><span class="sxs-lookup"><span data-stu-id="86d64-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d64-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86d64-116">Requirements</span></span>  
 <span data-ttu-id="86d64-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d64-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d64-118">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="86d64-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86d64-119">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86d64-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86d64-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d64-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d64-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86d64-121">See also</span></span>

- [<span data-ttu-id="86d64-122">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86d64-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="86d64-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="86d64-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
