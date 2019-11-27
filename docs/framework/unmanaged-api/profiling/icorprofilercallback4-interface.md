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
ms.openlocfilehash: a3394820f673e35777e1749229d4f8319841ca58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439389"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="54a54-102">ICorProfilerCallback4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="54a54-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="54a54-103">Zapewnia metody wywołania zwrotnego, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji do profilera.</span><span class="sxs-lookup"><span data-stu-id="54a54-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54a54-104">Metody</span><span class="sxs-lookup"><span data-stu-id="54a54-104">Methods</span></span>  
  
|<span data-ttu-id="54a54-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-105">Method</span></span>|<span data-ttu-id="54a54-106">Opis</span><span class="sxs-lookup"><span data-stu-id="54a54-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54a54-107">GetReJITParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="54a54-108">Umożliwia programowi Code Profiler Ustawianie alternatywnych flag generowania kodu dla nowej rekompilowanej treści metody.</span><span class="sxs-lookup"><span data-stu-id="54a54-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="54a54-109">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="54a54-110">Raportuje nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="54a54-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="54a54-111">ReJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="54a54-112">Powiadamia profiler, że kompilator just-in-Time (JIT) zakończył ponowną kompilację funkcji.</span><span class="sxs-lookup"><span data-stu-id="54a54-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="54a54-113">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="54a54-114">Powiadamia profiler, że został uruchomiony kompilator just-in-Time (JIT), aby ponownie skompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="54a54-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="54a54-115">ReJITError, metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="54a54-116">Zgłasza błąd podczas przetwarzania żądania ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="54a54-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="54a54-117">SurvivingReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="54a54-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="54a54-118">Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="54a54-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54a54-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54a54-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a54-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54a54-120">Requirements</span></span>  
 <span data-ttu-id="54a54-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54a54-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54a54-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="54a54-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54a54-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="54a54-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54a54-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54a54-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a54-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54a54-125">See also</span></span>

- [<span data-ttu-id="54a54-126">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="54a54-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="54a54-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="54a54-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="54a54-128">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="54a54-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
