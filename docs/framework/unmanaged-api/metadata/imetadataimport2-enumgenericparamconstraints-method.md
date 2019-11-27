---
title: IMetaDataImport2::EnumGenericParamConstraints — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: d1683965193801dbdee038ab06366178891fd978
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426723"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="33214-102">IMetaDataImport2::EnumGenericParamConstraints — Metoda</span><span class="sxs-lookup"><span data-stu-id="33214-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="33214-103">Pobiera moduł wyliczający dla tablicy ograniczeń parametrów ogólnych skojarzonych z parametrem ogólnym reprezentowanym przez określony token.</span><span class="sxs-lookup"><span data-stu-id="33214-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33214-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33214-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33214-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33214-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="33214-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="33214-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="33214-107">podczas   Token reprezentujący parametr generyczny, którego ograniczenia mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="33214-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="33214-108">określoną Tablica ograniczeń parametrów ogólnych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="33214-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="33214-109">podczas   Żądana Maksymalna liczba tokenów do umieszczenia w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="33214-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="33214-110">określoną Wskaźnik do liczby tokenów umieszczonych w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="33214-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33214-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33214-111">Return Value</span></span>  
  
|<span data-ttu-id="33214-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33214-112">HRESULT</span></span>|<span data-ttu-id="33214-113">Opis</span><span class="sxs-lookup"><span data-stu-id="33214-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="33214-114">`EnumGenericParameterConstraints` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="33214-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="33214-115">`phEnum` nie ma elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="33214-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="33214-116">W tym przypadku `pcGenericParameterConstraints` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="33214-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33214-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33214-117">Requirements</span></span>  
 <span data-ttu-id="33214-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33214-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33214-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="33214-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33214-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="33214-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33214-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33214-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33214-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33214-122">See also</span></span>

- [<span data-ttu-id="33214-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="33214-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="33214-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="33214-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
