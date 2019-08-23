---
title: ICorDebugProcess, interfejs
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
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943304"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="86655-102">ICorDebugProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="86655-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="86655-103">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="86655-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="86655-104">Ten interfejs jest podklasą elementu ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="86655-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86655-105">Metody</span><span class="sxs-lookup"><span data-stu-id="86655-105">Methods</span></span>  
  
|<span data-ttu-id="86655-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="86655-106">Method</span></span>|<span data-ttu-id="86655-107">Opis</span><span class="sxs-lookup"><span data-stu-id="86655-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86655-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="86655-109">Czyści bieżący wyjątek niezarządzany w danym wątku.</span><span class="sxs-lookup"><span data-stu-id="86655-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="86655-110">EnableLogMessages, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="86655-111">Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="86655-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="86655-112">EnumerateAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="86655-113">Wylicza wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="86655-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="86655-114">EnumerateObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="86655-115">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="86655-115">Not implemented.</span></span>|  
|[<span data-ttu-id="86655-116">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="86655-117">Pobiera dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="86655-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="86655-118">GetHelperThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="86655-119">Pobiera identyfikator wątku systemu operacyjnego dla wewnętrznego wątku pomocnika debugera.</span><span class="sxs-lookup"><span data-stu-id="86655-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="86655-120">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="86655-121">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="86655-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="86655-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="86655-123">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="86655-123">Not implemented.</span></span>|  
|[<span data-ttu-id="86655-124">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="86655-125">Pobiera wystąpienie ICorDebugThread o określonym IDENTYFIKATORze wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="86655-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="86655-126">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="86655-127">Pobiera kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="86655-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="86655-128">IsOSSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="86655-129">Określa, czy wątek został wstrzymany w wyniku debugera zatrzymywania procesu.</span><span class="sxs-lookup"><span data-stu-id="86655-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="86655-130">IsTransitionStub, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="86655-131">Określa, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="86655-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="86655-132">ModifyLogSwitch, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="86655-133">Ustawia poziom ważności określonego przełącznika dziennika.</span><span class="sxs-lookup"><span data-stu-id="86655-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="86655-134">ReadMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="86655-135">Odczytuje pamięć z procesu.</span><span class="sxs-lookup"><span data-stu-id="86655-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="86655-136">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="86655-137">Ustawia kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="86655-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="86655-138">ThreadForFiberCookie, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="86655-139">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="86655-139">Deprecated.</span></span>|  
|[<span data-ttu-id="86655-140">WriteMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="86655-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="86655-141">Zapisuje dane w obszarze pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="86655-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86655-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86655-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86655-143">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="86655-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86655-144">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86655-144">Requirements</span></span>  
 <span data-ttu-id="86655-145">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86655-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86655-146">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86655-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86655-147">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86655-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86655-148">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86655-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86655-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86655-149">See also</span></span>

- [<span data-ttu-id="86655-150">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="86655-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="86655-151">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="86655-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
