---
title: FunctionLeave3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: f7a945fb7ef10f995be2d779a88b98bbce2fdfb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866846"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="b6270-102">FunctionLeave3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b6270-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="b6270-103">Powiadamia profiler, że formant jest zwracany przez funkcję i udostępnia dojście, które można przesłać do [metody ICorProfilerInfo3:: GetFunctionLeave3Info —](icorprofilerinfo3-getfunctionleave3info-method.md) , aby pobrać ramkę stosu i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="b6270-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6270-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6270-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6270-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6270-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="b6270-106">\[in) identyfikator funkcji, z której jest zwracany formant.</span><span class="sxs-lookup"><span data-stu-id="b6270-106">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="b6270-107">\[w] nieprzezroczysty uchwyt reprezentujący informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="b6270-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b6270-108">To dojście jest prawidłowe tylko w przypadku wywołania zwrotnego, do którego zostało przesłane.</span><span class="sxs-lookup"><span data-stu-id="b6270-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6270-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6270-109">Remarks</span></span>  
 <span data-ttu-id="b6270-110">Metoda wywołania zwrotnego `FunctionLeave3WithInfo` powiadamia profiler w miarę wywoływania funkcji i umożliwia profilerowi użycie [metody ICorProfilerInfo3:: GetFunctionLeave3Info —](icorprofilerinfo3-getfunctionleave3info-method.md) w celu sprawdzenia wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="b6270-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="b6270-111">Aby można było uzyskać dostęp do informacji o wartości zwracanej, należy ustawić flagę `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="b6270-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="b6270-112">Profiler może użyć [metody ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń, a następnie użyć [metody ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo —](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b6270-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b6270-113">Funkcja `FunctionLeave3WithInfo` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="b6270-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="b6270-114">Implementacja musi używać atrybutu klasy magazynu `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="b6270-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b6270-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b6270-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b6270-116">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="b6270-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b6270-117">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="b6270-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b6270-118">Implementacja `FunctionLeave3WithInfo` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b6270-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="b6270-119">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b6270-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b6270-120">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionLeave3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="b6270-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="b6270-121">Funkcja `FunctionLeave3WithInfo` nie może wywoływać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="b6270-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6270-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6270-122">Requirements</span></span>  
 <span data-ttu-id="b6270-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6270-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6270-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b6270-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b6270-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6270-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6270-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6270-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6270-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6270-127">See also</span></span>

- [<span data-ttu-id="b6270-128">Getfunctionleave3info —</span><span class="sxs-lookup"><span data-stu-id="b6270-128">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="b6270-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="b6270-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="b6270-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="b6270-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="b6270-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="b6270-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="b6270-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b6270-132">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="b6270-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b6270-133">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b6270-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="b6270-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="b6270-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b6270-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="b6270-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="b6270-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="b6270-137">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="b6270-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="b6270-138">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b6270-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
