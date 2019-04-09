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
ms.openlocfilehash: 4ebd4e9beca315ef8284c915800afec6bdb78c78
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183238"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="6a688-102">IMetaDataEmit::DefineNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a688-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="6a688-103">Tworzy podpisu metadanych w definicji typu, zwraca `mdTypeDef` tokenu dla tego typu i określa, że typ zdefiniowany jest elementem członkowskim typu odwołuje się `tdEncloser` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a688-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a688-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a688-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6a688-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a688-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="6a688-106">[in] Nazwa typu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="6a688-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6a688-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6a688-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6a688-108">Jest to z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="6a688-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6a688-109">[in] Token klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6a688-109">[in] The token of the base class.</span></span> <span data-ttu-id="6a688-110">Jest to `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="6a688-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `rtkImplements`<span data-ttu-id="6a688-111">[]</span><span class="sxs-lookup"><span data-stu-id="6a688-111">[]</span></span>  
 <span data-ttu-id="6a688-112">[in] Tablica tokenów, które określają interfejsy, które implementuje tej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6a688-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="6a688-113">[in] Token typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="6a688-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="6a688-114">Ostatni element tablicy muszą być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="6a688-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="6a688-115">[out] `mdTypeDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="6a688-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a688-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a688-116">Requirements</span></span>  
 <span data-ttu-id="6a688-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a688-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a688-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6a688-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a688-119">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a688-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6a688-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6a688-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a688-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a688-121">See also</span></span>

- [<span data-ttu-id="6a688-122">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6a688-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6a688-123">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6a688-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
