---
title: "FunctionLeave3WithInfo — Funkcja"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f787b5bd78a575d862c198daeee99a0704734276
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="7f8cf-102">FunctionLeave3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7f8cf-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="7f8cf-103">Powiadamia profilera, że formant zostały zwrócone z funkcji, a także uchwytu, które mogą zostać przekazane do [ICorProfilerInfo3::GetFunctionLeave3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) można pobrać ramki stosu oraz wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f8cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f8cf-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f8cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f8cf-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="7f8cf-106">[in] Identyfikator funkcji zwróceniem sterowania.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7f8cf-107">[in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7f8cf-108">Ta dojścia jest prawidłowy tylko w trakcie wywołania zwrotnego, do którego jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f8cf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f8cf-109">Remarks</span></span>  
 <span data-ttu-id="7f8cf-110">`FunctionLeave3WithInfo` Metody wywołania zwrotnego powiadamia profilera funkcje są nazywane i pozwala profiler do użycia [ICorProfilerInfo3::GetFunctionLeave3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) do zbadania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="7f8cf-111">Dostęp do informacji zwracanej wartości, `COR_PRF_ENABLE_FUNCTION_RETVAL` flagi musi zostać ustawione.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="7f8cf-112">Profiler można użyć [ICorProfilerInfo::SetEventMask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) Ustaw flagi zdarzeń, a następnie użyć [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania użytkownika Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7f8cf-113">`FunctionLeave3WithInfo` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="7f8cf-114">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7f8cf-115">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="7f8cf-116">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="7f8cf-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="7f8cf-117">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7f8cf-118">Implementacja `FunctionLeave3WithInfo` nie zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="7f8cf-119">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7f8cf-120">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="7f8cf-121">`FunctionLeave3WithInfo` Funkcji nie musi wywołania wewnątrz kodu zarządzanego lub spowodować przydział pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="7f8cf-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f8cf-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f8cf-122">Requirements</span></span>  
 <span data-ttu-id="7f8cf-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f8cf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f8cf-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7f8cf-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7f8cf-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f8cf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f8cf-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f8cf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8cf-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f8cf-127">See Also</span></span>  
 [<span data-ttu-id="7f8cf-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="7f8cf-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)  
 [<span data-ttu-id="7f8cf-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="7f8cf-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="7f8cf-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="7f8cf-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="7f8cf-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="7f8cf-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="7f8cf-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7f8cf-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="7f8cf-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7f8cf-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="7f8cf-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="7f8cf-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="7f8cf-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7f8cf-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="7f8cf-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7f8cf-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="7f8cf-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7f8cf-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="7f8cf-138">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7f8cf-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
