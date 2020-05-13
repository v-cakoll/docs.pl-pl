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
ms.openlocfilehash: ab48efccc88787f099a182627777db95304cdc3e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212077"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="656e0-102">ICorDebugProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="656e0-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="656e0-103">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="656e0-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="656e0-104">Ten interfejs jest podklasą elementu ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="656e0-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="656e0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="656e0-105">Methods</span></span>  
  
|<span data-ttu-id="656e0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-106">Method</span></span>|<span data-ttu-id="656e0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="656e0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="656e0-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-108">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="656e0-109">Czyści bieżący wyjątek niezarządzany w danym wątku.</span><span class="sxs-lookup"><span data-stu-id="656e0-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="656e0-110">EnableLogMessages, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-110">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="656e0-111">Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="656e0-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="656e0-112">EnumerateAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-112">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="656e0-113">Wylicza wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="656e0-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="656e0-114">EnumerateObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-114">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="656e0-115">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="656e0-115">Not implemented.</span></span>|  
|[<span data-ttu-id="656e0-116">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-116">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="656e0-117">Pobiera dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="656e0-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="656e0-118">GetHelperThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-118">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="656e0-119">Pobiera identyfikator wątku systemu operacyjnego dla wewnętrznego wątku pomocnika debugera.</span><span class="sxs-lookup"><span data-stu-id="656e0-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="656e0-120">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-120">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="656e0-121">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="656e0-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="656e0-122">GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-122">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="656e0-123">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="656e0-123">Not implemented.</span></span>|  
|[<span data-ttu-id="656e0-124">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-124">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="656e0-125">Pobiera wystąpienie ICorDebugThread o określonym IDENTYFIKATORze wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="656e0-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="656e0-126">GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-126">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="656e0-127">Pobiera kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="656e0-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="656e0-128">IsOSSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-128">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="656e0-129">Określa, czy wątek został wstrzymany w wyniku debugera zatrzymywania procesu.</span><span class="sxs-lookup"><span data-stu-id="656e0-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="656e0-130">IsTransitionStub, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-130">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="656e0-131">Określa, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="656e0-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="656e0-132">ModifyLogSwitch, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-132">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="656e0-133">Ustawia poziom ważności określonego przełącznika dziennika.</span><span class="sxs-lookup"><span data-stu-id="656e0-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="656e0-134">ReadMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-134">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="656e0-135">Odczytuje pamięć z procesu.</span><span class="sxs-lookup"><span data-stu-id="656e0-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="656e0-136">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-136">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="656e0-137">Ustawia kontekst dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="656e0-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="656e0-138">ThreadForFiberCookie, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-138">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="656e0-139">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="656e0-139">Deprecated.</span></span>|  
|[<span data-ttu-id="656e0-140">WriteMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="656e0-140">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="656e0-141">Zapisuje dane w obszarze pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="656e0-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="656e0-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="656e0-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="656e0-143">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="656e0-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="656e0-144">Wymagania</span><span class="sxs-lookup"><span data-stu-id="656e0-144">Requirements</span></span>  
 <span data-ttu-id="656e0-145">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="656e0-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="656e0-146">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="656e0-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="656e0-147">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="656e0-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="656e0-148">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="656e0-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656e0-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="656e0-149">See also</span></span>

- [<span data-ttu-id="656e0-150">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="656e0-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="656e0-151">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="656e0-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
