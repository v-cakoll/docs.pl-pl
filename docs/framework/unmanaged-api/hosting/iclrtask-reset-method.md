---
title: ICLRTask::Reset — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124644"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset — Metoda
Informuje środowisko uruchomieniowe języka wspólnego (CLR), że host ukończył zadanie, i włącza środowisko CLR do ponownego użycia bieżącego wystąpienia [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) , aby reprezentować inne zadanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFull`  
 [in] `true`, jeśli środowisko uruchomieniowe powinno zresetować wszystkie wartości statyczne powiązane z wątkiem oprócz informacji o zabezpieczeniach i ustawieniach regionalnych związanych z bieżącym wystąpieniem `ICLRTask`; w przeciwnym razie `false`.  
  
 Jeśli wartość jest `true`, środowisko uruchomieniowe resetuje dane przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Reset` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania. została|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR może odtworzyć wcześniej utworzone wystąpienia `ICLRTask`, aby uniknąć narzutu wielokrotnego tworzenia nowych wystąpień za każdym razem, gdy potrzebne jest nowe zadanie. Host włącza tę funkcję, wywołując `ICLRTask::Reset` zamiast [ICLRTask:: ExitTask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po ukończeniu zadania. Poniższa lista podsumowuje normalny cykl życia wystąpienia `ICLRTask`:  
  
1. Środowisko uruchomieniowe tworzy nowe wystąpienie `ICLRTask`.  
  
2. Wywołania środowiska uruchomieniowego [IHostTaskManager:: GetCurrentTask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) w celu uzyskania odwołania do bieżącego zadania hosta.  
  
3. Wywołania środowiska uruchomieniowego [IHostTask:: SetCLRTask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) w celu skojarzenia nowego wystąpienia z zadaniem hosta.  
  
4. Zadanie jest wykonywane i uzupełniane.  
  
5. Host niszczy zadanie, wywołując `ICLRTask::ExitTask`.  
  
 `Reset` zmienić ten scenariusz na dwa sposoby. W kroku 5 powyżej, Host wywołuje `Reset` Resetowanie zadania do stanu czystego, a następnie oddziela wystąpienie `ICLRTask` od skojarzonego z nim wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) . W razie potrzeby host może również buforować wystąpienie `IHostTask` w celu ponownego użycia. W kroku 1 środowisko uruchomieniowe pobiera `ICLRTask` odtwarzania z pamięci podręcznej, zamiast tworzyć nowe wystąpienie.  
  
 Takie podejście działa prawidłowo, gdy host ma również pulę zadań wielokrotnego użytku. Gdy host niszczy jeden z jego `IHostTask` wystąpień, niszczy odpowiednie `ICLRTask` przez wywołanie `ExitTask`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
