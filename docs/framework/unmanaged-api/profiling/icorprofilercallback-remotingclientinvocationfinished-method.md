---
title: ICorProfilerCallback::RemotingClientInvocationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2722497db5622dee4adcfd9381837477b89a8f63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041889"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="0ee58-102">ICorProfilerCallback::RemotingClientInvocationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ee58-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="0ee58-103">Powiadamia program profilujący, że wywołanie komunikacji zdalnej zostało uruchomione ukończone na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="0ee58-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ee58-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0ee58-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ee58-105">Remarks</span></span>  
 <span data-ttu-id="0ee58-106">Jeśli wywołanie komunikacji zdalnej synchroniczne, jego również wykonaniu do zakończenia na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0ee58-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="0ee58-107">Jeśli asynchroniczne wywołanie komunikacji zdalnej, odpowiedź nadal może być oczekiwane w przypadku połączenie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0ee58-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="0ee58-108">Jeśli odpowiedź oczekuje się, nastąpi jako wywołanie [icorprofilercallback::remotingclientreceivingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i dodatkowe wywołanie `RemotingClientInvocationFinished` do wskazania wymagane przetwarzanie dodatkowej wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="0ee58-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="0ee58-109">Każdy następujące pary wywołania zwrotne mają miejsce, w tym samym wątku:</span><span class="sxs-lookup"><span data-stu-id="0ee58-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="0ee58-110">`RemotingClientInvocationStarted` i [icorprofilercallback::remotingclientsendingmessage —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="0ee58-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="0ee58-111">[Icorprofilercallback::remotingclientreceivingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i [icorprofilercallback::remotingclientinvocationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="0ee58-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="0ee58-112">[Icorprofilercallback::remotingserverinvocationreturned —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) i [icorprofilercallback::remotingserversendingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="0ee58-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="0ee58-113">Należy pamiętać o następujących problemów za pomocą wywołania zwrotne komunikacji zdalnej:</span><span class="sxs-lookup"><span data-stu-id="0ee58-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="0ee58-114">Wykonywanie funkcji komunikacji zdalnej nie zostaną uwzględnione przez profiler interfejsu API, dzięki czemu nie są prawidłowo odbierane powiadomienia dla funkcji, które są wywoływane z klienta i są stosowane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0ee58-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="0ee58-115">Rzeczywiste wywołanie się stanie, za pomocą obiektu serwera proxy; do programu profilującego wydaje się, że niektóre funkcje są skompilowane JIT, ale nigdy używane.</span><span class="sxs-lookup"><span data-stu-id="0ee58-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="0ee58-116">Program profilujący nie odbiera dokładnego powiadomienia o zdarzeniach asynchronicznych komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="0ee58-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ee58-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ee58-117">Requirements</span></span>  
 <span data-ttu-id="0ee58-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ee58-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ee58-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ee58-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ee58-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ee58-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ee58-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ee58-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee58-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ee58-122">See also</span></span>

- [<span data-ttu-id="0ee58-123">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ee58-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
