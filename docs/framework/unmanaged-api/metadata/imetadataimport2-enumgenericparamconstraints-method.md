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
ms.workload: dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="3c465-102">IMetaDataImport2::EnumGenericParamConstraints — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c465-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="3c465-103">Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="3c465-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c465-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c465-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c465-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3c465-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3c465-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="3c465-107">[in]   Token, który reprezentuje parametru ogólnego ograniczenia, których mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="3c465-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="3c465-108">[out] Tablica ograniczenia parametru ogólnego wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="3c465-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3c465-109">[in]   Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="3c465-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="3c465-110">[out] Wskaźnik do liczby tokenów umieszczone w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="3c465-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c465-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c465-111">Return Value</span></span>  
  
|<span data-ttu-id="3c465-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c465-112">HRESULT</span></span>|<span data-ttu-id="3c465-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3c465-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3c465-114">`EnumGenericParameterConstraints`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3c465-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3c465-115">`phEnum`nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3c465-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="3c465-116">W takim przypadku `pcGenericParameterConstraints` jest równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="3c465-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c465-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c465-117">Requirements</span></span>  
 <span data-ttu-id="3c465-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c465-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c465-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3c465-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c465-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c465-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c465-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c465-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c465-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c465-122">See Also</span></span>  
 [<span data-ttu-id="3c465-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c465-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="3c465-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c465-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
