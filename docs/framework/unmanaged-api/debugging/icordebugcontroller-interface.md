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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749504"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="9f3ef-102">ICorDebugController, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f3ef-102">ICorDebugController Interface</span></span>

<span data-ttu-id="9f3ef-103">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, wykonanie kodu, które mogą być kontrolowane kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f3ef-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9f3ef-104">Methods</span></span>  
  
|<span data-ttu-id="9f3ef-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-105">Method</span></span>|<span data-ttu-id="9f3ef-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9f3ef-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="9f3ef-107">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="9f3ef-108">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="9f3ef-109">Continue, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="9f3ef-110">Wznawia wykonywanie wątków zarządzanych po wywołaniu [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="9f3ef-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="9f3ef-111">Detach, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="9f3ef-112">Odłącza debuger z domeny aplikacji lub procesu.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="9f3ef-113">EnumerateThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="9f3ef-114">Pobiera moduł wyliczający dla aktywnego zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="9f3ef-115">HasQueuedCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="9f3ef-116">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne aktualnie czekają w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="9f3ef-117">IsRunning, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="9f3ef-118">Pobiera wartość wskazującą, czy wątki w procesie są aktualnie uruchomione za darmo.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="9f3ef-119">SetAllThreadsDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="9f3ef-120">Ustawia stan debugowania wszystkie zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="9f3ef-121">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="9f3ef-122">Wykonuje wspólne stop we wszystkich wątkach, na których uruchomiono kod zarządzany w procesie.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="9f3ef-123">Terminate, metoda</span><span class="sxs-lookup"><span data-stu-id="9f3ef-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="9f3ef-124">Kończy proces o określony kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f3ef-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f3ef-125">Remarks</span></span>  
 <span data-ttu-id="9f3ef-126">Jeśli `ICorDebugController` jest kontrolowanie procesu, zakres obejmuje wszystkie wątki tego procesu.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="9f3ef-127">Jeśli `ICorDebugController` jest kontrolowanie domenę aplikacji, zakres obejmuje tylko wątki tej domeny określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f3ef-128">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="9f3ef-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f3ef-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f3ef-129">Requirements</span></span>  
 <span data-ttu-id="9f3ef-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f3ef-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f3ef-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f3ef-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f3ef-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f3ef-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f3ef-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f3ef-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3ef-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f3ef-134">See also</span></span>

- [<span data-ttu-id="9f3ef-135">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9f3ef-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
