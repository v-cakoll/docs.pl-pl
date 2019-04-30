---
title: ICLRDebugManager::SetConnectionTasks — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700270"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks — Metoda
Kojarzy listę [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpień przy użyciu identyfikatora i przyjazną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator określonego hosta do nawiązania połączenia, z którą chcesz skojarzyć `ppCLRTask` tablicy.  
  
 `dwCount`  
 [in] Liczba elementów członkowskich `ppCLRTask`. Ta liczba musi być większa od zera.  
  
 `ppCLRTask`  
 [in] Tablica `ICLRTask` wskaźników do skojarzenia z tym połączeniem identyfikowane przez `id`. Tablica musi zawierać co najmniej jednego członka.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[Beginconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nie została wywołana przy użyciu tej wartości `id`, lub `dwCount` lub `id` wynosi zero lub jeden z elementów `ppCLRTask` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, `SetConnectionTasks`, i [endconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.  
  
> [!IMPORTANT]
>  Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań. `BeginConnection` nosi nazwę najpierw nawiązać nowe połączenie. `SetConnectionTasks` wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia. `EndConnection` wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [EndConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
