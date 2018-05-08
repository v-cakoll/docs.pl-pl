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
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>ICorProfilerCallback::RemotingClientInvocationFinished — Metoda
Powiadamia profilera czy wywołaniem funkcji zdalnych zostało uruchomione do wykonania na kliencie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wywołaniem funkcji zdalnych synchroniczne, go również dysponuje do wykonania na serwerze. Jeśli wywołaniem funkcji zdalnych asynchroniczne, odpowiedź nadal może oczekiwane w przypadku wywołania jest obsługiwane. Jeśli odpowiedź ma, nastąpi jako wywołanie [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i wywołanie dodatkowe `RemotingClientInvocationFinished` wskazująca wymagane przetwarzanie dodatkowej wywołania asynchronicznego.  
  
 Każdy z następujących par wywołania zwrotne zostanie przeprowadzona na tym samym wątku:  
  
-   `RemotingClientInvocationStarted` i [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
-   [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) i [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
-   [ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) i [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 Należy zwrócić uwagę na następujące problemy z wywołań zwrotnych usług zdalnych:  
  
-   Wykonanie funkcji komunikacji zdalnej nie jest widoczna przez profiler interfejsu API, więc nie są prawidłowo odbierane powiadomienia dla funkcji o nazwie z klienta i wykonywane na serwerze. Rzeczywiste wywołanie sytuacji za pośrednictwem obiektu proxy; Aby profilera wygląda na to, że niektóre funkcje są kompilowane JIT, lecz nigdy używane.  
  
-   Profiler nie otrzymuje dokładne powiadomienia o zdarzeniach asynchroniczną komunikację zdalną.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
