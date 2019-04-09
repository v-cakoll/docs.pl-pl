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
ms.openlocfilehash: 7edd2eeafcce6a22c3256d0684a9c4f961b34002
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157641"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="cb241-102">IMetaDataImport2::EnumGenericParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb241-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="cb241-103">Pobiera moduł wyliczający dla tablic, tokeny parametrów ogólnych skojarzone z określonego typu lub MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="cb241-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb241-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb241-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb241-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb241-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cb241-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cb241-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="cb241-107">[in] Element TypeDef lub MethodDef token, którego parametrów ogólnych są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb241-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="cb241-108">[out] Tablica parametrów ogólnych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb241-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cb241-109">[in] Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="cb241-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="cb241-110">[out] Zwrócona liczba tokenów umieszczone w `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="cb241-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb241-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cb241-111">Return Value</span></span>  
  
|<span data-ttu-id="cb241-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb241-112">HRESULT</span></span>|<span data-ttu-id="cb241-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cb241-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams` <span data-ttu-id="cb241-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cb241-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="cb241-115">nie ma żadnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="cb241-115">has no member elements.</span></span> <span data-ttu-id="cb241-116">W tym przypadku `pcGenericParams` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="cb241-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb241-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb241-117">Requirements</span></span>  
 <span data-ttu-id="cb241-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb241-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb241-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="cb241-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb241-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb241-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="cb241-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cb241-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb241-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb241-122">See also</span></span>

- [<span data-ttu-id="cb241-123">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cb241-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="cb241-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cb241-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
