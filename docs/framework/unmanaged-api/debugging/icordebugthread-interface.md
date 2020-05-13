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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379817"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="aa63b-102">ICorDebugThread, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa63b-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="aa63b-103">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="aa63b-103">Represents a thread in a process.</span></span> <span data-ttu-id="aa63b-104">Okres istnienia `ICorDebugThread` wystąpienia jest taki sam jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="aa63b-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa63b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aa63b-105">Methods</span></span>  
  
|<span data-ttu-id="aa63b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-106">Method</span></span>|<span data-ttu-id="aa63b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aa63b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa63b-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="aa63b-109">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="aa63b-109">This method is not implemented.</span></span> <span data-ttu-id="aa63b-110">Nie używaj go.</span><span class="sxs-lookup"><span data-stu-id="aa63b-110">Do not use it.</span></span>|  
|[<span data-ttu-id="aa63b-111">CreateEval, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="aa63b-112">Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-113">CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="aa63b-114">Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę w tym elemencie `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-115">EnumerateChains, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="aa63b-116">Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym elemencie `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-117">GetActiveChain, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="aa63b-118">Pobiera wskaźnik interfejsu do aktywnego ICorDebugChain `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-119">GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="aa63b-120">Pobiera wskaźnik interfejsu do aktywnego ICorDebugFrame `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-121">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="aa63b-122">Pobiera wskaźnik interfejsu do domeny aplikacji, w której `ICorDebugThread` jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="aa63b-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="aa63b-123">GetCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="aa63b-124">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="aa63b-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="aa63b-125">GetDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="aa63b-126">Pobiera wartość CorDebugThreadState —, która opisuje bieżący stan debugowania tego elementu `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-127">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="aa63b-128">Pobiera bieżące dojście dla aktywnej części tego elementu `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-129">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="aa63b-130">Pobiera bieżący identyfikator systemu operacyjnego aktywnej części tego elementu `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-131">GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="aa63b-132">Pobiera wskaźnik interfejsu do wątku środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="aa63b-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="aa63b-133">GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="aa63b-134">Pobiera wskaźnik interfejsu do procesu, którego `ICorDebugThread` częścią jest ten element.</span><span class="sxs-lookup"><span data-stu-id="aa63b-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="aa63b-135">GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="aa63b-136">Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonego z tym elementem `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-137">GetUserState, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="aa63b-138">Pobiera bitową kombinację wartości CorDebugUserState —, które opisują bieżący stan tego elementu `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="aa63b-139">SetDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="aa63b-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="aa63b-140">Ustawia bitową kombinację `CorDebugThreadState` wartości opisujących stan debugowania tego elementu `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="aa63b-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa63b-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa63b-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa63b-142">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="aa63b-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa63b-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa63b-143">Requirements</span></span>  
 <span data-ttu-id="aa63b-144">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa63b-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa63b-145">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa63b-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa63b-146">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aa63b-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa63b-147">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa63b-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa63b-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa63b-148">See also</span></span>

- [<span data-ttu-id="aa63b-149">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="aa63b-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
