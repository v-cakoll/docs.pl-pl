---
title: "ICorProfilerCallback::RuntimeThreadSuspended — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f22e9a6ed8c62256bb3e614dbc1278dea24d4e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="8f4b1-102">ICorProfilerCallback::RuntimeThreadSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f4b1-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="8f4b1-103">Powiadamia profilera, czy określony wątek został wstrzymany lub ma zostać zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f4b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f4b1-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f4b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f4b1-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8f4b1-106">[in] Identyfikator wątku, który został wstrzymany.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f4b1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f4b1-107">Remarks</span></span>  
 <span data-ttu-id="8f4b1-108">`RuntimeThreadSuspended` Powiadomień może wystąpić w dowolnej chwili między [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) oraz skojarzonych z nimi [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="8f4b1-109">Powiadomienia, które mają miejsce między [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` dla wątków, które były uruchomione w niezarządzanych kodu i konto zostało zawieszone po ich wprowadzeniu do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="8f4b1-110">Ogólnie rzecz biorąc to wywołanie zwrotne występuje tuż po wątek jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="8f4b1-111">Jeśli aktualnie wykonywane wątku (wątek tego wywołania zwrotnego wywoływana) jest ten, który jest wstrzymywane, to wywołanie zwrotne odbywa się jednak tuż przed wątek jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f4b1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f4b1-112">Requirements</span></span>  
 <span data-ttu-id="8f4b1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f4b1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f4b1-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f4b1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f4b1-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f4b1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f4b1-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f4b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f4b1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f4b1-117">See Also</span></span>  
 [<span data-ttu-id="8f4b1-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f4b1-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8f4b1-119">RuntimeThreadResumed, metoda</span><span class="sxs-lookup"><span data-stu-id="8f4b1-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
