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
ms.openlocfilehash: e9aaf7325b8e7e65aa98904513cc7efe94e35087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041811"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="54502-102">ICorProfilerCallback::RuntimeSuspendAborted — Metoda</span><span class="sxs-lookup"><span data-stu-id="54502-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="54502-103">Powiadamia program profilujący, że środowisko uruchomieniowe przerwała zawieszenie środowiska uruchomieniowego, który został pojawiają się.</span><span class="sxs-lookup"><span data-stu-id="54502-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54502-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54502-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="54502-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54502-105">Remarks</span></span>  
 <span data-ttu-id="54502-106">Zawieszenie środowiska wykonawczego mogą zostało przerwane, jeśli dwa wątki jednocześnie podejmie próbę wstrzymania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="54502-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="54502-107">Albo [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) wywołanie zwrotne lub `RuntimeSuspendAborted` nastąpi wywołanie zwrotne po jednym wątkiem [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) Wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="54502-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="54502-108">`RuntimeSuspendAborted` Wywołania zwrotnego jest gwarantowane, odbywa się na tym samym wątku jako `RuntimeSuspendStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="54502-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54502-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54502-109">Requirements</span></span>  
 <span data-ttu-id="54502-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54502-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54502-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54502-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54502-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54502-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54502-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54502-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54502-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54502-114">See also</span></span>

- [<span data-ttu-id="54502-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="54502-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
