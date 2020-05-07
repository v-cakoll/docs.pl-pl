---
title: ICorDebugController, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: e494bbb24e8f2245593e7945625e72e70ae1dde5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892773"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController, interfejs

Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, w którym można kontrolować kontekst wykonywania kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Ta metoda jest przestarzała.|  
|`ICorDebugController::CommitChanges`|Ta metoda jest przestarzała.|  
|[Continue, metoda](icordebugcontroller-continue-method.md)|Wznawia wykonywanie zarządzanych wątków po wywołaniu [ICorDebugController:: Stop](icordebugcontroller-stop-method.md).|  
|[Detach, metoda](icordebugcontroller-detach-method.md)|Odłącza debuger od domeny procesu lub aplikacji.|  
|[EnumerateThreads, metoda](icordebugcontroller-enumeratethreads-method.md)|Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.|  
|[HasQueuedCallbacks, metoda](icordebugcontroller-hasqueuedcallbacks-method.md)|Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne są obecnie umieszczane w kolejce dla określonego wątku.|  
|[IsRunning, metoda](icordebugcontroller-isrunning-method.md)|Pobiera wartość wskazującą, czy wątki w procesie są obecnie uruchomione swobodnie.|  
|[SetAllThreadsDebugState, metoda](icordebugcontroller-setallthreadsdebugstate-method.md)|Ustawia stan debugowania wszystkich zarządzanych wątków w procesie.|  
|[Stop, metoda](icordebugcontroller-stop-method.md)|Wykonuje przerwanie w ramach wszystkich wątków, które uruchamiają kod zarządzany w procesie.|  
|[Terminate — Metoda](icordebugcontroller-terminate-method.md)|Kończy proces z określonym kodem zakończenia.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `ICorDebugController` kontroluje proces, zakres obejmuje wszystkie wątki procesu. Jeśli `ICorDebugController` kontroluje domenę aplikacji, zakres obejmuje tylko wątki tej konkretnej domeny aplikacji.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
