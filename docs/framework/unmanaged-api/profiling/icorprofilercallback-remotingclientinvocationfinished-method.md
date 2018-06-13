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
ms.openlocfilehash: ec45b73b496efdbe6328985b5f77f731d8a78cc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453408"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="d1d88-102">ICorProfilerCallback::RemotingClientInvocationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1d88-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="d1d88-103">Powiadamia profilera czy wywołaniem funkcji zdalnych zostało uruchomione do wykonania na kliencie.</span><span class="sxs-lookup"><span data-stu-id="d1d88-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d88-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d1d88-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1d88-105">Remarks</span></span>  
 <span data-ttu-id="d1d88-106">Jeśli wywołaniem funkcji zdalnych synchroniczne, go również dysponuje do wykonania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d1d88-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="d1d88-107">Jeśli wywołaniem funkcji zdalnych asynchroniczne, odpowiedź nadal może oczekiwane w przypadku wywołania jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d1d88-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="d1d88-108">Jeśli odpowiedź ma, nastąpi jako wywołanie [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i wywołanie dodatkowe `RemotingClientInvocationFinished` wskazująca wymagane przetwarzanie dodatkowej wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="d1d88-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="d1d88-109">Każdy z następujących par wywołania zwrotne zostanie przeprowadzona na tym samym wątku:</span><span class="sxs-lookup"><span data-stu-id="d1d88-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="d1d88-110">`RemotingClientInvocationStarted` i [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="d1d88-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="d1d88-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="d1d88-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="d1d88-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) i [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="d1d88-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="d1d88-113">Należy zwrócić uwagę na następujące problemy z wywołań zwrotnych usług zdalnych:</span><span class="sxs-lookup"><span data-stu-id="d1d88-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="d1d88-114">Wykonanie funkcji komunikacji zdalnej nie jest widoczna przez profiler interfejsu API, więc nie są prawidłowo odbierane powiadomienia dla funkcji o nazwie z klienta i wykonywane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d1d88-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="d1d88-115">Rzeczywiste wywołanie sytuacji za pośrednictwem obiektu proxy; Aby profilera wygląda na to, że niektóre funkcje są kompilowane JIT, lecz nigdy używane.</span><span class="sxs-lookup"><span data-stu-id="d1d88-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="d1d88-116">Profiler nie otrzymuje dokładne powiadomienia o zdarzeniach asynchroniczną komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="d1d88-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d88-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1d88-117">Requirements</span></span>  
 <span data-ttu-id="d1d88-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d88-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d88-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1d88-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1d88-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1d88-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d88-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d88-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d88-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1d88-122">See Also</span></span>  
 [<span data-ttu-id="d1d88-123">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1d88-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
