---
title: "IHostSyncManager — Interfejs"
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
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby utworzyć przez wywołanie metody hosta zamiast funkcji synchronizacji Win32 elementy podstawowe synchronizacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateAutoEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Tworzy obiekt zdarzenie z resetowaniem automatycznym.|  
|[CreateCrst, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Tworzy obiekt sekcja krytyczna synchronizacji.|  
|[CreateCrstWithSpinCount, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Tworzy obiekt sekcja krytyczna z licznikiem pokrętła do synchronizacji.|  
|[CreateManualEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|Tworzy obiekt zdarzenia resetowania ręcznego.|  
|[CreateMonitorEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|Tworzy obiekt monitorowanych zdarzenie z resetowaniem automatycznym.|  
|[CreateRWLockReaderEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Tworzy obiekt zdarzenia resetowania ręcznego wykonania blokadę.|  
|[CreateRWLockWriterEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Tworzy obiekt zdarzenie z resetowaniem automatycznym dla implementacji blokadę.|  
|[CreateSemaphore, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Tworzy [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) obiektu CLR do użycia jako semafor Czekaj zdarzenia.|  
|[SetCLRSyncManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Ustawia [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) wystąpienie do skojarzenia z bieżącym `IHostSyncManager` wystąpienia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR odnajduje implementacja hosta `IHostSyncManager` przez wywołanie metody [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metody z `IID` z IID_IHostSyncManager.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
