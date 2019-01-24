---
title: ICorDebugManagedCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 516485d39f1e18a3b82886ed08cd0344c16236dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640540"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback — Interfejs
Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Break, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Powiadamia debuger po <xref:System.Reflection.Emit.OpCodes.Break> instrukcji w strumieniu kod jest wykonywany.|  
|[Breakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Powiadamia debugera, gdy zostanie osiągnięty punkt przerwania.|  
|[BreakpointSetError, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Powiadamia debugera, środowisko uruchomieniowe języka wspólnego (CLR) i nie można powiązać dokładnie punkcie przerwania, który został ustawiony, aby funkcja była just-in-time (JIT) skompilowany.|  
|[ControlCTrap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Powiadamia debugera, CTRL + C jest zablokował w debugowanym procesie.|  
|[CreateAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Powiadamia debuger utworzono domeny aplikacji.|  
|[CreateProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Powiadamia debuger został dołączony proces lub uruchomiona po raz pierwszy.|  
|[CreateThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Powiadamia debugera, czy wątek rozpoczęła wykonywanie kodu zarządzanego.|  
|[DebuggerError, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Powiadamia debuger wystąpił błąd podczas próby obsłużyć zdarzenie ze środowiska CLR.|  
|[EditAndContinueRemap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Przestarzałe. Powiadamia debugera, zdarzenia ponowne mapowanie została wysłana do środowiska IDE.|  
|[EvalComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Powiadamia użytkownika debugera o zakończeniu oceny.|  
|[EvalException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Powiadamia debugera, że ocena została przerwana z powodu nieobsługiwanego wyjątku.|  
|[Exception, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Powiadamia debuger zgłoszony wyjątek z kodu zarządzanego.|  
|[ExitAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Powiadamia debuger zakończył domeny aplikacji.|  
|[ExitProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Powiadamia debugera, że proces został zakończony.|  
|[ExitThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Powiadamia debugera, że zakończył się wątek, który był wykonywany kod zarządzany.|  
|[LoadAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Powiadamia debugera, czy zestaw CLR został pomyślnie załadowany.|  
|[LoadClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Powiadamia debuger załadowano klasy.|  
|[LoadModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Powiadamia debugera, że moduł CLR został pomyślnie załadowany.|  
|[LogMessage, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Powiadamia debuger wątku środowiska CLR zarządzane została wywołana metoda <xref:System.Diagnostics.EventLog> klasy, aby rejestrować zdarzenia.|  
|[LogSwitch, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Powiadamia debuger wątku środowiska CLR zarządzane została wywołana metoda <xref:System.Diagnostics.Switch> klasy, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowanie śledzenia.|  
|[NameChange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Powiadamia debugera, że zmieniono nazwę domeny aplikacji lub wątku.|  
|[StepComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Powiadamia debugera, że krok została zakończona.|  
|[UnloadAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Powiadamia debuger Zestaw CLR został zwolniony.|  
|[UnloadClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Powiadamia debuger jest zwalniany klasy.|  
|[UnloadModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Powiadamia debuger moduł CLR (DLL) został zwolniony.|  
|[UpdateModuleSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Powiadamia debugera, że symbole dla modułu CLR zostały zmienione.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania zwrotne są serializowane, o nazwie w tym samym wątku, a następnie wywołać z procesu w stanie zsynchronizowane.  
  
 Każda implementacja wywołania zwrotnego musi wywołać [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) można wznowić wykonywania. Jeśli `ICorDebugController::Continue` nie zostanie wywołana przed zwraca wywołanie zwrotne, proces pozostanie zatrzymany i nie więcej wywołań zwrotnych zdarzeń będzie powtarzana, dopóki nie `ICorDebugController::Continue` jest wywoływana.  
  
 Debuger musi implementować [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) Jeśli jest on debugowanie aplikacji w wersji 2.0 programu .NET Framework. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przekazywany jako obiektu wywołania zwrotnego do [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
