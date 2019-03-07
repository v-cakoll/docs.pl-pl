---
title: ICorDebugThread::SetDebugState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499696"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState — Metoda
Ustawia flagi opisujące stan debugowania tego ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 [in] Bitowa kombinacja wartości wyliczenia cordebugthreadstate —, określające stan debugowania tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 `SetDebugState` Ustawia bieżący stan debugowania w wątku. ("Bieżący stan debugowania" reprezentuje stan debugowania, gdyby proces będzie kontynuowane nie rzeczywiste bieżącego stanu.) Normalna wartość to jest THREAD_RUNNING. Tylko debuger może wpłynąć na stan debugowania wątku. Debugowanie stany ostatniego na będzie nadal występował, więc jeśli chcesz zachować wątku THREAD_SUSPENDed za pośrednictwem wielu będzie się powtarzać, można ustawić go jeden raz i dzięki temu nie trzeba martwić. Zawieszanie wątków i wznawianie procesu może spowodować zakleszczenia, chociaż jest mało prawdopodobne, zwykle. To jest wewnętrzne jakość wątków i procesów i projektem. Debuger asynchronicznie można przerwać i wznawianie wątków można przerwać zakleszczenia. Jeśli stan użytkownika dla wątku zawiera USER_UNSAFE_POINT, wątek może blokować wyrzucania elementów bezużytecznych (GC). Oznacza to, że wątek wstrzymania ma znacznie wyższe prawdopodobieństwo powoduje zakleszczenia. Nie może to mieć wpływ na debugowania, który już do kolejki zdarzeń. Ten sposób debuger powinien opróżnienia kolejki całe zdarzenie (przez wywołanie metody [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) przed zawieszanie lub wznawianie wątków. Inne może ją odbierać zdarzenia w wątku, który uważa, że została już wstrzymana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
