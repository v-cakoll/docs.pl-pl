---
title: ICorDebugStepper, interfejs
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
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962688"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="137a6-102">ICorDebugStepper, interfejs</span><span class="sxs-lookup"><span data-stu-id="137a6-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="137a6-103">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="137a6-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="137a6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="137a6-104">Methods</span></span>  
  
|<span data-ttu-id="137a6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-105">Method</span></span>|<span data-ttu-id="137a6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="137a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="137a6-107">Deactivate, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="137a6-108">`ICorDebugStepper` Powoduje, że zostanie anulowane odebrane polecenie ostatniego kroku.</span><span class="sxs-lookup"><span data-stu-id="137a6-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="137a6-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="137a6-110">Pobiera wartość wskazującą, czy `ICorDebugStepper` aktualnie wykonuje krok.</span><span class="sxs-lookup"><span data-stu-id="137a6-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="137a6-111">SetInterceptMask, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="137a6-112">Ustawia wartość CorDebugIntercept —, która określa typy kodu, do których nastąpi.</span><span class="sxs-lookup"><span data-stu-id="137a6-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="137a6-113">SetRangeIL, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="137a6-114">Ustawia wartość wskazującą, czy wywołania [ICorDebugStepper:: StepRange —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przechodzą wartości argumentów względem kodu natywnego lub kodu języka pośredniego firmy Microsoft (MSIL) metody, która jest testowana przez.</span><span class="sxs-lookup"><span data-stu-id="137a6-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="137a6-115">SetUnmappedStopMask, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="137a6-116">Ustawia wartość CorDebugUnmappedStop —, która określa typ niezamapowanego kodu, w którym wykonanie zostanie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="137a6-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="137a6-117">Step, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="137a6-118">Powoduje, `ICorDebugStepper` że jest to jeden krok poprzez zawierający go wątek i opcjonalnie, aby kontynuować wykonywanie pojedynczej czynności przez funkcje, które są wywoływane w wątku.</span><span class="sxs-lookup"><span data-stu-id="137a6-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="137a6-119">StepOut, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="137a6-120">Powoduje, `ICorDebugStepper` że jest to jeden krok za pomocą zawartego w nim wątku oraz do zakończenia, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.</span><span class="sxs-lookup"><span data-stu-id="137a6-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="137a6-121">StepRange, metoda</span><span class="sxs-lookup"><span data-stu-id="137a6-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="137a6-122">Powoduje, `ICorDebugStepper` że jest to jeden krok przez zawierający go wątek i zwraca, gdy osiągnie kod poza ostatnim z określonych zakresów.</span><span class="sxs-lookup"><span data-stu-id="137a6-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="137a6-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="137a6-123">Remarks</span></span>  
 <span data-ttu-id="137a6-124">`ICorDebugStepper` Interfejs służy do następujących celów:</span><span class="sxs-lookup"><span data-stu-id="137a6-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="137a6-125">Pełni rolę identyfikatora między wydanym poleceniem kroku a ukończeniem tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="137a6-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="137a6-126">Udostępnia centralny interfejs do hermetyzacji wszystkich kroków, które można wykonać.</span><span class="sxs-lookup"><span data-stu-id="137a6-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="137a6-127">Umożliwia przedwczesne anulowanie operacji wykonywania kroku.</span><span class="sxs-lookup"><span data-stu-id="137a6-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="137a6-128">Może istnieć więcej niż jeden stepper na wątek.</span><span class="sxs-lookup"><span data-stu-id="137a6-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="137a6-129">Na przykład punkt przerwania może być trafiony podczas przechodzenia przez funkcję, a użytkownik może chcieć rozpocząć nową operację krokową w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="137a6-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="137a6-130">Aby określić, jak obsługiwać tę sytuację, należy do debugera.</span><span class="sxs-lookup"><span data-stu-id="137a6-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="137a6-131">Debuger może chcieć anulować pierwotną operację taktowania lub zagnieździć dwie operacje.</span><span class="sxs-lookup"><span data-stu-id="137a6-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="137a6-132">`ICorDebugStepper` Interfejs obsługuje obie opcje.</span><span class="sxs-lookup"><span data-stu-id="137a6-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="137a6-133">Stepper może migrować między wątkami, jeśli środowisko uruchomieniowe języka wspólnego (CLR) wykonuje połączenie organizowane przez wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="137a6-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="137a6-134">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="137a6-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137a6-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="137a6-135">Requirements</span></span>  
 <span data-ttu-id="137a6-136">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137a6-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137a6-137">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="137a6-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="137a6-138">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="137a6-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="137a6-139">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="137a6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137a6-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="137a6-140">See also</span></span>

- [<span data-ttu-id="137a6-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="137a6-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
