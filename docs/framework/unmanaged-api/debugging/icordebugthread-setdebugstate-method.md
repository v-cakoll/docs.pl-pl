---
title: "ICorDebugThread::SetDebugState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2754caf11f89358b3e81e6324835d5b2e12f17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="bf5a9-102">ICorDebugThread::SetDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf5a9-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="bf5a9-103">Określa flagi opisujące stan debugowania tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf5a9-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf5a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf5a9-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="bf5a9-106">[in] Bitowe połączenie wartości wyliczenia CorDebugThreadState, określające stan debugowania tego wątku.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5a9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf5a9-107">Remarks</span></span>  
 <span data-ttu-id="bf5a9-108">`SetDebugState`Ustawia bieżący stan debugowania wątku.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="bf5a9-109">("Bieżący stan debugowania" reprezentuje stan debugowania, jeśli proces będzie kontynuowane, zamiast rzeczywistej bieżącego stanu.) Normalne wartość ta jest THREAD_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="bf5a9-110">Tylko debuger może mieć wpływ na stan debugowania wątku.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="bf5a9-111">Debugowanie stany ostatniego w poprzek będzie nadal występować, jeśli chcesz zachować wątku THREAD_SUSPENDed przez wiele będzie nadal występować, można ustawić go raz, a następnie nie są martwić się o jego.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="bf5a9-112">Zawieszanie wątków i wznawianie proces może spowodować zakleszczenie, chociaż jest mało prawdopodobne, zwykle.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="bf5a9-113">Jest to wewnętrzne jakości wątków i procesów, w projekcie.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="bf5a9-114">Debuger może asynchronicznie przerywanie i wznawianie wątków podziału zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="bf5a9-115">Jeśli stan użytkownika dla wątku zawiera USER_UNSAFE_POINT, wątek może zablokować wyrzucania elementów bezużytecznych (GC).</span><span class="sxs-lookup"><span data-stu-id="bf5a9-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="bf5a9-116">Oznacza to, że wątku zawieszonym ma znacznie wyższa szansy powodować zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="bf5a9-117">Nie może to mieć wpływ na debugowania, które zdarzenia już do kolejki.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="bf5a9-118">W związku z tym debuger powinien opróżniania kolejki całe zdarzenie (wywołując [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) przed wstrzymywanie i wznawianie wątków.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="bf5a9-119">Else on może pobrać zdarzenia w wątku, który określa, że została już wstrzymana.</span><span class="sxs-lookup"><span data-stu-id="bf5a9-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5a9-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf5a9-120">Requirements</span></span>  
 <span data-ttu-id="bf5a9-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5a9-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf5a9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf5a9-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf5a9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf5a9-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5a9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
