---
title: IHostSemaphore — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7d4a295832a958fb6a8fe2e6c43a09135500d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696683"
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore — Interfejs
Reprezentuje implementację hosta semafor dla wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ReleaseSemaphore, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|Zwiększa liczbę bieżącego `IHostSemaphore` wystąpienia według określonej ilości.|  
|[Wait, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|Powoduje, że bieżący `IHostSemaphore` wystąpienie do odczekania aż do jego właścicielem jest lub określoną ilość czasu upłynie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostManualEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
