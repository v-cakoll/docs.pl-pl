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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1baeac5db41aa64380d694ebab5419229d8adb4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088213"
---
# <a name="iclrtask-interface"></a>ICLRTask — Interfejs
Udostępnia metody, które umożliwiają hosta propozycji dotyczących środowiska uruchomieniowego języka wspólnego (CLR) lub w celu udostępnienia powiadomienia do CLR o skojarzone zadanie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Żądania, że środowisko CLR przerwać zadanie, bieżący `ICLRTask` wystąpienie reprezentuje.|  
|[ExitTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Powiadamia CLR, który zadanie skojarzone z bieżącym `ICLRTask` wystąpienia kończy się i próbuje przeprowadzić zamknięcie zadania.|  
|[GetMemStats, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Pobiera informacje statystyczne dotyczące użycia zasobów pamięci przez zadanie, reprezentowane przez bieżącą `ICLRTask` wystąpienia.|  
|[LocksHeld, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Pobiera liczbę blokad znajdujących się obecnie w zadania.|  
|[NeedsPriorityScheduling, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Pobiera wartość wskazującą, czy host należy przypisać wysoki priorytet ponowne planowanie zadania, reprezentowane przez bieżącą `ICLRTask` wystąpienia.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informuje środowisko CLR hosta zostało zakończone zadania i umożliwia CLR do ponownego użycia bieżącego `ICLRTask` wystąpienia do reprezentowania inne zadanie.|  
|[RudeAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Powoduje, że środowisko CLR przerwać zadanie, reprezentowane przez bieżącą `ICLRTask` wystąpienia natychmiast, bez gwarancji, że finalizatory zostaną wykonane.|  
|[SetTaskIdentifier, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Ustawia Unikatowy identyfikator dla tego zadania, reprezentowane przez bieżącą `ICLRTask` wystąpienie do użytku podczas debugowania.|  
|[SwitchIn, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Powiadamia CLR, który zadanie jest reprezentowane przez bieżącą `ICLRTask` wystąpienie jest w stanie uruchamiane ręcznie.|  
|[SwitchOut, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Powiadamia CLR, który zadanie jest reprezentowane przez bieżącą `ICLRTask` wystąpienia nie jest już w stanie uruchamiane ręcznie.|  
|[YieldTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Żądania wysyłane przez wartość czasu procesora upewnij CLR dostępne dla innych zadań. Środowisko CLR sprawia, że żadnej gwarancji, że zadania zostaną przełączeni w stan, w którym może przynieść czas przetwarzania.|  
  
## <a name="remarks"></a>Uwagi  
 `ICLRTask` Jest reprezentacją zadania dla środowiska CLR. W dowolnym momencie podczas wykonywania kodu zadanie może być opisany jako uruchomiona lub jest oczekiwanie na uruchomienie. Wywołania hosta `ICLRTask::SwitchIn` metodę, aby powiadomić środowiska CLR, zadania, bieżący `ICLRTask` reprezentuje wystąpienie znajduje się teraz w stanie wykonywalny. Po wywołaniu `ICLRTask::SwitchIn`, hosta można zaplanować zadania dotyczące dowolnego wątku systemu operacyjnego, z wyjątkiem w przypadkach, w których środowisko uruchomieniowe wymaga koligacji wątku, określony przez wywołania [ihosttaskmanager::beginthreadaffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) i [Ihosttaskmanager::endthreadaffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) metody. Pewien czas później, system operacyjny zdecydować usunąć zadanie z wątku i umieścić go w stan bez uruchamiania. Na przykład to może się zdarzyć, gdy zadanie blokuje się na podstawowych synchronizacji lub czeka na zakończenie operacji We/Wy. Wywołania hosta [switchout —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) powiadomić środowiska CLR, który zadanie jest reprezentowane przez bieżącą `ICLRTask` wystąpienia nie jest już w stanie uruchamiane ręcznie.  
  
 Zadania zazwyczaj kończy się na końcu wykonywania kodu. W tym czasie wywołania hosta `ICLRTask::ExitTask` zniszczyć skojarzonego `ICLRTask`. Jednak zadania, również można odtworzyć za pomocą wywołania `ICLRTask::Reset`, co pozwala `ICLRTask` wystąpienia ma być używany ponownie. To podejście zapobiega konieczności wielokrotnie tworzenie i niszczenie wystąpień.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
