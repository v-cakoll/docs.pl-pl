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
ms.openlocfilehash: 0ca66f001d04bc86b64e0fe2d1cd37559e4fc633
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785115"
---
# <a name="icordebug-interface"></a><span data-ttu-id="a010f-102">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a010f-102">ICorDebug Interface</span></span>
<span data-ttu-id="a010f-103">Zapewnia metody, które umożliwiają deweloperom debugowanie aplikacji w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a010f-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a010f-104">Debugowanie w trybie mieszanym (kod zarządzany i natywny) nie jest obsługiwane w systemach Windows 95, Windows 98 lub Windows ME ani na platformach innych niż x86 (takich jak IA64 i AMD64).</span><span class="sxs-lookup"><span data-stu-id="a010f-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a010f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a010f-105">Methods</span></span>  
  
|<span data-ttu-id="a010f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-106">Method</span></span>|<span data-ttu-id="a010f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a010f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a010f-108">CanLaunchOrAttach, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-108">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="a010f-109">Określa, czy ma być uruchamiany nowy proces, czy dołączany do danego procesu jest możliwy w kontekście bieżącego komputera i konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a010f-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="a010f-110">CreateProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-110">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="a010f-111">Uruchamia proces i jego główny wątek pod kontrolą debugera.</span><span class="sxs-lookup"><span data-stu-id="a010f-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="a010f-112">DebugActiveProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-112">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="a010f-113">Dołącza debuger do istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="a010f-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="a010f-114">EnumerateProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-114">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="a010f-115">Pobiera moduł wyliczający dla procesów, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="a010f-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="a010f-116">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-116">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="a010f-117">Zwraca obiekt "ICorDebugProcess" z danym IDENTYFIKATORem procesu.</span><span class="sxs-lookup"><span data-stu-id="a010f-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="a010f-118">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-118">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="a010f-119">Inicjuje obiekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="a010f-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="a010f-120">SetManagedHandler, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-120">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="a010f-121">Określa obiekt obsługi zdarzeń dla zdarzeń zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="a010f-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="a010f-122">SetUnmanagedHandler, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-122">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="a010f-123">Określa obiekt obsługi zdarzeń dla zdarzeń niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="a010f-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="a010f-124">Terminate, metoda</span><span class="sxs-lookup"><span data-stu-id="a010f-124">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="a010f-125">Kończy działanie obiektu `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="a010f-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a010f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a010f-126">Remarks</span></span>  
 <span data-ttu-id="a010f-127">`ICorDebug` reprezentuje pętlę przetwarzania zdarzeń dla procesu debugera.</span><span class="sxs-lookup"><span data-stu-id="a010f-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="a010f-128">Debuger musi oczekiwać na wywołanie zwrotne [ICorDebugManagedCallback:: ExitProcess —](icordebugmanagedcallback-exitprocess-method.md) ze wszystkich procesów, które są debugowane przed zwolnieniem tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a010f-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="a010f-129">Obiekt `ICorDebug` jest początkowym obiektem, który kontroluje wszystkie inne zarządzane debugowanie.</span><span class="sxs-lookup"><span data-stu-id="a010f-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="a010f-130">W .NET Framework wersje 1,0 i 1,1 ten obiekt był obiektem `CoClass` utworzonym na podstawie modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a010f-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="a010f-131">W .NET Framework w wersji 2,0 ten obiekt nie jest już obiektem `CoClass`.</span><span class="sxs-lookup"><span data-stu-id="a010f-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="a010f-132">Musi być utworzony przez funkcję [CreateDebuggingInterfaceFromVersion —](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , która jest większa od wersji.</span><span class="sxs-lookup"><span data-stu-id="a010f-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="a010f-133">Ta nowa funkcja tworzenia umożliwia klientom uzyskanie konkretnej implementacji `ICorDebug`, która również emuluje określoną wersję interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="a010f-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a010f-134">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a010f-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a010f-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a010f-135">Requirements</span></span>  
 <span data-ttu-id="a010f-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a010f-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a010f-137">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a010f-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a010f-138">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a010f-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a010f-139">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a010f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a010f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a010f-140">See also</span></span>

- [<span data-ttu-id="a010f-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a010f-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
