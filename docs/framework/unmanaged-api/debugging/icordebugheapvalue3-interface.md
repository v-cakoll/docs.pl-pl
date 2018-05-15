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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a59d8bce6ae565687e7ed906f6c14332f0c5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="bd89d-102">ICorDebugHeapValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bd89d-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="bd89d-103">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd89d-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="bd89d-104">Ten interfejs stanowi rozszerzenie ICorDebugHeapValue i ICorDebugHeapValue2 interfejsów.</span><span class="sxs-lookup"><span data-stu-id="bd89d-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd89d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bd89d-105">Methods</span></span>  
  
|<span data-ttu-id="bd89d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd89d-106">Method</span></span>|<span data-ttu-id="bd89d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bd89d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd89d-108">GetThreadOwningMonitorLock, metoda</span><span class="sxs-lookup"><span data-stu-id="bd89d-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="bd89d-109">Zwraca zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="bd89d-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="bd89d-110">GetMonitorEventWaitList, metoda</span><span class="sxs-lookup"><span data-stu-id="bd89d-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="bd89d-111">Udostępnia uporządkowaną listę wątków oczekujących w kolejce na zdarzenie, które jest skojarzone z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="bd89d-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd89d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd89d-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd89d-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="bd89d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd89d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd89d-114">Requirements</span></span>  
 <span data-ttu-id="bd89d-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd89d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd89d-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd89d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd89d-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd89d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd89d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd89d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd89d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd89d-119">See Also</span></span>  
 [<span data-ttu-id="bd89d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bd89d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bd89d-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bd89d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
