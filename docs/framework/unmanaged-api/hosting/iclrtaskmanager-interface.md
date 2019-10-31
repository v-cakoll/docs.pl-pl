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
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092187"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager — Interfejs
Dostarcza metody, które pozwalają hostowi jawnie zażądać, że środowisko uruchomieniowe języka wspólnego (CLR) tworzy nowe zadanie, pobiera aktualnie wykonywane zadanie i ustawia język geograficzny oraz kulturę dla zadania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Żądania jawnie, że środowisko CLR tworzy nowe wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .|  
|[GetCurrentTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Pobiera wystąpienie `ICLRTask`, które reprezentuje aktualnie wykonywane zadanie.|  
|[GetCurrentTaskType, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Pobiera typ zadania, które jest aktualnie wykonywane.|  
|[SetLocale, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Powiadamia środowisko CLR o modyfikacji identyfikatora ustawień regionalnych w aktualnie wykonywanym zadaniu.|  
|[SetUILocale, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Powiadamia środowisko uruchomieniowe języka wspólnego, że host zmodyfikował identyfikator ustawień regionalnych interfejsu użytkownika w aktualnie wykonywanym zadaniu.|  
  
## <a name="remarks"></a>Uwagi  
 Każde zadanie działające w środowisku hostowanym ma reprezentacje zarówno na stronie hosta (wystąpienie elementu [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)), jak i po stronie CLR (wystąpienie klasy [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Host lub środowisko CLR mogą inicjować Tworzenie zadania, ale reprezentacja po stronie hosta musi być skojarzona z odpowiednią reprezentacją po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a środowiskiem CLR dotyczącym zadania. Aby można było wykonać kod zarządzany w wątku systemu operacyjnego, należy utworzyć te dwa obiekty.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
