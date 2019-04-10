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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208452"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="a3806-102">IMetaDataImport::EnumEvents — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3806-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="a3806-103">Wylicza tokenów definicji zdarzeń dla określonego tokenu TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a3806-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3806-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3806-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3806-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3806-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a3806-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a3806-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="a3806-107">[in] Token TypeDef, których definicje zdarzeń są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a3806-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="a3806-108">[out] Tablica zwrócona zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3806-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a3806-109">[in] Maksymalny rozmiar `rEvents` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a3806-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="a3806-110">[out] Rzeczywista liczba zdarzeń zwróconych w `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="a3806-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3806-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3806-111">Return Value</span></span>  
  
|<span data-ttu-id="a3806-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3806-112">HRESULT</span></span>|<span data-ttu-id="a3806-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a3806-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumEvents` <span data-ttu-id="a3806-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a3806-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a3806-115">Brak zdarzeń do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a3806-115">There are no events to enumerate.</span></span> <span data-ttu-id="a3806-116">W takim przypadku `pcEvents` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="a3806-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3806-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3806-117">Requirements</span></span>  
 <span data-ttu-id="a3806-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3806-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3806-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a3806-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3806-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3806-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a3806-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a3806-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a3806-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3806-122">See also</span></span>

- [<span data-ttu-id="a3806-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3806-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a3806-124">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3806-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
