---
title: ICorDebugUnmanagedCallback::DebugEvent — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: 24c316ea6bab11fb55e8e0fc1dc9832a312dbc6a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397196"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent — Metoda
Powiadamia debuger, że zdarzenie natywne zostało wyzwolone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDebugEvent`  
 podczas Wskaźnik do zdarzenia natywnego.  
  
 `fOutOfBand`  
 [w] `true` , jeśli interakcja z zarządzanym stanem procesu jest niemożliwa po wystąpieniu zdarzenia niezarządzanego, do momentu, gdy debuger wywoła [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); w przeciwnym razie, `false` .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli debugowany wątek jest wątkiem Win32, nie należy używać żadnych elementów członkowskich interfejsu debugowania Win32. Można wywołać `ICorDebugController::Continue` tylko na wątku Win32 i tylko w przypadku kontynuowania ostatniego zdarzenia poza pasmem.  
  
 `DebugEvent`Wywołanie zwrotne nie jest zgodne ze standardowymi regułami wywołania zwrotnego. Po wywołaniu `DebugEvent` , proces będzie znajdował się w stanie zatrzymania w trybie nieprzetworzonym systemu operacyjnego. Proces nie zostanie zsynchronizowany. Stan zsynchronizowany zostanie automatycznie wprowadzony, gdy będzie to konieczne w celu spełnienia żądań informacji o zarządzanym kodzie, co może spowodować inne zagnieżdżone `DebugEvent` wywołania zwrotne.  
  
 Wywołaj [ICorDebugProcess:: ClearCurrentException —](icordebugprocess-clearcurrentexception-method.md) w procesie, aby zignorować zdarzenie wyjątku przed kontynuowaniem procesu. Wywołanie tej metody powoduje wysłanie DBG_CONTINUE, a nie DBG_EXCEPTION_NOT_HANDLED na żądanie kontynuowania, i automatycznie czyści punkty przerwania poza pasmem oraz wyjątki jednoetapowe. Zdarzenia poza pasmem mogą znajdować się w dowolnym momencie, nawet gdy debugowana aplikacja zostanie zatrzymana i gdy zaległe zdarzenie w paśmie już istnieje.  
  
 W .NET Framework w wersji 2,0 debuger powinien natychmiast kontynuować poprzednie zdarzenie punktu przerwania poza pasmem. Debuger powinien używać metod [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md) i [ICorDebugProcess2:: ClearUnmanagedBreakpoint —](icordebugprocess2-clearunmanagedbreakpoint-method.md) , aby dodawać i usuwać punkty przerwania. Te metody spowodują automatyczne pomijanie wszystkich punktów przerwania poza pasmem. W związku z tym tylko punkty przerwania poza pasmem, które są wysyłane, powinny być nieprzetworzonymi punktami przerwań, które znajdują się już w strumieniu instrukcji, takich jak wywołanie `DebugBreak` funkcji Win32. Nie należy próbować używać `ICorDebugProcess::ClearCurrentException` , [ICorDebugProcess:: GetThreadContext —](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext —](icordebugprocess-setthreadcontext-method.md)ani żadnych innych elementów członkowskich [debugowania API](index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugUnmanagedCallback — Interfejs](icordebugunmanagedcallback-interface.md)
