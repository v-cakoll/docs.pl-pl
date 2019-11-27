---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 5d3fe6691a2d9989de002bad09c2e8f66a094f56
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448434"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="75ac3-102">ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="75ac3-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="75ac3-103">Powiadamia profiler o rozpoczęciu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu natywnego generatora obrazu (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="75ac3-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ac3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75ac3-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75ac3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75ac3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="75ac3-106">podczas Identyfikator funkcji, dla której jest wykonywane wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="75ac3-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="75ac3-107">[out] `true`, jeśli aparat wykonywania powinien używać buforowanej wersji funkcji (jeśli jest dostępna); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="75ac3-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="75ac3-108">Jeśli wartość jest `false`, aparat wykonywania JIT — kompiluje funkcję zamiast korzystania z wersji, która nie jest skompilowana przez JIT.</span><span class="sxs-lookup"><span data-stu-id="75ac3-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75ac3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75ac3-109">Remarks</span></span>  
 <span data-ttu-id="75ac3-110">W .NET Framework w wersji 2,0 metody wywołania zwrotne `JITCachedFunctionSearchStarted` i [ICorProfilerCallback:: JITCachedFunctionSearchFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) nie będą wykonywane dla wszystkich funkcji w zwykłych obrazach Ngen.</span><span class="sxs-lookup"><span data-stu-id="75ac3-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="75ac3-111">Tylko obrazy NGen zoptymalizowane pod kątem profilu generują wywołania zwrotne dla wszystkich funkcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="75ac3-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="75ac3-112">Jednak ze względu na dodatkowe obciążenie, profiler powinien zażądać obrazów NGen zoptymalizowanych pod kątem profilera tylko wtedy, gdy zamierza użyć tych wywołań zwrotnych w celu wymuszenia skompilowania funkcji just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="75ac3-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="75ac3-113">W przeciwnym razie Profiler powinien używać strategii z opóźnieniem do zbierania informacji o funkcji.</span><span class="sxs-lookup"><span data-stu-id="75ac3-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="75ac3-114">Profilowani muszą obsługiwać przypadki, w których wiele wątków profilowanej aplikacji wywołuje tę samą metodę jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="75ac3-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="75ac3-115">Na przykład wywołania wątku A `JITCachedFunctionSearchStarted` i profilera reagują przez ustawienie *pbUseCachedFunction*na false, aby wymusić kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="75ac3-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="75ac3-116">Wątek A następnie wywołuje [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) i [ICorProfilerCallback:: JITCompilationFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="75ac3-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="75ac3-117">Teraz wątek B wywołuje `JITCachedFunctionSearchStarted` dla tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="75ac3-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="75ac3-118">Mimo że profiler stwierdził, że zamiaru JIT-kompiluje funkcję, profiler odbiera drugie wywołanie zwrotne, ponieważ wątek B wysyła wywołanie zwrotne, zanim profiler odpowiedział na wywołanie wątku A do `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="75ac3-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="75ac3-119">Kolejność, w jakiej wątki powodują wywołania, zależy od tego, jak wątki są zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="75ac3-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="75ac3-120">Gdy profiler odbiera zduplikowane wywołania zwrotne, musi ustawić wartość, do której odwołuje się `pbUseCachedFunction`, na tę samą wartość dla wszystkich zduplikowanych wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="75ac3-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="75ac3-121">Oznacza to, że gdy `JITCachedFunctionSearchStarted` jest wywoływana wielokrotnie z tą samą wartością `functionId`, profiler musi odpowiedzieć na ten sam czas.</span><span class="sxs-lookup"><span data-stu-id="75ac3-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ac3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75ac3-122">Requirements</span></span>  
 <span data-ttu-id="75ac3-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75ac3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75ac3-124">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="75ac3-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75ac3-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="75ac3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75ac3-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75ac3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ac3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75ac3-127">See also</span></span>

- [<span data-ttu-id="75ac3-128">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="75ac3-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
