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
ms.openlocfilehash: 96dedcd27e87c5afc504e7840100eb121410675e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130761"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback — Interfejs
Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Break, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Powiadamia debuger, gdy zostanie wykonana instrukcja <xref:System.Reflection.Emit.OpCodes.Break> w strumieniu kodu.|  
|[Breakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Powiadamia debuger w przypadku napotkania punktu przerwania.|  
|[BreakpointSetError, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Powiadamia debuger, że środowisko uruchomieniowe języka wspólnego (CLR) nie było w stanie prawidłowo powiązać punktu przerwania, który został ustawiony przed skompilowaniem funkcji just-in-Time (JIT).|  
|[ControlCTrap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Powiadamia debuger, że w debugowanym procesie jest zalewkowany skrót CTRL + C.|  
|[CreateAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Powiadamia debuger o utworzeniu domeny aplikacji.|  
|[CreateProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Powiadamia debuger, gdy proces został dołączony lub uruchomiony po raz pierwszy.|  
|[CreateThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Powiadamia debuger o rozpoczęciu wykonywania kodu zarządzanego przez wątek.|  
|[DebuggerError, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Powiadamia debuger, że wystąpił błąd podczas próby obsłużenia zdarzenia z CLR.|  
|[EditAndContinueRemap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Przestarzałe. Powiadamia debuger o wysłaniu zdarzenia ponownego mapowania do środowiska IDE.|  
|[EvalComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Powiadamia debuger o ukończeniu oceny.|  
|[EvalException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Powiadamia debuger o przerwaniu oceny z nieobsługiwanym wyjątkem.|  
|[Exception, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Powiadamia debugera o wygenerowanym wyjątku z kodu zarządzanego.|  
|[ExitAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Powiadamia debuger o zakończeniu domeny aplikacji.|  
|[ExitProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Powiadamia debugera o zakończeniu procesu.|  
|[ExitThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Powiadamia debuger, że wątek wykonujący kod zarządzany został zakończony.|  
|[LoadAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Powiadamia debuger o pomyślnym załadowaniu zestawu CLR.|  
|[LoadClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Powiadamia debuger o załadowaniu klasy.|  
|[LoadModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Powiadamia debuger o pomyślnym załadowaniu modułu CLR.|  
|[LogMessage, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Powiadamia debuger, że wątek zarządzany przez środowisko CLR wezwał metodę w klasie <xref:System.Diagnostics.EventLog>, aby zarejestrować zdarzenie.|  
|[LogSwitch, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Powiadamia debuger, że wątek zarządzany przez środowisko CLR wezwał metodę w klasie <xref:System.Diagnostics.Switch>, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowania/śledzenia.|  
|[NameChange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Powiadamia debuger o zmianie nazwy domeny lub wątku aplikacji.|  
|[StepComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Powiadamia debuger o ukończeniu kroku.|  
|[UnloadAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Powiadamia debuger o tym, że zestaw CLR został zwolniony.|  
|[UnloadClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Powiadamia debuger, że Klasa jest zwalniana.|  
|[UnloadModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Powiadamia debuger o tym, że moduł CLR (DLL) został zwolniony.|  
|[UpdateModuleSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Powiadamia debuger o zmianie symboli dla modułu CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania zwrotne są serializowane, wywoływane w tym samym wątku i wywoływane z procesem w stanie zsynchronizowanym.  
  
 Każda implementacja wywołania zwrotnego musi wywołać [ICorDebugController:: Kontynuuj](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby wznowić wykonywanie. Jeśli `ICorDebugController::Continue` nie zostanie wywołana przed zwróceniem wywołania zwrotnego, proces pozostanie zatrzymany, a kolejne wywołania zwrotne zdarzeń nie będą wykonywane do momentu wywołania `ICorDebugController::Continue`.  
  
 Debuger musi implementować [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) , jeśli debugowanie .NET Framework w wersji 2,0 aplikacji. Wystąpienie `ICorDebugManagedCallback` lub `ICorDebugManagedCallback2` jest przesyłane jako obiekt wywołania zwrotnego do [ICorDebug:: SetManagedHandler —](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
