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
ms.openlocfilehash: b00be90316598e458f01f6cd440d0ad0a2e79c50
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212363"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 — Interfejs
Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2`jest logicznym rozszerzeniem interfejsu [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .  
  
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
 `ICorDebugManagedCallback2`Interfejs rozszerza `ICorDebugManagedCallback` interfejs obsługujący nowe zdarzenia debugowania wprowadzone w .NET Framework w wersji 2,0.  
  
 Debuger musi implementować w `ICorDebugManagedCallback2` przypadku debugowania aplikacji .NET Framework 2,0. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ICorDebugManagedCallback — Interfejs](icordebugmanagedcallback-interface.md)
