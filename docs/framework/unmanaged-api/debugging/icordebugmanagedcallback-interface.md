---
title: "ICorDebugManagedCallback — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback
helpviewer_keywords: ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b72a2814ee2276363152052c7bf734104d4f395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback — Interfejs
Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BREAK — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Powiadamia debuger podczas <xref:System.Reflection.Emit.OpCodes.Break> wykonaniem instrukcji w strumieniu kodu.|  
|[Breakpoint — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Powiadamia debugera w przypadku napotkania punktu przerwania.|  
|[BreakpointSetError — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Powiadamia debugera, że środowisko uruchomieniowe języka wspólnego (CLR) nie może powiązać dokładnie punkt przerwania ustawiony przed funkcją just-in-time (JIT) skompilowany.|  
|[ControlCTrap — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Powiadamia debugera, że klawisze CTRL + C jest kolor w debugowanym procesie.|  
|[CreateAppDomain — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Powiadamia debugera, czy domena aplikacji została utworzona.|  
|[CreateProcess — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Powiadamia debuger został dołączony proces lub uruchomiony po raz pierwszy.|  
|[CreateThread — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Powiadamia debugera, że wątek rozpoczęła wykonywanie kodu zarządzanego.|  
|[DebuggerError — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Powiadamia debugera wystąpił błąd podczas próby obsługi zdarzenia ze środowiska CLR.|  
|[EditAndContinueRemap — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Przestarzałe. Powiadamia debugera, czy zdarzenie ponownego mapowania zostało wysłane do środowiska IDE.|  
|[EvalComplete — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Powiadamia debuger ocenę została ukończona.|  
|[EvalException — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Powiadamia debugera, że ocenę zostało przerwane z powodu nieobsługiwanego wyjątku.|  
|[Exception — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Powiadamia debugera, czy wyjątek został zgłoszony z kodu zarządzanego.|  
|[ExitAppDomain — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Powiadamia debuger zakończył domeny aplikacji.|  
|[ExitProcess — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Powiadamia debugera, że proces został zakończony.|  
|[ExitThread — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Powiadamia debuger zakończył wątku, który został wykonywania kodu zarządzanego.|  
|[LoadAssembly — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Powiadamia debugera, czy zestaw CLR został załadowany pomyślnie.|  
|[LoadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Powiadamia debuger załadowaniu klasy.|  
|[LoadModule — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Powiadamia debugera, że moduł CLR został pomyślnie załadowany.|  
|[LogMessage — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Powiadamia debuger wątku CLR zarządzanych została wywołana metoda <xref:System.Diagnostics.EventLog> klasę, aby rejestrować zdarzenia.|  
|[LogSwitch — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Powiadamia debuger wątku CLR zarządzanych została wywołana metoda <xref:System.Diagnostics.Switch> klasę, aby utworzyć, zmodyfikować lub usunąć przełącznika debugowania śledzenia.|  
|[NameChange — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Powiadamia debugera, że nazwa domeny aplikacji lub wątek został zmieniony.|  
|[StepComplete — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Powiadamia debugera, czy krok zostało zakończone.|  
|[UnloadAssembly — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Powiadamia debuger Zestaw CLR został usunięty z pamięci.|  
|[UnloadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Powiadamia debugera jest zwalniany klasy.|  
|[UnloadModule — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Powiadamia debuger CLR modułu (dynamicznie DLL) został usunięty z pamięci.|  
|[UpdateModuleSymbols — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Powiadamia debugera, że symboli dla modułu CLR zostały zmienione.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania zwrotne serializacji, w tym samym wątku i wywoływana z procesem w stanie zsynchronizowane.  
  
 Każda implementacja wywołania zwrotnego należy wywołać [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) można wznowić wykonywania. Jeśli `ICorDebugController::Continue` nie jest wywoływana przed zwraca wywołania zwrotnego, proces pozostanie zatrzymana i nie więcej wywołania zwrotne zdarzeń będzie powtarzana, dopóki nie `ICorDebugController::Continue` jest wywoływana.  
  
 Debuger musi implementować [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) Jeśli trwa debugowanie aplikacji .NET Framework w wersji 2.0. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przekazywany jako obiektu wywołania zwrotnego do [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
