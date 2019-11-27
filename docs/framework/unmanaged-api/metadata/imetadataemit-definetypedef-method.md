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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450217"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="edc7f-102">IMetaDataEmit::DefineTypeDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="edc7f-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="edc7f-103">Tworzy definicję typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych dla tej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="edc7f-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edc7f-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edc7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edc7f-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="edc7f-106">podczas Nazwa typu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="edc7f-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="edc7f-107">[in] `TypeDef` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="edc7f-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="edc7f-108">To jest maska bitów wartości `CoreTypeAttr`.</span><span class="sxs-lookup"><span data-stu-id="edc7f-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="edc7f-109">podczas Token klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="edc7f-109">[in] The token of the base class.</span></span> <span data-ttu-id="edc7f-110">Musi to być `mdTypeDef` lub token `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="edc7f-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="edc7f-111">podczas Tablica tokenów określająca interfejsy, które implementuje Ta klasa lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="edc7f-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="edc7f-112">określoną Przypisany token `mdTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="edc7f-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edc7f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edc7f-113">Remarks</span></span>  
 <span data-ttu-id="edc7f-114">Flaga w `dwTypeDefFlags` określa, czy tworzony typ jest typem referencyjnym systemu typu wspólnego (Class lub Interface) czy typem wartości typu wspólnego systemu.</span><span class="sxs-lookup"><span data-stu-id="edc7f-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="edc7f-115">W zależności od dostarczonych parametrów, ta metoda jako efekt uboczny może również utworzyć rekord `mdInterfaceImpl` dla każdego interfejsu, który jest dziedziczony lub zaimplementowany przez ten typ.</span><span class="sxs-lookup"><span data-stu-id="edc7f-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="edc7f-116">Jednak ta metoda nie zwraca żadnego z tych tokenów `mdInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="edc7f-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="edc7f-117">Jeśli klient chce później dodać lub zmodyfikować token `mdInterfaceImpl`, musi użyć interfejsu `IMetaDataImport`, aby je wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="edc7f-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="edc7f-118">Jeśli chcesz używać semantyki COM interfejsu `[default]`, należy podać domyślny interfejs jako pierwszy element w `rtkImplements`; niestandardowy atrybut ustawiony dla klasy wskazuje, że Klasa ma interfejs domyślny (który zawsze przyjmuje się, że jest to pierwszy token `mdInterfaceImpl` zadeklarowany dla klasy).</span><span class="sxs-lookup"><span data-stu-id="edc7f-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="edc7f-119">Każdy element tablicy `rtkImplements` zawiera token `mdTypeDef` lub `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="edc7f-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="edc7f-120">Ostatni element w tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="edc7f-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edc7f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edc7f-121">Requirements</span></span>  
 <span data-ttu-id="edc7f-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edc7f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edc7f-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="edc7f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edc7f-124">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="edc7f-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edc7f-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edc7f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc7f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edc7f-126">See also</span></span>

- [<span data-ttu-id="edc7f-127">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="edc7f-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="edc7f-128">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="edc7f-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
