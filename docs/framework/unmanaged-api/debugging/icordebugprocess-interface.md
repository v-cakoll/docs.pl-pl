---
title: ICorDebugProcess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee526a79d89a9e4e3483daa07a512b6b7f920e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
Reprezentuje proces, który wykonuje kod zarządzany. Ten interfejs jest podklasą klasy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Czyści niezarządzane bieżącego wyjątku dla danego wątku.|  
|[EnableLogMessages — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.|  
|[EnumerateAppDomains — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Wylicza wszystkie domeny aplikacji w procesie.|  
|[EnumerateObjects — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Nie jest zaimplementowana.|  
|[GetHandle — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Pobiera dojścia do procesu.|  
|[GetHelperThreadID — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego (OS) dla debugera wewnętrzny wątek pomocniczy.|  
|[GetID — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Pobiera identyfikator systemu operacyjnego (OS) procesu.|  
|[GetObject — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Nie jest zaimplementowana.|  
|[GetThread — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Pobiera nazwę wystąpienia ICorDebugThread z określonego wątku systemu operacyjnego.|  
|[GetThreadContext — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Pobiera kontekst dla danego wątku.|  
|[IsOSSuspended — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Określa, czy wątek został wstrzymany wyniku debugera zatrzymywania procesu.|  
|[IsTransitionStub — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Określa, czy adres jest wewnątrz skrótowa, która spowoduje przejście do kodu zarządzanego.|  
|[ModifyLogSwitch — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Ustawia poziom ważności określony dziennik przełącznika.|  
|[ReadMemory — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Odczytuje pamięci w procesie.|  
|[SetThreadContext — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Ustawia kontekst dla danego wątku.|  
|[ThreadForFiberCookie — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Przestarzałe.|  
|[WriteMemory — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapisuje dane do to obszar pamięci w procesie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
