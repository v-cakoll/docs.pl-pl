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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2ba46c025c2d031f0526c6a9da5f6ab07023741
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208452"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="cb499-102">IMetaDataImport::EnumEvents — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb499-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="cb499-103">Wylicza tokenów definicji zdarzeń dla określonego tokenu TypeDef.</span><span class="sxs-lookup"><span data-stu-id="cb499-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb499-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb499-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb499-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb499-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cb499-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cb499-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="cb499-107">[in] Token TypeDef, których definicje zdarzeń są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb499-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="cb499-108">[out] Tablica zwrócona zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cb499-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cb499-109">[in] Maksymalny rozmiar `rEvents` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb499-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="cb499-110">[out] Rzeczywista liczba zdarzeń zwróconych w `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="cb499-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb499-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cb499-111">Return Value</span></span>  
  
|<span data-ttu-id="cb499-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb499-112">HRESULT</span></span>|<span data-ttu-id="cb499-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cb499-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cb499-114">`EnumEvents` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cb499-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cb499-115">Brak zdarzeń do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb499-115">There are no events to enumerate.</span></span> <span data-ttu-id="cb499-116">W takim przypadku `pcEvents` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="cb499-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb499-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb499-117">Requirements</span></span>  
 <span data-ttu-id="cb499-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb499-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb499-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="cb499-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb499-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb499-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb499-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb499-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb499-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb499-122">See also</span></span>

- [<span data-ttu-id="cb499-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb499-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cb499-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb499-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
