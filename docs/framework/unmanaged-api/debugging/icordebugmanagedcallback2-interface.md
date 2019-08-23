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
ms.openlocfilehash: ca33436d98edf5844a5ca27c9ac89648f10ec0c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909985"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="93936-102">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93936-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="93936-103">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="93936-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="93936-104">`ICorDebugManagedCallback2`jest logicznym rozszerzeniem interfejsu [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="93936-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93936-105">Metody</span><span class="sxs-lookup"><span data-stu-id="93936-105">Methods</span></span>  
  
|<span data-ttu-id="93936-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="93936-106">Method</span></span>|<span data-ttu-id="93936-107">Opis</span><span class="sxs-lookup"><span data-stu-id="93936-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93936-108">ChangeConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="93936-109">Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="93936-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="93936-110">CreateConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="93936-111">Powiadamia debuger o utworzeniu nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="93936-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="93936-112">DestroyConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="93936-113">Powiadamia debuger o przerwaniu określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="93936-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="93936-114">Exception, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="93936-115">Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="93936-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="93936-116">ExceptionUnwind, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="93936-117">Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="93936-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="93936-118">FunctionRemapComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="93936-119">Powiadamia debuger, że wykonywanie kodu zostało przełączone do nowej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="93936-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="93936-120">FunctionRemapOpportunity, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="93936-121">Powiadamia debuger, że wykonanie kodu osiągnęło punkt sekwencji w starszej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="93936-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="93936-122">MDANotification, metoda</span><span class="sxs-lookup"><span data-stu-id="93936-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="93936-123">Zapewnia powiadomienie, że wykonanie kodu napotkało komunikat asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="93936-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93936-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93936-124">Remarks</span></span>  
 <span data-ttu-id="93936-125">`ICorDebugManagedCallback2` Interfejs`ICorDebugManagedCallback` rozszerza interfejs obsługujący nowe zdarzenia debugowania wprowadzone w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="93936-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="93936-126">Debuger musi implementować `ICorDebugManagedCallback2` w przypadku debugowania aplikacji .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="93936-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="93936-127">Wystąpienie `ICorDebugManagedCallback` lub`ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="93936-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93936-128">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="93936-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93936-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93936-129">Requirements</span></span>  
 <span data-ttu-id="93936-130">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93936-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93936-131">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93936-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93936-132">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93936-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93936-133">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93936-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93936-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93936-134">See also</span></span>

- [<span data-ttu-id="93936-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="93936-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="93936-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="93936-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="93936-137">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="93936-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
