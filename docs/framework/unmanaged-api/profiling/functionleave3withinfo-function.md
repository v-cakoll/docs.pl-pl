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
ms.openlocfilehash: a62f402fbfae6188ab0423ea7a55a4dfc6cb4112
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427400"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="65139-102">FunctionLeave3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="65139-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="65139-103">Powiadamia profiler, że formant jest zwracany przez funkcję i udostępnia dojście, które można przesłać do [metody ICorProfilerInfo3:: GetFunctionLeave3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) , aby pobrać ramkę stosu i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="65139-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65139-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65139-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65139-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65139-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="65139-106">podczas Identyfikator funkcji, z której jest zwracany formant.</span><span class="sxs-lookup"><span data-stu-id="65139-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="65139-107">podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="65139-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="65139-108">To dojście jest prawidłowe tylko w przypadku wywołania zwrotnego, do którego zostało przesłane.</span><span class="sxs-lookup"><span data-stu-id="65139-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65139-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65139-109">Remarks</span></span>  
 <span data-ttu-id="65139-110">Metoda wywołania zwrotnego `FunctionLeave3WithInfo` powiadamia profiler w miarę wywoływania funkcji i umożliwia profilerowi użycie [metody ICorProfilerInfo3:: GetFunctionLeave3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) w celu sprawdzenia wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="65139-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="65139-111">Aby można było uzyskać dostęp do informacji o wartości zwracanej, należy ustawić flagę `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="65139-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="65139-112">Profiler może użyć [metody ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń, a następnie użyć [metody ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="65139-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="65139-113">Funkcja `FunctionLeave3WithInfo` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="65139-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="65139-114">Implementacja musi używać atrybutu klasy magazynu `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="65139-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="65139-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="65139-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="65139-116">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="65139-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="65139-117">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="65139-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="65139-118">Implementacja `FunctionLeave3WithInfo` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="65139-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="65139-119">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="65139-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="65139-120">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionLeave3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="65139-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="65139-121">Funkcja `FunctionLeave3WithInfo` nie może wywoływać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="65139-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65139-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65139-122">Requirements</span></span>  
 <span data-ttu-id="65139-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65139-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65139-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="65139-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="65139-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65139-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65139-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65139-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65139-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65139-127">See also</span></span>

- [<span data-ttu-id="65139-128">Getfunctionleave3info —</span><span class="sxs-lookup"><span data-stu-id="65139-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="65139-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="65139-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="65139-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="65139-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="65139-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="65139-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="65139-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="65139-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="65139-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="65139-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="65139-134">Setenterleavefunctionhooks3 —</span><span class="sxs-lookup"><span data-stu-id="65139-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="65139-135">Setenterleavefunctionhooks3withinfo —</span><span class="sxs-lookup"><span data-stu-id="65139-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="65139-136">SetFunctionIDMapper —</span><span class="sxs-lookup"><span data-stu-id="65139-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="65139-137">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="65139-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="65139-138">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="65139-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
