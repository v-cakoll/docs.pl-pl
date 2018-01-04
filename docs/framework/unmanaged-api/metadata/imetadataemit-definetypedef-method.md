---
title: "IMetaDataEmit::DefineTypeDef — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="37051-102">IMetaDataEmit::DefineTypeDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="37051-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="37051-103">Tworzy definicji typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych dla tej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="37051-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37051-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37051-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37051-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37051-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="37051-106">[in] Nazwa typu w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="37051-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="37051-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="37051-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="37051-108">To jest maską bitów z `CoreTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="37051-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="37051-109">[in] Token klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="37051-109">[in] The token of the base class.</span></span> <span data-ttu-id="37051-110">Musi to być albo `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="37051-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="37051-111">[in] Tablica określenie interfejsów, które implementuje w tej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="37051-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="37051-112">[out] `mdTypeDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="37051-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37051-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37051-113">Remarks</span></span>  
 <span data-ttu-id="37051-114">Flaga w `dwTypeDefFlags` Określa, czy typ tworzony jest wspólnego typu system typu odwołania (klasy lub interfejsu) lub typu wartości system typu wspólnego.</span><span class="sxs-lookup"><span data-stu-id="37051-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="37051-115">W zależności od podanych parametrów tej metody jako efekt uboczny może także utworzyć `mdInterfaceImpl` rekordu dla każdego interfejsu, który jest dziedziczone lub zaimplementowany przez tego typu.</span><span class="sxs-lookup"><span data-stu-id="37051-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="37051-116">Jednak ta metoda nie zwraca żadnego z tych adresów `mdInterfaceImpl` tokenów.</span><span class="sxs-lookup"><span data-stu-id="37051-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="37051-117">Jeśli klient będzie chciał później dodać lub zmodyfikować `mdInterfaceImpl` tokenów, należy użyć `IMetaDataImport` interfejs do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="37051-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="37051-118">Jeśli chcesz użyć semantykę COM `[default]` interfejsu, należy określić domyślnego interfejsu jako pierwszy element w `rtkImplements`; atrybut niestandardowy ustawiony dla klasy wskaże, że klasa ma domyślnego interfejsu (który zawsze zakłada się, że najpierw `mdInterfaceImpl` token zadeklarowana w klasie).</span><span class="sxs-lookup"><span data-stu-id="37051-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="37051-119">Każdy element `rtkImplements` tablicy blokad `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="37051-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="37051-120">Ostatni element w tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="37051-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37051-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37051-121">Requirements</span></span>  
 <span data-ttu-id="37051-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37051-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37051-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37051-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37051-124">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37051-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37051-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37051-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37051-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37051-126">See Also</span></span>  
 [<span data-ttu-id="37051-127">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="37051-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="37051-128">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="37051-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
