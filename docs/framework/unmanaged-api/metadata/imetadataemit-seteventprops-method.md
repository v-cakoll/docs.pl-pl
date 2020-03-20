---
title: IMetaDataEmit::SetEventProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177527"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="a3cc4-102">IMetaDataEmit::SetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3cc4-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="a3cc4-103">Ustawia lub aktualizuje określoną funkcję zdarzenia zdefiniowanego przez wcześniejsze wywołanie [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="a3cc4-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3cc4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3cc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3cc4-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="a3cc4-106">[w] Token zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="a3cc4-107">[w] Flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-107">[in] Event flags.</span></span> <span data-ttu-id="a3cc4-108">Jest to maska `CorEventAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="a3cc4-109">[w] Token dla klasy zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-109">[in] The token for the event class.</span></span> <span data-ttu-id="a3cc4-110">Jest to token `mdTypeDef` lub `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="a3cc4-111">[w] Metoda używana do subskrybowania zdarzenia lub null.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="a3cc4-112">[w] Metoda używana do anulowania subskrypcji zdarzenia lub null.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="a3cc4-113">[w] Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="a3cc4-114">[w] Tablica tokenów dla innych metod skojarzonych ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="a3cc4-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="a3cc4-115">Ostatnim elementem tablicy `mdMethodDefNil`musi być .</span><span class="sxs-lookup"><span data-stu-id="a3cc4-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3cc4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3cc4-116">Requirements</span></span>  
 <span data-ttu-id="a3cc4-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cc4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3cc4-118">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3cc4-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3cc4-119">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3cc4-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3cc4-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3cc4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cc4-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3cc4-121">See also</span></span>

- [<span data-ttu-id="a3cc4-122">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3cc4-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a3cc4-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3cc4-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
