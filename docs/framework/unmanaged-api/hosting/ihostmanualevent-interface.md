---
title: IHostManualEvent — Interfejs
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136783"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent — Interfejs
Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|Resetuje bieżące wystąpienie `IHostManualEvent` do stanu bez sygnalizowania.|  
|[Set, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|Ustawia bieżące wystąpienie `IHostManualEvent` na sygnał.|  
|[Wait, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|Powoduje, że bieżące wystąpienie `IHostManualEvent` zaczeka, aż będzie własnością lub upłynie określony czas.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
