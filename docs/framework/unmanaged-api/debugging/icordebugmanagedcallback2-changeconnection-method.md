---
title: ICorDebugManagedCallback2::ChangeConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 4558074bc23334bd697461a00ccb31db3e3fe397
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130597"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection — Metoda
Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces zawierający połączenie, które uległo zmianie.  
  
 `dwConnectionId`  
 podczas Identyfikator zmienionego połączenia.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne `ChangeConnection` zostanie wyzwolone w jednej z następujących sytuacji:  
  
- Gdy debuger dołącza do procesu, który zawiera połączenia. W takim przypadku środowisko uruchomieniowe generuje i wyśle zdarzenie [ICorDebugManagedCallback2::](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) CreateProcess oraz zdarzenie `ChangeConnection` dla każdego połączenia w procesie. Dla każdego istniejącego połączenia jest generowane zdarzenie `ChangeConnection` niezależnie od tego, czy zestaw zadań tego połączenia został zmieniony od czasu jego utworzenia.  
  
- Gdy host wywołuje [ICLRDebugManager:: SetConnectionTasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) w [interfejsie API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Debuger powinien skanować wszystkie wątki w procesie, aby pobrać nowe zmiany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
