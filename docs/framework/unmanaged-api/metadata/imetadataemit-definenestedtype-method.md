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
ms.openlocfilehash: a0d105679a749b8c87099af871bdb42874d440b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="3172d-102">IMetaDataEmit::DefineNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="3172d-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="3172d-103">Tworzy metadane podpis definicji typu, zwraca `mdTypeDef` token dla tego typu, a następnie określa zdefiniowanego typu elementu członkowskiego typu odwołuje się `tdEncloser` parametru.</span><span class="sxs-lookup"><span data-stu-id="3172d-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3172d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3172d-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3172d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3172d-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="3172d-106">[in] Nazwa typu w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="3172d-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="3172d-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3172d-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="3172d-108">To jest maską bitów z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="3172d-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="3172d-109">[in] Token klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3172d-109">[in] The token of the base class.</span></span> <span data-ttu-id="3172d-110">Jest to `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="3172d-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="3172d-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="3172d-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="3172d-112">[in] Tablica określające interfejsów, które implementuje w tej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3172d-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="3172d-113">[in] Token typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="3172d-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="3172d-114">Musi być ostatnim elementem tablicy `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="3172d-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="3172d-115">[out] `mdTypeDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="3172d-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3172d-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3172d-116">Requirements</span></span>  
 <span data-ttu-id="3172d-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3172d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3172d-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3172d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3172d-119">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3172d-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3172d-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3172d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3172d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3172d-121">See Also</span></span>  
 [<span data-ttu-id="3172d-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="3172d-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3172d-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3172d-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
