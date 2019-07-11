---
title: ICorDebugRemote::DebugActiveProcessEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13371d15c8b29f9ef93cc4af87acf85029404644
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744770"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx — Metoda
Uruchamia proces na komputerze zdalnym w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [in] Wskaźnik do [icordebugremotetarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Ten parametr jest używany do określenia komputera, na którym jest uruchomiony proces.  
  
 `id`  
 [in] Identyfikator procesu, do którego ma zostać dołączony debuger.  
  
 `win32Attach`  
 [in] `true` Jeśli debuger powinien zachowywać się jak debugera Win32 dla procesu i wysyłania niezarządzanych wywołań zwrotnych; w przeciwnym razie `false`.  
  
 `ppProcess`  
 [out] Wskaźnik na adres obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie dołączono do procesu na komputerze zdalnym.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można dołączyć do procesu na komputerze zdalnym.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
