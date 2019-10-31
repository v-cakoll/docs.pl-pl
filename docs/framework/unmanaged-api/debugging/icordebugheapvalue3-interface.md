---
title: ICorDebugHeapValue3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: b062faffc22e444bd4d3b4a0c67f2a08d7af3560
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131105"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="96aa3-102">ICorDebugHeapValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96aa3-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="96aa3-103">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="96aa3-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="96aa3-104">Ten interfejs rozszerza interfejsy ICorDebugHeapValue i ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="96aa3-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96aa3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="96aa3-105">Methods</span></span>  
  
|<span data-ttu-id="96aa3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="96aa3-106">Method</span></span>|<span data-ttu-id="96aa3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="96aa3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96aa3-108">GetThreadOwningMonitorLock, metoda</span><span class="sxs-lookup"><span data-stu-id="96aa3-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="96aa3-109">Zwraca zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="96aa3-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="96aa3-110">GetMonitorEventWaitList, metoda</span><span class="sxs-lookup"><span data-stu-id="96aa3-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="96aa3-111">Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce dla zdarzenia, które jest skojarzone z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="96aa3-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96aa3-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96aa3-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96aa3-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="96aa3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96aa3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96aa3-114">Requirements</span></span>  
 <span data-ttu-id="96aa3-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96aa3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96aa3-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96aa3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96aa3-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96aa3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96aa3-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96aa3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96aa3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96aa3-119">See also</span></span>

- [<span data-ttu-id="96aa3-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="96aa3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="96aa3-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="96aa3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
