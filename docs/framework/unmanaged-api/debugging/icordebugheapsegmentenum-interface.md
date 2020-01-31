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
ms.openlocfilehash: 98e3351c9c86961d11b0985117259d0ff3b609ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794416"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="f08ce-102">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f08ce-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="f08ce-103">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="f08ce-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="f08ce-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f08ce-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f08ce-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f08ce-105">Methods</span></span>  
  
|<span data-ttu-id="f08ce-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f08ce-106">Method</span></span>|<span data-ttu-id="f08ce-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f08ce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f08ce-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="f08ce-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="f08ce-109">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o regionach zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="f08ce-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f08ce-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f08ce-110">Remarks</span></span>  
 <span data-ttu-id="f08ce-111">Interfejs `ICorDebugHeapSegmentEnum` implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f08ce-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f08ce-112">Wystąpienie `ICorDebugHeapSegmentEnum` jest wypełniane wystąpieniami [COR_HEAPOBJECT](cor-heapobject-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateHeapRegions —](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f08ce-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="f08ce-113">[COR_HEAPOBJECT](cor-heapobject-structure.md) obiektów w kolekcji można wyliczyć, wywołując metodę [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f08ce-113">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="f08ce-114">Obiekt kolekcji `ICorDebugHeapSegmentEnum` wylicza wszystkie obszary pamięci, które mogą zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach.</span><span class="sxs-lookup"><span data-stu-id="f08ce-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="f08ce-115">Może zawierać informacje dotyczące pustych lub zarezerwowanych regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f08ce-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f08ce-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f08ce-116">Requirements</span></span>  
 <span data-ttu-id="f08ce-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f08ce-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f08ce-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f08ce-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f08ce-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f08ce-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f08ce-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f08ce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08ce-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f08ce-121">See also</span></span>

- [<span data-ttu-id="f08ce-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f08ce-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
