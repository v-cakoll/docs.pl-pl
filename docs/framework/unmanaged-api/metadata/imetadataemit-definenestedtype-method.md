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
ms.openlocfilehash: 5d985e22ba77053127610445374b8c13ca6b97f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431706"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="f3836-102">IMetaDataEmit::DefineNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3836-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="f3836-103">Tworzy sygnaturę metadanych definicji typu, zwraca token `mdTypeDef` dla tego typu i określa, że zdefiniowany typ jest członkiem typu, do którego odwołuje się parametr `tdEncloser`.</span><span class="sxs-lookup"><span data-stu-id="f3836-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3836-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3836-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f3836-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3836-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="f3836-106">podczas Nazwa typu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="f3836-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="f3836-107">[in] `TypeDef` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="f3836-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="f3836-108">To jest maska bitów wartości `CorTypeAttr`.</span><span class="sxs-lookup"><span data-stu-id="f3836-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="f3836-109">podczas Token klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="f3836-109">[in] The token of the base class.</span></span> <span data-ttu-id="f3836-110">Jest to `mdTypeDef` lub token `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="f3836-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="f3836-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="f3836-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="f3836-112">podczas Tablica tokenów, które określają interfejsy, które implementuje Ta klasa lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="f3836-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="f3836-113">podczas Token typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="f3836-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="f3836-114">Ostatni element tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="f3836-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="f3836-115">określoną Przypisany token `mdTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="f3836-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3836-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3836-116">Requirements</span></span>  
 <span data-ttu-id="f3836-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3836-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3836-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3836-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3836-119">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3836-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3836-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3836-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3836-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3836-121">See also</span></span>

- [<span data-ttu-id="f3836-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3836-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f3836-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3836-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
