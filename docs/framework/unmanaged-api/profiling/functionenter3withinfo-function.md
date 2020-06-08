---
title: FunctionEnter3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: ff4b32185e604611eaaead2847c11bc139d405a6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500692"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="0aff6-102">FunctionEnter3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0aff6-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="0aff6-103">Powiadamia profiler, że formant jest przesyłany do funkcji i udostępnia dojście, które może być przekazane do [metody ICorProfilerInfo3:: GetFunctionEnter3Info —](icorprofilerinfo3-getfunctionenter3info-method.md) w celu pobrania ramki stosu i argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="0aff6-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aff6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0aff6-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aff6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0aff6-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="0aff6-106">\[in) identyfikator funkcji, do której jest przenoszona kontrola.</span><span class="sxs-lookup"><span data-stu-id="0aff6-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="0aff6-107">\[w] nieprzezroczysty uchwyt reprezentujący informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="0aff6-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="0aff6-108">To dojście jest prawidłowe tylko w przypadku wywołania zwrotnego, do którego zostało przesłane.</span><span class="sxs-lookup"><span data-stu-id="0aff6-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0aff6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0aff6-109">Remarks</span></span>  
 <span data-ttu-id="0aff6-110">`FunctionEnter3WithInfo`Metoda wywołania zwrotnego powiadamia profiler w miarę wywoływania funkcji i umożliwia profilerowi użycie [metody ICorProfilerInfo3:: GetFunctionEnter3Info —](icorprofilerinfo3-getfunctionenter3info-method.md) w celu sprawdzenia wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="0aff6-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="0aff6-111">Aby uzyskać dostęp do informacji o argumencie, `COR_PRF_ENABLE_FUNCTION_ARGS` należy ustawić flagę.</span><span class="sxs-lookup"><span data-stu-id="0aff6-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="0aff6-112">Profiler może użyć [metody ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń, a następnie użyć [metody ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo —](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0aff6-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="0aff6-113">`FunctionEnter3WithInfo`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="0aff6-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="0aff6-114">Implementacja musi używać `__declspec(naked)` atrybutu klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="0aff6-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="0aff6-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0aff6-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0aff6-116">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="0aff6-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0aff6-117">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0aff6-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0aff6-118">Implementacja `FunctionEnter3WithInfo` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0aff6-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="0aff6-119">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0aff6-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0aff6-120">W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionEnter3WithInfo` powracania.</span><span class="sxs-lookup"><span data-stu-id="0aff6-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="0aff6-121">`FunctionEnter3WithInfo`Funkcja nie może wywołać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="0aff6-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aff6-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0aff6-122">Requirements</span></span>  
 <span data-ttu-id="0aff6-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aff6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aff6-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="0aff6-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0aff6-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0aff6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aff6-126">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aff6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aff6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0aff6-127">See also</span></span>

- [<span data-ttu-id="0aff6-128">Getfunctionenter3info —</span><span class="sxs-lookup"><span data-stu-id="0aff6-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="0aff6-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="0aff6-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="0aff6-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0aff6-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="0aff6-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0aff6-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
