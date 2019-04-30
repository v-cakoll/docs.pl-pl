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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748958"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent — Metoda
Powiadamia debuger natywny zdarzenia uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDebugEvent`  
 [in] Wskaźnik do macierzystych zdarzeń.  
  
 `fOutOfBand`  
 [in] `true`, jeżeli interakcji ze stanem procesu zarządzanego nie jest możliwe po wystąpieniu zdarzenia niezarządzane, aż do wywołań debugera [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli debugowany wątek znajduje się wątek Win32, nie należy używać wszystkie elementy członkowskie Win32 debugowanie interfejsu. Możesz wywołać `ICorDebugController::Continue` tylko wątek Win32 i tylko wtedy, gdy kontynuowanie ostatnie zdarzenie poza pasmem.  
  
 `DebugEvent` Wywołania zwrotnego nie jest zgodna z standardowe reguły dla wywołań zwrotnych. Gdy wywołujesz `DebugEvent`, proces będzie znajdować się w surowych, stanem zatrzymany debugowania systemu operacyjnego. Ten proces nie będą synchronizowane. Automatycznie przejdzie zsynchronizowane stan, gdy jest to niezbędne do spełnienia żądania informacji o kodu zarządzanego, co może spowodować innych zagnieżdżonych `DebugEvent` wywołań zwrotnych.  
  
 Wywołaj [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) na temat procesu do ignorowania zdarzenie wyjątku, przed kontynuowaniem procesu. Wywołanie tej metody wysyła żądania continue DBG_CONTINUE zamiast DBG_EXCEPTION_NOT_HANDLED i automatycznie usuwa out-of-band punktów przerwania i wyjątków w jednym kroku. Out-of-band zdarzenia mogą pochodzić w dowolnym momencie, nawet wtedy, gdy debugowanej aplikacji zostanie wyświetlony zatrzymania i zaległych zdarzeń wewnątrzpasmowe już istnieje.  
  
 W .NET Framework w wersji 2.0 debuger powinien natychmiast kontynuować ostatnie zdarzenie punktu przerwania out-of-band. Debuger powinien używać [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) i [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody dodawania i usuwania punktów przerwania. Te metody pomija wszelkie punkty przerwania, out-of-band automatycznie. W związku z tym, punktów przerwania tylko poza pasmem, które Pobierz wysyłane powinny być pierwotne punktów przerwania, które znajdują się już w usłudze stream instrukcji, takie jak wywołanie Win32 `DebugBreak` funkcji. Nie należy próbować użyć `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), lub dowolnym innym [pomocy API debugowania](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugUnmanagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
