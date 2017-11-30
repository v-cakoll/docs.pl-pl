---
title: "IMetaDataImport2::EnumGenericParamConstraints — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParamConstraints
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9afbcae016ce111456588ddbbc9f664dd7e76196
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="9236b-102">IMetaDataImport2::EnumGenericParamConstraints — Metoda</span><span class="sxs-lookup"><span data-stu-id="9236b-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="9236b-103">Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="9236b-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9236b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9236b-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9236b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9236b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9236b-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="9236b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="9236b-107">[in]   Token, który reprezentuje parametru ogólnego ograniczenia, których mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="9236b-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="9236b-108">[out] Tablica ograniczenia parametru ogólnego wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="9236b-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9236b-109">[in]   Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="9236b-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="9236b-110">[out] Wskaźnik do liczby tokenów umieszczone w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="9236b-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9236b-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9236b-111">Return Value</span></span>  
  
|<span data-ttu-id="9236b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9236b-112">HRESULT</span></span>|<span data-ttu-id="9236b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9236b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9236b-114">`EnumGenericParameterConstraints`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9236b-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9236b-115">`phEnum`nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9236b-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="9236b-116">W takim przypadku `pcGenericParameterConstraints` jest równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="9236b-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9236b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9236b-117">Requirements</span></span>  
 <span data-ttu-id="9236b-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9236b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9236b-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9236b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9236b-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9236b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9236b-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9236b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9236b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9236b-122">See Also</span></span>  
 [<span data-ttu-id="9236b-123">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9236b-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="9236b-124">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="9236b-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
