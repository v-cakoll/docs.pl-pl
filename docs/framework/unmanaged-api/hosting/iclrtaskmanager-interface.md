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
ms.openlocfilehash: 14c2c9b70ac2e57983ea4b16772add6a1dff5ff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438070"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager — Interfejs
Znajdują się metod, które umożliwiają hosta, aby zażądać jawnie środowisko uruchomieniowe języka wspólnego (CLR) umożliwia utworzenie nowego zadania, Pobierz aktualnie wykonywanego zadania i geograficzne języka i kultury dla zadania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Jawnie żądań, że środowisko CLR, Utwórz nową [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.|  
|[GetCurrentTask, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Pobiera `ICLRTask` wystąpienia reprezentujący zadanie, które jest aktualnie wykonywany.|  
|[GetCurrentTaskType, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Pobiera typ zadania, które jest aktualnie wykonywany.|  
|[SetLocale, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Powiadamia CLR, że host został zmodyfikowany identyfikator ustawień regionalnych na aktualnie wykonywanego zadania.|  
|[SetUILocale, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Powiadamia środowisko uruchomieniowe języka wspólnego, że host został zmodyfikowany identyfikator ustawień regionalnych interfejsu użytkownika na aktualnie wykonywanego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 Każde zadanie, który jest uruchomiony w środowisku hostowanej ma reprezentacje zarówno po stronie hosta (wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) i po stronie CLR (wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Host lub CLR można inicjować tworzenia zadania, ale reprezentacja po stronie hosta musi być skojarzony z odpowiedniego reprezentacja po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a CLR dotyczące zadania. Dwa obiekty należy utworzyć i utworzyć kod zarządzany może zostać uruchomiony w wątku systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
