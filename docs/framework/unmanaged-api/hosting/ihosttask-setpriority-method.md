---
title: IHostTask::SetPriority — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 533e3d715b46b4ef6d473795a010fa3ad297ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913751"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority — Metoda
Żądania, dla których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `newPriority`  
 podczas Liczba całkowita reprezentująca żądaną wartość priorytetu wątku dla zadania reprezentowanego przez bieżące `IHostTask` wystąpienie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetPriority`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wątki otrzymują czas przetwarzania przy użyciu systemu działania okrężnego, który jest częściowo oparty na poziomie priorytetu wątku. `SetPriority`umożliwia środowisku CLR Ustawianie tego poziomu priorytetu wątku dla bieżącego zadania. Obsługiwane są `newPriority` następujące wartości.  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 Środowisko CLR wywołuje `SetPriority` , gdy wartość <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> elementu jest modyfikowana przez kod użytkownika. Host może definiować własne algorytmy do przypisywania priorytetów wątków i jest bezpłatny do ignorowania tego żądania.  
  
> [!NOTE]
> `SetPriority`nie zgłasza tego, czy poziom priorytetu wątku został zmieniony. Wywołaj [IHostTask:: GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) , aby określić wartość poziomu priorytetu wątku zadania.  
  
 Wartości poziomu priorytetu wątku są definiowane przez funkcję `SetThreadPriority` Win32. Więcej informacji o priorytecie wątku znajduje się w dokumentacji platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MSCorEE. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [GetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
