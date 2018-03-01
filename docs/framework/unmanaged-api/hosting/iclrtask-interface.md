---
title: "ICLRTask — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6fcce85e56abae561b05364a925fdb6b55825669
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask-interface"></a>ICLRTask — Interfejs
Udostępnia metody umożliwiające hosta do wysyłania żądań środowisko uruchomieniowe języka wspólnego (CLR) lub w celu udostępnienia powiadomień do środowiska CLR o skojarzonego zadania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Żądania, że środowisko CLR przerwać zadanie który bieżącego `ICLRTask` reprezentuje wystąpienie.|  
|[ExitTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Powiadamia CLR, które zadania skojarzone z bieżącym `ICLRTask` wystąpienia kończy się i podejmie próbę prawidłowe zamknięcie zadania.|  
|[GetMemStats, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Pobiera informacje statystyczne dotyczące wykorzystania zasobów pamięci przez zadanie reprezentowany przez bieżący `ICLRTask` wystąpienia.|  
|[LocksHeld, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Pobiera liczbę blokad znajdujących się obecnie w zadania.|  
|[NeedsPriorityScheduling, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Pobiera wartość wskazującą, czy hosta należy przypisać o wysokim priorytecie ponowne zaplanowanie zadania reprezentowane przez bieżące `ICLRTask` wystąpienia.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informuje o środowisko CLR zostało zakończone zadanie hosta i umożliwia CLR do ponownego użycia bieżącego `ICLRTask` wystąpienie do reprezentowania inne zadanie.|  
|[RudeAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Powoduje, że CLR przerwania reprezentowany przez bieżące zadanie `ICLRTask` wystąpienie bezpośrednio, bez gwarancji, że finalizatory będą wykonywane.|  
|[SetTaskIdentifier, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Ustawia Unikatowy identyfikator dla zadania reprezentowany przez bieżący `ICLRTask` wystąpienie do użytku w debugowaniu.|  
|[SwitchIn, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Powiadamia CLR, która bieżącego zadania `ICLRTask` wystąpienie jest w stanie obsługiwane.|  
|[SwitchOut, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Powiadamia CLR, która bieżącego zadania `ICLRTask` wystąpienia nie jest już w stanie obsługiwane.|  
|[YieldTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Żądania wysyłane przez wartość czasu procesora upewnij CLR dostępne dla innych zadań. Środowisko CLR sprawia, że żadnej gwarancji, że zadania będą umieszczane w stanie, w którym mogą spowodować czas przetwarzania.|  
  
## <a name="remarks"></a>Uwagi  
 `ICLRTask` Reprezentacja zadania dla środowiska CLR. W dowolnym momencie podczas wykonywania kodu zadania można przedstawić jako uruchomione lub oczekuje na uruchomienie. Wywołania hosta `ICLRTask::SwitchIn` metodę, aby powiadomić CLR który zadania który bieżącego `ICLRTask` reprezentuje wystąpienie jest teraz w stanie obsługiwane. Po wywołaniu `ICLRTask::SwitchIn`, hosta można zaplanować zadanie w którymkolwiek wątku systemu operacyjnego, z wyjątkiem w przypadkach, gdy środowiska uruchomieniowego wymaga koligacji wątków, określony przez wywołania [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) i [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) metody. Pewien czas później, system operacyjny zdecydować się na usunięcie zadania z wątku i umieszczenie go w stanie pracy z systemem innym niż. Na przykład to może się zdarzyć, gdy zadanie blokuje na elementy podstawowe synchronizacji lub czeka na zakończenie operacji We/Wy. Wywołania hosta [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) powiadomiono CLR, która bieżącego zadania `ICLRTask` wystąpienia nie jest już w stanie obsługiwane.  
  
 Zadania zazwyczaj kończy się na końcu wykonanie kodu. W tym czasie wywołania hosta `ICLRTask::ExitTask` do zniszczenia skojarzony `ICLRTask`. Jednak zadań można również będzie wykonywane za pomocą wywołania `ICLRTask::Reset`, dzięki czemu `ICLRTask` wystąpienie do ponownego wykorzystania. Takie podejście zapobiega koszty wielokrotnie tworzenia i niszczenie wystąpień.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
