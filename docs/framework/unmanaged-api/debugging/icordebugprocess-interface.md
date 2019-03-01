---
title: ICorDebugProcess — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dc732a8e3419a7ca42f5180d1bd32128ec33417
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967519"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="20aaf-102">ICorDebugProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20aaf-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="20aaf-103">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="20aaf-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="20aaf-104">Ten interfejs jest podklasą icordebugcontroller —.</span><span class="sxs-lookup"><span data-stu-id="20aaf-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20aaf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="20aaf-105">Methods</span></span>  
  
|<span data-ttu-id="20aaf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-106">Method</span></span>|<span data-ttu-id="20aaf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20aaf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20aaf-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="20aaf-109">Czyści niezarządzane bieżącego wyjątku dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="20aaf-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="20aaf-110">EnableLogMessages, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="20aaf-111">Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="20aaf-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="20aaf-112">EnumerateAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="20aaf-113">Wylicza wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="20aaf-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="20aaf-114">EnumerateObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="20aaf-115">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="20aaf-115">Not implemented.</span></span>|  
|[<span data-ttu-id="20aaf-116">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="20aaf-117">Pobiera uchwyt do procesu.</span><span class="sxs-lookup"><span data-stu-id="20aaf-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="20aaf-118">GetHelperThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="20aaf-119">Pobiera identyfikator wątku systemu operacyjnego (OS) dla debugera wewnętrzny wątek pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="20aaf-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="20aaf-120">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="20aaf-121">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="20aaf-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="20aaf-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="20aaf-123">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="20aaf-123">Not implemented.</span></span>|  
|[<span data-ttu-id="20aaf-124">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="20aaf-125">Pobiera identyfikator wystąpienia ICorDebugThread, który ma określony wątek systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="20aaf-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="20aaf-126">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="20aaf-127">Pobiera kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="20aaf-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="20aaf-128">IsOSSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="20aaf-129">Określa, czy wątek została zawieszona wyniku debugera zatrzymywania procesu.</span><span class="sxs-lookup"><span data-stu-id="20aaf-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="20aaf-130">IsTransitionStub, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="20aaf-131">Określa, czy adres znajduje się wewnątrz odcinek, który spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="20aaf-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="20aaf-132">ModifyLogSwitch, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="20aaf-133">Ustawia poziom ważności przełącznika określonego dziennika.</span><span class="sxs-lookup"><span data-stu-id="20aaf-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="20aaf-134">ReadMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="20aaf-135">Odczytuje pamięć procesu.</span><span class="sxs-lookup"><span data-stu-id="20aaf-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="20aaf-136">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="20aaf-137">Ustawia kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="20aaf-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="20aaf-138">ThreadForFiberCookie, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="20aaf-139">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="20aaf-139">Deprecated.</span></span>|  
|[<span data-ttu-id="20aaf-140">WriteMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="20aaf-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="20aaf-141">Zapisuje dane do obszar pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="20aaf-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20aaf-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20aaf-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20aaf-143">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="20aaf-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20aaf-144">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20aaf-144">Requirements</span></span>  
 <span data-ttu-id="20aaf-145">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20aaf-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20aaf-146">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20aaf-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20aaf-147">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20aaf-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20aaf-148">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20aaf-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20aaf-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20aaf-149">See also</span></span>
- [<span data-ttu-id="20aaf-150">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="20aaf-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="20aaf-151">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="20aaf-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
