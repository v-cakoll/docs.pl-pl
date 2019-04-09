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
ms.openlocfilehash: 9b6f5881f289bed258191baf4f43264ea6ba35db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141807"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="0ade7-102">IMetaDataEmit::DefineTypeDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ade7-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="0ade7-103">Tworzy definicję typu na typ środowiska uruchomieniowego języka wspólnego, a następnie pobiera token metadanych dla tej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="0ade7-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ade7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ade7-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ade7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ade7-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="0ade7-106">[in] Nazwa typu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="0ade7-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="0ade7-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0ade7-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="0ade7-108">Jest to z `CoreTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="0ade7-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="0ade7-109">[in] Token klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="0ade7-109">[in] The token of the base class.</span></span> <span data-ttu-id="0ade7-110">Musi być albo `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="0ade7-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="0ade7-111">[in] Tablica Określanie interfejsy, które implementuje tej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0ade7-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0ade7-112">[out] `mdTypeDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="0ade7-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ade7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ade7-113">Remarks</span></span>  
 <span data-ttu-id="0ade7-114">Flaga w `dwTypeDefFlags` Określa, czy typ tworzona jest wspólnego typu systemu typu odwołania (klasę lub interfejs) lub typu wartościowego system typu wspólnego.</span><span class="sxs-lookup"><span data-stu-id="0ade7-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="0ade7-115">W zależności od podanych parametrów tej metody jako efekt uboczny może również utworzyć `mdInterfaceImpl` rekordów dla każdego interfejsu, który jest dziedziczony lub zaimplementować według tego typu.</span><span class="sxs-lookup"><span data-stu-id="0ade7-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="0ade7-116">Jednak ta metoda nie zwraca żadnego z tych `mdInterfaceImpl` tokenów.</span><span class="sxs-lookup"><span data-stu-id="0ade7-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="0ade7-117">Jeśli klient chce, aby później dodać lub zmodyfikować `mdInterfaceImpl` tokenów, należy użyć `IMetaDataImport` interfejs do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0ade7-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="0ade7-118">Jeśli chcesz używać COM bezpośrednio z semantyki `[default]` interfejsu, należy podać domyślny interfejs jako pierwszego elementu w `rtkImplements`; atrybutu niestandardowego, ustaw klasy wskaże, że klasa ma domyślnego interfejsu (który jest zawsze zakłada się, że najpierw `mdInterfaceImpl` token zadeklarowana w klasie).</span><span class="sxs-lookup"><span data-stu-id="0ade7-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="0ade7-119">Każdy element obiektu `rtkImplements` tablica zawierająca `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="0ade7-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="0ade7-120">Po ostatnim elemencie w tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="0ade7-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ade7-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ade7-121">Requirements</span></span>  
 <span data-ttu-id="0ade7-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ade7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ade7-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0ade7-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ade7-124">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ade7-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0ade7-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0ade7-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0ade7-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ade7-126">See also</span></span>

- [<span data-ttu-id="0ade7-127">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ade7-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0ade7-128">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ade7-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
