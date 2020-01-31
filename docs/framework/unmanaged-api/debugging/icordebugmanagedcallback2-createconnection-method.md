---
title: ICorDebugManagedCallback2::CreateConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: e98748b523b948dc002f2ebc4e2e79fc7d659918
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781593"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection — Metoda
Powiadamia debuger o utworzeniu nowego połączenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym utworzono połączenie  
  
 `dwConnectionId`  
 podczas Identyfikator nowego połączenia.  
  
 `pConnName`  
 podczas Wskaźnik do nazwy nowego połączenia.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne `CreateConnection` zostanie wyzwolone w jednej z następujących sytuacji:  
  
- Gdy debuger dołącza do procesu, który zawiera połączenia. W takim przypadku środowisko uruchomieniowe generuje i wyśle zdarzenie `CreateConnection` i [ICorDebugManagedCallback2:: ChangeConnection —](icordebugmanagedcallback2-changeconnection-method.md) dla każdego połączenia w procesie.  
  
- Gdy host wywołuje [ICLRDebugManager:: BeginConnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) w [interfejsie API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2, interfejs](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
