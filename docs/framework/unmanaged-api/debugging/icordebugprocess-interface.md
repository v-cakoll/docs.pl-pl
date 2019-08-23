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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943304"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess, interfejs
Reprezentuje proces, który wykonuje kod zarządzany. Ten interfejs jest podklasą elementu ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Czyści bieżący wyjątek niezarządzany w danym wątku.|  
|[EnableLogMessages, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.|  
|[EnumerateAppDomains, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Wylicza wszystkie domeny aplikacji w procesie.|  
|[EnumerateObjects, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Nie zaimplementowane.|  
|[GetHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Pobiera dojście do procesu.|  
|[GetHelperThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego dla wewnętrznego wątku pomocnika debugera.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Pobiera identyfikator systemu operacyjnego (OS) procesu.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Nie zaimplementowane.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Pobiera wystąpienie ICorDebugThread o określonym IDENTYFIKATORze wątku systemu operacyjnego.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Pobiera kontekst dla danego wątku.|  
|[IsOSSuspended, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Określa, czy wątek został wstrzymany w wyniku debugera zatrzymywania procesu.|  
|[IsTransitionStub, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Określa, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.|  
|[ModifyLogSwitch, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Ustawia poziom ważności określonego przełącznika dziennika.|  
|[ReadMemory, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Odczytuje pamięć z procesu.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Ustawia kontekst dla danego wątku.|  
|[ThreadForFiberCookie, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Przestarzałe.|  
|[WriteMemory, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapisuje dane w obszarze pamięci w procesie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
