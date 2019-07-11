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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7676c83e8b231606896cb6d1224633b4fa15e725
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777559"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="53c48-102">IMetaDataEmit::DefineNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="53c48-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="53c48-103">Tworzy podpisu metadanych w definicji typu, zwraca `mdTypeDef` tokenu dla tego typu i określa, że typ zdefiniowany jest elementem członkowskim typu odwołuje się `tdEncloser` parametru.</span><span class="sxs-lookup"><span data-stu-id="53c48-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53c48-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="53c48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53c48-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="53c48-106">[in] Nazwa typu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="53c48-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="53c48-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="53c48-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="53c48-108">Jest to z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="53c48-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="53c48-109">[in] Token klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="53c48-109">[in] The token of the base class.</span></span> <span data-ttu-id="53c48-110">Jest to `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="53c48-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="53c48-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="53c48-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="53c48-112">[in] Tablica tokenów, które określają interfejsy, które implementuje tej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="53c48-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="53c48-113">[in] Token typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="53c48-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="53c48-114">Ostatni element tablicy muszą być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="53c48-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="53c48-115">[out] `mdTypeDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="53c48-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53c48-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53c48-116">Requirements</span></span>  
 <span data-ttu-id="53c48-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53c48-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c48-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="53c48-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53c48-119">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53c48-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53c48-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c48-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c48-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53c48-121">See also</span></span>

- [<span data-ttu-id="53c48-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="53c48-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="53c48-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="53c48-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
