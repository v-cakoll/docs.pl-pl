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
ms.openlocfilehash: 39e3e71185051435afcf03d51ec62742c080b02a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855712"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="3f4e8-102">IMetaDataImport2::EnumGenericParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f4e8-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="3f4e8-103">Pobiera moduł wyliczający dla tablicy tokenów parametrów ogólnych skojarzonych z określonym tokenem TypeDef lub MethodDef.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f4e8-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f4e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f4e8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3f4e8-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="3f4e8-107">podczas Token TypeDef lub MethodDef, którego parametry ogólne mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="3f4e8-108">określoną Tablica parametrów ogólnych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3f4e8-109">podczas Żądana Maksymalna liczba tokenów do umieszczenia `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="3f4e8-110">określoną Zwrócona liczba tokenów umieszczonych `rGenericParams`w.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f4e8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3f4e8-111">Return Value</span></span>  
  
|<span data-ttu-id="3f4e8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f4e8-112">HRESULT</span></span>|<span data-ttu-id="3f4e8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3f4e8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3f4e8-114">`EnumGenericParams`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3f4e8-115">`phEnum`nie ma elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3f4e8-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="3f4e8-116">W tym przypadku `pcGenericParams` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="3f4e8-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f4e8-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f4e8-117">Requirements</span></span>  
 <span data-ttu-id="3f4e8-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f4e8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f4e8-119">**Nagłówki** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3f4e8-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f4e8-120">**Biblioteki** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3f4e8-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f4e8-121">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f4e8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4e8-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f4e8-122">See also</span></span>

- [<span data-ttu-id="3f4e8-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f4e8-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="3f4e8-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f4e8-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
