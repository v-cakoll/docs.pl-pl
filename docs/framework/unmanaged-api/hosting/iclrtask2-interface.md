---
title: ICLRTask2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cbd627eff9318fce38ec238e5fa686cc9d759b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627190"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 — Interfejs
Oferuje wszystkie funkcje [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfejsu; ponadto udostępnia metody, które umożliwiają wątku przerywa opóźnionych w bieżącym wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Nowy wątek opóźnienia przerwać żądania w bieżącym wątku.|  
|[EndPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Zezwala na nowe lub oczekujące żądania przerwania wątku spowoduje w wątku przerywa w bieżącym wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `ICLRTask2` Interfejs dziedziczy `ICLRTask` interfejs i dodaje metody, które umożliwiają hosta opóźnienia przerwań wątku, do ochrony region kodu, które muszą zakończyć się niepowodzeniem. Wywoływanie `BeginPreventAsyncAbort` zwiększa licznik opóźnienie wątku przerwania dla bieżącego wątku i wywołania `EndPreventAsyncAbort` zmniejsza ją. Wywołania `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` mogą być zagnieżdżone. Tak długo, jak długo wartość licznika jest większa od zera, opóźnienia przerwania wątku dla bieżącego wątku.  
  
 Jeśli wywołania `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` są nie sparowano istnieje możliwość osiągnąć stan, w który wątek przerwań nie można dostarczyć do bieżącego wątku.  
  
 Opóźnienie nie jest uznawane wątku, który przerywa sam.  
  
 Funkcje, które jest uwidaczniany przez ta funkcja jest używana wewnętrznie przez maszynę wirtualną (VM). Niewłaściwe korzystanie z tych metod może spowodować nieokreślone zachowanie na maszynie wirtualnej. Na przykład, wywołanie `EndPreventAsyncAbort` bez wywoływania pierwszy `BeginPreventAsyncAbort` można ustawić licznik na zero, gdy maszyna wirtualna wcześniej jest zwiększany. Podobnie Licznik wewnętrzny nie jest sprawdzane pod kątem przepełnienia. Jeśli przekracza całkowity limit, ponieważ jest zwiększany zarówno przez host i maszyna wirtualna, wynikowe zachowanie jest nieokreślone.  
  
 Dla informacji na temat elementów członkowskich są dziedziczone z `ICLRTask` i informacje o innych zastosowań tego interfejsu, [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
