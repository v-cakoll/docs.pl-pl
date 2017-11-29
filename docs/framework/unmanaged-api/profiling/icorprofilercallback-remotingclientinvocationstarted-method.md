---
title: "ICorProfilerCallback::RemotingClientInvocationStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae91a35af0e4a0895fa58783521de1d3b95179a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="0087a-102">ICorProfilerCallback::RemotingClientInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="0087a-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="0087a-103">Powiadamia profilera rozpoczęto wywołaniem funkcji zdalnych.</span><span class="sxs-lookup"><span data-stu-id="0087a-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0087a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0087a-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0087a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0087a-105">Remarks</span></span>  
 <span data-ttu-id="0087a-106">To zdarzenie jest taka sama dla wywołania synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="0087a-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="0087a-107">Każdy z następujących par wywołania zwrotne zostanie przeprowadzona na tym samym wątku:</span><span class="sxs-lookup"><span data-stu-id="0087a-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="0087a-108">`RemotingClientInvocationStarted`i [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="0087a-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="0087a-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="0087a-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="0087a-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) i [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="0087a-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="0087a-111">Należy zwrócić uwagę na następujące problemy z wywołań zwrotnych usług zdalnych:</span><span class="sxs-lookup"><span data-stu-id="0087a-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="0087a-112">Wykonanie funkcji komunikacji zdalnej nie jest widoczna przez profiler interfejsu API, więc nie są prawidłowo odbierane powiadomienia dla funkcji o nazwie z klienta i wykonywane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0087a-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="0087a-113">Rzeczywiste wywołanie sytuacji za pośrednictwem obiektu proxy; Aby profilera wygląda na to, że niektóre funkcje są kompilowane JIT, lecz nigdy używane.</span><span class="sxs-lookup"><span data-stu-id="0087a-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="0087a-114">Profiler nie otrzymuje dokładne powiadomienia o zdarzeniach asynchroniczną komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="0087a-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0087a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0087a-115">Requirements</span></span>  
 <span data-ttu-id="0087a-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0087a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0087a-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0087a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0087a-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0087a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0087a-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0087a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0087a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0087a-120">See Also</span></span>  
 [<span data-ttu-id="0087a-121">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="0087a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
