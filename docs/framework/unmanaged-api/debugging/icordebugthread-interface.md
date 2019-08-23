---
title: ICorDebugThread, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923142"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="e7177-102">ICorDebugThread, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7177-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="e7177-103">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="e7177-103">Represents a thread in a process.</span></span> <span data-ttu-id="e7177-104">Okres istnienia `ICorDebugThread` wystąpienia jest taki sam jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="e7177-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7177-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e7177-105">Methods</span></span>  
  
|<span data-ttu-id="e7177-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-106">Method</span></span>|<span data-ttu-id="e7177-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e7177-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7177-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="e7177-109">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="e7177-109">This method is not implemented.</span></span> <span data-ttu-id="e7177-110">Nie używaj go.</span><span class="sxs-lookup"><span data-stu-id="e7177-110">Do not use it.</span></span>|  
|[<span data-ttu-id="e7177-111">CreateEval, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="e7177-112">Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="e7177-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-113">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="e7177-114">Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę `ICorDebugThread`w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="e7177-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-115">EnumerateChains, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="e7177-116">Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu `ICorDebugThread`w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="e7177-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-117">GetActiveChain, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="e7177-118">Pobiera wskaźnik interfejsu do aktywnego ICorDebugChain `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="e7177-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-119">GetActiveFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="e7177-120">Pobiera wskaźnik interfejsu do aktywnego ICorDebugFrame `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="e7177-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-121">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="e7177-122">Pobiera wskaźnik interfejsu do domeny aplikacji, w której `ICorDebugThread` jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e7177-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="e7177-123">GetCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="e7177-124">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="e7177-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="e7177-125">GetDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="e7177-126">Pobiera wartość CorDebugThreadState —, która opisuje bieżący stan debugowania tego `ICorDebugThread`elementu.</span><span class="sxs-lookup"><span data-stu-id="e7177-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-127">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="e7177-128">Pobiera bieżące dojście dla aktywnej części tego `ICorDebugThread`elementu.</span><span class="sxs-lookup"><span data-stu-id="e7177-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-129">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="e7177-130">Pobiera bieżący identyfikator systemu operacyjnego aktywnej części tego `ICorDebugThread`elementu.</span><span class="sxs-lookup"><span data-stu-id="e7177-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-131">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="e7177-132">Pobiera wskaźnik interfejsu do wątku środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e7177-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="e7177-133">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="e7177-134">Pobiera wskaźnik interfejsu do procesu, którego częścią jest `ICorDebugThread` ten element.</span><span class="sxs-lookup"><span data-stu-id="e7177-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="e7177-135">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="e7177-136">Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonego z tym `ICorDebugThread`elementem.</span><span class="sxs-lookup"><span data-stu-id="e7177-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-137">GetUserState, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="e7177-138">Pobiera bitową kombinację wartości CorDebugUserState —, które opisują bieżący stan tego `ICorDebugThread`elementu.</span><span class="sxs-lookup"><span data-stu-id="e7177-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e7177-139">SetDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="e7177-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="e7177-140">Ustawia bitową kombinację `CorDebugThreadState` wartości opisujących stan debugowania tego `ICorDebugThread`elementu.</span><span class="sxs-lookup"><span data-stu-id="e7177-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7177-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7177-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7177-142">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e7177-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7177-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7177-143">Requirements</span></span>  
 <span data-ttu-id="e7177-144">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7177-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7177-145">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7177-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7177-146">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7177-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7177-147">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7177-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7177-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7177-148">See also</span></span>

- [<span data-ttu-id="e7177-149">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e7177-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
