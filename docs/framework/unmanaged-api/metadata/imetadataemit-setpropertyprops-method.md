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
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177475"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="7c46d-102">IMetaDataEmit::SetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c46d-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="7c46d-103">Ustawia obiekty przechowywane w metadanych dla właściwości zdefiniowanej przez wcześniejsze [wywołanie metody DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="7c46d-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c46d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c46d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7c46d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c46d-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="7c46d-106">[w] Token dla właściwości, która ma zostać zmieniona</span><span class="sxs-lookup"><span data-stu-id="7c46d-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="7c46d-107">[w] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c46d-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7c46d-108">[w] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c46d-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7c46d-109">[w] Wartość domyślna właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c46d-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7c46d-110">[w] Liczba znaków (Unicode) `pValue`w pliku .</span><span class="sxs-lookup"><span data-stu-id="7c46d-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="7c46d-111">[w] Metoda, która ustawia wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c46d-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="7c46d-112">[w] Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c46d-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="7c46d-113">[w] Tablica innych metod skojarzonych z właściwością.</span><span class="sxs-lookup"><span data-stu-id="7c46d-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="7c46d-114">Zakończ tę tablicę `mdTokenNil` za pomocą tokenu.</span><span class="sxs-lookup"><span data-stu-id="7c46d-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c46d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c46d-115">Requirements</span></span>  
 <span data-ttu-id="7c46d-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c46d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c46d-117">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c46d-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c46d-118">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c46d-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c46d-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c46d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c46d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c46d-120">See also</span></span>

- [<span data-ttu-id="7c46d-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7c46d-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7c46d-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c46d-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
