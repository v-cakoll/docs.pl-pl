---
title: IHostTask — Interfejs
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121394"
---
# <a name="ihosttask-interface"></a>IHostTask — Interfejs
Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) komunikowanie się z hostem w celu zarządzania zadaniami.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alert, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Żąda, aby Host wznowił zadanie reprezentowane przez bieżące wystąpienie `IHostTask`, więc zadanie można przerwać.|  
|[GetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Pobiera poziom priorytetu wątku zadania reprezentowanego przez bieżące wystąpienie `IHostTask`.|  
|[Join, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Blokuje zadanie wywołujące do momentu zakończenia zadania reprezentowanego przez bieżące wystąpienie `IHostTask`, upłynie określony przedział czasu lub [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) .|  
|[SetCLRTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Kojarzy wystąpienie [interfejsu ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) z bieżącym wystąpieniem `IHostTask`.|  
|[SetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Żądania, dla których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie `IHostTask`.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Żąda, aby Host przeniesieł zadanie reprezentowane przez bieżące wystąpienie `IHostTask` ze stanu wstrzymania do stanu na żywo, w którym można wykonać kod.|  
  
## <a name="remarks"></a>Uwagi  
 CLR wywołuje metody zdefiniowane przez `IHostTask`, aby uruchomić zadanie, ustawić jego poziom priorytetu wątku i tak dalej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
