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
ms.openlocfilehash: 8a042e71690b5ae77c1e4cda7be394a163ab2774
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503266"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="c824b-102">ICorProfilerCallback::RemotingClientInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="c824b-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="c824b-103">Powiadamia program profilujący o rozpoczęciu wywołania usług zdalnych.</span><span class="sxs-lookup"><span data-stu-id="c824b-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c824b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c824b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c824b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c824b-105">Remarks</span></span>  
 <span data-ttu-id="c824b-106">To zdarzenie jest takie samo dla wywołań synchronicznych i asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="c824b-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="c824b-107">Każda z następujących par wywołań zwrotnych nastąpi w tym samym wątku:</span><span class="sxs-lookup"><span data-stu-id="c824b-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="c824b-108">`RemotingClientInvocationStarted`i [ICorProfilerCallback:: RemotingClientSendingMessage —](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="c824b-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="c824b-109">[ICorProfilerCallback:: RemotingClientReceivingReply —](icorprofilercallback-remotingclientreceivingreply-method.md) i [ICorProfilerCallback:: RemotingClientInvocationFinished —](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="c824b-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="c824b-110">[ICorProfilerCallback:: RemotingServerInvocationReturned —](icorprofilercallback-remotingserverinvocationreturned-method.md) i [ICorProfilerCallback:: RemotingServerSendingReply —](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="c824b-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="c824b-111">Należy pamiętać o następujących problemach z wywołaniami zwrotnymi usług zdalnych:</span><span class="sxs-lookup"><span data-stu-id="c824b-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="c824b-112">Wykonanie funkcji zdalnej nie jest odzwierciedlone przez interfejs API profilera, więc powiadomienia o funkcjach, które są wywoływane z klienta i wykonywane na serwerze, nie są prawidłowo odbierane.</span><span class="sxs-lookup"><span data-stu-id="c824b-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="c824b-113">Rzeczywiste wywołanie odbywa się za pośrednictwem obiektu serwera proxy; do profilera pojawia się, że niektóre funkcje są skompilowane JIT, ale nigdy nie były używane.</span><span class="sxs-lookup"><span data-stu-id="c824b-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="c824b-114">Profiler nie odbiera dokładne powiadomienia o asynchronicznych zdarzeniach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="c824b-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c824b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c824b-115">Requirements</span></span>  
 <span data-ttu-id="c824b-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c824b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c824b-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c824b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c824b-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c824b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c824b-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c824b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c824b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c824b-120">See also</span></span>

- [<span data-ttu-id="c824b-121">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c824b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
