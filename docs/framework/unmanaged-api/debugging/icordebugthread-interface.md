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
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184707"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="5f043-102">ICorDebugThread, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f043-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="5f043-103">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="5f043-103">Represents a thread in a process.</span></span> <span data-ttu-id="5f043-104">Okres istnienia `ICorDebugThread` wystąpienie jest taki sam, jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="5f043-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f043-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5f043-105">Methods</span></span>  
  
|<span data-ttu-id="5f043-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-106">Method</span></span>|<span data-ttu-id="5f043-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5f043-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f043-108">ClearCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="5f043-109">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="5f043-109">This method is not implemented.</span></span> <span data-ttu-id="5f043-110">Nie używaj go.</span><span class="sxs-lookup"><span data-stu-id="5f043-110">Do not use it.</span></span>|  
|[<span data-ttu-id="5f043-111">CreateEval, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="5f043-112">Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-113">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="5f043-114">Tworzy obiekt ICorDebugStepper —, który umożliwia krokowe wykonywanie aktywnej ramki, w tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-115">EnumerateChains, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="5f043-116">Pobiera wskaźnik interfejsu do moduł wyliczający icordebugchainenum —, który zawiera wszystkie łańcuchów stosu, w tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-117">GetActiveChain, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="5f043-118">Pobiera wskaźnik interfejsu do aktywnego icordebugchain — w tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-119">GetActiveFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="5f043-120">Pobiera wskaźnik interfejsu do aktywnego icordebugframe — w tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-121">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="5f043-122">Pobiera wskaźnik interfejsu do domeny aplikacji, w którym znajduje się ten `ICorDebugThread` jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5f043-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="5f043-123">GetCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="5f043-124">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, która reprezentuje wyjątek zgłaszane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="5f043-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="5f043-125">GetDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="5f043-126">Pobiera wartość cordebugthreadstate —, który opisuje bieżący stan debugowania tego `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-127">GetHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="5f043-128">Pobiera bieżący uchwytu dla części active `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-129">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="5f043-130">Pobiera identyfikator bieżącego systemu operacyjnego części active `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-131">GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="5f043-132">Pobiera wskaźnik interfejsu do wspólnym mianownikiem języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5f043-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="5f043-133">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="5f043-134">Pobiera wskaźnik interfejsu do procesu, którego należy to `ICorDebugThread` część stanowi.</span><span class="sxs-lookup"><span data-stu-id="5f043-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="5f043-135">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="5f043-136">Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonych z tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-137">GetUserState, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="5f043-138">Pobiera bitowa kombinacja wartości cordebuguserstate —, które opisują bieżący stan to `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f043-139">SetDebugState, metoda</span><span class="sxs-lookup"><span data-stu-id="5f043-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="5f043-140">Bitowa kombinacja ustawia `CorDebugThreadState` wartości, które opisują stan debugowania `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5f043-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f043-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f043-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f043-142">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5f043-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f043-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f043-143">Requirements</span></span>  
 <span data-ttu-id="5f043-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f043-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f043-145">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f043-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f043-146">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f043-146">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5f043-147">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5f043-147">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f043-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f043-148">See also</span></span>

- [<span data-ttu-id="5f043-149">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5f043-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
