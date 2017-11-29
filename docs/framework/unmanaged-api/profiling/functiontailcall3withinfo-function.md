---
title: "FunctionTailcall3WithInfo — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3WithInfo
helpviewer_keywords: FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c22f00678f707df04a69104fedef87aa6d5e3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="a6edc-102">FunctionTailcall3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a6edc-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="a6edc-103">Powiadamia profilera, który aktualnie wykonywane funkcji ma wykonywać wywołania tail do innej funkcji, a także uchwytu, które mogą zostać przekazane do [ICorProfilerInfo3::GetFunctionTailcall3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) do pobrania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="a6edc-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6edc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6edc-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6edc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6edc-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="a6edc-106">[in] Identyfikator aktualnie wykonywane funkcji, która wprowadzi tail wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6edc-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="a6edc-107">[in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="a6edc-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="a6edc-108">Ta dojścia jest prawidłowy tylko w trakcie wywołania zwrotnego, do którego jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="a6edc-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6edc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6edc-109">Remarks</span></span>  
 <span data-ttu-id="a6edc-110">`FunctionTailcall3WithInfo` Metody wywołania zwrotnego powiadamia profilera funkcje są nazywane i pozwala profiler do użycia [ICorProfilerInfo3::GetFunctionTailcall3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) do zbadania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="a6edc-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="a6edc-111">Dostęp do informacji ramki stosu, `COR_PRF_ENABLE_FRAME_INFO` flagi musi zostać ustawione.</span><span class="sxs-lookup"><span data-stu-id="a6edc-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="a6edc-112">Profiler można użyć [ICorProfilerInfo::SetEventMask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) Ustaw flagi zdarzeń, a następnie użyć [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania użytkownika Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6edc-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a6edc-113">`FunctionTailcall3WithInfo` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="a6edc-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="a6edc-114">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="a6edc-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a6edc-115">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6edc-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="a6edc-116">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="a6edc-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="a6edc-117">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a6edc-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a6edc-118">Implementacja `FunctionTailcall3WithInfo` nie zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a6edc-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="a6edc-119">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="a6edc-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a6edc-120">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionTailcall3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="a6edc-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="a6edc-121">Functiontailcall3withinfo — funkcja nie musi także wywołania wewnątrz kodu zarządzanego lub spowodować przydział pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="a6edc-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6edc-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6edc-122">Requirements</span></span>  
 <span data-ttu-id="a6edc-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6edc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6edc-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a6edc-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a6edc-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6edc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6edc-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6edc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6edc-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6edc-127">See Also</span></span>  
 [<span data-ttu-id="a6edc-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a6edc-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="a6edc-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a6edc-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="a6edc-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a6edc-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="a6edc-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a6edc-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="a6edc-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a6edc-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="a6edc-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a6edc-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="a6edc-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a6edc-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="a6edc-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a6edc-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="a6edc-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a6edc-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="a6edc-137">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="a6edc-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
