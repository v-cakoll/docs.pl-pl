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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177081"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="5943a-102">ICorProfilerCallback4::ReJITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="5943a-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="5943a-103">Powiadamia profiler, że kompilator just-in-time (JIT) rozpoczął ponowne kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="5943a-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5943a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5943a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5943a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5943a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5943a-106">[w] Identyfikator funkcji, którą kompilator JIT zaczął ponownie kompilować.</span><span class="sxs-lookup"><span data-stu-id="5943a-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="5943a-107">[w] Identyfikator ponownej kompilacji nowej wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="5943a-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="5943a-108">[w] `true` aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe czekać na wątek wywołujący do powrotu z tego wywołania zwrotnego; `false` , aby wskazać, że blokowanie nie wpłynie na działanie środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="5943a-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="5943a-109">Wartość `true` nie szkodzi środowiska wykonawczego, ale może mieć wpływ na wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="5943a-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5943a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5943a-110">Remarks</span></span>  
 <span data-ttu-id="5943a-111">Istnieje możliwość odbierania więcej niż `ReJITCompilationStarted` jedną parę i [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) metoda wywołuje dla każdej funkcji ze względu na sposób, w jaki środowisko uruchomieniowe obsługuje konstruktorów klas.</span><span class="sxs-lookup"><span data-stu-id="5943a-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="5943a-112">Na przykład środowisko wykonawcze rozpoczyna ponowne kompilowanie metody A, ale konstruktor klasy dla klasy B musi zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5943a-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="5943a-113">W związku z tym środowisko wykonawcze ponownie kompiluje konstruktora dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="5943a-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="5943a-114">Gdy konstruktor jest uruchomiony, wywołuje metodę A, co powoduje, że metoda A ma zostać ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="5943a-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="5943a-115">W tym scenariuszu pierwsza ponowna kompilacja metody A jest zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="5943a-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="5943a-116">Jednak obie próby ponownej kompilacji metody A są zgłaszane ze zdarzeniami ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="5943a-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="5943a-117">Profilerzy muszą obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, gdy dwa wątki są jednocześnie wykonywanie wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="5943a-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="5943a-118">Na przykład wątek A wywołuje `ReJITCompilationStarted`; jednak przed wątkiem A wywołuje [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), wątek B wywołuje [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) z funkcją ID z wywołania zwrotnego `ReJITCompilationStarted` dla wątku A. Może się wydawać, że identyfikator funkcji nie powinien być jeszcze prawidłowy, ponieważ wywołanie [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) nie zostało jeszcze odebrane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="5943a-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="5943a-119">Jednak w tym przypadku identyfikator funkcji jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5943a-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5943a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5943a-120">Requirements</span></span>  
 <span data-ttu-id="5943a-121">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5943a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5943a-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5943a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5943a-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5943a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5943a-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5943a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5943a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5943a-125">See also</span></span>

- [<span data-ttu-id="5943a-126">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5943a-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5943a-127">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="5943a-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="5943a-128">JITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="5943a-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="5943a-129">ReJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="5943a-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
