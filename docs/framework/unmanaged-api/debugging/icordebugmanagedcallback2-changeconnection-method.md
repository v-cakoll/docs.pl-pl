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
ms.openlocfilehash: d60644d54373dfb3d1d191900df71d3e5f6547a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788291"
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
  
- Gdy debuger dołącza do procesu, który zawiera połączenia. W takim przypadku środowisko uruchomieniowe generuje i wyśle zdarzenie [ICorDebugManagedCallback2::](icordebugmanagedcallback2-createconnection-method.md) CreateProcess oraz zdarzenie `ChangeConnection` dla każdego połączenia w procesie. Dla każdego istniejącego połączenia jest generowane zdarzenie `ChangeConnection` niezależnie od tego, czy zestaw zadań tego połączenia został zmieniony od czasu jego utworzenia.  
  
- Gdy host wywołuje [ICLRDebugManager:: SetConnectionTasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) w [interfejsie API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Debuger powinien skanować wszystkie wątki w procesie, aby pobrać nowe zmiany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2, interfejs](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
