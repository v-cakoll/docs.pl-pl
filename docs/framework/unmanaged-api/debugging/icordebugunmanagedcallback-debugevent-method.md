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
ms.openlocfilehash: 2d865f837d38894e8449af671e2d12e7676dd040
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129136"
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
 [in] `true`, jeśli interakcja z zarządzanym stanem procesu jest niemożliwa po wystąpieniu zdarzenia niezarządzanego, dopóki debuger wywoła [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli debugowany wątek jest wątkiem Win32, nie należy używać żadnych elementów członkowskich interfejsu debugowania Win32. Można wywołać `ICorDebugController::Continue` tylko w wątku Win32 i tylko w przypadku kontynuowania poza pasmem.  
  
 Wywołania zwrotne `DebugEvent` nie są zgodne ze standardowymi regułami wywołania zwrotnego. Gdy wywołasz `DebugEvent`, proces będzie znajdował się w stanie zatrzymania w trybie nieprzetworzonym systemu operacyjnego. Proces nie zostanie zsynchronizowany. Stan zsynchronizowany zostanie automatycznie wprowadzony, gdy będzie to konieczne w celu spełnienia żądań informacji o kodzie zarządzanym, co może spowodować inne zagnieżdżone `DebugEvent` wywołania zwrotne.  
  
 Wywołaj [ICorDebugProcess:: ClearCurrentException —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) w procesie, aby zignorować zdarzenie wyjątku przed kontynuowaniem procesu. Wywołanie tej metody powoduje wysłanie DBG_CONTINUE zamiast DBG_EXCEPTION_NOT_HANDLED w żądaniu kontynuacji, a automatycznie czyści punkty przerwania poza pasmem i wyjątki jednoetapowe. Zdarzenia poza pasmem mogą znajdować się w dowolnym momencie, nawet gdy debugowana aplikacja zostanie zatrzymana i gdy zaległe zdarzenie w paśmie już istnieje.  
  
 W .NET Framework w wersji 2,0 debuger powinien natychmiast kontynuować poprzednie zdarzenie punktu przerwania poza pasmem. Debuger powinien używać metod [ICorDebugProcess2:: SetUnmanagedBreakpoint —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) i [ICorDebugProcess2:: ClearUnmanagedBreakpoint —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) , aby dodawać i usuwać punkty przerwania. Te metody spowodują automatyczne pomijanie wszystkich punktów przerwania poza pasmem. W związku z tym tylko punkty przerwania poza pasmem, które są wysyłane, powinny być nieprzetworzonymi punktami przerwania, które znajdują się już w strumieniu instrukcji, takich jak wywołanie funkcji Win32 `DebugBreak`. Nie należy próbować używać `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)ani żadnych innych elementów członkowskich [debugowania API](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugUnmanagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
