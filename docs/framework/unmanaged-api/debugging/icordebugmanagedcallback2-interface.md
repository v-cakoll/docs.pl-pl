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
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793313"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 — Interfejs
Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2` jest logicznym rozszerzeniem interfejsu [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ChangeConnection, metoda](icordebugmanagedcallback2-changeconnection-method.md)|Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.|  
|[CreateConnection, metoda](icordebugmanagedcallback2-createconnection-method.md)|Powiadamia debuger o utworzeniu nowego połączenia.|  
|[DestroyConnection, metoda](icordebugmanagedcallback2-destroyconnection-method.md)|Powiadamia debuger o przerwaniu określonego połączenia.|  
|[Exception, metoda](icordebugmanagedcallback2-exception-method.md)|Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.|  
|[ExceptionUnwind, metoda](icordebugmanagedcallback2-exceptionunwind-method.md)|Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.|  
|[FunctionRemapComplete, metoda](icordebugmanagedcallback2-functionremapcomplete-method.md)|Powiadamia debuger, że wykonywanie kodu zostało przełączone do nowej wersji edytowanej funkcji.|  
|[FunctionRemapOpportunity, metoda](icordebugmanagedcallback2-functionremapopportunity-method.md)|Powiadamia debuger, że wykonanie kodu osiągnęło punkt sekwencji w starszej wersji edytowanej funkcji.|  
|[MDANotification, metoda](icordebugmanagedcallback2-mdanotification-method.md)|Zapewnia powiadomienie, że wykonanie kodu napotkało komunikat asystenta debugowania (MDA).|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugManagedCallback2` rozszerza interfejs `ICorDebugManagedCallback`, aby obsługiwał nowe zdarzenia debugowania wprowadzone w .NET Framework wersji 2,0.  
  
 Debuger musi implementować `ICorDebugManagedCallback2`, jeśli debugowanie .NET Framework 2,0 aplikacji. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
