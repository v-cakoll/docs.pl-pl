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
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792592"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="df7cc-102">ICorDebugProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="df7cc-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="df7cc-103">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="df7cc-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="df7cc-104">Ten interfejs jest podklasą elementu ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="df7cc-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df7cc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="df7cc-105">Methods</span></span>  
  
|<span data-ttu-id="df7cc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-106">Method</span></span>|<span data-ttu-id="df7cc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="df7cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df7cc-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-108">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="df7cc-109">Czyści bieżący wyjątek niezarządzany w danym wątku.</span><span class="sxs-lookup"><span data-stu-id="df7cc-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="df7cc-110">EnableLogMessages, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-110">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="df7cc-111">Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="df7cc-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="df7cc-112">EnumerateAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-112">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="df7cc-113">Wylicza wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="df7cc-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="df7cc-114">EnumerateObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-114">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="df7cc-115">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="df7cc-115">Not implemented.</span></span>|  
|[<span data-ttu-id="df7cc-116">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-116">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="df7cc-117">Pobiera dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="df7cc-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="df7cc-118">GetHelperThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-118">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="df7cc-119">Pobiera identyfikator wątku systemu operacyjnego dla wewnętrznego wątku pomocnika debugera.</span><span class="sxs-lookup"><span data-stu-id="df7cc-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="df7cc-120">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-120">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="df7cc-121">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="df7cc-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="df7cc-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-122">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="df7cc-123">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="df7cc-123">Not implemented.</span></span>|  
|[<span data-ttu-id="df7cc-124">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-124">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="df7cc-125">Pobiera wystąpienie ICorDebugThread o określonym IDENTYFIKATORze wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="df7cc-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="df7cc-126">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-126">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="df7cc-127">Pobiera kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="df7cc-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="df7cc-128">IsOSSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-128">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="df7cc-129">Określa, czy wątek został wstrzymany w wyniku debugera zatrzymywania procesu.</span><span class="sxs-lookup"><span data-stu-id="df7cc-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="df7cc-130">IsTransitionStub, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-130">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="df7cc-131">Określa, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="df7cc-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="df7cc-132">ModifyLogSwitch, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-132">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="df7cc-133">Ustawia poziom ważności określonego przełącznika dziennika.</span><span class="sxs-lookup"><span data-stu-id="df7cc-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="df7cc-134">ReadMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-134">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="df7cc-135">Odczytuje pamięć z procesu.</span><span class="sxs-lookup"><span data-stu-id="df7cc-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="df7cc-136">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-136">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="df7cc-137">Ustawia kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="df7cc-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="df7cc-138">ThreadForFiberCookie, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-138">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="df7cc-139">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="df7cc-139">Deprecated.</span></span>|  
|[<span data-ttu-id="df7cc-140">WriteMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="df7cc-140">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="df7cc-141">Zapisuje dane w obszarze pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="df7cc-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df7cc-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df7cc-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df7cc-143">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="df7cc-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df7cc-144">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df7cc-144">Requirements</span></span>  
 <span data-ttu-id="df7cc-145">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df7cc-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df7cc-146">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df7cc-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df7cc-147">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df7cc-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df7cc-148">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df7cc-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7cc-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df7cc-149">See also</span></span>

- [<span data-ttu-id="df7cc-150">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="df7cc-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="df7cc-151">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="df7cc-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
