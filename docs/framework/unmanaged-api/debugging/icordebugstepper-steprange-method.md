---
title: ICorDebugStepper::StepRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760536"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="38b52-102">ICorDebugStepper::StepRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="38b52-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="38b52-103">Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku i wrócić po osiągnięciu kodu poza ostatnią z określonymi zakresami.</span><span class="sxs-lookup"><span data-stu-id="38b52-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38b52-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38b52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38b52-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="38b52-106">[in] Ustaw `true` aby wejść do funkcji, która jest wywołana w wątku.</span><span class="sxs-lookup"><span data-stu-id="38b52-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="38b52-107">Ustaw `false` do kroku za pośrednictwem funkcji.</span><span class="sxs-lookup"><span data-stu-id="38b52-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="38b52-108">[in] Tablica cor_debug_step_range — struktur, z których każdy określa zakres.</span><span class="sxs-lookup"><span data-stu-id="38b52-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="38b52-109">[in] Rozmiar `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="38b52-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38b52-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38b52-110">Remarks</span></span>  
 <span data-ttu-id="38b52-111">`StepRange` Metoda działa jak [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, z tą różnicą, że nie zostanie zakończone aż do kodu, zakres zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="38b52-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="38b52-112">Może to być bardziej efektywne niż przechodzenie krok po kroku jednej instrukcji w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="38b52-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="38b52-113">Zakresy są określane jako lista par przesunięcia od początku stepper ramki.</span><span class="sxs-lookup"><span data-stu-id="38b52-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="38b52-114">Zakresy są względne wobec kod Microsoft intermediate language (MSIL) metody.</span><span class="sxs-lookup"><span data-stu-id="38b52-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="38b52-115">Wywołaj [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false` się zakresy względem kodu natywnego metody.</span><span class="sxs-lookup"><span data-stu-id="38b52-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b52-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38b52-116">Requirements</span></span>  
 <span data-ttu-id="38b52-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38b52-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38b52-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38b52-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38b52-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38b52-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38b52-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38b52-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
