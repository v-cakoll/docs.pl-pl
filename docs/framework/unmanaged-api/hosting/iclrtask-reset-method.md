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
ms.openlocfilehash: 15004238ee296e44ae77cd8739b7f62ea2a7a100
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762971"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset — Metoda
Informuje środowisko uruchomieniowe języka wspólnego (CLR), że host ukończył zadanie, i włącza środowisko CLR do ponownego użycia bieżącego wystąpienia [ICLRTask](iclrtask-interface.md) , aby reprezentować inne zadanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFull`  
 [in] `true` , jeśli środowisko uruchomieniowe powinno zresetować wszystkie wartości statyczne powiązane z wątkiem oprócz informacji o zabezpieczeniach i ustawieniach regionalnych związanych z bieżącym `ICLRTask` wystąpieniem; w przeciwnym razie `false` .  
  
 Jeśli wartość to `true` , środowisko uruchomieniowe resetuje dane przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Reset`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania. została|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR może odtworzyć wcześniej utworzone `ICLRTask` wystąpienia, aby uniknąć narzutu wielokrotnego tworzenia nowych wystąpień za każdym razem, gdy potrzebne jest nowe zadanie. Host włącza tę funkcję, wywołując `ICLRTask::Reset` zamiast [ICLRTask:: ExitTask —](iclrtask-exittask-method.md) , gdy ukończył zadanie. Poniższa lista podsumowuje normalny cykl życia `ICLRTask` wystąpienia:  
  
1. Środowisko uruchomieniowe tworzy nowe `ICLRTask` wystąpienie.  
  
2. Wywołania środowiska uruchomieniowego [IHostTaskManager:: GetCurrentTask —](ihosttaskmanager-getcurrenttask-method.md) w celu uzyskania odwołania do bieżącego zadania hosta.  
  
3. Wywołania środowiska uruchomieniowego [IHostTask:: SetCLRTask —](ihosttask-setclrtask-method.md) w celu skojarzenia nowego wystąpienia z zadaniem hosta.  
  
4. Zadanie jest wykonywane i uzupełniane.  
  
5. Host niszczy zadanie, wywołując metodę `ICLRTask::ExitTask` .  
  
 `Reset`zmienia ten scenariusz na dwa sposoby. W kroku 5 powyżej, Host wywołuje `Reset` w celu zresetowania zadania do stanu czystego, a następnie oddziela `ICLRTask` wystąpienie od skojarzonego z nim wystąpienia [IHostTask](ihosttask-interface.md) . Jeśli to konieczne, host może również buforować `IHostTask` wystąpienie do ponownego użycia. W kroku 1 środowisko uruchomieniowe pobierze ponownie `ICLRTask` z pamięci podręcznej, zamiast tworzyć nowe wystąpienie.  
  
 Takie podejście działa prawidłowo, gdy host ma również pulę zadań wielokrotnego użytku. Gdy host niszczy jedno z jego `IHostTask` wystąpień, niszczy odpowiednie `ICLRTask` wywołanie `ExitTask` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRTask — Interfejs](iclrtask-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
