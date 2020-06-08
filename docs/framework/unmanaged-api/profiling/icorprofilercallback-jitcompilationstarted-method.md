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
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500042"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="84db8-102">ICorProfilerCallback::JITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="84db8-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="84db8-103">Powiadamia program profilujący, że kompilator just in Time (JIT) rozpoczął Kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="84db8-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84db8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84db8-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84db8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84db8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="84db8-106">podczas Identyfikator funkcji, dla której rozpoczyna się kompilacja.</span><span class="sxs-lookup"><span data-stu-id="84db8-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="84db8-107">podczas Wartość wskazująca, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="84db8-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="84db8-108">Wartość jest `true` Jeśli blokowanie może spowodować, że środowisko uruchomieniowe poczeka na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="84db8-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="84db8-109">Chociaż wartość `true` nie będzie szkodliwa dla środowiska uruchomieniowego, może pochylić wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="84db8-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84db8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84db8-110">Remarks</span></span>  
 <span data-ttu-id="84db8-111">Istnieje możliwość otrzymywania więcej niż jednej pary `JITCompilationStarted` i [ICorProfilerCallback:: JITCompilationFinished —](icorprofilercallback-jitcompilationfinished-method.md) wywołań dla każdej funkcji ze względu na sposób, w jaki środowisko uruchomieniowe obsługuje konstruktory klas.</span><span class="sxs-lookup"><span data-stu-id="84db8-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="84db8-112">Na przykład środowisko uruchomieniowe zaczyna się od JIT-Kompiluj metodę A, ale Konstruktor klasy dla klasy B musi być uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="84db8-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="84db8-113">W związku z tym kompilator JIT środowiska uruchomieniowego kompiluje Konstruktor dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="84db8-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="84db8-114">Gdy Konstruktor jest uruchomiony, wywołuje metodę A, która powoduje ponowną kompilację w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="84db8-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="84db8-115">W tym scenariuszu pierwsza kompilacja JIT metody A jest zatrzymywana.</span><span class="sxs-lookup"><span data-stu-id="84db8-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="84db8-116">Jednak obie próby JIT-Kompiluj metodę A są raportowane przy użyciu zdarzeń kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="84db8-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="84db8-117">Jeśli profiler zamierza zastąpić kod języka pośredniego firmy Microsoft (MSIL) dla metody A przez wywołanie metody [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) , musi to zrobić dla obu `JITCompilationStarted` zdarzeń, ale może użyć tego samego bloku MSIL dla obu tych elementów.</span><span class="sxs-lookup"><span data-stu-id="84db8-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="84db8-118">Profilowani muszą obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, gdy dwa wątki jednocześnie generują wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="84db8-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="84db8-119">Na przykład wątek A wywołuje `JITCompilationStarted` .</span><span class="sxs-lookup"><span data-stu-id="84db8-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="84db8-120">Jednak przed wywołaniem wątku `JITCompilationFinished` wątek B wywołuje [ICorProfilerCallback:: EXCEPTIONSEARCHFUNCTIONENTER —](icorprofilercallback-exceptionsearchfunctionenter-method.md) z identyfikatorem funkcji z `JITCompilationStarted` wywołania zwrotnego wątku a.</span><span class="sxs-lookup"><span data-stu-id="84db8-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="84db8-121">Może się wydawać, że identyfikator funkcji nie powinien jeszcze być prawidłowy, ponieważ wywołanie `JITCompilationFinished` nie zostało jeszcze odebrane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="84db8-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="84db8-122">Jednak w przypadku takiej sytuacji identyfikator funkcji jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="84db8-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84db8-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84db8-123">Requirements</span></span>  
 <span data-ttu-id="84db8-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84db8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84db8-125">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="84db8-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84db8-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="84db8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84db8-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84db8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84db8-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84db8-128">See also</span></span>

- [<span data-ttu-id="84db8-129">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="84db8-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="84db8-130">JITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="84db8-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
