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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bec96ef50416d946b1f12fd503e04f976ca58f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662933"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="fb3d2-102">ICorProfilerCallback::RemotingClientInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb3d2-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="fb3d2-103">Powiadamia program profilujący, że wywołanie komunikacji zdalnej została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="fb3d2-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb3d2-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb3d2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb3d2-105">Remarks</span></span>  
 <span data-ttu-id="fb3d2-106">To zdarzenie jest taka sama dla wywołania synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="fb3d2-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="fb3d2-107">Każdy następujące pary wywołania zwrotne mają miejsce, w tym samym wątku:</span><span class="sxs-lookup"><span data-stu-id="fb3d2-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="fb3d2-108">`RemotingClientInvocationStarted` i [icorprofilercallback::remotingclientsendingmessage —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb3d2-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="fb3d2-109">[Icorprofilercallback::remotingclientreceivingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i [icorprofilercallback::remotingclientinvocationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb3d2-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="fb3d2-110">[Icorprofilercallback::remotingserverinvocationreturned —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) i [icorprofilercallback::remotingserversendingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb3d2-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="fb3d2-111">Należy pamiętać o następujących problemów za pomocą wywołania zwrotne komunikacji zdalnej:</span><span class="sxs-lookup"><span data-stu-id="fb3d2-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="fb3d2-112">Wykonywanie funkcji komunikacji zdalnej nie zostaną uwzględnione przez profiler interfejsu API, dzięki czemu nie są prawidłowo odbierane powiadomienia dla funkcji, które są wywoływane z klienta i są stosowane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="fb3d2-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="fb3d2-113">Rzeczywiste wywołanie się stanie, za pomocą obiektu serwera proxy; do programu profilującego wydaje się, że niektóre funkcje są skompilowane JIT, ale nigdy używane.</span><span class="sxs-lookup"><span data-stu-id="fb3d2-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="fb3d2-114">Program profilujący nie odbiera dokładnego powiadomienia o zdarzeniach asynchronicznych komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="fb3d2-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb3d2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb3d2-115">Requirements</span></span>  
 <span data-ttu-id="fb3d2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb3d2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb3d2-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb3d2-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb3d2-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb3d2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb3d2-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb3d2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3d2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb3d2-120">See also</span></span>

- [<span data-ttu-id="fb3d2-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb3d2-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
