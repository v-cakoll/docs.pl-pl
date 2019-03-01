---
title: ICorDebugStepper — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bd650178c787440941b9fd9a84b1e85c55aac61
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973720"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="b0c11-102">ICorDebugStepper — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b0c11-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="b0c11-103">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="b0c11-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0c11-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0c11-104">Methods</span></span>  
  
|<span data-ttu-id="b0c11-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-105">Method</span></span>|<span data-ttu-id="b0c11-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b0c11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0c11-107">Deactivate, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="b0c11-108">Powoduje to, że `ICorDebugStepper` ostatnie polecenie kroku otrzymał anulowania.</span><span class="sxs-lookup"><span data-stu-id="b0c11-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="b0c11-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="b0c11-110">Pobiera wartość wskazującą, czy to `ICorDebugStepper` jest w trakcie wykonywania kroku.</span><span class="sxs-lookup"><span data-stu-id="b0c11-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="b0c11-111">SetInterceptMask, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="b0c11-112">Ustawia wartość cordebugintercept —, który określa typy kodu, które zostaną wykorzystane do.</span><span class="sxs-lookup"><span data-stu-id="b0c11-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="b0c11-113">SetRangeIL, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="b0c11-114">Ustawia wartość wskazującą, czy wywołania [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przekazywanie wartości argumentu względem kodu natywnego lub kod intermediate language (MSIL) firmy Microsoft metody, która jest jest zmieniana za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="b0c11-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="b0c11-115">SetUnmappedStopMask, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="b0c11-116">Ustawia wartość cordebugunmappedstop —, określający typ niezamapowane kodu, w którym wykonywanie zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="b0c11-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="b0c11-117">Step, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="b0c11-118">Powoduje to, że `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku i, opcjonalnie, aby kontynuować, krokowe funkcje, które są wywoływane w wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="b0c11-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="b0c11-119">StepOut, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="b0c11-120">Powoduje to, że `ICorDebugStepper` krokowej za pośrednictwem jego zawierającego wątku i gdy zakończenie bieżącej ramki zwraca sterowanie do wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="b0c11-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="b0c11-121">StepRange, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c11-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="b0c11-122">Powoduje to, że `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku, a także do zwrócenia, gdy osiągnie kod poza ostatnią z określonymi zakresami.</span><span class="sxs-lookup"><span data-stu-id="b0c11-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0c11-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0c11-123">Remarks</span></span>  
 <span data-ttu-id="b0c11-124">`ICorDebugStepper` Interfejsu służy do następujących celów:</span><span class="sxs-lookup"><span data-stu-id="b0c11-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="b0c11-125">Działa ona jako identyfikator między polecenie kroku, wydawanego i wykonania tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="b0c11-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="b0c11-126">Go udostępnia interfejs centralny do hermetyzacji wszystkich przechodzenie krok po kroku, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b0c11-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="b0c11-127">Zapewnia sposób przedwcześnie anulowania operacji przechodzenia krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="b0c11-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="b0c11-128">Może istnieć więcej niż jeden stepper na wątek.</span><span class="sxs-lookup"><span data-stu-id="b0c11-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="b0c11-129">Na przykład może trafień punktu przerwania w wchodząc funkcji, a użytkownik może chcesz uruchomić nowej operacji przechodzenia krok po kroku wewnątrz tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b0c11-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="b0c11-130">Jest debugera, aby określić sposób obsłużyć taką sytuację.</span><span class="sxs-lookup"><span data-stu-id="b0c11-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="b0c11-131">Debuger może być zagnieździć dwóch operacji lub Anuluj operację przechodzenia krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="b0c11-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="b0c11-132">`ICorDebugStepper` Interfejs obsługuje obie te opcje.</span><span class="sxs-lookup"><span data-stu-id="b0c11-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="b0c11-133">Stepper mogą dokonać migracji między wątkami, jeśli wywołanie cross Threading, zorganizowanej sprawia, że środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b0c11-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0c11-134">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="b0c11-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0c11-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0c11-135">Requirements</span></span>  
 <span data-ttu-id="b0c11-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0c11-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0c11-137">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0c11-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0c11-138">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0c11-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0c11-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0c11-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c11-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0c11-140">See also</span></span>
- [<span data-ttu-id="b0c11-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b0c11-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
