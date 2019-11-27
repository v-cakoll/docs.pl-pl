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
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450322"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="330c6-102">IMetaDataEmit::SetEventProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="330c6-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="330c6-103">Ustawia lub aktualizuje określoną funkcję zdarzenia zdefiniowaną przez poprzednie wywołanie do [IMetaDataEmit::D efineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="330c6-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="330c6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="330c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="330c6-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="330c6-106">podczas Token zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="330c6-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="330c6-107">podczas Flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="330c6-107">[in] Event flags.</span></span> <span data-ttu-id="330c6-108">To jest maska bitów wartości `CorEventAttr`.</span><span class="sxs-lookup"><span data-stu-id="330c6-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="330c6-109">podczas Token dla klasy Event.</span><span class="sxs-lookup"><span data-stu-id="330c6-109">[in] The token for the event class.</span></span> <span data-ttu-id="330c6-110">Jest to `mdTypeDef` lub token `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="330c6-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="330c6-111">podczas Metoda używana do subskrybowania zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="330c6-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="330c6-112">podczas Metoda używana do anulowania subskrypcji zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="330c6-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="330c6-113">podczas Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="330c6-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="330c6-114">podczas Tablica tokenów dla innych metod skojarzonych ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="330c6-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="330c6-115">Ostatni element tablicy musi być `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="330c6-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330c6-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="330c6-116">Requirements</span></span>  
 <span data-ttu-id="330c6-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="330c6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="330c6-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="330c6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="330c6-119">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="330c6-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="330c6-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="330c6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330c6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="330c6-121">See also</span></span>

- [<span data-ttu-id="330c6-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="330c6-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="330c6-123">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="330c6-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
