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
ms.openlocfilehash: 7079a915c0402df62afa5648317619af82c943b0
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841987"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask — Metoda
Żąda utworzenia nowego zadania przez hosta.  
  
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
 podczas Żądany rozmiar (w bajtach) żądanego stosu lub 0 (zero) dla rozmiaru domyślnego.  
  
 `pStartAddress`  
 podczas Wskaźnik do funkcji, która ma zostać wykonana.  
  
 `pParameter`  
 podczas Wskaźnik do danych użytkownika, który ma zostać przesłany do funkcji, lub wartość null, jeśli funkcja nie przyjmuje żadnych parametrów.  
  
 `ppTask`  
 określoną Wskaźnik do adresu wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) utworzonego przez hosta lub wartość null, jeśli nie można utworzyć zadania. Zadanie pozostaje w stanie wstrzymania, dopóki nie zostanie jawnie uruchomione przez wywołanie [IHostTask:: Start](ihosttask-start-method.md).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateTask`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci, aby utworzyć żądane zadanie.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje `CreateTask` żądanie utworzenia nowego zadania przez hosta. Host zwraca wskaźnik interfejsu do `IHostTask` wystąpienia. Zwrócone zadanie musi pozostać zawieszone, dopóki nie zostanie jawnie uruchomione przez wywołanie `IHostTask::Start` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](iclrtask-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
