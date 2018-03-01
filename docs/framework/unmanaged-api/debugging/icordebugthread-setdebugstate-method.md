---
title: "ICorDebugThread::SetDebugState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2754caf11f89358b3e81e6324835d5b2e12f17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState — Metoda
Określa flagi opisujące stan debugowania tego ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 [in] Bitowe połączenie wartości wyliczenia CorDebugThreadState, określające stan debugowania tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 `SetDebugState`Ustawia bieżący stan debugowania wątku. ("Bieżący stan debugowania" reprezentuje stan debugowania, jeśli proces będzie kontynuowane, zamiast rzeczywistej bieżącego stanu.) Normalne wartość ta jest THREAD_RUNNING. Tylko debuger może mieć wpływ na stan debugowania wątku. Debugowanie stany ostatniego w poprzek będzie nadal występować, jeśli chcesz zachować wątku THREAD_SUSPENDed przez wiele będzie nadal występować, można ustawić go raz, a następnie nie są martwić się o jego. Zawieszanie wątków i wznawianie proces może spowodować zakleszczenie, chociaż jest mało prawdopodobne, zwykle. Jest to wewnętrzne jakości wątków i procesów, w projekcie. Debuger może asynchronicznie przerywanie i wznawianie wątków podziału zakleszczenia. Jeśli stan użytkownika dla wątku zawiera USER_UNSAFE_POINT, wątek może zablokować wyrzucania elementów bezużytecznych (GC). Oznacza to, że wątku zawieszonym ma znacznie wyższa szansy powodować zakleszczenie. Nie może to mieć wpływ na debugowania, które zdarzenia już do kolejki. W związku z tym debuger powinien opróżniania kolejki całe zdarzenie (wywołując [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) przed wstrzymywanie i wznawianie wątków. Else on może pobrać zdarzenia w wątku, który określa, że została już wstrzymana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
