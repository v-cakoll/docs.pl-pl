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
ms.openlocfilehash: 9a33b90bf39103756ab4fd07157739633997fb61
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788396"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback — Interfejs
Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Break, metoda](icordebugmanagedcallback-break-method.md)|Powiadamia debuger, gdy zostanie wykonana instrukcja <xref:System.Reflection.Emit.OpCodes.Break> w strumieniu kodu.|  
|[Breakpoint, metoda](icordebugmanagedcallback-breakpoint-method.md)|Powiadamia debuger w przypadku napotkania punktu przerwania.|  
|[BreakpointSetError, metoda](icordebugmanagedcallback-breakpointseterror-method.md)|Powiadamia debuger, że środowisko uruchomieniowe języka wspólnego (CLR) nie było w stanie prawidłowo powiązać punktu przerwania, który został ustawiony przed skompilowaniem funkcji just-in-Time (JIT).|  
|[ControlCTrap, metoda](icordebugmanagedcallback-controlctrap-method.md)|Powiadamia debuger, że w debugowanym procesie jest zalewkowany skrót CTRL + C.|  
|[CreateAppDomain, metoda](icordebugmanagedcallback-createappdomain-method.md)|Powiadamia debuger o utworzeniu domeny aplikacji.|  
|[CreateProcess, metoda](icordebugmanagedcallback-createprocess-method.md)|Powiadamia debuger, gdy proces został dołączony lub uruchomiony po raz pierwszy.|  
|[CreateThread, metoda](icordebugmanagedcallback-createthread-method.md)|Powiadamia debuger o rozpoczęciu wykonywania kodu zarządzanego przez wątek.|  
|[DebuggerError, metoda](icordebugmanagedcallback-debuggererror-method.md)|Powiadamia debuger, że wystąpił błąd podczas próby obsłużenia zdarzenia z CLR.|  
|[EditAndContinueRemap, metoda](icordebugmanagedcallback-editandcontinueremap-method.md)|Przestarzałe. Powiadamia debuger o wysłaniu zdarzenia ponownego mapowania do środowiska IDE.|  
|[EvalComplete, metoda](icordebugmanagedcallback-evalcomplete-method.md)|Powiadamia debuger o ukończeniu oceny.|  
|[EvalException, metoda](icordebugmanagedcallback-evalexception-method.md)|Powiadamia debuger o przerwaniu oceny z nieobsługiwanym wyjątkem.|  
|[Exception, metoda](icordebugmanagedcallback-exception-method.md)|Powiadamia debugera o wygenerowanym wyjątku z kodu zarządzanego.|  
|[ExitAppDomain, metoda](icordebugmanagedcallback-exitappdomain-method.md)|Powiadamia debuger o zakończeniu domeny aplikacji.|  
|[ExitProcess, metoda](icordebugmanagedcallback-exitprocess-method.md)|Powiadamia debugera o zakończeniu procesu.|  
|[ExitThread, metoda](icordebugmanagedcallback-exitthread-method.md)|Powiadamia debuger, że wątek wykonujący kod zarządzany został zakończony.|  
|[LoadAssembly, metoda](icordebugmanagedcallback-loadassembly-method.md)|Powiadamia debuger o pomyślnym załadowaniu zestawu CLR.|  
|[LoadClass, metoda](icordebugmanagedcallback-loadclass-method.md)|Powiadamia debuger o załadowaniu klasy.|  
|[LoadModule, metoda](icordebugmanagedcallback-loadmodule-method.md)|Powiadamia debuger o pomyślnym załadowaniu modułu CLR.|  
|[LogMessage, metoda](icordebugmanagedcallback-logmessage-method.md)|Powiadamia debuger, że wątek zarządzany przez środowisko CLR wezwał metodę w klasie <xref:System.Diagnostics.EventLog>, aby zarejestrować zdarzenie.|  
|[LogSwitch, metoda](icordebugmanagedcallback-logswitch-method.md)|Powiadamia debuger, że wątek zarządzany przez środowisko CLR wezwał metodę w klasie <xref:System.Diagnostics.Switch>, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowania/śledzenia.|  
|[NameChange, metoda](icordebugmanagedcallback-namechange-method.md)|Powiadamia debuger o zmianie nazwy domeny lub wątku aplikacji.|  
|[StepComplete, metoda](icordebugmanagedcallback-stepcomplete-method.md)|Powiadamia debuger o ukończeniu kroku.|  
|[UnloadAssembly, metoda](icordebugmanagedcallback-unloadassembly-method.md)|Powiadamia debuger o tym, że zestaw CLR został zwolniony.|  
|[UnloadClass, metoda](icordebugmanagedcallback-unloadclass-method.md)|Powiadamia debuger, że Klasa jest zwalniana.|  
|[UnloadModule, metoda](icordebugmanagedcallback-unloadmodule-method.md)|Powiadamia debuger o tym, że moduł CLR (DLL) został zwolniony.|  
|[UpdateModuleSymbols, metoda](icordebugmanagedcallback-updatemodulesymbols-method.md)|Powiadamia debuger o zmianie symboli dla modułu CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania zwrotne są serializowane, wywoływane w tym samym wątku i wywoływane z procesem w stanie zsynchronizowanym.  
  
 Każda implementacja wywołania zwrotnego musi wywołać [ICorDebugController:: Kontynuuj](icordebugcontroller-continue-method.md) , aby wznowić wykonywanie. Jeśli `ICorDebugController::Continue` nie zostanie wywołana przed zwróceniem wywołania zwrotnego, proces pozostanie zatrzymany, a kolejne wywołania zwrotne zdarzeń nie będą wykonywane do momentu wywołania `ICorDebugController::Continue`.  
  
 Debuger musi implementować [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) , jeśli debugowanie .NET Framework w wersji 2,0 aplikacji. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](icordebug-interface.md)
- [ICorDebugManagedCallback2, interfejs](icordebugmanagedcallback2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
