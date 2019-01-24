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
ms.openlocfilehash: 08a9bc8aa4aa70ad6b01c58abccd145ae43d8a52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568299"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="024fe-102">ICorDebugHeapValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="024fe-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="024fe-103">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="024fe-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="024fe-104">Ten interfejs rozszerza ICorDebugHeapValue i icordebugheapvalue2 — interfejsy.</span><span class="sxs-lookup"><span data-stu-id="024fe-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="024fe-105">Metody</span><span class="sxs-lookup"><span data-stu-id="024fe-105">Methods</span></span>  
  
|<span data-ttu-id="024fe-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="024fe-106">Method</span></span>|<span data-ttu-id="024fe-107">Opis</span><span class="sxs-lookup"><span data-stu-id="024fe-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="024fe-108">GetThreadOwningMonitorLock, metoda</span><span class="sxs-lookup"><span data-stu-id="024fe-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="024fe-109">Zwraca wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="024fe-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="024fe-110">GetMonitorEventWaitList, metoda</span><span class="sxs-lookup"><span data-stu-id="024fe-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="024fe-111">Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce na zdarzenia skojarzonego z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="024fe-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="024fe-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="024fe-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="024fe-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="024fe-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="024fe-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="024fe-114">Requirements</span></span>  
 <span data-ttu-id="024fe-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="024fe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="024fe-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="024fe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="024fe-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="024fe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="024fe-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="024fe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024fe-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="024fe-119">See also</span></span>
- [<span data-ttu-id="024fe-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="024fe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="024fe-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="024fe-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
