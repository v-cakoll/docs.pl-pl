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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804596"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent — Interfejs
Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Reset — Metoda](ihostmanualevent-reset-method.md)|Resetuje bieżące `IHostManualEvent` wystąpienie do stanu niesygnalizującego.|  
|[Set, metoda](ihostmanualevent-set-method.md)|Ustawia bieżące `IHostManualEvent` wystąpienie na sygnał.|  
|[Wait, metoda](ihostmanualevent-wait-method.md)|Powoduje, że bieżące `IHostManualEvent` wystąpienie zaczeka, aż będzie jego właścicielem lub upłynie określony czas.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)
- [IHostAutoEvent — Interfejs](ihostautoevent-interface.md)
- [IHostSemaphore, interfejs](ihostsemaphore-interface.md)
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
