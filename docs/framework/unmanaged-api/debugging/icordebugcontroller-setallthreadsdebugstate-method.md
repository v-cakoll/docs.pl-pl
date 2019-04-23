---
title: ICorDebugController::SetAllThreadsDebugState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 280dc3f0271d7326fe4c22b813abebfd4d45c89e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138479"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState — Metoda
Ustawia stan debugowania wszystkie zarządzane wątki w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 [in] Wartość wyliczenia "Cordebugthreadstate —", który określa stan wątku do debugowania.  
  
 `pExceptThisThread`  
 [in] Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek zwolnione z ustawieniem stanu debugowania. Jeżeli ta wartość jest równa null, jest wykluczany żadnego wątku.  
  
## <a name="remarks"></a>Uwagi  
 `SetAllThreadsDebugState` Metoda może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [enumeratethreads — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), więc wątków, które zostały wstrzymane z `SetAllThreadsDebugState` metody będą musieli można wznowić z `SetAllThreadsDebugState` metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
