---
title: ICorDebugThread::SetDebugState — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987145"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="8e92f-102">ICorDebugThread::SetDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e92f-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="8e92f-103">Ustawia flagi opisujące stan debugowania tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="8e92f-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e92f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e92f-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e92f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e92f-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="8e92f-106">[in] Bitowa kombinacja wartości wyliczenia cordebugthreadstate —, określające stan debugowania tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8e92f-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e92f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e92f-107">Remarks</span></span>  
 <span data-ttu-id="8e92f-108">`SetDebugState` Ustawia bieżący stan debugowania w wątku.</span><span class="sxs-lookup"><span data-stu-id="8e92f-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="8e92f-109">("Bieżący stan debugowania" reprezentuje stan debugowania, gdyby proces będzie kontynuowane nie rzeczywiste bieżącego stanu.) Normalna wartość to jest THREAD_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="8e92f-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="8e92f-110">Tylko debuger może wpłynąć na stan debugowania wątku.</span><span class="sxs-lookup"><span data-stu-id="8e92f-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="8e92f-111">Debugowanie stany ostatniego na będzie nadal występował, więc jeśli chcesz zachować wątku THREAD_SUSPENDed za pośrednictwem wielu będzie się powtarzać, można ustawić go jeden raz i dzięki temu nie trzeba martwić.</span><span class="sxs-lookup"><span data-stu-id="8e92f-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="8e92f-112">Zawieszanie wątków i wznawianie procesu może spowodować zakleszczenia, chociaż jest mało prawdopodobne, zwykle.</span><span class="sxs-lookup"><span data-stu-id="8e92f-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="8e92f-113">To jest wewnętrzne jakość wątków i procesów i projektem.</span><span class="sxs-lookup"><span data-stu-id="8e92f-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="8e92f-114">Debuger asynchronicznie można przerwać i wznawianie wątków można przerwać zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="8e92f-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="8e92f-115">Jeśli stan użytkownika dla wątku zawiera USER_UNSAFE_POINT, wątek może blokować wyrzucania elementów bezużytecznych (GC).</span><span class="sxs-lookup"><span data-stu-id="8e92f-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="8e92f-116">Oznacza to, że wątek wstrzymania ma znacznie wyższe prawdopodobieństwo powoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="8e92f-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="8e92f-117">Nie może to mieć wpływ na debugowania, który już do kolejki zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8e92f-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="8e92f-118">Ten sposób debuger powinien opróżnienia kolejki całe zdarzenie (przez wywołanie metody [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) przed zawieszanie lub wznawianie wątków.</span><span class="sxs-lookup"><span data-stu-id="8e92f-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="8e92f-119">Inne może ją odbierać zdarzenia w wątku, który uważa, że została już wstrzymana.</span><span class="sxs-lookup"><span data-stu-id="8e92f-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e92f-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e92f-120">Requirements</span></span>  
 <span data-ttu-id="8e92f-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e92f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e92f-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e92f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e92f-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e92f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e92f-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e92f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
