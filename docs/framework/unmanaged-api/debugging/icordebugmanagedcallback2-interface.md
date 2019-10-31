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
ms.openlocfilehash: 97f103844c38ebd3dbff058bfe96ab953cdba960
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131473"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="d8daf-102">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d8daf-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="d8daf-103">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="d8daf-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="d8daf-104">`ICorDebugManagedCallback2` jest logicznym rozszerzeniem interfejsu [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d8daf-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8daf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d8daf-105">Methods</span></span>  
  
|<span data-ttu-id="d8daf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-106">Method</span></span>|<span data-ttu-id="d8daf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d8daf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8daf-108">ChangeConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="d8daf-109">Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="d8daf-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="d8daf-110">CreateConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="d8daf-111">Powiadamia debuger o utworzeniu nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="d8daf-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="d8daf-112">DestroyConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="d8daf-113">Powiadamia debuger o przerwaniu określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="d8daf-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="d8daf-114">Exception, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="d8daf-115">Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d8daf-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="d8daf-116">ExceptionUnwind, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="d8daf-117">Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d8daf-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="d8daf-118">FunctionRemapComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="d8daf-119">Powiadamia debuger, że wykonywanie kodu zostało przełączone do nowej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8daf-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="d8daf-120">FunctionRemapOpportunity, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="d8daf-121">Powiadamia debuger, że wykonanie kodu osiągnęło punkt sekwencji w starszej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8daf-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="d8daf-122">MDANotification, metoda</span><span class="sxs-lookup"><span data-stu-id="d8daf-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="d8daf-123">Zapewnia powiadomienie, że wykonanie kodu napotkało komunikat asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="d8daf-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8daf-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8daf-124">Remarks</span></span>  
 <span data-ttu-id="d8daf-125">Interfejs `ICorDebugManagedCallback2` rozszerza interfejs `ICorDebugManagedCallback`, aby obsługiwał nowe zdarzenia debugowania wprowadzone w .NET Framework wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8daf-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="d8daf-126">Debuger musi implementować `ICorDebugManagedCallback2`, jeśli debugowanie .NET Framework 2,0 aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8daf-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="d8daf-127">Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8daf-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8daf-128">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d8daf-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8daf-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8daf-129">Requirements</span></span>  
 <span data-ttu-id="d8daf-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8daf-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8daf-131">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8daf-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8daf-132">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d8daf-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8daf-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8daf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8daf-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8daf-134">See also</span></span>

- [<span data-ttu-id="d8daf-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d8daf-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d8daf-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d8daf-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d8daf-137">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8daf-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
