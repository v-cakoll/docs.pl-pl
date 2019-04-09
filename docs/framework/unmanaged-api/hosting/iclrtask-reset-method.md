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
ms.openlocfilehash: 3889e48019f30f93a9eaa677de26445dbcc33d80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198806"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset — Metoda
Informuje środowisko uruchomieniowe języka wspólnego (CLR), hosta zostało zakończone zadania i umożliwia CLR do ponownego użycia bieżącego [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia do reprezentowania inne zadanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFull`  
 [in] `true`, jeśli środowisko wykonawcze zresetować wszystkie wątku statyczne wartościom oprócz zabezpieczeń i ustawień regionalnych informacji powiązanych z bieżącym `ICLRTask` wystąpienia; w przeciwnym razie `false`.  
  
 Jeśli wartość jest `true`, środowisko uruchomieniowe przywraca dane, które są przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Reset` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetwarzania wywołania. pomyślnie|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR można odzyskać utworzone wcześniej `ICLRTask` wystąpienia, aby uniknąć zadań wielokrotnie tworzenia nowych wystąpień za każdym razem, gdy potrzebuje zadanie od nowa. Host oferuje tę funkcję, wywołując `ICLRTask::Reset` zamiast [iclrtask::exittask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po zakończeniu zadania. Poniższa lista zawiera podsumowanie cyklu życia normalne `ICLRTask` wystąpienie:  
  
1.  Środowisko uruchomieniowe tworzy nową `ICLRTask` wystąpienia.  
  
2.  Środowisko uruchomieniowe wywołuje [ihosttaskmanager::getcurrenttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) można pobrać odwołania do bieżącego zadania hosta.  
  
3.  Środowisko uruchomieniowe wywołuje [ihosttask::setclrtask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) Aby skojarzyć nowe wystąpienie z zadaniem hosta.  
  
4.  Zadanie wykonuje i kończy.  
  
5.  Host niszczy zadania, wywołując `ICLRTask::ExitTask`.  
  
 `Reset` Zmienia tego scenariusza na dwa sposoby. W kroku 5 powyżej wywołania hosta `Reset` zresetować zadania do stanu czystego i następnie oddziela `ICLRTask` wystąpienia związanych z nią [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia. Jeśli to konieczne, można buforować hosta `IHostTask` wystąpienia do ponownego wykorzystania. W kroku 1 powyżej, środowisko uruchomieniowe ściąga odtwarzania `ICLRTask` z pamięci podręcznej, zamiast tworzenia nowego wystąpienia.  
  
 To podejście działa dobrze w przypadku, gdy host ma też puli zadania procesu roboczego wielokrotnego użytku. Gdy host niszczy, jeden z jego `IHostTask` wystąpień niszczy, odpowiedni `ICLRTask` przez wywołanie metody `ExitTask`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
