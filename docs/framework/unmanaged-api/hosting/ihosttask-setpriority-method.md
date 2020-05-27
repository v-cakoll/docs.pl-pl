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
ms.openlocfilehash: ac3a8479cdf05e55885bd55d4e4fb8e6e47686f9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842403"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority — Metoda
Żądania, dla których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie [IHostTask](ihosttask-interface.md) .  
  
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
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wątki otrzymują czas przetwarzania przy użyciu systemu działania okrężnego, który jest częściowo oparty na poziomie priorytetu wątku. `SetPriority`umożliwia środowisku CLR Ustawianie tego poziomu priorytetu wątku dla bieżącego zadania. `newPriority`Obsługiwane są następujące wartości.  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 Środowisko CLR wywołuje, `SetPriority` gdy wartość elementu <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> jest modyfikowana przez kod użytkownika. Host może definiować własne algorytmy do przypisywania priorytetów wątków i jest bezpłatny do ignorowania tego żądania.  
  
> [!NOTE]
> `SetPriority`nie zgłasza tego, czy poziom priorytetu wątku został zmieniony. Wywołaj [IHostTask:: GetPriority](ihosttask-getpriority-method.md) , aby określić wartość poziomu priorytetu wątku zadania.  
  
 Wartości poziomu priorytetu wątku są definiowane przez `SetThreadPriority` funkcję Win32. Więcej informacji o priorytecie wątku znajduje się w dokumentacji platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- [ICLRTask — Interfejs](iclrtask-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [GetPriority, metoda](ihosttask-getpriority-method.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
