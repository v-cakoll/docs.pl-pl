---
title: ICLRTask::SwitchIn — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f408dd5e4d383040d9e3c03cd5bba8ebd320610f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938369"
---
# <a name="iclrtaskswitchin-method"></a>ICLRTask::SwitchIn — Metoda
Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o tym, że zadanie, które reprezentuje bieżące wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) , jest teraz w stanie nieobsługiwanym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadHandle`  
 podczas Dojście do wątku fizycznego, w którym wykonywane jest zadanie reprezentowane przez bieżące `ICLRTask` wystąpienie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SwitchIn`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`SwitchIn`został wywołany bez wcześniejszego wywołania [metody SwitchOut —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).|  
  
## <a name="remarks"></a>Uwagi  
 Parametr reprezentuje dojście do wątku systemu operacyjnego, w którym zaplanowano zadanie reprezentowane przez bieżące `ICLRTask` wystąpienie. `threadHandle` W przypadku wystąpienia personifikacji w tym wątku należy wywołać metodę [IHostSecurityManager:: RevertToSelf —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) przed przełączeniem w zadaniu.  
  
> [!NOTE]
> Wywołanie `SwitchIn` bez wcześniejszego wywołania do `SwitchOut` nie powiodło się z wartością HRESULT równą HOST_E_INVALIDOPERATION.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MSCorEE. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
