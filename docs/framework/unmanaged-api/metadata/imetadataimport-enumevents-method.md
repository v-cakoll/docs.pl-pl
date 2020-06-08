---
title: IMetaDataImport::EnumEvents — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 53b1234a176cade5876d70da0cb4eadc18802c69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492307"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="fabaf-102">IMetaDataImport::EnumEvents — Metoda</span><span class="sxs-lookup"><span data-stu-id="fabaf-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="fabaf-103">Wylicza tokeny definicji zdarzeń dla określonego tokenu TypeDef.</span><span class="sxs-lookup"><span data-stu-id="fabaf-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fabaf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fabaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fabaf-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fabaf-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="fabaf-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="fabaf-107">podczas Token TypeDef, którego definicje zdarzeń mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="fabaf-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="fabaf-108">określoną Tablica zwracanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fabaf-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fabaf-109">podczas Maksymalny rozmiar `rEvents` tablicy.</span><span class="sxs-lookup"><span data-stu-id="fabaf-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="fabaf-110">określoną Rzeczywista liczba zdarzeń zwrócona w `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="fabaf-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fabaf-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fabaf-111">Return Value</span></span>  
  
|<span data-ttu-id="fabaf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fabaf-112">HRESULT</span></span>|<span data-ttu-id="fabaf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fabaf-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fabaf-114">`EnumEvents`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="fabaf-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fabaf-115">Brak zdarzeń do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fabaf-115">There are no events to enumerate.</span></span> <span data-ttu-id="fabaf-116">W takim przypadku `pcEvents` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="fabaf-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fabaf-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fabaf-117">Requirements</span></span>  
 <span data-ttu-id="fabaf-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fabaf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fabaf-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fabaf-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fabaf-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fabaf-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fabaf-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fabaf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabaf-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fabaf-122">See also</span></span>

- [<span data-ttu-id="fabaf-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fabaf-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fabaf-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fabaf-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
