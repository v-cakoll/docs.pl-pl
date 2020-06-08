---
title: IMetaDataImport::EnumCustomAttributes — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 9b0da8a06259fe99da52497da3011da94289d301
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492333"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="03876-102">IMetaDataImport::EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="03876-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="03876-103">Wylicza niestandardowe tokeny definicji atrybutów skojarzone z określonym typem lub członkiem.</span><span class="sxs-lookup"><span data-stu-id="03876-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03876-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03876-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03876-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03876-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="03876-106">[in. out] Wskaźnik do zwróconego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="03876-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="03876-107">podczas Token dla zakresu wyliczenia lub zero dla wszystkich atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="03876-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="03876-108">podczas Token dla konstruktora typu atrybutów do wyliczenia lub `null` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="03876-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="03876-109">określoną Tablica tokenów atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="03876-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="03876-110">podczas Maksymalny rozmiar `rCustomAttributes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="03876-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="03876-111">[out, opcjonalne] Rzeczywista liczba zwracanych wartości tokenu `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="03876-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03876-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03876-112">Return Value</span></span>  
  
|<span data-ttu-id="03876-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03876-113">HRESULT</span></span>|<span data-ttu-id="03876-114">Opis</span><span class="sxs-lookup"><span data-stu-id="03876-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="03876-115">`EnumCustomAttributes`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="03876-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="03876-116">Brak atrybutów niestandardowych do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="03876-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="03876-117">W takim przypadku `pcCustomAttributes` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="03876-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03876-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03876-118">Requirements</span></span>  
 <span data-ttu-id="03876-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03876-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03876-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="03876-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03876-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03876-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03876-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03876-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03876-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03876-123">See also</span></span>

- [<span data-ttu-id="03876-124">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03876-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="03876-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03876-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
