---
title: ICorDebugController Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a>ICorDebugController Interface1
Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, których wykonanie kodu mogą być kontrolowane kontekstu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Ta metoda jest przestarzała.|  
|`ICorDebugController::CommitChanges`|Ta metoda jest przestarzała.|  
|[Continue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Wznawia wykonywanie wątków zarządzanych po wywołaniu [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Odłącza debugera z domeny proces lub aplikacji.|  
|[EnumerateThreads, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.|  
|[HasQueuedCallbacks, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne aktualnie czekają w kolejce dla określonego wątku.|  
|[IsRunning, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Pobiera wartość wskazującą, czy wątki tego procesu są aktualnie uruchomione za darmo.|  
|[SetAllThreadsDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Ustawia stan debugowania wszystkie wątki zarządzane w procesie.|  
|[Stop, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Wykonuje wspólne Zatrzymaj wszystkie wątki uruchomione kodu zarządzanego w procesie.|  
|[Terminate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Kończy proces o określony kod zakończenia.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `ICorDebugController` jest sterowanie procesem, zakres obejmuje wszystkie wątki tego procesu. Jeśli `ICorDebugController` jest kontrolowanie domeny aplikacji, zakres obejmuje tylko wątki tej domeny aplikacji.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
