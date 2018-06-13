---
title: ICorDebugManagedCallback2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22f4b2cb1bafefefaf3a3fc207af76c80c0c9798
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420345"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="b136a-102">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b136a-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="b136a-103">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="b136a-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="b136a-104">`ICorDebugManagedCallback2` jest logiczną rozszerzenie [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b136a-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b136a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b136a-105">Methods</span></span>  
  
|<span data-ttu-id="b136a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-106">Method</span></span>|<span data-ttu-id="b136a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b136a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b136a-108">ChangeConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="b136a-109">Powiadamia debuger zmiana zestawu zadań powiązanych z określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="b136a-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="b136a-110">CreateConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="b136a-111">Powiadamia debugera, że utworzono nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="b136a-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="b136a-112">DestroyConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="b136a-113">Powiadamia debuger określone połączenie zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="b136a-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="b136a-114">Exception, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="b136a-115">Powiadamia debuger rozpoczęto wyszukiwanie obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b136a-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="b136a-116">ExceptionUnwind, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="b136a-117">Udostępnia powiadomienia o stanie podczas procesu odwijaniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b136a-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="b136a-118">FunctionRemapComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="b136a-119">Powiadamia debugera, że wykonanie kodu została przełączona do nowej wersji funkcji edytowany.</span><span class="sxs-lookup"><span data-stu-id="b136a-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="b136a-120">FunctionRemapOpportunity, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="b136a-121">Powiadamia debuger osiągnięcie w wykonanie kodu punktu sekwencji w starszej wersji funkcji edytowany.</span><span class="sxs-lookup"><span data-stu-id="b136a-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="b136a-122">MDANotification, metoda</span><span class="sxs-lookup"><span data-stu-id="b136a-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="b136a-123">Zapewnia powiadomienie, że wykonywanie kodu napotkał zarządzany Asystent (MDA) komunikat dotyczący debugowania.</span><span class="sxs-lookup"><span data-stu-id="b136a-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b136a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b136a-124">Remarks</span></span>  
 <span data-ttu-id="b136a-125">`ICorDebugManagedCallback2` Rozszerza interfejs `ICorDebugManagedCallback` interfejs do obsługi nowych zdarzeń debugowania wprowadzone w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b136a-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="b136a-126">Debuger musi implementować `ICorDebugManagedCallback2` Jeśli trwa debugowanie aplikacji .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="b136a-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="b136a-127">Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przekazywany jako obiektu wywołania zwrotnego do [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="b136a-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b136a-128">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="b136a-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b136a-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b136a-129">Requirements</span></span>  
 <span data-ttu-id="b136a-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b136a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b136a-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b136a-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b136a-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b136a-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b136a-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b136a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b136a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b136a-134">See Also</span></span>  
 [<span data-ttu-id="b136a-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b136a-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="b136a-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b136a-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b136a-137">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b136a-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
