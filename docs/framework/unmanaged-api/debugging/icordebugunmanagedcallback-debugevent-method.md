---
title: "ICorDebugUnmanagedCallback::DebugEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 008ae1bd1a5774604bf2c0f196352dcf07da6ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent — Metoda
Powiadamia debugera natywnego zdarzenia uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDebugEvent`  
 [in] Wskaźnik do natywnej zdarzeń.  
  
 `fOutOfBand`  
 [in] `true`, jeżeli interakcji z stan procesu zarządzanego nie jest możliwe po wystąpieniu zdarzenia niezarządzane, dopóki wywołania debugera [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli debugowany wątek wątku Win32, nie należy używać żadnych członków środowiska Win32, debugowanie interfejsu. Możesz wywołać `ICorDebugController::Continue` tylko w wątku Win32 i tylko wtedy, gdy kontynuowanie poza zdarzenia poza pasmem.  
  
 `DebugEvent` Wywołania zwrotnego nie jest zgodna z standardowych zasad dla wywołań zwrotnych. Podczas wywoływania `DebugEvent`, proces zostanie w surowych, stanem zatrzymany debugowania systemu operacyjnego. Proces nie będą synchronizowane. Automatycznie wprowadzi zsynchronizowane stan, gdy jest to niezbędne do spełnienia żądania informacji o kodu zarządzanego, co może spowodować innych zagnieżdżonych `DebugEvent` wywołań zwrotnych.  
  
 Wywołanie [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) dla procesu, aby zignorować zdarzenie wyjątku przed kontynuowaniem procesu. Wywołanie tej metody wysyła żądanie Kontynuuj DBG_CONTINUE zamiast DBG_EXCEPTION_NOT_HANDLED i automatycznie usuwa punkty przerwania poza pasmem i wyjątków pojedynczy krok. Zdarzenia poza pasmem są dostępne w dowolnym momencie, nawet wtedy, gdy debugowanej aplikacji pojawia się zatrzymana i zaległych zdarzeń wewnątrzpasmowe już istnieje.  
  
 W programie .NET Framework w wersji 2.0 debuger powinien natychmiast kontynuować mimo zdarzenie punktu przerwania poza pasmem. Debuger powinien być używany [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) i [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody do dodawania i usuwania punktów przerwania. Te metody pomija wszystkie punkty przerwania poza pasmem automatycznie. W związku z tym punkty przerwania tylko poza pasmem, które get wysyłane powinna być pierwotnych punktów kontrolnych, które znajdują się już w strumieniu instrukcji, takie jak wywołania Win32 `DebugBreak` funkcji. Nie należy próbować użyć `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), lub wszystkich innych członków [API — debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugUnmanagedCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
