---
title: "ICorDebugStepper::StepRange — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72a68000691dd23a55b77265cae839bea8b4ae1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="aad1d-102">ICorDebugStepper::StepRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="aad1d-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="aad1d-103">Powoduje to ICorDebugStepper — aby pojedynczy krok za pomocą jego zawierającego wątku i zwracane w przypadku osiągnie kodu poza ostatniego z określonymi zakresami.</span><span class="sxs-lookup"><span data-stu-id="aad1d-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aad1d-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aad1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aad1d-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="aad1d-106">[in] Ustaw `true` do kroku do funkcji, która jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="aad1d-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="aad1d-107">Ustaw `false` do kroku przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="aad1d-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="aad1d-108">[in] Tablica struktur COR_DEBUG_STEP_RANGE, z których każdy określa zakres.</span><span class="sxs-lookup"><span data-stu-id="aad1d-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="aad1d-109">[in] Rozmiar `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="aad1d-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad1d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aad1d-110">Remarks</span></span>  
 <span data-ttu-id="aad1d-111">`StepRange` Metody działa jak [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, z wyjątkiem tego, że nie zostanie ukończone do kodu zakres zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="aad1d-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="aad1d-112">Może to być skuteczniejsze niż krokowe wykonywanie jednej instrukcji w czasie.</span><span class="sxs-lookup"><span data-stu-id="aad1d-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="aad1d-113">Zakresy są określone jako lista par przesunięcia od początku stepper ramki.</span><span class="sxs-lookup"><span data-stu-id="aad1d-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="aad1d-114">Zakresy są względem kodu języka pośredniego (MSIL) firmy Microsoft metody.</span><span class="sxs-lookup"><span data-stu-id="aad1d-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="aad1d-115">Wywołanie [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false` aby zakresy względem kodu natywnego metody.</span><span class="sxs-lookup"><span data-stu-id="aad1d-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad1d-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aad1d-116">Requirements</span></span>  
 <span data-ttu-id="aad1d-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad1d-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aad1d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aad1d-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aad1d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aad1d-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad1d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
