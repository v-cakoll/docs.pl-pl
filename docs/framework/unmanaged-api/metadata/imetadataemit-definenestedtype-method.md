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
ms.openlocfilehash: 2b24c2ca6907dfdb63ad934ec30557c246db174c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004359"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="681e3-102">IMetaDataEmit::DefineNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="681e3-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="681e3-103">Tworzy sygnaturę metadanych definicji typu, zwraca `mdTypeDef` token dla tego typu i określa, że zdefiniowany typ jest składową typu, do którego odwołuje się `tdEncloser` parametr.</span><span class="sxs-lookup"><span data-stu-id="681e3-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="681e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="681e3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="681e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="681e3-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="681e3-106">podczas Nazwa typu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="681e3-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="681e3-107">[w] `TypeDef` Attributes.</span><span class="sxs-lookup"><span data-stu-id="681e3-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="681e3-108">To jest maska bitów `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="681e3-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="681e3-109">podczas Token klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="681e3-109">[in] The token of the base class.</span></span> <span data-ttu-id="681e3-110">Jest to albo `mdTypeDef` `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="681e3-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="681e3-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="681e3-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="681e3-112">podczas Tablica tokenów, które określają interfejsy, które implementuje Ta klasa lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="681e3-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="681e3-113">podczas Token typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="681e3-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="681e3-114">Ostatni element tablicy musi być `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="681e3-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="681e3-115">określoną `mdTypeDef`Przypisany token.</span><span class="sxs-lookup"><span data-stu-id="681e3-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="681e3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="681e3-116">Requirements</span></span>  
 <span data-ttu-id="681e3-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="681e3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681e3-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="681e3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="681e3-119">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="681e3-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="681e3-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681e3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681e3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="681e3-121">See also</span></span>

- [<span data-ttu-id="681e3-122">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="681e3-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="681e3-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="681e3-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
