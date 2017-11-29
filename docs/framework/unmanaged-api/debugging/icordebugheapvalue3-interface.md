---
title: "ICorDebugHeapValue3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3
helpviewer_keywords: ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5531689a3a4ba66fddfc98cadec7dc8d51c8629a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="2c4ca-102">ICorDebugHeapValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2c4ca-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="2c4ca-103">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="2c4ca-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="2c4ca-104">Ten interfejs stanowi rozszerzenie ICorDebugHeapValue i ICorDebugHeapValue2 interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2c4ca-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c4ca-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2c4ca-105">Methods</span></span>  
  
|<span data-ttu-id="2c4ca-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2c4ca-106">Method</span></span>|<span data-ttu-id="2c4ca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2c4ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c4ca-108">GetThreadOwningMonitorLock — metoda</span><span class="sxs-lookup"><span data-stu-id="2c4ca-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="2c4ca-109">Zwraca zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="2c4ca-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="2c4ca-110">GetMonitorEventWaitList — metoda</span><span class="sxs-lookup"><span data-stu-id="2c4ca-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="2c4ca-111">Udostępnia uporządkowaną listę wątków oczekujących w kolejce na zdarzenie, które jest skojarzone z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="2c4ca-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c4ca-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c4ca-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c4ca-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="2c4ca-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c4ca-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c4ca-114">Requirements</span></span>  
 <span data-ttu-id="2c4ca-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c4ca-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c4ca-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c4ca-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c4ca-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c4ca-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c4ca-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c4ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4ca-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c4ca-119">See Also</span></span>  
 [<span data-ttu-id="2c4ca-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="2c4ca-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2c4ca-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2c4ca-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
