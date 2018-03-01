---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2208a1a1637b3bb8dd7d7963ab806aeae7921dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="fe65b-102">ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe65b-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="fe65b-103">Powiadamia profilera, że wyszukiwanie została uruchomiona dla funkcji skompilowanego wcześniej przy użyciu Generator obrazu natywnego (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="fe65b-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe65b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe65b-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe65b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe65b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fe65b-106">[in] Identyfikator funkcji, dla którego będzie prowadzone wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="fe65b-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="fe65b-107">[out] `true` Jeśli aparat wykonywania powinien używać wersja buforowana funkcji (jeśli jest dostępny); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fe65b-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="fe65b-108">Jeśli wartość jest `false`, wykonywanie aparatu kompiluje JIT funkcja zamiast wersji, która nie jest skompilowany JIT.</span><span class="sxs-lookup"><span data-stu-id="fe65b-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe65b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe65b-109">Remarks</span></span>  
 <span data-ttu-id="fe65b-110">W programie .NET Framework w wersji 2.0 `JITCachedFunctionSearchStarted` i [ICorProfilerCallback::JITCachedFunctionSearchFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) wywołania zwrotne nie zostaną wprowadzone dla wszystkich funkcji w regularnych obrazów NGen.</span><span class="sxs-lookup"><span data-stu-id="fe65b-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="fe65b-111">Tylko obrazów NGen zoptymalizowane pod kątem profilu wygeneruje wywołań zwrotnych dla wszystkich funkcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="fe65b-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="fe65b-112">Jednak ze względu na dodatkowe obciążenie profiler powinien zażądać zoptymalizowanych pod kątem profilera obrazów NGen tylko, jeśli zamierza użyć tych wywołań zwrotnych, aby wymusić funkcję, która ma być skompilowany just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="fe65b-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="fe65b-113">W przeciwnym razie do zbierania informacji o funkcji strategii opóźnieniem należy używać profilera.</span><span class="sxs-lookup"><span data-stu-id="fe65b-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="fe65b-114">Profilery musi obsługiwać przypadków, w której wiele wątków profilowana aplikacja wywoływania tej samej metody jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fe65b-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="fe65b-115">Na przykład wywołuje wątku A `JITCachedFunctionSearchStarted` i profilera odpowiada ustawiając *pbUseCachedFunction*na FAŁSZ, aby wymusić kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="fe65b-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="fe65b-116">Wątek, następnie wywołuje [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) i [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="fe65b-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="fe65b-117">Teraz wątków B wywołania `JITCachedFunctionSearchStarted` dla tej samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fe65b-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="fe65b-118">Mimo że profiler stwierdził zamiarze JIT-kompilacji funkcji, profilera odbiera drugi wywołania zwrotnego, ponieważ wątek B wysyła wywołania zwrotnego, zanim profilera odpowiedział na wywołanie wątku A `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="fe65b-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="fe65b-119">Kolejność, w którym wątków wykonywania wywołań zależy od tego, jak są zaplanowane wątki.</span><span class="sxs-lookup"><span data-stu-id="fe65b-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="fe65b-120">Profiler odebrania zduplikowane wywołania zwrotne musi ustawić wartość odwołuje się `pbUseCachedFunction` na tę samą wartość dla wszystkich duplikatów wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="fe65b-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="fe65b-121">Oznacza to, gdy `JITCachedFunctionSearchStarted` jest wywołana wiele razy z tym samym `functionId` wartość profilera musi odpowiadać takie same zawsze.</span><span class="sxs-lookup"><span data-stu-id="fe65b-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe65b-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe65b-122">Requirements</span></span>  
 <span data-ttu-id="fe65b-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe65b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe65b-124">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe65b-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe65b-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe65b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe65b-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe65b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe65b-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe65b-127">See Also</span></span>  
 [<span data-ttu-id="fe65b-128">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe65b-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
