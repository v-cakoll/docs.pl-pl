---
title: ICorDebugHeapSegmentEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: acf490895db35af1c5d0d1e7fe7e3de5ae2a16b6
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904289"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="94bd1-102">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="94bd1-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="94bd1-103">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="94bd1-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="94bd1-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="94bd1-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94bd1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="94bd1-105">Methods</span></span>  
  
|<span data-ttu-id="94bd1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="94bd1-106">Method</span></span>|<span data-ttu-id="94bd1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="94bd1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94bd1-108">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="94bd1-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="94bd1-109">Pobiera określoną liczbę wystąpień [COR_SEGMENT](cor-segment-structure.md) , które zawierają informacje o regionach zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="94bd1-109">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94bd1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94bd1-110">Remarks</span></span>  
 <span data-ttu-id="94bd1-111">`ICorDebugHeapSegmentEnum`Interfejs implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="94bd1-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="94bd1-112">`ICorDebugHeapSegmentEnum`Wystąpienie jest wypełniane wystąpieniami [COR_SEGMENT](cor-segment-structure.md) , wywołując metodę [ICorDebugProcess5:: EnumerateHeapRegions —](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="94bd1-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="94bd1-113">[COR_SEGMENT](cor-segment-structure.md) obiektów w kolekcji można wyliczyć, wywołując metodę [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="94bd1-113">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="94bd1-114">`ICorDebugHeapSegmentEnum`Obiekt kolekcji wylicza wszystkie obszary pamięci, które mogą zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach.</span><span class="sxs-lookup"><span data-stu-id="94bd1-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="94bd1-115">Może zawierać informacje dotyczące pustych lub zarezerwowanych regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="94bd1-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94bd1-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94bd1-116">Requirements</span></span>  
 <span data-ttu-id="94bd1-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94bd1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94bd1-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94bd1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94bd1-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="94bd1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94bd1-120">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94bd1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bd1-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94bd1-121">See also</span></span>

- [<span data-ttu-id="94bd1-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="94bd1-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
