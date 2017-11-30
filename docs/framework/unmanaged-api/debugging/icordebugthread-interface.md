---
title: ICorDebugThread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b5c8f0720402cce56c69394c6fbe2fb70a6177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="9667a-102">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="9667a-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="9667a-103">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="9667a-103">Represents a thread in a process.</span></span> <span data-ttu-id="9667a-104">Okres istnienia `ICorDebugThread` wystąpienie jest taki sam jak okres istnienia reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="9667a-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9667a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9667a-105">Methods</span></span>  
  
|<span data-ttu-id="9667a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-106">Method</span></span>|<span data-ttu-id="9667a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9667a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9667a-108">ClearCurrentException — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="9667a-109">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="9667a-109">This method is not implemented.</span></span> <span data-ttu-id="9667a-110">Nie używaj go.</span><span class="sxs-lookup"><span data-stu-id="9667a-110">Do not use it.</span></span>|  
|[<span data-ttu-id="9667a-111">CreateEval — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="9667a-112">Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-113">CreateStepper — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="9667a-114">Tworzy obiekt ICorDebugStepper —, który umożliwia krokowe aktywną ramkę w tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-115">EnumerateChains — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="9667a-116">Pobiera wskaźnika interfejsu, aby moduł wyliczający ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-117">GetActiveChain — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="9667a-118">Pobiera wskaźnika interfejsu do aktywnego ICorDebugChain na tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-119">GetActiveFrame — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="9667a-120">Pobiera wskaźnika interfejsu do aktywnego ICorDebugFrame na tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-121">GetAppDomain — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="9667a-122">Pobiera wskaźnika interfejsu do domeny aplikacji, w której ta `ICorDebugThread` jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="9667a-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="9667a-123">GetCurrentException — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="9667a-124">Pobiera wskaźnika interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek obecnie wywoływany przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="9667a-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="9667a-125">GetDebugState — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="9667a-126">Pobiera wartość CorDebugThreadState, które opisują bieżący stan debugowania to `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-127">GetHandle — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="9667a-128">Pobiera bieżący dojścia dla części active `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-129">GetID — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="9667a-130">Pobiera identyfikator bieżącego systemu operacyjnego części active `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-131">GetObject — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="9667a-132">Pobiera wskaźnika interfejsu do wspólnego języka wątku środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="9667a-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="9667a-133">GetProcess — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="9667a-134">Pobiera wskaźnika interfejsu, na którym znajduje się ten proces `ICorDebugThread` część stanowi.</span><span class="sxs-lookup"><span data-stu-id="9667a-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="9667a-135">GetRegisterSet — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="9667a-136">Pobiera wskaźnika interfejsu do zestawu rejestru, skojarzone z tym `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-137">GetUserState — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="9667a-138">Pobiera bitowe połączenie wartości CorDebugUserState, które opisują bieżący stan to `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9667a-139">SetDebugState — metoda</span><span class="sxs-lookup"><span data-stu-id="9667a-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="9667a-140">Ustawia bitowe połączenie `CorDebugThreadState` wartości, które opisują stan debugowania `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9667a-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9667a-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9667a-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9667a-142">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="9667a-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9667a-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9667a-143">Requirements</span></span>  
 <span data-ttu-id="9667a-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9667a-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9667a-145">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9667a-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9667a-146">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9667a-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9667a-147">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9667a-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9667a-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9667a-148">See Also</span></span>  
 [<span data-ttu-id="9667a-149">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="9667a-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
