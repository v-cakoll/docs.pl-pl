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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29267d032f5e38e352592edc50dbded68aaa9f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset — Metoda
Informuje o środowisko uruchomieniowe języka wspólnego (CLR) została ukończona zadania hosta i umożliwia CLR do ponownego użycia bieżącego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie do reprezentowania inne zadanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fFull`  
 [in] `true`, jeśli środowisko uruchomieniowe powinni resetować wszystkie wątku statyczne wartości dotyczące zabezpieczeń i ustawień regionalnych informacji powiązanych z bieżącym `ICLRTask` wystąpienia; w przeciwnym razie `false`.  
  
 Jeśli wartość jest `true`, środowisko uruchomieniowe resetuje danych, które były przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Reset` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub przetwarzania wywołania. pomyślnie|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR można odtworzyć wcześniej utworzony `ICLRTask` instancje, aby uniknąć zadań wielokrotnie tworzenia nowych wystąpień każdej próbie jej nowego zadania. Host umożliwia tej funkcji, wywołując `ICLRTask::Reset` zamiast [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po zakończeniu zadania. Poniższa lista zawiera podsumowanie normalnego cyklu życia `ICLRTask` wystąpienie:  
  
1.  Tworzy nowe środowisko uruchomieniowe `ICLRTask` wystąpienia.  
  
2.  Wywołania środowiska uruchomieniowego [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) Aby pobrać odwołanie do bieżącego zadania hosta.  
  
3.  Wywołania środowiska uruchomieniowego [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) Aby skojarzyć nowe wystąpienie z hosta zadań.  
  
4.  Zadania wykonuje i kończy działanie.  
  
5.  Host niszczy zadania, wywołując `ICLRTask::ExitTask`.  
  
 `Reset` Zmienia tego scenariusza na dwa sposoby. W kroku 5 powyżej wywołania hosta `Reset` zresetować zadania do stanu czystego, a następnie oddziela `ICLRTask` wystąpienie z jego skojarzony [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia. W razie potrzeby można buforować hosta `IHostTask` wystąpienie do ponownego użycia. W kroku 1 powyżej, środowisko uruchomieniowe ściąga odtwarzania `ICLRTask` z pamięci podręcznej, zamiast tworzyć nowe wystąpienie.  
  
 Takie podejście dobrze działa w przypadku hosta ma również pulą zadania procesu roboczego do ponownego użycia. Gdy host niszczy jednego z jego `IHostTask` wystąpień, niszczy, odpowiadającego `ICLRTask` przez wywołanie metody `ExitTask`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
