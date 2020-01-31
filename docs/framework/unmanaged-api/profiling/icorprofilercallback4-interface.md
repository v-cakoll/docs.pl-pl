---
title: ICorProfilerCallback4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 1b85c48859ac29738347d112dd0466a76bfdfd2c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865340"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="15a6e-102">ICorProfilerCallback4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="15a6e-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="15a6e-103">Zapewnia metody wywołania zwrotnego, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji do profilera.</span><span class="sxs-lookup"><span data-stu-id="15a6e-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15a6e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="15a6e-104">Methods</span></span>  
  
|<span data-ttu-id="15a6e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-105">Method</span></span>|<span data-ttu-id="15a6e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="15a6e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15a6e-107">GetReJITParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-107">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="15a6e-108">Umożliwia programowi Code Profiler Ustawianie alternatywnych flag generowania kodu dla nowej rekompilowanej treści metody.</span><span class="sxs-lookup"><span data-stu-id="15a6e-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="15a6e-109">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-109">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="15a6e-110">Raportuje nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="15a6e-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="15a6e-111">ReJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-111">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="15a6e-112">Powiadamia profiler, że kompilator just-in-Time (JIT) zakończył ponowną kompilację funkcji.</span><span class="sxs-lookup"><span data-stu-id="15a6e-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="15a6e-113">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-113">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="15a6e-114">Powiadamia profiler, że został uruchomiony kompilator just-in-Time (JIT), aby ponownie skompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="15a6e-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="15a6e-115">ReJITError, metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-115">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="15a6e-116">Zgłasza błąd podczas przetwarzania żądania ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="15a6e-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="15a6e-117">SurvivingReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="15a6e-117">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="15a6e-118">Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="15a6e-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15a6e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15a6e-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a6e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15a6e-120">Requirements</span></span>  
 <span data-ttu-id="15a6e-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a6e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a6e-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15a6e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15a6e-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15a6e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15a6e-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a6e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a6e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15a6e-125">See also</span></span>

- [<span data-ttu-id="15a6e-126">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="15a6e-126">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="15a6e-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="15a6e-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="15a6e-128">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="15a6e-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
