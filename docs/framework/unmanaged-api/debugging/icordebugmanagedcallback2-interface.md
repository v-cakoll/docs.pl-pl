---
title: ICorDebugManagedCallback2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1ecfea208f87f53f15fcc4cdafb58341c293e43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763831"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 — Interfejs
Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2` jest logicznym rozszerzeniem [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interfejsu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ChangeConnection, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Powiadamia debuger zmieniono zestaw zadań skojarzonych z określonego połączenia.|  
|[CreateConnection, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Powiadamia debugera, że utworzono nowe połączenie.|  
|[DestroyConnection, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Powiadamia debugera, że określone połączenie zostało zakończone.|  
|[Exception, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Powiadamia debuger rozpoczęto wyszukiwania dla obsługi wyjątków.|  
|[ExceptionUnwind, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Zawiera powiadomienia o stanie podczas procesu odwijania wyjątku.|  
|[FunctionRemapComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Powiadamia debugera, że wykonywanie kodu zostało przełączone do nowej wersji przeprowadzono edycję funkcji.|  
|[FunctionRemapOpportunity, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Powiadamia debugera, że wykonywanie kodu osiągnęła punktu sekwencji w starszej wersji przeprowadzono edycję funkcji.|  
|[MDANotification, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Zapewnia powiadomienie napotkała wykonywania kodu zarządzanego Asystenta ustawień (MDA) komunikat dotyczący debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugManagedCallback2` Interfejs rozszerza `ICorDebugManagedCallback` interfejsu do obsługi nowych zdarzeń debugowania wprowadzone w programie .NET Framework w wersji 2.0.  
  
 Debuger musi implementować `ICorDebugManagedCallback2` Jeśli jest on debugowania aplikacji .NET Framework 2.0. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przekazywany jako obiektu wywołania zwrotnego do [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
