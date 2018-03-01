---
title: "ICorDebugStepper — Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 266e8c664ac7c5efa1b199efc522f0b890e38e3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="c7834-102">ICorDebugStepper — Interface1</span><span class="sxs-lookup"><span data-stu-id="c7834-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="c7834-103">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="c7834-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7834-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7834-104">Methods</span></span>  
  
|<span data-ttu-id="c7834-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-105">Method</span></span>|<span data-ttu-id="c7834-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c7834-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7834-107">Deactivate, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="c7834-108">Powoduje to `ICorDebugStepper` anulować ostatnie odebrała polecenie kroku.</span><span class="sxs-lookup"><span data-stu-id="c7834-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="c7834-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="c7834-110">Pobiera wartość wskazującą, czy to `ICorDebugStepper` jest w trakcie wykonywania kroku.</span><span class="sxs-lookup"><span data-stu-id="c7834-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="c7834-111">SetInterceptMask, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="c7834-112">Ustawia wartość CorDebugIntercept, która określa typy kodu, które zostaną wykorzystane do.</span><span class="sxs-lookup"><span data-stu-id="c7834-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="c7834-113">SetRangeIL, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="c7834-114">Ustawia wartość wskazującą, czy wywołań [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przekazać wartości argumentu względem kodu natywnego lub kod języka pośredniego (MSIL) firmy Microsoft metody, która jest trwa przeprowadził przez.</span><span class="sxs-lookup"><span data-stu-id="c7834-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="c7834-115">SetUnmappedStopMask, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="c7834-116">Ustawia wartość CorDebugUnmappedStop, która określa typ Niemapowane kodu, w którym zostanie zatrzymanie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c7834-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="c7834-117">Step, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="c7834-118">Powoduje to `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku oraz opcjonalnie można kontynuować krokowe funkcje, które są wywoływane w wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="c7834-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="c7834-119">StepOut, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="c7834-120">Powoduje to `ICorDebugStepper` pojedynczy krok za pomocą jego zawierającego wątku i gdy zakończenie bieżącej ramki zwraca sterowania do wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="c7834-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="c7834-121">StepRange, metoda</span><span class="sxs-lookup"><span data-stu-id="c7834-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="c7834-122">Powoduje to `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku i zwracany, gdy osiągnie kodu poza ostatniego z określonymi zakresami.</span><span class="sxs-lookup"><span data-stu-id="c7834-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7834-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7834-123">Remarks</span></span>  
 <span data-ttu-id="c7834-124">`ICorDebugStepper` Interfejs służy do następujących celów:</span><span class="sxs-lookup"><span data-stu-id="c7834-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="c7834-125">Działa ona jako identyfikator między wystawiony polecenie kroku i wykonanie tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c7834-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="c7834-126">Zapewnia centralnego interfejsu hermetyzacji wszystkich stepping, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="c7834-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="c7834-127">Zapewnia sposób przedwcześnie anulować operację wykonywania krokowego.</span><span class="sxs-lookup"><span data-stu-id="c7834-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="c7834-128">Może istnieć więcej niż jeden stepper na wątek.</span><span class="sxs-lookup"><span data-stu-id="c7834-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="c7834-129">Na przykład punkt przerwania można napotkać podczas pominięcie funkcję, a użytkownik może chcesz uruchomić nowej operacji wykonywania krokowego wewnątrz tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7834-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="c7834-130">Jest debugera, aby określić sposób obsługi tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="c7834-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="c7834-131">Debuger może być zagnieździć tych dwóch operacji lub Anuluj operację wykonywania krokowego.</span><span class="sxs-lookup"><span data-stu-id="c7834-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="c7834-132">`ICorDebugStepper` Interfejs obsługuje obie te opcje.</span><span class="sxs-lookup"><span data-stu-id="c7834-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="c7834-133">Obiekt stepper może dokonać migracji między wątkami, jeśli środowisko uruchomieniowe języka wspólnego (CLR) nawiązuje połączenie między wątku, organizowane.</span><span class="sxs-lookup"><span data-stu-id="c7834-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7834-134">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="c7834-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7834-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7834-135">Requirements</span></span>  
 <span data-ttu-id="c7834-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7834-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7834-137">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7834-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7834-138">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7834-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7834-139">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7834-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7834-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7834-140">See Also</span></span>  
 [<span data-ttu-id="c7834-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c7834-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
