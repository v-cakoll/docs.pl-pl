---
title: ICorDebugController Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="86723-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="86723-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="86723-103">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, których wykonanie kodu mogą być kontrolowane kontekstu.</span><span class="sxs-lookup"><span data-stu-id="86723-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86723-104">Metody</span><span class="sxs-lookup"><span data-stu-id="86723-104">Methods</span></span>  
  
|<span data-ttu-id="86723-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="86723-105">Method</span></span>|<span data-ttu-id="86723-106">Opis</span><span class="sxs-lookup"><span data-stu-id="86723-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="86723-107">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="86723-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="86723-108">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="86723-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="86723-109">Continue, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="86723-110">Wznawia wykonywanie wątków zarządzanych po wywołaniu [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="86723-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="86723-111">Detach, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="86723-112">Odłącza debugera z domeny proces lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86723-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="86723-113">EnumerateThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="86723-114">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="86723-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="86723-115">HasQueuedCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="86723-116">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne aktualnie czekają w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="86723-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="86723-117">IsRunning, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="86723-118">Pobiera wartość wskazującą, czy wątki tego procesu są aktualnie uruchomione za darmo.</span><span class="sxs-lookup"><span data-stu-id="86723-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="86723-119">SetAllThreadsDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="86723-120">Ustawia stan debugowania wszystkie wątki zarządzane w procesie.</span><span class="sxs-lookup"><span data-stu-id="86723-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="86723-121">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="86723-122">Wykonuje wspólne Zatrzymaj wszystkie wątki uruchomione kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="86723-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="86723-123">Terminate, metoda</span><span class="sxs-lookup"><span data-stu-id="86723-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="86723-124">Kończy proces o określony kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="86723-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86723-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86723-125">Remarks</span></span>  
 <span data-ttu-id="86723-126">Jeśli `ICorDebugController` jest sterowanie procesem, zakres obejmuje wszystkie wątki tego procesu.</span><span class="sxs-lookup"><span data-stu-id="86723-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="86723-127">Jeśli `ICorDebugController` jest kontrolowanie domeny aplikacji, zakres obejmuje tylko wątki tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86723-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86723-128">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="86723-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86723-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86723-129">Requirements</span></span>  
 <span data-ttu-id="86723-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86723-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86723-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86723-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86723-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86723-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86723-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86723-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86723-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86723-134">See Also</span></span>  
 [<span data-ttu-id="86723-135">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="86723-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
