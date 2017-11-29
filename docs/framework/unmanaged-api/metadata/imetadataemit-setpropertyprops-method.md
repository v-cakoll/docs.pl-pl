---
title: "IMetaDataEmit::SetPropertyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe79846b9fd576941c706b48a7aed0667c264a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="5b611-102">IMetaDataEmit::SetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b611-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="5b611-103">Ustawia przechowywane w metadanych dla właściwości zdefiniowane przez poprzednie wywołanie funkcji [DefineProperty — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="5b611-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b611-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b611-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="5b611-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b611-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="5b611-106">[in] Token dla właściwości zostanie zmieniony</span><span class="sxs-lookup"><span data-stu-id="5b611-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="5b611-107">[in] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b611-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="5b611-108">[in] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b611-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5b611-109">[in] Wartość domyślna właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b611-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="5b611-110">[in] Liczba (Unicode) znaków `pValue`.</span><span class="sxs-lookup"><span data-stu-id="5b611-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="5b611-111">[in] Metoda, która ustawia wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b611-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="5b611-112">[in] Metoda, która pobiera wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b611-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="5b611-113">[in] Tablica innych metod skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="5b611-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="5b611-114">Przerwanie tej tablicy z `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="5b611-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b611-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b611-115">Requirements</span></span>  
 <span data-ttu-id="5b611-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b611-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b611-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5b611-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b611-118">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b611-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b611-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b611-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b611-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b611-120">See Also</span></span>  
 [<span data-ttu-id="5b611-121">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="5b611-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5b611-122">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="5b611-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
