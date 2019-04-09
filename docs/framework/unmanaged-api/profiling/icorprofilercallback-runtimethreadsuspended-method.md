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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0748802599926f4ec218362e6f7d086aab2d8f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080231"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="5b0bc-102">ICorProfilerCallback::RuntimeThreadSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b0bc-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="5b0bc-103">Powiadamia program profilujący, że określony wątek zostało zawieszone lub ma zostać zawieszone.</span><span class="sxs-lookup"><span data-stu-id="5b0bc-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b0bc-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b0bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b0bc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5b0bc-106">[in] Identyfikator wątku, który zostało zawieszone.</span><span class="sxs-lookup"><span data-stu-id="5b0bc-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b0bc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b0bc-107">Remarks</span></span>  
 <span data-ttu-id="5b0bc-108">`RuntimeThreadSuspended` Powiadomień mogą wystąpić w dowolnym czasie między [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) oraz skojarzonych z nimi [icorprofilercallback::runtimeresumestarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="5b0bc-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="5b0bc-109">Powiadomienia, które mają miejsce między [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` dla wątków, które były uruchomione w kod niezarządzany i konto zostało zawieszone po wejściu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5b0bc-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="5b0bc-110">Ogólnie rzecz biorąc to wywołanie zwrotne występuje po wątek jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="5b0bc-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="5b0bc-111">Jednak jeśli aktualnie wykonywany wątek (wątku, który wywołał to wywołanie zwrotne) jest tą, która jest wstrzymana, to wywołanie zwrotne wystąpi przed wątek jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="5b0bc-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b0bc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b0bc-112">Requirements</span></span>  
 <span data-ttu-id="5b0bc-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b0bc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b0bc-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b0bc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b0bc-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b0bc-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5b0bc-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5b0bc-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b0bc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b0bc-117">See also</span></span>

- [<span data-ttu-id="5b0bc-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5b0bc-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5b0bc-119">RuntimeThreadResumed, metoda</span><span class="sxs-lookup"><span data-stu-id="5b0bc-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
