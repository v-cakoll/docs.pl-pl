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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1159e91004152b6c1393b87f25ff7964456adffc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498227"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="bfd94-102">IMetaDataEmit::SetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="bfd94-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="bfd94-103">Ustawia lub aktualizuje określoną funkcję zdarzenie zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfd94-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfd94-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="bfd94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfd94-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="bfd94-106">[in] Token zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bfd94-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="bfd94-107">[in] Flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bfd94-107">[in] Event flags.</span></span> <span data-ttu-id="bfd94-108">Jest to z `CorEventAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="bfd94-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="bfd94-109">[in] Token dla klasy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bfd94-109">[in] The token for the event class.</span></span> <span data-ttu-id="bfd94-110">Jest to `mdTypeDef` lub `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="bfd94-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="bfd94-111">[in] Metoda używana do subskrybowania zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="bfd94-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="bfd94-112">[in] Metoda użyta Aby anulować subskrypcję zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="bfd94-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="bfd94-113">[in] Metoda używana (przez klasę pochodną), aby zgłosić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bfd94-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="bfd94-114">[in] Tablica do innych metod, skojarzone ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="bfd94-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="bfd94-115">Ostatni element tablicy muszą być `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="bfd94-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfd94-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfd94-116">Requirements</span></span>  
 <span data-ttu-id="bfd94-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfd94-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd94-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bfd94-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfd94-119">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bfd94-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfd94-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfd94-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd94-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfd94-121">See also</span></span>
- [<span data-ttu-id="bfd94-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfd94-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bfd94-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfd94-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
