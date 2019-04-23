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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad580f7cab81323e09a24dc12db39f223be3aeb4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208634"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent — Interfejs
Udostępnia implementację hosta reprezentacji zdarzenie resetowania ręcznego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|Przywraca bieżące `IHostManualEvent` wystąpienia do stanu zasygnalizowane.|  
|[Set, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|Ustawia bieżący `IHostManualEvent` wystąpienie do sygnalizowanego stanu.|  
|[Wait, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|Powoduje, że bieżący `IHostManualEvent` wystąpienia do odczekania aż do jego właścicielem jest lub określoną ilość czasu upłynie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
