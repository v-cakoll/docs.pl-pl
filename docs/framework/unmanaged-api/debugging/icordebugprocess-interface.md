---
title: ICorDebugProcess Interface1
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
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423172"
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="9cceb-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="9cceb-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="9cceb-103">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="9cceb-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="9cceb-104">Ten interfejs jest podklasą klasy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="9cceb-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9cceb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9cceb-105">Methods</span></span>  
  
|<span data-ttu-id="9cceb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-106">Method</span></span>|<span data-ttu-id="9cceb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9cceb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cceb-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="9cceb-109">Czyści niezarządzane bieżącego wyjątku dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="9cceb-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="9cceb-110">EnableLogMessages, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="9cceb-111">Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="9cceb-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="9cceb-112">EnumerateAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="9cceb-113">Wylicza wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="9cceb-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="9cceb-114">EnumerateObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="9cceb-115">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="9cceb-115">Not implemented.</span></span>|  
|[<span data-ttu-id="9cceb-116">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="9cceb-117">Pobiera dojścia do procesu.</span><span class="sxs-lookup"><span data-stu-id="9cceb-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="9cceb-118">GetHelperThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="9cceb-119">Pobiera identyfikator wątku systemu operacyjnego (OS) dla debugera wewnętrzny wątek pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="9cceb-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="9cceb-120">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="9cceb-121">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="9cceb-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="9cceb-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="9cceb-123">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="9cceb-123">Not implemented.</span></span>|  
|[<span data-ttu-id="9cceb-124">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="9cceb-125">Pobiera nazwę wystąpienia ICorDebugThread z określonego wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9cceb-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="9cceb-126">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="9cceb-127">Pobiera kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="9cceb-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="9cceb-128">IsOSSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="9cceb-129">Określa, czy wątek został wstrzymany wyniku debugera zatrzymywania procesu.</span><span class="sxs-lookup"><span data-stu-id="9cceb-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="9cceb-130">IsTransitionStub, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="9cceb-131">Określa, czy adres jest wewnątrz skrótowa, która spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9cceb-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="9cceb-132">ModifyLogSwitch, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="9cceb-133">Ustawia poziom ważności określony dziennik przełącznika.</span><span class="sxs-lookup"><span data-stu-id="9cceb-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="9cceb-134">ReadMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="9cceb-135">Odczytuje pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="9cceb-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="9cceb-136">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="9cceb-137">Ustawia kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="9cceb-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="9cceb-138">ThreadForFiberCookie, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="9cceb-139">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="9cceb-139">Deprecated.</span></span>|  
|[<span data-ttu-id="9cceb-140">WriteMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="9cceb-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="9cceb-141">Zapisuje dane do to obszar pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="9cceb-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cceb-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cceb-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cceb-143">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="9cceb-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cceb-144">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cceb-144">Requirements</span></span>  
 <span data-ttu-id="9cceb-145">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cceb-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cceb-146">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cceb-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cceb-147">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cceb-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cceb-148">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cceb-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cceb-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cceb-149">See Also</span></span>  
 [<span data-ttu-id="9cceb-150">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cceb-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="9cceb-151">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9cceb-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
