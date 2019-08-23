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
ms.openlocfilehash: ca33436d98edf5844a5ca27c9ac89648f10ec0c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909985"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 — Interfejs
Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2`jest logicznym rozszerzeniem interfejsu [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ChangeConnection, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.|  
|[CreateConnection, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Powiadamia debuger o utworzeniu nowego połączenia.|  
|[DestroyConnection, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Powiadamia debuger o przerwaniu określonego połączenia.|  
|[Exception, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.|  
|[ExceptionUnwind, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.|  
|[FunctionRemapComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Powiadamia debuger, że wykonywanie kodu zostało przełączone do nowej wersji edytowanej funkcji.|  
|[FunctionRemapOpportunity, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Powiadamia debuger, że wykonanie kodu osiągnęło punkt sekwencji w starszej wersji edytowanej funkcji.|  
|[MDANotification, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Zapewnia powiadomienie, że wykonanie kodu napotkało komunikat asystenta debugowania (MDA).|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugManagedCallback2` Interfejs`ICorDebugManagedCallback` rozszerza interfejs obsługujący nowe zdarzenia debugowania wprowadzone w .NET Framework w wersji 2,0.  
  
 Debuger musi implementować `ICorDebugManagedCallback2` w przypadku debugowania aplikacji .NET Framework 2,0. Wystąpienie `ICorDebugManagedCallback` lub`ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
