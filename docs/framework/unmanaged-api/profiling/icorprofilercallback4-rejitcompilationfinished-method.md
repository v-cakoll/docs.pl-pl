---
title: "ICorProfilerCallback4::ReJITCompilationFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 768c77a91c072cadc2975d9dde704c134e719220
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="6f6ed-102">ICorProfilerCallback4::ReJITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ed-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="6f6ed-103">Powiadamia profilera przy użyciu kompilatora just in time (JIT) zakończenie ponownego kompilowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f6ed-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f6ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f6ed-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6f6ed-106">[in] Identyfikator funkcji, która została ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="6f6ed-107">[in] Tożsamość funkcja ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6f6ed-108">[in] Wartość, która wskazuje, czy ponownej kompilacji JIT zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="6f6ed-109">[in] `true` wskazująca, czy blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="6f6ed-110">Wartość `true` nie uszkodzić środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="6f6ed-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f6ed-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f6ed-111">Requirements</span></span>  
 <span data-ttu-id="6f6ed-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f6ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f6ed-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f6ed-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f6ed-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f6ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f6ed-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6ed-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f6ed-116">See Also</span></span>  
 [<span data-ttu-id="6f6ed-117">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="6f6ed-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6f6ed-118">ICorProfilerCallback4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6f6ed-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="6f6ed-119">JITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ed-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="6f6ed-120">ReJITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ed-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
