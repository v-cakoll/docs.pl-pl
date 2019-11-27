---
title: ICorProfilerCallback::RemotingClientInvocationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
ms.openlocfilehash: 5de291774f1e20b4c399c416f9f52657fa8a9a84
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445827"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="b9a82-102">ICorProfilerCallback::RemotingClientInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="b9a82-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="b9a82-103">Powiadamia program profilujący o rozpoczęciu wywołania usług zdalnych.</span><span class="sxs-lookup"><span data-stu-id="b9a82-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9a82-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9a82-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9a82-105">Remarks</span></span>  
 <span data-ttu-id="b9a82-106">To zdarzenie jest takie samo dla wywołań synchronicznych i asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="b9a82-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="b9a82-107">Każda z następujących par wywołań zwrotnych nastąpi w tym samym wątku:</span><span class="sxs-lookup"><span data-stu-id="b9a82-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="b9a82-108">`RemotingClientInvocationStarted` i [ICorProfilerCallback:: RemotingClientSendingMessage —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="b9a82-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="b9a82-109">[ICorProfilerCallback:: RemotingClientReceivingReply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i [ICorProfilerCallback:: RemotingClientInvocationFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="b9a82-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="b9a82-110">[ICorProfilerCallback:: RemotingServerInvocationReturned —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) i [ICorProfilerCallback:: RemotingServerSendingReply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="b9a82-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="b9a82-111">Należy pamiętać o następujących problemach z wywołaniami zwrotnymi usług zdalnych:</span><span class="sxs-lookup"><span data-stu-id="b9a82-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="b9a82-112">Wykonanie funkcji zdalnej nie jest odzwierciedlone przez interfejs API profilera, więc powiadomienia o funkcjach, które są wywoływane z klienta i wykonywane na serwerze, nie są prawidłowo odbierane.</span><span class="sxs-lookup"><span data-stu-id="b9a82-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="b9a82-113">Rzeczywiste wywołanie odbywa się za pośrednictwem obiektu serwera proxy; do profilera pojawia się, że niektóre funkcje są skompilowane JIT, ale nigdy nie były używane.</span><span class="sxs-lookup"><span data-stu-id="b9a82-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="b9a82-114">Profiler nie odbiera dokładne powiadomienia o asynchronicznych zdarzeniach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="b9a82-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a82-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9a82-115">Requirements</span></span>  
 <span data-ttu-id="b9a82-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a82-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a82-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9a82-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9a82-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b9a82-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9a82-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a82-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a82-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9a82-120">See also</span></span>

- [<span data-ttu-id="b9a82-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9a82-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
