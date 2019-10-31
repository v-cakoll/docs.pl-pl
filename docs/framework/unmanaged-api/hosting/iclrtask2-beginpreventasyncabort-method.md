---
title: ICLRTask2::BeginPreventAsyncAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: 67841bbcd796e41b3b81f922020fe6c3677730c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124567"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort — Metoda
Opóźnia nowe żądania przerwania wątku z wyniku przerwania wątku w bieżącym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HOST_E_INVALIDOPERATION|Metoda została wywołana w wątku, który nie jest bieżącym wątkiem.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody zwiększa licznik Opóźnij wątek wątku dla bieżącego wątku o jeden.  
  
 Wywołania `BeginPreventAsyncAbort` i [ICLRTask2:: EndPreventAsyncAbort —](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) mogą być zagnieżdżane. Tak długo, jak licznik jest większy od zera, przerwania wątku dla bieżącego wątku są opóźnione. Jeśli to wywołanie nie jest sparowane z wywołaniem metody `EndPreventAsyncAbort`, możliwe jest osiągnięcie stanu, w którym przerwania wątku nie można dostarczyć do bieżącego wątku.  
  
 Opóźnienie nie jest uznawane za wątek, który przerywa siebie.  
  
 Funkcja, która jest udostępniona przez tę funkcję, jest używana wewnętrznie przez maszynę wirtualną (VM). Użycie tych metod może spowodować nieokreślone zachowanie maszyny wirtualnej. Na przykład wywoływanie `EndPreventAsyncAbort` bez uprzedniego wywołania `BeginPreventAsyncAbort` może spowodować, że licznik ma wartość zero, gdy maszyna wirtualna została wcześniej zwiększona. Podobnie licznik wewnętrzny nie jest sprawdzany pod kątem przepełnienia. W przypadku przekroczenia limitu całkowitego, ponieważ jest zwiększana przez zarówno hosta, jak i maszynę wirtualną, zachowanie nie zostanie określone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EndPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
