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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501927"
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
 `CreateConnection`Wywołanie zwrotne zostanie wyzwolone w jednej z następujących sytuacji:  
  
- Gdy debuger dołącza do procesu, który zawiera połączenia. W takim przypadku środowisko uruchomieniowe generuje i wyśle `CreateConnection` zdarzenie oraz [ICorDebugManagedCallback2:: ChangeConnection —](icordebugmanagedcallback2-changeconnection-method.md) dla każdego połączenia w procesie.  
  
- Gdy host wywołuje [ICLRDebugManager:: BeginConnection —](../hosting/iclrdebugmanager-beginconnection-method.md) w [interfejsie API hostingu](../hosting/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2 — Interfejs](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback — Interfejs](icordebugmanagedcallback-interface.md)
