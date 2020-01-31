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
ms.openlocfilehash: e05cb944ea4f3a9ca718dc22c6cd726b6a516ea9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866237"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="f8c87-102">ICorProfilerCallback::JITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8c87-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="f8c87-103">Powiadamia program profilujący, że kompilator just in Time (JIT) rozpoczął Kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8c87-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8c87-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8c87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8c87-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f8c87-106">podczas Identyfikator funkcji, dla której rozpoczyna się kompilacja.</span><span class="sxs-lookup"><span data-stu-id="f8c87-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="f8c87-107">podczas Wartość wskazująca, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f8c87-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="f8c87-108">Wartość jest `true`, jeśli blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="f8c87-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="f8c87-109">Mimo że wartość `true` nie będzie szkodliwe dla środowiska uruchomieniowego, może pochylić wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="f8c87-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8c87-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8c87-110">Remarks</span></span>  
 <span data-ttu-id="f8c87-111">Istnieje możliwość otrzymywania więcej niż jednej pary `JITCompilationStarted` i [ICorProfilerCallback:: JITCompilationFinished —](icorprofilercallback-jitcompilationfinished-method.md) wywołań dla każdej funkcji ze względu na sposób, w jaki środowisko uruchomieniowe obsługuje konstruktory klas.</span><span class="sxs-lookup"><span data-stu-id="f8c87-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="f8c87-112">Na przykład środowisko uruchomieniowe zaczyna się od JIT-Kompiluj metodę A, ale Konstruktor klasy dla klasy B musi być uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f8c87-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="f8c87-113">W związku z tym kompilator JIT środowiska uruchomieniowego kompiluje Konstruktor dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="f8c87-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="f8c87-114">Gdy Konstruktor jest uruchomiony, wywołuje metodę A, która powoduje ponowną kompilację w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="f8c87-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="f8c87-115">W tym scenariuszu pierwsza kompilacja JIT metody A jest zatrzymywana.</span><span class="sxs-lookup"><span data-stu-id="f8c87-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="f8c87-116">Jednak obie próby JIT-Kompiluj metodę A są raportowane przy użyciu zdarzeń kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="f8c87-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="f8c87-117">Jeśli profiler zamierza zastąpić kod języka pośredniego firmy Microsoft (MSIL) dla metody A przez wywołanie metody [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) , musi to zrobić dla obu zdarzeń `JITCompilationStarted`, ale może użyć tego samego bloku MSIL dla obu tych elementów.</span><span class="sxs-lookup"><span data-stu-id="f8c87-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="f8c87-118">Profilowani muszą obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, gdy dwa wątki jednocześnie generują wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="f8c87-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="f8c87-119">Na przykład wątek A wywołuje `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="f8c87-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="f8c87-120">Jednak przed wywołaniem wątku `JITCompilationFinished`, wątek B wywołuje [ICorProfilerCallback:: ExceptionSearchFunctionEnter —](icorprofilercallback-exceptionsearchfunctionenter-method.md) z identyfikatorem funkcji z wywołania zwrotnego wątku `JITCompilationStarted` A.</span><span class="sxs-lookup"><span data-stu-id="f8c87-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="f8c87-121">Może się wydawać, że identyfikator funkcji nie powinien jeszcze być prawidłowy, ponieważ wywołanie `JITCompilationFinished` nie zostało jeszcze odebrane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="f8c87-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="f8c87-122">Jednak w przypadku takiej sytuacji identyfikator funkcji jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f8c87-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c87-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8c87-123">Requirements</span></span>  
 <span data-ttu-id="f8c87-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c87-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8c87-125">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f8c87-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8c87-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f8c87-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8c87-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c87-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c87-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8c87-128">See also</span></span>

- [<span data-ttu-id="f8c87-129">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8c87-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f8c87-130">JITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="f8c87-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
