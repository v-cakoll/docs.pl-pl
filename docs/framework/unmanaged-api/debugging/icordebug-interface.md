---
title: ICorDebug — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05c95d47d57525aa2aebe16d536b771042600000
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509730"
---
# <a name="icordebug-interface"></a><span data-ttu-id="d0885-102">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d0885-102">ICorDebug Interface</span></span>
<span data-ttu-id="d0885-103">Udostępnia metody, które umożliwiają deweloperom debugowanie aplikacji w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d0885-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0885-104">Debugowanie trybu mieszanego (kodu zarządzanego i natywnego) nie jest obsługiwana na Windows 95, Windows 98 lub Windows ME lub na platformach innych niż x86 (na przykład IA64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="d0885-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0885-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d0885-105">Methods</span></span>  
  
|<span data-ttu-id="d0885-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-106">Method</span></span>|<span data-ttu-id="d0885-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d0885-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0885-108">CanLaunchOrAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="d0885-109">Określa, czy uruchamianie nowego procesu lub dołączanie do danego procesu jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d0885-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="d0885-110">CreateProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="d0885-111">Uruchamia proces i jego podstawowym wątku pod kontrolą debugera.</span><span class="sxs-lookup"><span data-stu-id="d0885-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="d0885-112">DebugActiveProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="d0885-113">Dołącza debuger do istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="d0885-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="d0885-114">EnumerateProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="d0885-115">Pobiera moduł wyliczający dla procesów, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="d0885-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="d0885-116">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="d0885-117">Zwraca obiekt "ICorDebugProcess" o identyfikatorze danego procesu.</span><span class="sxs-lookup"><span data-stu-id="d0885-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="d0885-118">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="d0885-119">Inicjuje `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0885-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="d0885-120">SetManagedHandler, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="d0885-121">Określa obiekt programu obsługi zdarzeń dla zdarzeń zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d0885-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="d0885-122">SetUnmanagedHandler, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="d0885-123">Określa obiekt programu obsługi zdarzeń dla zdarzenia niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="d0885-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="d0885-124">Terminate, metoda</span><span class="sxs-lookup"><span data-stu-id="d0885-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="d0885-125">Kończy `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0885-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0885-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0885-126">Remarks</span></span>  
 <span data-ttu-id="d0885-127">`ICorDebug` reprezentuje pętlę przetwarzania zdarzeń dla procesu, debuger.</span><span class="sxs-lookup"><span data-stu-id="d0885-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="d0885-128">Debuger musi czekać [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) wywołania zwrotnego od wszystkich procesów debugowany przed wydaniem tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d0885-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="d0885-129">`ICorDebug` Obiekt jest obiektem początkowej do kontrolowania wszystkich dalszych zarządzanych debugowania.</span><span class="sxs-lookup"><span data-stu-id="d0885-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="d0885-130">W .NET Framework w wersji 1.0 i 1.1, ten obiekt był `CoClass` obiektu utworzonego na podstawie modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d0885-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="d0885-131">W .NET Framework w wersji 2.0, ten obiekt nie jest już `CoClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0885-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="d0885-132">Musi ona zostać utworzona przez [createdebugginginterfacefromversion —](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkcji, która jest bardziej rozpoznający wersje.</span><span class="sxs-lookup"><span data-stu-id="d0885-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="d0885-133">Ta nowa funkcja tworzenia pozwala klientom na pobieranie określonej implementacji `ICorDebug`, które również emuluje określoną wersję interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="d0885-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0885-134">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="d0885-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0885-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0885-135">Requirements</span></span>  
 <span data-ttu-id="d0885-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0885-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0885-137">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0885-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0885-138">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0885-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0885-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0885-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0885-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0885-140">See also</span></span>
- [<span data-ttu-id="d0885-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0885-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
