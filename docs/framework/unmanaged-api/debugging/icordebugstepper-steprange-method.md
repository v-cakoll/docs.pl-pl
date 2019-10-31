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
ms.openlocfilehash: 2ca4542fe42fab0b5ff54b23b9492d3906698c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120620"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="a635c-102">ICorDebugStepper::StepRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="a635c-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="a635c-103">Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku i zwraca, gdy osiągnie kod poza ostatnim z określonych zakresów.</span><span class="sxs-lookup"><span data-stu-id="a635c-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a635c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a635c-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a635c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a635c-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="a635c-106">podczas Ustaw, aby `true` wkroczyć do funkcji, która jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="a635c-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="a635c-107">Ustaw na `false`, aby przekroczyć funkcję.</span><span class="sxs-lookup"><span data-stu-id="a635c-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="a635c-108">podczas Tablica struktur COR_DEBUG_STEP_RANGE, z których każdy określa zakres.</span><span class="sxs-lookup"><span data-stu-id="a635c-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="a635c-109">podczas Rozmiar tablicy `ranges`.</span><span class="sxs-lookup"><span data-stu-id="a635c-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a635c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a635c-110">Remarks</span></span>  
 <span data-ttu-id="a635c-111">Metoda `StepRange` działa jak Metoda [ICorDebugStepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) , z tą różnicą, że nie zostanie ukończona, dopóki nie zostanie osiągnięty kod poza podanym zakresem.</span><span class="sxs-lookup"><span data-stu-id="a635c-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="a635c-112">Może to być wydajniejsze niż wykonywanie jednej instrukcji w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="a635c-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="a635c-113">Zakresy są określone jako lista par przesunięcia od początku ramki stepper.</span><span class="sxs-lookup"><span data-stu-id="a635c-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="a635c-114">Zakresy są względne dla kodu języka pośredniego firmy Microsoft (MSIL) metody.</span><span class="sxs-lookup"><span data-stu-id="a635c-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="a635c-115">Wywołaj [ICorDebugStepper:: SetRangeIL —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false`, aby uczynić zakresy względem kodu natywnego metody.</span><span class="sxs-lookup"><span data-stu-id="a635c-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a635c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a635c-116">Requirements</span></span>  
 <span data-ttu-id="a635c-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a635c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a635c-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a635c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a635c-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a635c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a635c-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a635c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
