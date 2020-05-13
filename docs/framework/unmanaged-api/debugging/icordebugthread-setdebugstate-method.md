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
ms.openlocfilehash: 05ae2791ee7f8bd31be38ec4d2117ddc3c2ea2bc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377942"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="51936-102">ICorDebugThread::SetDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="51936-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="51936-103">Ustawia flagi opisujące stan debugowania tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="51936-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51936-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51936-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51936-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51936-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="51936-106">podczas Bitowa kombinacja CorDebugThreadState — wartości wyliczenia, które określają stan debugowania tego wątku.</span><span class="sxs-lookup"><span data-stu-id="51936-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51936-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51936-107">Remarks</span></span>  
 <span data-ttu-id="51936-108">`SetDebugState`ustawia bieżący stan debugowania wątku.</span><span class="sxs-lookup"><span data-stu-id="51936-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="51936-109">("Bieżący stan debugowania" reprezentuje stan debugowania, jeśli proces ma być kontynuowany, a nie z rzeczywistym bieżącym stanem). Wartość normalna jest THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="51936-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="51936-110">Tylko debuger może mieć wpływ na stan debugowania wątku.</span><span class="sxs-lookup"><span data-stu-id="51936-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="51936-111">Stany debugowania są w dalszym ciągu kontynuowane, więc jeśli chcesz utrzymywać wątek THREAD_SUSPENDed przez wiele kontynuuje, możesz go skonfigurować raz i jeszcze nie musi się martwić.</span><span class="sxs-lookup"><span data-stu-id="51936-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="51936-112">Wstrzymywanie wątków i wznawianie procesu może spowodować zakleszczenie, chociaż zwykle jest to mało prawdopodobne.</span><span class="sxs-lookup"><span data-stu-id="51936-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="51936-113">Jest to wewnętrzna jakość wątków i procesów. jest ona zaprojektowana.</span><span class="sxs-lookup"><span data-stu-id="51936-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="51936-114">Debuger może asynchronicznie przerwać i wznowić wątki w celu przerwania zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="51936-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="51936-115">Jeśli stan użytkownika wątku zawiera USER_UNSAFE_POINT, wątek może blokować wyrzucanie elementów bezużytecznych (GC).</span><span class="sxs-lookup"><span data-stu-id="51936-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="51936-116">Oznacza to, że zawieszony wątek ma znacznie większą szansę na spowodowanie zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="51936-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="51936-117">To może nie wpływać na zdarzenia debugowania, które zostały już dodane do kolejki.</span><span class="sxs-lookup"><span data-stu-id="51936-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="51936-118">W ten sposób debuger powinien opróżnić całą kolejkę zdarzeń (przez wywołanie [ICorDebugController:: HasQueuedCallbacks —](icordebugcontroller-hasqueuedcallbacks-method.md)) przed zawieszeniem lub wznowieniem wątków.</span><span class="sxs-lookup"><span data-stu-id="51936-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="51936-119">W przeciwnym razie mogą wystąpić zdarzenia w wątku, który uważa, że jest już wstrzymany.</span><span class="sxs-lookup"><span data-stu-id="51936-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51936-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51936-120">Requirements</span></span>  
 <span data-ttu-id="51936-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51936-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51936-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51936-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51936-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="51936-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51936-124">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51936-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
