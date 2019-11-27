---
title: ICorProfilerCallback::RuntimeThreadSuspended — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: 509d6cd2e65c2eb8c92f6d79deae9e01e75298f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433446"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="21439-102">ICorProfilerCallback::RuntimeThreadSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="21439-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="21439-103">Powiadamia profiler o wstrzymaniu określonego wątku lub o zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="21439-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21439-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21439-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21439-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21439-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="21439-106">podczas Identyfikator wątku, który został zawieszony.</span><span class="sxs-lookup"><span data-stu-id="21439-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21439-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21439-107">Remarks</span></span>  
 <span data-ttu-id="21439-108">Powiadomienie `RuntimeThreadSuspended` może wystąpić w dowolnym momencie między [ICorProfilerCallback:: RuntimeSuspendStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) i skojarzonymi [ICorProfilerCallback:: RuntimeResumeStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołaniami zwrotnymi.</span><span class="sxs-lookup"><span data-stu-id="21439-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="21439-109">Powiadomienia występujące między [ICorProfilerCallback:: RuntimeSuspendFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` są przeznaczone dla wątków, które były uruchomione w kodzie niezarządzanym i zostały zawieszone po wprowadzeniu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="21439-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="21439-110">Ogólnie rzecz biorąc to wywołanie zwrotne występuje zaraz po wstrzymaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="21439-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="21439-111">Jeśli jednak aktualnie wykonywany wątek (wątek, który wywołuje to wywołanie zwrotne) jest zawieszeniem, to wywołanie zwrotne zostanie wykonane tuż przed wstrzymaniem wątku.</span><span class="sxs-lookup"><span data-stu-id="21439-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21439-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21439-112">Requirements</span></span>  
 <span data-ttu-id="21439-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21439-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21439-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21439-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21439-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="21439-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21439-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21439-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21439-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21439-117">See also</span></span>

- [<span data-ttu-id="21439-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="21439-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="21439-119">RuntimeThreadResumed, metoda</span><span class="sxs-lookup"><span data-stu-id="21439-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
