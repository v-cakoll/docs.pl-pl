---
title: IHostTaskManager::CreateTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178001"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask — Metoda
Żąda, aby host utworzył nowe zadanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `stacksize`  
 [w] Żądany rozmiar w bajtach żądanego stosu lub 0 (zero) dla rozmiaru domyślnego.  
  
 `pStartAddress`  
 [w] Wskaźnik do funkcji, której zadanie ma wykonać.  
  
 `pParameter`  
 [w] Wskaźnik do danych użytkownika, które mają być przekazywane do funkcji lub null, jeśli funkcja nie przyjmuje żadnych parametrów.  
  
 `ppTask`  
 [na zewnątrz] Wskaźnik do adresu wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) utworzonego przez hosta lub null, jeśli nie można utworzyć zadania. Zadanie pozostaje w stanie wstrzymanym, dopóki nie zostanie jawnie rozpoczęte przez wywołanie [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateTask`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_outofmemory|Za mało pamięci było dostępne do utworzenia żądanego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 Clr wywołuje `CreateTask` żądanie, aby host utworzyć nowe zadanie. Host zwraca wskaźnik interfejsu `IHostTask` do wystąpienia. Zwrócone zadanie musi pozostać zawieszone, dopóki nie `IHostTask::Start`zostanie jawnie rozpoczęte przez wywołanie .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
