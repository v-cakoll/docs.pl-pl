---
title: "ICorDebugManagedCallback2::ChangeConnection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ChangeConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c62859cb6a3e61af9670834db169410cecb6787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection — Metoda
Powiadamia debuger zmiana zestawu zadań powiązanych z określonego połączenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces zawierający połączenie, które zmienione.  
  
 `dwConnectionId`  
 [in] Identyfikator połączenia, które zmienione.  
  
## <a name="remarks"></a>Uwagi  
 A `ChangeConnection` wywołania zwrotnego zostanie wyzwolone w następujących przypadkach:  
  
-   Gdy debuger dołącza do procesu, który zawiera połączenia. W takim przypadku wygenerowania i wysyłania środowiska uruchomieniowego [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) zdarzeń i `ChangeConnection` zdarzeń dla każdego połączenia w procesie. A `ChangeConnection` zdarzenie jest generowane dla każdego istniejącego połączenia, niezależnie od tego, czy to połączenie zestawu zadań został zmieniony od czasu jego utworzenia.  
  
-   Gdy host wywołuje [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) w [hostingu API](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Debuger powinien skanować wszystkie wątki tego procesu w celu odebrania nowych zmian.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugManagedCallback2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
