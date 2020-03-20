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
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175307"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="22321-102">IMetaDataImport2::EnumGenericParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="22321-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="22321-103">Pobiera wyliczenia dla tablicy tokenów parametrów ogólnych skojarzonych z określonym TypeDef lub MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="22321-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22321-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22321-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22321-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22321-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="22321-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="22321-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="22321-107">[w] TypeDef lub MethodDef token, którego parametry ogólne mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="22321-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="22321-108">[na zewnątrz] Tablica parametrów ogólnych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="22321-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="22321-109">[w] Żądana maksymalna liczba tokenów `rGenericParams`do umieszczenia w .</span><span class="sxs-lookup"><span data-stu-id="22321-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="22321-110">[na zewnątrz] Zwrócona liczba tokenów `rGenericParams`umieszczonych w .</span><span class="sxs-lookup"><span data-stu-id="22321-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22321-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="22321-111">Return Value</span></span>  
  
|<span data-ttu-id="22321-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22321-112">HRESULT</span></span>|<span data-ttu-id="22321-113">Opis</span><span class="sxs-lookup"><span data-stu-id="22321-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="22321-114">`EnumGenericParams`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="22321-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="22321-115">`phEnum`nie ma elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="22321-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="22321-116">W takim `pcGenericParams` przypadku jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="22321-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22321-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22321-117">Requirements</span></span>  
 <span data-ttu-id="22321-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22321-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22321-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="22321-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22321-120">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22321-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22321-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22321-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22321-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22321-122">See also</span></span>

- [<span data-ttu-id="22321-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="22321-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="22321-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="22321-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
