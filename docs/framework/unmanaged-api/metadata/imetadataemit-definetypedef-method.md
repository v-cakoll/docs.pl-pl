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
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175762"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="a6359-102">IMetaDataEmit::DefineTypeDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6359-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="a6359-103">Tworzy definicję typu dla wspólnego typu środowiska uruchomieniowego języka i pobiera token metadanych dla tej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="a6359-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6359-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6359-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6359-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6359-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="a6359-106">[w] Nazwa typu w Unicode.</span><span class="sxs-lookup"><span data-stu-id="a6359-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="a6359-107">[w] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a6359-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="a6359-108">Jest to maska `CoreTypeAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="a6359-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="a6359-109">[w] Token klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a6359-109">[in] The token of the base class.</span></span> <span data-ttu-id="a6359-110">Musi to być `mdTypeDef` token `mdTypeRef` lub token.</span><span class="sxs-lookup"><span data-stu-id="a6359-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="a6359-111">[w] Tablica tokenów określających interfejsy, które implementuje ta klasa lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="a6359-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="a6359-112">[na zewnątrz] Token `mdTypeDef` przypisany.</span><span class="sxs-lookup"><span data-stu-id="a6359-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6359-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6359-113">Remarks</span></span>  
 <span data-ttu-id="a6359-114">Flaga `dwTypeDefFlags` w określa, czy tworzony typ jest typem odwołania do systemu typu typ (klasa lub interfejs) lub typem wartości systemu typu wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a6359-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="a6359-115">W zależności od dostarczonych parametrów ta metoda, jako `mdInterfaceImpl` efekt uboczny, może również utworzyć rekord dla każdego interfejsu, który jest dziedziczony lub implementowany przez ten typ.</span><span class="sxs-lookup"><span data-stu-id="a6359-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="a6359-116">Jednak ta metoda nie zwraca `mdInterfaceImpl` żadnego z tych tokenów.</span><span class="sxs-lookup"><span data-stu-id="a6359-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="a6359-117">Jeśli klient chce później dodać lub `mdInterfaceImpl` zmodyfikować token, `IMetaDataImport` musi użyć interfejsu, aby je wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="a6359-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="a6359-118">Jeśli chcesz użyć semantyki COM `[default]` interfejsu, należy podać domyślny interfejs jako `rtkImplements`pierwszy element w ; atrybut niestandardowy ustawiony w klasie wskazuje, że klasa ma domyślny interfejs (który jest zawsze zakłada się, że jest pierwszym `mdInterfaceImpl` tokenem zadeklarowanym dla klasy).</span><span class="sxs-lookup"><span data-stu-id="a6359-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="a6359-119">Każdy element `rtkImplements` tablicy `mdTypeDef` zawiera `mdTypeRef` lub token.</span><span class="sxs-lookup"><span data-stu-id="a6359-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="a6359-120">Ostatnim elementem w tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="a6359-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6359-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6359-121">Requirements</span></span>  
 <span data-ttu-id="a6359-122">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6359-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6359-123">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6359-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6359-124">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6359-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6359-125">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6359-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6359-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6359-126">See also</span></span>

- [<span data-ttu-id="a6359-127">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a6359-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a6359-128">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6359-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
