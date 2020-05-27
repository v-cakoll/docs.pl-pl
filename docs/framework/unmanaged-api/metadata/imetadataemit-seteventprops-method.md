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
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008758"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="6c325-102">IMetaDataEmit::SetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c325-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="6c325-103">Ustawia lub aktualizuje określoną funkcję zdarzenia zdefiniowaną przez poprzednie wywołanie do [IMetaDataEmit::D efineevent](imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="6c325-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c325-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c325-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6c325-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c325-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="6c325-106">podczas Token zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6c325-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="6c325-107">podczas Flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6c325-107">[in] Event flags.</span></span> <span data-ttu-id="6c325-108">To jest maska bitów `CorEventAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="6c325-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="6c325-109">podczas Token dla klasy Event.</span><span class="sxs-lookup"><span data-stu-id="6c325-109">[in] The token for the event class.</span></span> <span data-ttu-id="6c325-110">Jest to albo `mdTypeDef` `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="6c325-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="6c325-111">podczas Metoda używana do subskrybowania zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="6c325-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="6c325-112">podczas Metoda używana do anulowania subskrypcji zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="6c325-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="6c325-113">podczas Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6c325-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="6c325-114">podczas Tablica tokenów dla innych metod skojarzonych ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="6c325-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="6c325-115">Ostatni element tablicy musi być `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="6c325-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c325-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c325-116">Requirements</span></span>  
 <span data-ttu-id="6c325-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c325-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c325-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6c325-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c325-119">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c325-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c325-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c325-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c325-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c325-121">See also</span></span>

- [<span data-ttu-id="6c325-122">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6c325-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6c325-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c325-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
