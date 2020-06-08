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
ms.openlocfilehash: f918d4e7b95922734d70ed832581e6c494c70b05
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501641"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager — Interfejs
Dostarcza metody, które pozwalają hostowi jawnie zażądać, że środowisko uruchomieniowe języka wspólnego (CLR) tworzy nowe zadanie, pobiera aktualnie wykonywane zadanie i ustawia język geograficzny oraz kulturę dla zadania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateTask, metoda](iclrtaskmanager-createtask-method.md)|Żądania jawnie, że środowisko CLR tworzy nowe wystąpienie [ICLRTask](iclrtask-interface.md) .|  
|[GetCurrentTask, metoda](iclrtaskmanager-getcurrenttask-method.md)|Pobiera `ICLRTask` wystąpienie reprezentujące aktualnie wykonywane zadanie.|  
|[GetCurrentTaskType, metoda](iclrtaskmanager-getcurrenttasktype-method.md)|Pobiera typ zadania, które jest aktualnie wykonywane.|  
|[SetLocale, metoda](iclrtaskmanager-setlocale-method.md)|Powiadamia środowisko CLR o modyfikacji identyfikatora ustawień regionalnych w aktualnie wykonywanym zadaniu.|  
|[SetUILocale, metoda](iclrtaskmanager-setuilocale-method.md)|Powiadamia środowisko uruchomieniowe języka wspólnego, że host zmodyfikował identyfikator ustawień regionalnych interfejsu użytkownika w aktualnie wykonywanym zadaniu.|  
  
## <a name="remarks"></a>Uwagi  
 Każde zadanie działające w środowisku hostowanym ma reprezentacje zarówno na stronie hosta (wystąpienie elementu [IHostTask](ihosttask-interface.md)), jak i po stronie CLR (wystąpienie klasy [ICLRTask](iclrtask-interface.md)). Host lub środowisko CLR mogą inicjować Tworzenie zadania, ale reprezentacja po stronie hosta musi być skojarzona z odpowiednią reprezentacją po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a środowiskiem CLR dotyczącym zadania. Aby można było wykonać kod zarządzany w wątku systemu operacyjnego, należy utworzyć te dwa obiekty.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](iclrtask-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
