---
title: ICorProfilerCallback4::ReJITCompilationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83caaa04481b4ed92407294584512b38553710b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501491"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="791e7-102">ICorProfilerCallback4::ReJITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="791e7-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="791e7-103">Powiadamia program profilujący, że kompilator just-in-time (JIT) została uruchomiona ponownie skompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="791e7-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="791e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="791e7-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="791e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="791e7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="791e7-106">[in] Identyfikator funkcji, która została uruchomiona ponownie skompilować kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="791e7-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="791e7-107">[in] Identyfikator kompilacji nową wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="791e7-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="791e7-108">[in] `true` do wskazania, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="791e7-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="791e7-109">Wartość `true` nie negatywnie wpłynąć na środowisko uruchomieniowe, ale mogą mieć wpływ na wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="791e7-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="791e7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="791e7-110">Remarks</span></span>  
 <span data-ttu-id="791e7-111">Jest to możliwe, aby otrzymać więcej niż jedną parę `ReJITCompilationStarted` i [rejitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metoda wywołuje dla każdej funkcji ze względu na sposób środowisko wykonawcze obsługuje Konstruktory klasy.</span><span class="sxs-lookup"><span data-stu-id="791e7-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="791e7-112">Na przykład środowisko uruchomieniowe uruchamia ponownie skompilować metody A, ale konstruktora klasy dla klasy B musi zostać uruchomione.</span><span class="sxs-lookup"><span data-stu-id="791e7-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="791e7-113">W związku z tym środowisko uruchomieniowe następuje rekompilacja konstruktora dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="791e7-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="791e7-114">Po uruchomieniu Konstruktora tworzy wywołanie metody A, co powoduje, że metoda A ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="791e7-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="791e7-115">W tym scenariuszu kompilację pierwszej metody A jest zatrzymywana.</span><span class="sxs-lookup"><span data-stu-id="791e7-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="791e7-116">Jednak zarówno próbuje ponownie skompilować metody, które są zgłaszane wraz z zdarzenia ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="791e7-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="791e7-117">Profilery muszą obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, w której dwa wątki jednocześnie wykorzystują wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="791e7-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="791e7-118">Na przykład, wątek A wywołuje `ReJITCompilationStarted`; jednak przed wywołań wątku A [rejitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), wywołań wątku B [icorprofilercallback::exceptionsearchfunctionenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) o identyfikatorze — funkcja z `ReJITCompilationStarted` wywołania zwrotnego dla wątku A. Wydaje się, że identyfikator funkcji nie powinny jeszcze być prawidłowy ponieważ wywołanie [rejitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) nie ma jeszcze odebrane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="791e7-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="791e7-119">Jednak w tym przypadku identyfikator funkcji jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="791e7-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="791e7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="791e7-120">Requirements</span></span>  
 <span data-ttu-id="791e7-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="791e7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="791e7-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="791e7-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="791e7-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="791e7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="791e7-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="791e7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791e7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="791e7-125">See also</span></span>
- [<span data-ttu-id="791e7-126">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="791e7-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="791e7-127">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="791e7-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="791e7-128">JITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="791e7-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="791e7-129">ReJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="791e7-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
