---
title: ICorDebugProcess, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: ab48efccc88787f099a182627777db95304cdc3e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212077"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess, interfejs
Reprezentuje proces, który wykonuje kod zarządzany. Ten interfejs jest podklasą elementu ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](icordebugprocess-clearcurrentexception-method.md)|Czyści bieżący wyjątek niezarządzany w danym wątku.|  
|[EnableLogMessages, metoda](icordebugprocess-enablelogmessages-method.md)|Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.|  
|[EnumerateAppDomains, metoda](icordebugprocess-enumerateappdomains-method.md)|Wylicza wszystkie domeny aplikacji w procesie.|  
|[EnumerateObjects, metoda](icordebugprocess-enumerateobjects-method.md)|Nie zaimplementowano.|  
|[GetHandle, metoda](icordebugprocess-gethandle-method.md)|Pobiera dojście do procesu.|  
|[GetHelperThreadID, metoda](icordebugprocess-gethelperthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego dla wewnętrznego wątku pomocnika debugera.|  
|[GetID, metoda](icordebugprocess-getid-method.md)|Pobiera identyfikator systemu operacyjnego (OS) procesu.|  
|[GetObject — Metoda](icordebugprocess-getobject-method.md)|Nie zaimplementowano.|  
|[GetThread, metoda](icordebugprocess-getthread-method.md)|Pobiera wystąpienie ICorDebugThread o określonym IDENTYFIKATORze wątku systemu operacyjnego.|  
|[GetThreadContext — Metoda](icordebugprocess-getthreadcontext-method.md)|Pobiera kontekst dla danego wątku.|  
|[IsOSSuspended, metoda](icordebugprocess-isossuspended-method.md)|Określa, czy wątek został wstrzymany w wyniku debugera zatrzymywania procesu.|  
|[IsTransitionStub, metoda](icordebugprocess-istransitionstub-method.md)|Określa, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.|  
|[ModifyLogSwitch, metoda](icordebugprocess-modifylogswitch-method.md)|Ustawia poziom ważności określonego przełącznika dziennika.|  
|[ReadMemory, metoda](icordebugprocess-readmemory-method.md)|Odczytuje pamięć z procesu.|  
|[SetThreadContext, metoda](icordebugprocess-setthreadcontext-method.md)|Ustawia kontekst dla danego wątku.|  
|[ThreadForFiberCookie, metoda](icordebugprocess-threadforfibercookie-method.md)|Przestarzałe.|  
|[WriteMemory, metoda](icordebugprocess-writememory-method.md)|Zapisuje dane w obszarze pamięci w procesie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebug — Interfejs](icordebug-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
