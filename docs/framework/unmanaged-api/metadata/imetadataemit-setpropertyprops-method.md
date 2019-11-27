---
title: IMetaDataEmit::SetPropertyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: 0fdec87324d6efa0f911e37573093c19b93c0349
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440547"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="73e9b-102">IMetaDataEmit::SetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="73e9b-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="73e9b-103">Ustawia funkcje przechowywane w metadanych dla właściwości zdefiniowanej przez poprzednie wywołanie [metody DefineProperty —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="73e9b-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73e9b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73e9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73e9b-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="73e9b-106">podczas Token dla właściwości, która ma zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="73e9b-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="73e9b-107">podczas Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="73e9b-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="73e9b-108">podczas Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="73e9b-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="73e9b-109">podczas Wartość domyślna właściwości.</span><span class="sxs-lookup"><span data-stu-id="73e9b-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="73e9b-110">podczas Liczba znaków (Unicode) w `pValue`.</span><span class="sxs-lookup"><span data-stu-id="73e9b-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="73e9b-111">podczas Metoda, która ustawia wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="73e9b-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="73e9b-112">podczas Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="73e9b-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="73e9b-113">podczas Tablica innych metod skojarzonych z właściwością.</span><span class="sxs-lookup"><span data-stu-id="73e9b-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="73e9b-114">Przerwij tę tablicę z tokenem `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="73e9b-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73e9b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73e9b-115">Requirements</span></span>  
 <span data-ttu-id="73e9b-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e9b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e9b-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="73e9b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73e9b-118">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73e9b-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73e9b-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e9b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e9b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73e9b-120">See also</span></span>

- [<span data-ttu-id="73e9b-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e9b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="73e9b-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="73e9b-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
