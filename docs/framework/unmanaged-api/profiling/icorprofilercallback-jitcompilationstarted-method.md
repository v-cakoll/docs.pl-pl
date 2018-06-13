---
title: ICorProfilerCallback::JITCompilationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fa1081afc77c8116d8858c187401555409b4dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453984"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="3d17b-102">ICorProfilerCallback::JITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d17b-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="3d17b-103">Powiadamia profilera, aby skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).</span><span class="sxs-lookup"><span data-stu-id="3d17b-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d17b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d17b-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d17b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d17b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3d17b-106">[in] Identyfikator funkcji, dla których trwa uruchamianie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3d17b-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="3d17b-107">[in] Wartość wskazującą profilera, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3d17b-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="3d17b-108">Wartość jest `true` Jeśli blokuje może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3d17b-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="3d17b-109">Chociaż wartość `true` nie będzie uszkodzić środowiska uruchomieniowego, jego pochylanie wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="3d17b-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d17b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d17b-110">Remarks</span></span>  
 <span data-ttu-id="3d17b-111">Istnieje możliwość odbierania więcej niż jedną parę `JITCompilationStarted` i [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) wywołuje dla każdej funkcji ze względu na sposób środowiska uruchomieniowego konstruktorów klas uchwytów.</span><span class="sxs-lookup"><span data-stu-id="3d17b-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="3d17b-112">Na przykład środowiska uruchomieniowego rozpoczyna Metoda kompilacji JIT, ale konstruktora klasy dla klasy B musi zostać uruchomione.</span><span class="sxs-lookup"><span data-stu-id="3d17b-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="3d17b-113">W związku z tym środowiska uruchomieniowego kompiluje JIT konstruktora dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="3d17b-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="3d17b-114">Konstruktor jest uruchomiona, powoduje wywołanie do metody A, co powoduje, że metoda być ponownie kompilowane JIT.</span><span class="sxs-lookup"><span data-stu-id="3d17b-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="3d17b-115">W tym scenariuszu pierwszej kompilacji JIT metody A jest zatrzymywane.</span><span class="sxs-lookup"><span data-stu-id="3d17b-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="3d17b-116">Jednak zarówno próby Metoda kompilacji JIT są zgłaszane ze zdarzeń kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="3d17b-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="3d17b-117">Jeśli profilera ma zastąpić kod języka pośredniego (MSIL) firmy Microsoft dla metody A wywołując [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody, należy wykonać czynności dla obu `JITCompilationStarted` zdarzeń, ale może używać tego samego bloku MSIL dla obu.</span><span class="sxs-lookup"><span data-stu-id="3d17b-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="3d17b-118">Profilery musi obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, gdy dwa wątków jednocześnie dokonywania wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="3d17b-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="3d17b-119">Na przykład wywołuje wątku A `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="3d17b-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="3d17b-120">Jednak przed wywołania wątku A `JITCompilationFinished`, wywołania wątku B [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) z Identyfikatorem funkcji z wątku A `JITCompilationStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3d17b-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="3d17b-121">Wydaje się, że identyfikator funkcji należy jeszcze być nieprawidłowe ponieważ wywołania `JITCompilationFinished` nie ma jeszcze odebrane profilera.</span><span class="sxs-lookup"><span data-stu-id="3d17b-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="3d17b-122">Jednak w przypadku takich jak ta, identyfikator funkcji jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="3d17b-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d17b-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d17b-123">Requirements</span></span>  
 <span data-ttu-id="3d17b-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d17b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d17b-125">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d17b-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d17b-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d17b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d17b-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d17b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d17b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d17b-128">See Also</span></span>  
 [<span data-ttu-id="3d17b-129">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3d17b-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3d17b-130">JITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="3d17b-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
