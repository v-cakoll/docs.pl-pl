---
title: ICorProfilerCallback::RuntimeSuspendAborted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: a3fb5c398b8ccd7caba0b005bcf03e64ecef4ba5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503253"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="7a2d1-102">ICorProfilerCallback::RuntimeSuspendAborted — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a2d1-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="7a2d1-103">Powiadamia profiler o przerwaniu zawieszenia środowiska uruchomieniowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7a2d1-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a2d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a2d1-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7a2d1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a2d1-105">Remarks</span></span>  
 <span data-ttu-id="7a2d1-106">Zawieszenie w czasie wykonywania może zostać przerwane, jeśli dwa wątki jednocześnie podejmują próbę wstrzymania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7a2d1-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="7a2d1-107">Wywołanie zwrotne [ICorProfilerCallback:: RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md) lub `RuntimeSuspendAborted` wywołanie zwrotne nastąpi w pojedynczym wątku po wywołaniu wywołania zwrotnego [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7a2d1-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="7a2d1-108">`RuntimeSuspendAborted`Wywołanie zwrotne jest gwarantowane w tym samym wątku co `RuntimeSuspendStarted` wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="7a2d1-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a2d1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a2d1-109">Requirements</span></span>  
 <span data-ttu-id="7a2d1-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a2d1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a2d1-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7a2d1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a2d1-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7a2d1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a2d1-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a2d1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2d1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a2d1-114">See also</span></span>

- [<span data-ttu-id="7a2d1-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7a2d1-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
