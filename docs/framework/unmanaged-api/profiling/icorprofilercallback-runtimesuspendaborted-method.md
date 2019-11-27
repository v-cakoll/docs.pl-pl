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
ms.openlocfilehash: fb09a9422f2aeec239f9aef25fb61c731e0aa2e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430610"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="aab35-102">ICorProfilerCallback::RuntimeSuspendAborted — Metoda</span><span class="sxs-lookup"><span data-stu-id="aab35-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="aab35-103">Powiadamia profiler o przerwaniu zawieszenia środowiska uruchomieniowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aab35-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aab35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aab35-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="aab35-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aab35-105">Remarks</span></span>  
 <span data-ttu-id="aab35-106">Zawieszenie w czasie wykonywania może zostać przerwane, jeśli dwa wątki jednocześnie podejmują próbę wstrzymania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="aab35-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="aab35-107">Wywołanie zwrotne [ICorProfilerCallback:: RuntimeSuspendFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) lub `RuntimeSuspendAborted` wywołanie zwrotne nastąpi w jednym wątku po wywołaniu wywołania zwrotnego [ICorProfilerCallback:: RuntimeSuspendStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aab35-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="aab35-108">Wywołanie zwrotne `RuntimeSuspendAborted` jest gwarantowane w tym samym wątku co `RuntimeSuspendStarted` wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="aab35-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aab35-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aab35-109">Requirements</span></span>  
 <span data-ttu-id="aab35-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aab35-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aab35-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="aab35-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aab35-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aab35-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aab35-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aab35-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab35-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aab35-114">See also</span></span>

- [<span data-ttu-id="aab35-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="aab35-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
