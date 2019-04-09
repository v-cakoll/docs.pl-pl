---
title: ICorProfilerCallback::RemotingClientReceivingReply — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5865935af96260982d47b778d208f4235f6245e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164921"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>ICorProfilerCallback::RemotingClientReceivingReply — Metoda
Powiadamia program profilujący po stronie serwera część wywołanie komunikacji zdalnej została zakończona i klient otrzymuje teraz i wkrótce do przetwarzania odpowiedzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a>Parametry  
 `pCookie`  
 [in] Wartość, która będzie odpowiadać za pomocą wartość podana w [icorprofilercallback::remotingserversendingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) w tych warunkach:  
  
-   Pliki cookie identyfikatora GUID komunikacji zdalnej są aktywne.  
  
-   Kanał powiedzie się podczas przesyłania wiadomości.  
  
-   Identyfikator GUID pliki cookie są aktywne na proces po stronie serwera.  
  
 Dzięki temu można łatwo parowanie wywołaniem funkcji zdalnych wywołań.  
  
 `fIsAsync`  
 [in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
