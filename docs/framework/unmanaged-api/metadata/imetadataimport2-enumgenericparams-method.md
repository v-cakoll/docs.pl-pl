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
ms.openlocfilehash: 093e3edf0a3c06222ebc56a4876fca08d1b7578f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490732"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="345dc-102">IMetaDataImport2::EnumGenericParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="345dc-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="345dc-103">Pobiera moduł wyliczający dla tablicy tokenów parametrów ogólnych skojarzonych z określonym tokenem TypeDef lub MethodDef.</span><span class="sxs-lookup"><span data-stu-id="345dc-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="345dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="345dc-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="345dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="345dc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="345dc-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="345dc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="345dc-107">podczas Token TypeDef lub MethodDef, którego parametry ogólne mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="345dc-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="345dc-108">określoną Tablica parametrów ogólnych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="345dc-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="345dc-109">podczas Żądana Maksymalna liczba tokenów do umieszczenia `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="345dc-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="345dc-110">określoną Zwrócona liczba tokenów umieszczonych w `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="345dc-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="345dc-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="345dc-111">Return Value</span></span>  
  
|<span data-ttu-id="345dc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="345dc-112">HRESULT</span></span>|<span data-ttu-id="345dc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="345dc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="345dc-114">`EnumGenericParams`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="345dc-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="345dc-115">`phEnum`nie ma elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="345dc-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="345dc-116">W tym przypadku `pcGenericParams` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="345dc-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="345dc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="345dc-117">Requirements</span></span>  
 <span data-ttu-id="345dc-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="345dc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="345dc-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="345dc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="345dc-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="345dc-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="345dc-121">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="345dc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345dc-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="345dc-122">See also</span></span>

- [<span data-ttu-id="345dc-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="345dc-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="345dc-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="345dc-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
