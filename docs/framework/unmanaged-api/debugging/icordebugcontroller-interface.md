---
title: ICorDebugController Interface1
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
ms.openlocfilehash: c0651f8cd63f2ebdc6b81e92c0b55d94fe51316b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645304"
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="ca6c0-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="ca6c0-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="ca6c0-103">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, wykonanie kodu, które mogą być kontrolowane kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca6c0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca6c0-104">Methods</span></span>  
  
|<span data-ttu-id="ca6c0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-105">Method</span></span>|<span data-ttu-id="ca6c0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ca6c0-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="ca6c0-107">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="ca6c0-108">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="ca6c0-109">Continue, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="ca6c0-110">Wznawia wykonywanie wątków zarządzanych po wywołaniu [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="ca6c0-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="ca6c0-111">Detach, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="ca6c0-112">Odłącza debuger z domeny aplikacji lub procesu.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="ca6c0-113">EnumerateThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="ca6c0-114">Pobiera moduł wyliczający dla aktywnego zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="ca6c0-115">HasQueuedCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="ca6c0-116">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne aktualnie czekają w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="ca6c0-117">IsRunning, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="ca6c0-118">Pobiera wartość wskazującą, czy wątki w procesie są aktualnie uruchomione za darmo.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="ca6c0-119">SetAllThreadsDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="ca6c0-120">Ustawia stan debugowania wszystkie zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="ca6c0-121">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="ca6c0-122">Wykonuje wspólne stop we wszystkich wątkach, na których uruchomiono kod zarządzany w procesie.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="ca6c0-123">Terminate, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6c0-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="ca6c0-124">Kończy proces o określony kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca6c0-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca6c0-125">Remarks</span></span>  
 <span data-ttu-id="ca6c0-126">Jeśli `ICorDebugController` jest kontrolowanie procesu, zakres obejmuje wszystkie wątki tego procesu.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="ca6c0-127">Jeśli `ICorDebugController` jest kontrolowanie domenę aplikacji, zakres obejmuje tylko wątki tej domeny określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca6c0-128">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ca6c0-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6c0-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca6c0-129">Requirements</span></span>  
 <span data-ttu-id="ca6c0-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6c0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6c0-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca6c0-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca6c0-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca6c0-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca6c0-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6c0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6c0-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca6c0-134">See also</span></span>
- [<span data-ttu-id="ca6c0-135">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca6c0-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
