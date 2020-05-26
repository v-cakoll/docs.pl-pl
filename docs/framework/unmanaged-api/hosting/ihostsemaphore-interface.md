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
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803695"
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore — Interfejs
Reprezentuje implementację semafora na hoście dla wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ReleaseSemaphore, metoda](ihostsemaphore-releasesemaphore-method.md)|Zwiększa liczbę `IHostSemaphore` wystąpień bieżącego wystąpienia o określoną liczbę.|  
|[Wait, metoda](ihostsemaphore-wait-method.md)|Powoduje, że bieżące `IHostSemaphore` wystąpienie zaczeka, aż będzie własnością lub określony czas upłynął.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)
- [IHostAutoEvent — Interfejs](ihostautoevent-interface.md)
- [IHostManualEvent, interfejs](ihostmanualevent-interface.md)
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
