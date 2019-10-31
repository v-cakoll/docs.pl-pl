---
title: ICLRTask — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: c4f27a73022b0495b2772c0485c14a1b007dc883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132647"
---
# <a name="iclrtask-interface"></a>ICLRTask — Interfejs
Dostarcza metody, które umożliwiają hostowi wykonywanie żądań środowiska uruchomieniowego języka wspólnego (CLR) lub dostarczenie do środowiska CLR powiadomienia o skojarzonym zadaniu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Żąda, aby środowisko CLR przerywał zadanie, które reprezentuje bieżące wystąpienie `ICLRTask`.|  
|[ExitTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Powiadamia środowisko CLR o zakończeniu zadania skojarzonego z bieżącym wystąpieniem `ICLRTask` i próbuje bezproblemowo zamknąć zadanie.|  
|[GetMemStats, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Pobiera informacje statystyczne dotyczące korzystania z zasobów pamięci przez zadanie reprezentowane przez bieżące wystąpienie `ICLRTask`.|  
|[LocksHeld, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Pobiera liczbę blokad aktualnie przechowywanych w zadaniu.|  
|[NeedsPriorityScheduling, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Pobiera wartość wskazującą, czy host powinien przypisać wysoki priorytet, aby ponownie zaplanować zadanie reprezentowane przez bieżące wystąpienie `ICLRTask`.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informuje środowisko CLR, że host ukończył zadanie, i włącza środowisko CLR do ponownego użycia bieżącego wystąpienia `ICLRTask`, aby reprezentować inne zadanie.|  
|[RudeAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Powoduje natychmiastowe przerwanie przez środowisko CLR zadania reprezentowanego przez bieżące wystąpienie `ICLRTask` bez gwarancji, że finalizatory zostaną wykonane.|  
|[SetTaskIdentifier, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Ustawia unikatowy identyfikator zadania reprezentowanego przez bieżące wystąpienie `ICLRTask`, do użycia podczas debugowania.|  
|[SwitchIn, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Powiadamia środowisko CLR o tym, że zadanie reprezentowane przez bieżące wystąpienie `ICLRTask` jest w stanie nieobsługiwanym.|  
|[SwitchOut, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Powiadamia CLR, że zadanie reprezentowane przez bieżące wystąpienie `ICLRTask` nie jest już w stanie obsługiwanym.|  
|[YieldTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Żąda, aby środowisko CLR udostępnić czas procesora innym zadanie. Środowisko CLR nie gwarantuje, że zadanie zostanie umieszczone w stanie, w którym może dać czas przetwarzania.|  
  
## <a name="remarks"></a>Uwagi  
 `ICLRTask` jest reprezentacją zadania dla środowiska CLR. W dowolnym momencie wykonywania kodu zadanie można opisać jako uruchomione lub oczekiwanie na uruchomienie. Host wywołuje metodę `ICLRTask::SwitchIn` w celu powiadomienia środowiska CLR o tym, że zadanie, które jest reprezentowane przez bieżące wystąpienie `ICLRTask`, jest teraz w stanie nieobsługiwanym. Po wywołaniu `ICLRTask::SwitchIn`host może zaplanować zadanie w dowolnym wątku systemu operacyjnego, z wyjątkiem przypadków, gdy środowisko uruchomieniowe wymaga koligacji wątków, jak określono przez wywołania do [IHostTaskManager:: BeginThreadAffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) i [IHostTaskManager:: Metody EndThreadAffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) . Czasami system operacyjny może zdecydować się na usunięcie zadania z wątku i umieszczenie go w stanie nieuruchomionym. Na przykład może się to zdarzyć, gdy zadanie jest blokowane w przypadku elementów pierwotnych synchronizacji lub czeka na ukończenie operacji we/wy. Host wywołuje [SwitchOut —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) w celu powiadomienia środowiska CLR, że zadanie reprezentowane przez bieżące wystąpienie `ICLRTask` nie jest już w stanie obsługiwanym.  
  
 Zadanie zwykle kończy się na końcu wykonywania kodu. W tym czasie Host wywoła `ICLRTask::ExitTask`, aby zniszczyć powiązane `ICLRTask`. Zadania mogą być również odtwarzane przy użyciu wywołania do `ICLRTask::Reset`, co umożliwia ponowne użycie wystąpienia `ICLRTask`. Takie podejście uniemożliwia narzutowanie wielokrotnego tworzenia i niszczenia wystąpień.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
