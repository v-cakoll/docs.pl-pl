---
title: ICLRTaskManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134662"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager — Interfejs
Znajdują się metody, które umożliwiają hosta do jawnego żądania, aby środowisko uruchomieniowe języka wspólnego (CLR) Utwórz nowe zadanie, Pobierz aktualnie wykonywane zadanie i geograficzne języka i kultury dla zadania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Żąda jawnie, że środowisko CLR, Utwórz nową [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.|  
|[GetCurrentTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Pobiera `ICLRTask` wystąpienia, która reprezentuje zadania, które jest w trakcie wykonywania.|  
|[GetCurrentTaskType, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Pobiera typ zadania, które jest w trakcie wykonywania.|  
|[SetLocale, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Powiadamia środowiska CLR, że host został zmodyfikowany identyfikator ustawień regionalnych na aktualnie wykonywane zadanie.|  
|[SetUILocale, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Powiadamia środowiska uruchomieniowego języka wspólnego, że host został zmodyfikowany identyfikator ustawień regionalnych interfejsu użytkownika na aktualnie wykonywane zadanie.|  
  
## <a name="remarks"></a>Uwagi  
 Każde zadanie, który jest uruchomiony w środowisku hostowanej ma reprezentacji zarówno po stronie hosta (wystąpienie [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) i po stronie CLR (wystąpienie [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Środowisko CLR lub hosta można zainicjować tworzenia zadania, ale reprezentacji po stronie hosta muszą być skojarzone z odpowiedniego reprezentacji po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a CLR dotyczące zadania. Dwa obiekty muszą być tworzone i utworzyć ich kodu zarządzanego, można wykonać na wątku systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
