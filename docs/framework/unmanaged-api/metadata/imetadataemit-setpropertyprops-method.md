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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 997e43e6a8be1ac2859e7338751272f3074be11d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523133"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="c5f0a-102">IMetaDataEmit::SetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5f0a-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="c5f0a-103">Ustawia funkcje przechowywany w metadanych dla właściwości zdefiniowane przez wcześniejsze wywołanie [defineproperty — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="c5f0a-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5f0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5f0a-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="c5f0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5f0a-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="c5f0a-106">[in] Token dla właściwości, które mają być zmienione</span><span class="sxs-lookup"><span data-stu-id="c5f0a-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="c5f0a-107">[in] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="c5f0a-108">[in] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c5f0a-109">[in] Wartość domyślna dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="c5f0a-110">[in] Liczba (Unicode) znaki w `pValue`.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="c5f0a-111">[in] Metoda, która ustawia wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="c5f0a-112">[in] Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c5f0a-113">[in] Tablica innych metod skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="c5f0a-114">Zakończenie tej tablicy przy użyciu `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="c5f0a-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5f0a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5f0a-115">Requirements</span></span>  
 <span data-ttu-id="c5f0a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5f0a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5f0a-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c5f0a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5f0a-118">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5f0a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5f0a-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5f0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f0a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5f0a-120">See also</span></span>
- [<span data-ttu-id="c5f0a-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5f0a-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c5f0a-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5f0a-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
