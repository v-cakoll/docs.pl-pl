---
title: IMetaDataImport2::EnumGenericParams — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ecd1c714f41c76833ef6a0a4b7be87e338ca1a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="cdbbf-102">IMetaDataImport2::EnumGenericParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="cdbbf-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="cdbbf-103">Pobiera moduł wyliczający dla tablicy parametrów ogólnych tokenów skojarzone z określonym TypeDef lub MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbbf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdbbf-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdbbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdbbf-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cdbbf-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="cdbbf-107">[in] Token TypeDef lub MethodDef, którego parametry ogólne mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="cdbbf-108">[out] Tablica parametrów ogólnych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cdbbf-109">[in] Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="cdbbf-110">[out] Zwrócona liczba tokenów umieszczonych w `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdbbf-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdbbf-111">Return Value</span></span>  
  
|<span data-ttu-id="cdbbf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdbbf-112">HRESULT</span></span>|<span data-ttu-id="cdbbf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cdbbf-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cdbbf-114">`EnumGenericParams` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cdbbf-115">`phEnum` nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="cdbbf-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="cdbbf-116">W takim przypadku `pcGenericParams` jest równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="cdbbf-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdbbf-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdbbf-117">Requirements</span></span>  
 <span data-ttu-id="cdbbf-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdbbf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdbbf-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cdbbf-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdbbf-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cdbbf-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdbbf-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbbf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbbf-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdbbf-122">See Also</span></span>  
 [<span data-ttu-id="cdbbf-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdbbf-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="cdbbf-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdbbf-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
