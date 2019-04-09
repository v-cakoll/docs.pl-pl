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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f66b0145dbaece7292d2ccad169a97fbb10b6d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186685"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="813d2-102">IMetaDataImport2::EnumGenericParamConstraints — Metoda</span><span class="sxs-lookup"><span data-stu-id="813d2-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="813d2-103">Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="813d2-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="813d2-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="813d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="813d2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="813d2-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="813d2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="813d2-107">[in]   Token, który reprezentuje parametr ogólny, z którego ograniczenia są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="813d2-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="813d2-108">[out] Tablica ograniczenia parametru ogólnego do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="813d2-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="813d2-109">[in]   Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="813d2-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="813d2-110">[out] Wskaźnik do liczby tokenów umieszczone w `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="813d2-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="813d2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="813d2-111">Return Value</span></span>  
  
|<span data-ttu-id="813d2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="813d2-112">HRESULT</span></span>|<span data-ttu-id="813d2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="813d2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` <span data-ttu-id="813d2-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="813d2-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="813d2-115">nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="813d2-115">has no member elements.</span></span> <span data-ttu-id="813d2-116">W tym przypadku `pcGenericParameterConstraints` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="813d2-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="813d2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="813d2-117">Requirements</span></span>  
 <span data-ttu-id="813d2-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="813d2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="813d2-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="813d2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="813d2-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="813d2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="813d2-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="813d2-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="813d2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="813d2-122">See also</span></span>

- [<span data-ttu-id="813d2-123">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="813d2-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="813d2-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="813d2-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
