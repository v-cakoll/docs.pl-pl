---
title: IMetaDataEmit::DefineTypeDef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54691785e3b2619b5f4a2eecc510800b4b5cee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446600"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="5bd4a-102">IMetaDataEmit::DefineTypeDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="5bd4a-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="5bd4a-103">Tworzy definicji typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych dla tej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bd4a-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bd4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bd4a-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="5bd4a-106">[in] Nazwa typu w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5bd4a-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5bd4a-108">To jest maską bitów z `CoreTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5bd4a-109">[in] Token klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-109">[in] The token of the base class.</span></span> <span data-ttu-id="5bd4a-110">Musi to być albo `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="5bd4a-111">[in] Tablica określenie interfejsów, które implementuje w tej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5bd4a-112">[out] `mdTypeDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bd4a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bd4a-113">Remarks</span></span>  
 <span data-ttu-id="5bd4a-114">Flaga w `dwTypeDefFlags` Określa, czy typ tworzony jest wspólnego typu system typu odwołania (klasy lub interfejsu) lub typu wartości system typu wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="5bd4a-115">W zależności od podanych parametrów tej metody jako efekt uboczny może także utworzyć `mdInterfaceImpl` rekordu dla każdego interfejsu, który jest dziedziczone lub zaimplementowany przez tego typu.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="5bd4a-116">Jednak ta metoda nie zwraca żadnego z tych adresów `mdInterfaceImpl` tokenów.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="5bd4a-117">Jeśli klient będzie chciał później dodać lub zmodyfikować `mdInterfaceImpl` tokenów, należy użyć `IMetaDataImport` interfejs do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="5bd4a-118">Jeśli chcesz użyć semantykę COM `[default]` interfejsu, należy określić domyślnego interfejsu jako pierwszy element w `rtkImplements`; atrybut niestandardowy ustawiony dla klasy wskaże, że klasa ma domyślnego interfejsu (który zawsze zakłada się, że najpierw `mdInterfaceImpl` token zadeklarowana w klasie).</span><span class="sxs-lookup"><span data-stu-id="5bd4a-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="5bd4a-119">Każdy element `rtkImplements` tablicy blokad `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="5bd4a-120">Ostatni element w tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="5bd4a-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd4a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5bd4a-121">Requirements</span></span>  
 <span data-ttu-id="5bd4a-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bd4a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd4a-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5bd4a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5bd4a-124">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5bd4a-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bd4a-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd4a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd4a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bd4a-126">See Also</span></span>  
 [<span data-ttu-id="5bd4a-127">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bd4a-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5bd4a-128">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bd4a-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
