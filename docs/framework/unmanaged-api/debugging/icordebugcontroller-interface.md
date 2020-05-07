---
title: ICorDebugController, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: e494bbb24e8f2245593e7945625e72e70ae1dde5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892773"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="3f6c1-102">ICorDebugController, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f6c1-102">ICorDebugController Interface</span></span>

<span data-ttu-id="3f6c1-103">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, w którym można kontrolować kontekst wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f6c1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3f6c1-104">Methods</span></span>  
  
|<span data-ttu-id="3f6c1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-105">Method</span></span>|<span data-ttu-id="3f6c1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3f6c1-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="3f6c1-107">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="3f6c1-108">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="3f6c1-109">Continue, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="3f6c1-110">Wznawia wykonywanie zarządzanych wątków po wywołaniu [ICorDebugController:: Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="3f6c1-111">Detach, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="3f6c1-112">Odłącza debuger od domeny procesu lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="3f6c1-113">EnumerateThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="3f6c1-114">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="3f6c1-115">HasQueuedCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="3f6c1-116">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne są obecnie umieszczane w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="3f6c1-117">IsRunning, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="3f6c1-118">Pobiera wartość wskazującą, czy wątki w procesie są obecnie uruchomione swobodnie.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="3f6c1-119">SetAllThreadsDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="3f6c1-120">Ustawia stan debugowania wszystkich zarządzanych wątków w procesie.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="3f6c1-121">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="3f6c1-122">Wykonuje przerwanie w ramach wszystkich wątków, które uruchamiają kod zarządzany w procesie.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="3f6c1-123">Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f6c1-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="3f6c1-124">Kończy proces z określonym kodem zakończenia.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f6c1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f6c1-125">Remarks</span></span>  
 <span data-ttu-id="3f6c1-126">Jeśli `ICorDebugController` kontroluje proces, zakres obejmuje wszystkie wątki procesu.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="3f6c1-127">Jeśli `ICorDebugController` kontroluje domenę aplikacji, zakres obejmuje tylko wątki tej konkretnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f6c1-128">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f6c1-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f6c1-129">Requirements</span></span>  
 <span data-ttu-id="3f6c1-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f6c1-131">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f6c1-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f6c1-132">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3f6c1-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f6c1-133">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f6c1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6c1-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f6c1-134">See also</span></span>

- [<span data-ttu-id="3f6c1-135">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3f6c1-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
