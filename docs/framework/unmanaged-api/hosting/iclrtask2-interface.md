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
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124525"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 — Interfejs
Oferuje wszystkie funkcje interfejsu [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ; Ponadto udostępnia metody zezwalające na opóźnione przerywanie wątków w bieżącym wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Opóźnia nowe żądania przerwania wątku w bieżącym wątku.|  
|[EndPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Zezwala na to, aby nowe lub oczekujące żądania przerwania wątku powodowały przerwania wątku w bieżącym wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICLRTask2` dziedziczy interfejs `ICLRTask` i dodaje metody, które pozwalają hostowi opóźnić przerwania wątku, aby chronić region kodu, który nie może kończyć się niepowodzeniem. Wywołanie `BeginPreventAsyncAbort` zwiększa licznik Opóźnij wątek i Przerwij dla bieżącego wątku, a wywoływanie `EndPreventAsyncAbort` powoduje jego zmniejszenie. Wywołania `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` mogą być zagnieżdżane. Tak długo, jak licznik jest większy od zera, przerwania wątku dla bieżącego wątku są opóźnione.  
  
 Jeśli wywołania `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` nie są sparowane, możliwe jest osiągnięcie stanu, w którym przerwania wątku nie można dostarczyć do bieżącego wątku.  
  
 Opóźnienie nie jest uznawane za wątek, który przerywa siebie.  
  
 Funkcja, która jest udostępniona przez tę funkcję, jest używana wewnętrznie przez maszynę wirtualną (VM). Użycie tych metod może spowodować nieokreślone zachowanie maszyny wirtualnej. Na przykład wywoływanie `EndPreventAsyncAbort` bez uprzedniego wywołania `BeginPreventAsyncAbort` może spowodować, że licznik ma wartość zero, gdy maszyna wirtualna została wcześniej zwiększona. Podobnie licznik wewnętrzny nie jest sprawdzany pod kątem przepełnienia. W przypadku przekroczenia limitu całkowitego, ponieważ jest zwiększana przez zarówno hosta, jak i maszynę wirtualną, zachowanie nie zostanie określone.  
  
 Aby uzyskać informacje na temat członków dziedziczonych z `ICLRTask` i innych sposobów korzystania z tego interfejsu, zobacz Interfejs [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
