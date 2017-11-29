---
title: "ICorDebugController::SetAllThreadsDebugState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.SetAllThreadsDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5a033ef2efd8fa5e3b519e19b62ce2dfb84a5e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState — Metoda
Ustawia stan debugowania wszystkie wątki zarządzane w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 [in] Wartość wyliczenia "CorDebugThreadState", który określa stan wątku do debugowania.  
  
 `pExceptThisThread`  
 [in] Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątku zwolnione z ustawienia stanu debugowania. Jeśli ta wartość jest równa null, jest wykluczany żadnego wątku.  
  
## <a name="remarks"></a>Uwagi  
 `SetAllThreadsDebugState` Metody może mieć wpływ na wątków, które nie są widoczne za pośrednictwem [EnumerateThreads — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), tak wątków, które zostały wstrzymane z `SetAllThreadsDebugState` — metoda musi zostać przywrócone `SetAllThreadsDebugState` metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
