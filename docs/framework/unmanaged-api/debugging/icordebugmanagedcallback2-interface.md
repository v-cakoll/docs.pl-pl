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
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793313"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="f5ccc-102">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5ccc-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="f5ccc-103">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="f5ccc-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="f5ccc-104">`ICorDebugManagedCallback2` jest logicznym rozszerzeniem interfejsu [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f5ccc-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5ccc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f5ccc-105">Methods</span></span>  
  
|<span data-ttu-id="f5ccc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-106">Method</span></span>|<span data-ttu-id="f5ccc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f5ccc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5ccc-108">ChangeConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-108">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="f5ccc-109">Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="f5ccc-110">CreateConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-110">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="f5ccc-111">Powiadamia debuger o utworzeniu nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="f5ccc-112">DestroyConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-112">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="f5ccc-113">Powiadamia debuger o przerwaniu określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="f5ccc-114">Exception, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-114">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="f5ccc-115">Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="f5ccc-116">ExceptionUnwind, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-116">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="f5ccc-117">Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="f5ccc-118">FunctionRemapComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-118">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="f5ccc-119">Powiadamia debuger, że wykonywanie kodu zostało przełączone do nowej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="f5ccc-120">FunctionRemapOpportunity, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-120">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="f5ccc-121">Powiadamia debuger, że wykonanie kodu osiągnęło punkt sekwencji w starszej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="f5ccc-122">MDANotification, metoda</span><span class="sxs-lookup"><span data-stu-id="f5ccc-122">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="f5ccc-123">Zapewnia powiadomienie, że wykonanie kodu napotkało komunikat asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="f5ccc-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5ccc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5ccc-124">Remarks</span></span>  
 <span data-ttu-id="f5ccc-125">Interfejs `ICorDebugManagedCallback2` rozszerza interfejs `ICorDebugManagedCallback`, aby obsługiwał nowe zdarzenia debugowania wprowadzone w .NET Framework wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="f5ccc-126">Debuger musi implementować `ICorDebugManagedCallback2`, jeśli debugowanie .NET Framework 2,0 aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="f5ccc-127">Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="f5ccc-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5ccc-128">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f5ccc-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5ccc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5ccc-129">Requirements</span></span>  
 <span data-ttu-id="f5ccc-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ccc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ccc-131">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5ccc-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5ccc-132">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5ccc-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5ccc-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ccc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ccc-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5ccc-134">See also</span></span>

- [<span data-ttu-id="f5ccc-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f5ccc-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f5ccc-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f5ccc-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f5ccc-137">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5ccc-137">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
