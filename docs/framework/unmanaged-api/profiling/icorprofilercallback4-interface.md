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
ms.openlocfilehash: 3eb1f46900199db65be5d14c56bfc0b6f55bf269
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205137"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="13a2a-102">ICorProfilerCallback4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="13a2a-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="13a2a-103">Udostępnia metody wywołania zwrotnego, używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji do programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="13a2a-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13a2a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="13a2a-104">Methods</span></span>  
  
|<span data-ttu-id="13a2a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-105">Method</span></span>|<span data-ttu-id="13a2a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="13a2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13a2a-107">GetReJITParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="13a2a-108">Umożliwia programowi profilującemu kodu Ustaw flagi generowania kodu alternatywnej dla nowej treści metody ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13a2a-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="13a2a-109">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="13a2a-110">Raporty nowy układ obiektów w stercie wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="13a2a-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="13a2a-111">ReJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="13a2a-112">Powiadamia program profilujący, że kompilator just-in-time (JIT) została zakończona kompilację funkcji.</span><span class="sxs-lookup"><span data-stu-id="13a2a-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="13a2a-113">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="13a2a-114">Powiadamia program profilujący, że kompilator just-in-time (JIT) została uruchomiona ponownie skompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="13a2a-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="13a2a-115">ReJITError, metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="13a2a-116">Zgłasza błąd podczas przetwarzania żądania ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13a2a-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="13a2a-117">SurvivingReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="13a2a-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="13a2a-118">Raportuje układ obiektów w stercie wyrzucania elementów bezużytecznych bez kondensowania w wyniku.</span><span class="sxs-lookup"><span data-stu-id="13a2a-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13a2a-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13a2a-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a2a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13a2a-120">Requirements</span></span>  
 <span data-ttu-id="13a2a-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a2a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a2a-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13a2a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13a2a-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a2a-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="13a2a-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="13a2a-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13a2a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13a2a-125">See also</span></span>

- [<span data-ttu-id="13a2a-126">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="13a2a-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="13a2a-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="13a2a-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="13a2a-128">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="13a2a-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
