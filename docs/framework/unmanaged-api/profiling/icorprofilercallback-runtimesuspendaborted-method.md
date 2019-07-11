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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62682ca19b9f987370ca11d2bda63fba27f28474
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782992"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="1f555-102">ICorProfilerCallback::RuntimeSuspendAborted — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f555-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="1f555-103">Powiadamia program profilujący, że środowisko uruchomieniowe przerwała zawieszenie środowiska uruchomieniowego, który został pojawiają się.</span><span class="sxs-lookup"><span data-stu-id="1f555-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f555-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f555-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1f555-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f555-105">Remarks</span></span>  
 <span data-ttu-id="1f555-106">Zawieszenie środowiska wykonawczego mogą zostało przerwane, jeśli dwa wątki jednocześnie podejmie próbę wstrzymania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1f555-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="1f555-107">Albo [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) wywołanie zwrotne lub `RuntimeSuspendAborted` nastąpi wywołanie zwrotne po jednym wątkiem [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) Wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="1f555-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="1f555-108">`RuntimeSuspendAborted` Wywołania zwrotnego jest gwarantowane, odbywa się na tym samym wątku jako `RuntimeSuspendStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1f555-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f555-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f555-109">Requirements</span></span>  
 <span data-ttu-id="1f555-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f555-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f555-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f555-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f555-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f555-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f555-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f555-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f555-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f555-114">See also</span></span>

- [<span data-ttu-id="1f555-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f555-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
