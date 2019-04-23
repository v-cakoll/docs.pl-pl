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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3550f4da497574ea5076766ad201e9431af52e4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174307"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="b26d6-102">ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="b26d6-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="b26d6-103">Powiadamia program profilujący, że wyszukiwania została uruchomiona dla funkcji, która została skompilowana wcześniej przy użyciu Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="b26d6-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b26d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b26d6-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b26d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b26d6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b26d6-106">[in] Identyfikator funkcji, dla którego wyszukiwanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b26d6-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="b26d6-107">[out] `true` Jeśli silnik wykonywania powinien używać zbuforowaną wersję funkcji (jeśli dostępne); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b26d6-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="b26d6-108">Jeśli wartość jest `false`, wykonywanie aparatu JIT kompiluje funkcję zamiast wersji, który nie jest kompilowany dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="b26d6-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b26d6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b26d6-109">Remarks</span></span>  
 <span data-ttu-id="b26d6-110">W .NET Framework w wersji 2.0 `JITCachedFunctionSearchStarted` i [icorprofilercallback::jitcachedfunctionsearchfinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) wywołania zwrotne nie zostaną wprowadzone dla wszystkich funkcji w zwykłych obrazów NGen.</span><span class="sxs-lookup"><span data-stu-id="b26d6-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="b26d6-111">Tylko obrazów NGen zoptymalizowane pod kątem profilu wygeneruje wywołania zwrotne dla wszystkich funkcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="b26d6-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="b26d6-112">Jednak ze względu na dodatkowe obciążenie, program profilujący powinien zażądać profiler zoptymalizowane pod kątem obrazów NGen tylko wtedy, gdy zamierza korzystać z tych wywołań zwrotnych do wymuszenia funkcję, która ma być skompilowany just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="b26d6-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="b26d6-113">W przeciwnym razie do zbierania informacji o funkcji strategii z opóźnieniem należy używać programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="b26d6-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="b26d6-114">Profilery muszą obsługiwać przypadki, gdy wiele wątków profilowana aplikacja wywołania dotyczą tej samej metody jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b26d6-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="b26d6-115">Na przykład, wywołania wątku A `JITCachedFunctionSearchStarted` , a program profilujący, ustawiając *pbUseCachedFunction*na wartość FALSE, aby wymusić kompilacja JIT.</span><span class="sxs-lookup"><span data-stu-id="b26d6-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="b26d6-116">Wątek, następnie wywołuje [icorprofilercallback::jitcompilationstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) i [icorprofilercallback::jitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="b26d6-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="b26d6-117">Teraz wątek jest wywołany B `JITCachedFunctionSearchStarted` dla tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b26d6-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="b26d6-118">Mimo że program profilujący ma stwierdziła swój zamiar funkcji skompilować wg JIT, profiler otrzymuje drugi wywołania zwrotnego, ponieważ wątek B wysyła wywołania zwrotnego, zanim program profilujący odpowiedział na wywołania wątku, A `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="b26d6-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="b26d6-119">Kolejność, w którym wątki wykonywanie wywołań zależy od tego, jak wątki są zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="b26d6-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="b26d6-120">Gdy profiler otrzymuje zduplikowane wywołań zwrotnych, należy ustawić w niej wartość przywołana przez `pbUseCachedFunction` taką samą wartość dla wszystkich duplikatów wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="b26d6-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="b26d6-121">Oznacza to, kiedy `JITCachedFunctionSearchStarted` jest wywoływana wiele razy z takimi samymi `functionId` wartości, program profilujący musi odpowiadać takie same każdorazowo.</span><span class="sxs-lookup"><span data-stu-id="b26d6-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b26d6-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b26d6-122">Requirements</span></span>  
 <span data-ttu-id="b26d6-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b26d6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b26d6-124">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b26d6-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b26d6-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b26d6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b26d6-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b26d6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26d6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b26d6-127">See also</span></span>

- [<span data-ttu-id="b26d6-128">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b26d6-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
