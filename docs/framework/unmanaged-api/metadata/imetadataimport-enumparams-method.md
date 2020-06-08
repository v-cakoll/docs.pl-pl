---
title: IMetaDataImport::EnumParams — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: f9a58a70b5264d7f1eb33fb0e09c702c94a13e85
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491770"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="626a5-102">IMetaDataImport::EnumParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="626a5-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="626a5-103">Wylicza tokeny ParamDef reprezentujące parametry metody przywoływanej przez określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="626a5-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="626a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="626a5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="626a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="626a5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="626a5-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="626a5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="626a5-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="626a5-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="626a5-108">podczas Token MethodDef reprezentujący metodę z parametrami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="626a5-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="626a5-109">określoną Tablica służąca do przechowywania tokenów ParamDef.</span><span class="sxs-lookup"><span data-stu-id="626a5-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="626a5-110">podczas Maksymalny rozmiar `rParams` tablicy.</span><span class="sxs-lookup"><span data-stu-id="626a5-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="626a5-111">określoną Liczba tokenów ParamDef zwróconych w `rParams` .</span><span class="sxs-lookup"><span data-stu-id="626a5-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="626a5-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="626a5-112">Return Value</span></span>  
  
|<span data-ttu-id="626a5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="626a5-113">HRESULT</span></span>|<span data-ttu-id="626a5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="626a5-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="626a5-115">`EnumParams`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="626a5-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="626a5-116">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="626a5-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="626a5-117">W takim przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="626a5-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="626a5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="626a5-118">Requirements</span></span>  
 <span data-ttu-id="626a5-119">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="626a5-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="626a5-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="626a5-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="626a5-121">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="626a5-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="626a5-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="626a5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626a5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="626a5-123">See also</span></span>

- [<span data-ttu-id="626a5-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="626a5-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="626a5-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="626a5-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
