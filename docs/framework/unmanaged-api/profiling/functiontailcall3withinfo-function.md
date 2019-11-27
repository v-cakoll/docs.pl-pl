---
title: FunctionTailcall3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: 202aed64de78675c79f998afb4483e0d19b811de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445969"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="dbace-102">FunctionTailcall3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="dbace-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="dbace-103">Powiadamia program profilujący, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i udostępnia dojście, które może zostać przesłane do [metody ICorProfilerInfo3:: GetFunctionTailcall3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) w celu pobrania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="dbace-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbace-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbace-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbace-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbace-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="dbace-106">podczas Identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="dbace-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="dbace-107">podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="dbace-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="dbace-108">To dojście jest prawidłowe tylko w przypadku wywołania zwrotnego, do którego zostało przesłane.</span><span class="sxs-lookup"><span data-stu-id="dbace-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbace-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbace-109">Remarks</span></span>  
 <span data-ttu-id="dbace-110">Metoda wywołania zwrotnego `FunctionTailcall3WithInfo` powiadamia profiler w miarę wywoływania funkcji i umożliwia profilerowi użycie [metody ICorProfilerInfo3:: GetFunctionTailcall3Info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) w celu sprawdzenia ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="dbace-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="dbace-111">Aby uzyskać dostęp do informacji o ramce stosu, należy ustawić flagę `COR_PRF_ENABLE_FRAME_INFO`.</span><span class="sxs-lookup"><span data-stu-id="dbace-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="dbace-112">Profiler może użyć [metody ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń, a następnie użyć [metody ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dbace-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="dbace-113">Funkcja `FunctionTailcall3WithInfo` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="dbace-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="dbace-114">Implementacja musi używać atrybutu klasy magazynu `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="dbace-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="dbace-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dbace-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="dbace-116">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="dbace-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="dbace-117">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="dbace-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="dbace-118">Implementacja `FunctionTailcall3WithInfo` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dbace-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="dbace-119">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dbace-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="dbace-120">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionTailcall3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="dbace-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="dbace-121">Ponadto funkcja FunctionTailcall3WithInfo nie może wywoływać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="dbace-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbace-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbace-122">Requirements</span></span>  
 <span data-ttu-id="dbace-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbace-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbace-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="dbace-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dbace-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dbace-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbace-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbace-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbace-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbace-127">See also</span></span>

- [<span data-ttu-id="dbace-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="dbace-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="dbace-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="dbace-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="dbace-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="dbace-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="dbace-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="dbace-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="dbace-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="dbace-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="dbace-133">Setenterleavefunctionhooks3 —</span><span class="sxs-lookup"><span data-stu-id="dbace-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="dbace-134">Setenterleavefunctionhooks3withinfo —</span><span class="sxs-lookup"><span data-stu-id="dbace-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="dbace-135">SetFunctionIDMapper —</span><span class="sxs-lookup"><span data-stu-id="dbace-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="dbace-136">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="dbace-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="dbace-137">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="dbace-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
