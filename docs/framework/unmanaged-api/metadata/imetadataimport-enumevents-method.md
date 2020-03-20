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
ms.openlocfilehash: bd50d63b1f7080f510c29f90979b7b36242af1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177371"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="06edb-102">IMetaDataImport::EnumEvents — Metoda</span><span class="sxs-lookup"><span data-stu-id="06edb-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="06edb-103">Wylicza tokeny definicji zdarzeń dla określonego tokenu TypeDef.</span><span class="sxs-lookup"><span data-stu-id="06edb-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06edb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06edb-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06edb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06edb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="06edb-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="06edb-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="06edb-107">[w] TypeDef token, którego definicje zdarzeń mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="06edb-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="06edb-108">[na zewnątrz] Tablica zwróconych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="06edb-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="06edb-109">[w] Maksymalny rozmiar `rEvents` tablicy.</span><span class="sxs-lookup"><span data-stu-id="06edb-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="06edb-110">[na zewnątrz] Rzeczywista liczba zdarzeń `rEvents`zwróconych w .</span><span class="sxs-lookup"><span data-stu-id="06edb-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06edb-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="06edb-111">Return Value</span></span>  
  
|<span data-ttu-id="06edb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06edb-112">HRESULT</span></span>|<span data-ttu-id="06edb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="06edb-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="06edb-114">`EnumEvents`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="06edb-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="06edb-115">Nie ma żadnych zdarzeń do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="06edb-115">There are no events to enumerate.</span></span> <span data-ttu-id="06edb-116">W takim `pcEvents` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="06edb-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06edb-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06edb-117">Requirements</span></span>  
 <span data-ttu-id="06edb-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06edb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06edb-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="06edb-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06edb-120">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06edb-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06edb-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06edb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06edb-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06edb-122">See also</span></span>

- [<span data-ttu-id="06edb-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06edb-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="06edb-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="06edb-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
