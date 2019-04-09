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
ms.openlocfilehash: 4b75eebd8d9bf439a0317521a61c06ece3745be0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075324"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="2efd2-102">ICorProfilerCallback::JITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="2efd2-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="2efd2-103">Powiadamia program profilujący, że kompilator just-in-time (JIT) została uruchomiona kompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="2efd2-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2efd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2efd2-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2efd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2efd2-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2efd2-106">[in] Identyfikator funkcji, dla których jest uruchamiana kompilacja.</span><span class="sxs-lookup"><span data-stu-id="2efd2-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="2efd2-107">[in] Wartość do programu profilującego wskazującą, czy blokowanie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2efd2-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="2efd2-108">Wartość jest `true` Jeśli blokowanie może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2efd2-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="2efd2-109">Mimo, że wartość `true` nie uszkodzi środowiska uruchomieniowego, jego pochylanie wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="2efd2-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2efd2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2efd2-110">Remarks</span></span>  
 <span data-ttu-id="2efd2-111">Jest to możliwe, aby otrzymać więcej niż jedną parę `JITCompilationStarted` i [icorprofilercallback::jitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) wywołuje dla każdej funkcji ze względu na sposób środowisko wykonawcze obsługuje Konstruktory klasy.</span><span class="sxs-lookup"><span data-stu-id="2efd2-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="2efd2-112">Na przykład środowisko uruchomieniowe rozpoczyna się skompilować wg JIT metody A, ale konstruktora klasy dla klasy B musi zostać uruchomione.</span><span class="sxs-lookup"><span data-stu-id="2efd2-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="2efd2-113">W związku z tym, środowisko uruchomieniowe kompiluje JIT konstruktora dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="2efd2-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="2efd2-114">Konstruktor jest uruchomiona, tworzy wywołanie metody A, co powoduje, że metoda ponownie być kompilowany dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="2efd2-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="2efd2-115">W tym scenariuszu pierwszy kompilację JIT metody A jest zatrzymywana.</span><span class="sxs-lookup"><span data-stu-id="2efd2-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="2efd2-116">Jednak zarówno próby metoda skompilować wg JIT są zgłaszane ze zdarzeniami kompilacja JIT.</span><span class="sxs-lookup"><span data-stu-id="2efd2-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="2efd2-117">Jeśli program profilujący ma zastąpić kod intermediate language (MSIL) firmy Microsoft dla metody element przez wywołanie metody [icorprofilerinfo::setilfunctionbody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody, należy wykonać czynności dla obu `JITCompilationStarted` zdarzenia, ale mogą używać tego samego bloku MSIL dla obu przypadków.</span><span class="sxs-lookup"><span data-stu-id="2efd2-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="2efd2-118">Profilery muszą obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, w której dwa wątki jednocześnie wykorzystują wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="2efd2-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="2efd2-119">Na przykład, wywołania wątku A `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="2efd2-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="2efd2-120">Jednak przed wywołań wątku A `JITCompilationFinished`, wywołań wątku B [icorprofilercallback::exceptionsearchfunctionenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) identyfikatorem funkcji z wątku, A `JITCompilationStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2efd2-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="2efd2-121">Wydaje się, że identyfikator funkcji nie powinny jeszcze być prawidłowy ponieważ wywołanie `JITCompilationFinished` nie ma jeszcze odebrane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="2efd2-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="2efd2-122">Jednak w przypadku podobny do tego identyfikator funkcji jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2efd2-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2efd2-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2efd2-123">Requirements</span></span>  
 <span data-ttu-id="2efd2-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2efd2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2efd2-125">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2efd2-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2efd2-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2efd2-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2efd2-127">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2efd2-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2efd2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2efd2-128">See also</span></span>

- [<span data-ttu-id="2efd2-129">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2efd2-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="2efd2-130">JITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="2efd2-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
