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
ms.openlocfilehash: ff06c285bf5306977b520ed9ff845e70fb25989a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499388"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="7757b-102">ICorProfilerCallback4::ReJITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="7757b-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="7757b-103">Powiadamia profiler, że kompilator just-in-Time (JIT) zakończył ponowną kompilację funkcji.</span><span class="sxs-lookup"><span data-stu-id="7757b-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7757b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7757b-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7757b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7757b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7757b-106">podczas Identyfikator funkcji, która została ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="7757b-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="7757b-107">podczas Tożsamość funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="7757b-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7757b-108">podczas Wartość wskazująca, czy ponowna kompilacja JIT zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7757b-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="7757b-109">[w] `true` Aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false`, aby wskazać, że blokowanie nie wpłynie na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7757b-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="7757b-110">Wartość nie jest `true` szkodliwe dla środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="7757b-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7757b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7757b-111">Requirements</span></span>  
 <span data-ttu-id="7757b-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7757b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7757b-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7757b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7757b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7757b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7757b-115">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7757b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7757b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7757b-116">See also</span></span>

- [<span data-ttu-id="7757b-117">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7757b-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7757b-118">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="7757b-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="7757b-119">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="7757b-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="7757b-120">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="7757b-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
