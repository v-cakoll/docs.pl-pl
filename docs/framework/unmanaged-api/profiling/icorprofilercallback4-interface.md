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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bcddc143cacc3df016e6b8dd7907a67354c4311
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="c760c-102">ICorProfilerCallback4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c760c-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="c760c-103">Udostępnia metody wywołania zwrotnego, używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji do profilera.</span><span class="sxs-lookup"><span data-stu-id="c760c-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c760c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c760c-104">Methods</span></span>  
  
|<span data-ttu-id="c760c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-105">Method</span></span>|<span data-ttu-id="c760c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c760c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c760c-107">GetReJITParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="c760c-108">Umożliwia profilującego można ustawić flagi generowania inny kod dla nowych treści metody ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c760c-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="c760c-109">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="c760c-110">Raporty nowy układ obiektów na stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c760c-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="c760c-111">ReJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="c760c-112">Powiadamia profilera zakończenie przy użyciu kompilatora just in time (JIT) kompilację funkcji.</span><span class="sxs-lookup"><span data-stu-id="c760c-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="c760c-113">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="c760c-114">Powiadamia profilera, czy można ponownie skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c760c-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="c760c-115">ReJITError, metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="c760c-116">Zgłasza błąd podczas przetwarzania żądania ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c760c-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="c760c-117">SurvivingReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="c760c-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="c760c-118">Raporty układ obiektów na stercie wyniku-kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c760c-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c760c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c760c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c760c-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c760c-120">Requirements</span></span>  
 <span data-ttu-id="c760c-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c760c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c760c-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c760c-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c760c-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c760c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c760c-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c760c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c760c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c760c-125">See Also</span></span>  
 [<span data-ttu-id="c760c-126">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c760c-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="c760c-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c760c-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c760c-128">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c760c-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
