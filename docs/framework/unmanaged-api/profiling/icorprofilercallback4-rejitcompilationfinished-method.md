---
title: ICorProfilerCallback4::ReJITCompilationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ec2981cbee4675f9cd2a4fd13d507f50ad2a3ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597144"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="330ca-102">ICorProfilerCallback4::ReJITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="330ca-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="330ca-103">Powiadamia program profilujący, że kompilator just-in-time (JIT) została zakończona, ponownej kompilacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="330ca-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="330ca-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="330ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="330ca-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="330ca-106">[in] Identyfikator funkcji, która była ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="330ca-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="330ca-107">[in] Tożsamość funkcja ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="330ca-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="330ca-108">[in] Wartość, która wskazuje, czy JIT — rekompilacja zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="330ca-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="330ca-109">[in] `true` do wskazania, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="330ca-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="330ca-110">Wartość `true` nie negatywnie wpłynąć na środowisko uruchomieniowe, ale mogą mieć wpływ na wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="330ca-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330ca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="330ca-111">Requirements</span></span>  
 <span data-ttu-id="330ca-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="330ca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="330ca-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="330ca-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="330ca-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="330ca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="330ca-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="330ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330ca-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="330ca-116">See also</span></span>

- [<span data-ttu-id="330ca-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="330ca-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="330ca-118">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="330ca-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="330ca-119">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="330ca-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="330ca-120">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="330ca-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
