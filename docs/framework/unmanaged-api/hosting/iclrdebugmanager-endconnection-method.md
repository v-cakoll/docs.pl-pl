---
title: ICLRDebugManager::EndConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 425f40da7a53aa4af1bd14964a8136add2f59f0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135215"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection — Metoda
Usuwa skojarzenie między listą zadań i identyfikatorem i przyjazną nazwą.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 podczas Identyfikator specyficzny dla hosta i skojarzona lista zadań środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`EndConnection` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[BeginConnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nigdy nie został wywołany przy użyciu `dwConnectionId`lub `dwConnectionId` była równa zero.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody, `BeginConnection`, [SetConnectionTasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)i `EndConnection`, do kojarzenia list zadań z identyfikatorami i przyjaznymi nazwami.  
  
> [!IMPORTANT]
> Te trzy metody muszą być wywoływane w określonej kolejności dla każdego zestawu zadań. `BeginConnection` jest wywoływana najpierw w celu nawiązania nowego połączenia. `SetConnectionTasks` jest wywoływana dalej, aby określić zestaw zadań, które mają być skojarzone z tym połączeniem. `EndConnection` jest wywoływana jako Ostatnia, aby usunąć skojarzenie między listą zadań a identyfikatorem i przyjazną nazwą. Jednak wywołania dla różnych połączeń mogą być zagnieżdżane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [SetConnectionTasks, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
