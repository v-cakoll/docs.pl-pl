---
title: "ICorProfilerCallback::RemotingServerReceivingMessage — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerReceivingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5947541204edf7fd4359dfa3aca78ea62c8009c6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage — Metoda
Powiadamia profilera, że proces odebrał żądanie aktywacji lub wywołanie metody zdalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCookie`  
 [in] Wartość, która będzie zgodne z wartością w [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) w tych warunkach:  
  
-   Pliki cookie GUID komunikacji zdalnej są aktywne.  
  
-   Kanał pomyślnie przesyła komunikat.  
  
-   Identyfikator GUID pliki cookie są aktywne w procesie po stronie klienta.  
  
 Umożliwia łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logiczne.  
  
 `fIsAsync`  
 [in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne, a w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli żądanie komunikatu jest asynchroniczny, żądanie może być obsługiwany przez wszystkie wątki dowolnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
