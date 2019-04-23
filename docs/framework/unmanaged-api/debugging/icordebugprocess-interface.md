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
ms.openlocfilehash: 46d96d66f16cd956d8fab1afe00486d564e37953
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216798"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess, interfejs
Reprezentuje proces, który wykonuje kod zarządzany. Ten interfejs jest podklasą icordebugcontroller —.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Czyści niezarządzane bieżącego wyjątku dla danego wątku.|  
|[EnableLogMessages, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Włącza i wyłącza wysyłanie komunikatów dziennika do debugera.|  
|[EnumerateAppDomains, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Wylicza wszystkie domeny aplikacji w procesie.|  
|[EnumerateObjects, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Nie zaimplementowano.|  
|[GetHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Pobiera uchwyt do procesu.|  
|[GetHelperThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego (OS) dla debugera wewnętrzny wątek pomocniczy.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Pobiera identyfikator systemu operacyjnego (OS) procesu.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Nie zaimplementowano.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Pobiera identyfikator wystąpienia ICorDebugThread, który ma określony wątek systemu operacyjnego.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Pobiera kontekst dla danego wątku.|  
|[IsOSSuspended, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Określa, czy wątek została zawieszona wyniku debugera zatrzymywania procesu.|  
|[IsTransitionStub, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Określa, czy adres znajduje się wewnątrz odcinek, który spowoduje przejście do kodu zarządzanego.|  
|[ModifyLogSwitch, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Ustawia poziom ważności przełącznika określonego dziennika.|  
|[ReadMemory, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Odczytuje pamięć procesu.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Ustawia kontekst dla danego wątku.|  
|[ThreadForFiberCookie, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Przestarzałe.|  
|[WriteMemory, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapisuje dane do obszar pamięci w procesie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
