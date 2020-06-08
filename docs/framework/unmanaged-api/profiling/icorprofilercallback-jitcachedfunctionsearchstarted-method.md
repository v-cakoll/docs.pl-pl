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
ms.openlocfilehash: d8f4a04abea0bd5eb9bf38629a8fcaf76479bcc9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500063"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="8cfe5-102">ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="8cfe5-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="8cfe5-103">Powiadamia profiler o rozpoczęciu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu natywnego generatora obrazu (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="8cfe5-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfe5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cfe5-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cfe5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cfe5-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8cfe5-106">\[in) identyfikator funkcji, dla której jest wykonywane wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-106">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="8cfe5-107">\[out], `true` Jeśli aparat wykonywania powinien używać buforowanej wersji funkcji (jeśli jest dostępna); w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="8cfe5-107">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="8cfe5-108">Jeśli wartość to `false` , aparat wykonywania JIT — kompiluje funkcję zamiast używania wersji, która nie jest skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cfe5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cfe5-109">Remarks</span></span>  
 <span data-ttu-id="8cfe5-110">W .NET Framework w wersji 2,0 `JITCachedFunctionSearchStarted` metody wywołania zwrotne i [ICorProfilerCallback:: JITCachedFunctionSearchFinished —](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) nie będą wykonywane dla wszystkich funkcji w zwykłych obrazach Ngen.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="8cfe5-111">Tylko obrazy NGen zoptymalizowane pod kątem profilu generują wywołania zwrotne dla wszystkich funkcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="8cfe5-112">Jednak ze względu na dodatkowe obciążenie, profiler powinien zażądać obrazów NGen zoptymalizowanych pod kątem profilera tylko wtedy, gdy zamierza użyć tych wywołań zwrotnych w celu wymuszenia skompilowania funkcji just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="8cfe5-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="8cfe5-113">W przeciwnym razie Profiler powinien używać strategii z opóźnieniem do zbierania informacji o funkcji.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="8cfe5-114">Profilowani muszą obsługiwać przypadki, w których wiele wątków profilowanej aplikacji wywołuje tę samą metodę jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="8cfe5-115">Na przykład wywołania wątku A `JITCachedFunctionSearchStarted` i profilera reagują przez ustawienie *PBUSECACHEDFUNCTION*na false, aby wymusić kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="8cfe5-116">Wątek A następnie wywołuje [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) i [ICorProfilerCallback:: JITCompilationFinished —](icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="8cfe5-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="8cfe5-117">Teraz wątek B wywołuje tę `JITCachedFunctionSearchStarted` samą funkcję.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="8cfe5-118">Mimo że profiler stwierdził, że zamiaru JIT-kompiluje funkcję, profiler odbiera drugie wywołanie zwrotne, ponieważ wątek B wysyła wywołanie zwrotne, zanim profiler odpowiedział na wywołanie wątku A `JITCachedFunctionSearchStarted` .</span><span class="sxs-lookup"><span data-stu-id="8cfe5-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="8cfe5-119">Kolejność, w jakiej wątki powodują wywołania, zależy od tego, jak wątki są zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="8cfe5-120">Gdy profiler odbiera zduplikowane wywołania zwrotne, musi ustawić wartość, do której odwołuje się ta `pbUseCachedFunction` sama wartość dla wszystkich zduplikowanych wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="8cfe5-121">Oznacza to, że gdy `JITCachedFunctionSearchStarted` jest wywoływana wiele razy z tą samą `functionId` wartością, profiler musi odpowiedzieć na ten sam czas.</span><span class="sxs-lookup"><span data-stu-id="8cfe5-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cfe5-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cfe5-122">Requirements</span></span>  
 <span data-ttu-id="8cfe5-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cfe5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cfe5-124">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8cfe5-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cfe5-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8cfe5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cfe5-126">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cfe5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfe5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cfe5-127">See also</span></span>

- [<span data-ttu-id="8cfe5-128">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8cfe5-128">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
