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
ms.openlocfilehash: 74c5036bdc8a4a75e5711c6dc1d34d8f2c21128f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebug-interface"></a><span data-ttu-id="03084-102">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03084-102">ICorDebug Interface</span></span>
<span data-ttu-id="03084-103">Udostępnia metody, które umożliwiają deweloperom debugowanie aplikacji w środowisku środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="03084-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03084-104">Debugowanie trybu mieszanego (kodu zarządzanego i natywnego) nie jest obsługiwane w systemie Windows 95, Windows 98 lub Windows ME lub na platformach innych niż x86 (na przykład IA64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="03084-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03084-105">Metody</span><span class="sxs-lookup"><span data-stu-id="03084-105">Methods</span></span>  
  
|<span data-ttu-id="03084-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="03084-106">Method</span></span>|<span data-ttu-id="03084-107">Opis</span><span class="sxs-lookup"><span data-stu-id="03084-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03084-108">CanLaunchOrAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="03084-109">Określa, czy uruchamianie nowego procesu lub dołączanie do procesu danego jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="03084-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="03084-110">CreateProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="03084-111">Uruchamia proces i jego podstawowym wątku pod kontrolą debugera.</span><span class="sxs-lookup"><span data-stu-id="03084-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="03084-112">DebugActiveProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="03084-113">Dołącza debuger do istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="03084-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="03084-114">EnumerateProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="03084-115">Pobiera moduł wyliczający dla procesów, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="03084-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="03084-116">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="03084-117">Zwraca obiekt "ICorDebugProcess" z identyfikatorem danego procesu.</span><span class="sxs-lookup"><span data-stu-id="03084-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="03084-118">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="03084-119">Inicjuje `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="03084-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="03084-120">SetManagedHandler, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="03084-121">Określa obiekt programu obsługi zdarzeń dla zdarzeń zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="03084-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="03084-122">SetUnmanagedHandler, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="03084-123">Określa obiekt programu obsługi zdarzeń dla niezarządzanego zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="03084-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="03084-124">Terminate, metoda</span><span class="sxs-lookup"><span data-stu-id="03084-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="03084-125">Kończy `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="03084-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03084-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03084-126">Remarks</span></span>  
 <span data-ttu-id="03084-127">`ICorDebug` reprezentuje pętli przetwarzania zdarzeń dla procesu debugera.</span><span class="sxs-lookup"><span data-stu-id="03084-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="03084-128">Debuger musi czekać, aż [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) wywołania zwrotnego od wszystkich procesów debugowany przed wydaniem tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="03084-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="03084-129">`ICorDebug` Obiekt jest obiektem początkowej do sterowania wszystkie dalsze zarządzane debugowania.</span><span class="sxs-lookup"><span data-stu-id="03084-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="03084-130">W wersji systemu .NET Framework 1.0 i 1.1, ten obiekt był `CoClass` obiektu utworzone na podstawie modelu COM.</span><span class="sxs-lookup"><span data-stu-id="03084-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="03084-131">W programie .NET Framework w wersji 2.0, ten obiekt nie jest już `CoClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="03084-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="03084-132">Musi być utworzony przez [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkcji, która jest bardziej wersji obsługujących.</span><span class="sxs-lookup"><span data-stu-id="03084-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="03084-133">Ta nowa funkcja tworzenia umożliwia klientom uzyskanie określonej implementacji `ICorDebug`, które również emuluje określoną wersję interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="03084-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03084-134">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="03084-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03084-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03084-135">Requirements</span></span>  
 <span data-ttu-id="03084-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03084-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03084-137">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03084-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03084-138">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03084-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03084-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03084-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03084-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03084-140">See Also</span></span>  
 [<span data-ttu-id="03084-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="03084-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
