---
title: ICLRTask2::EndPreventAsyncAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124552"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort — Metoda
Zezwala na to, aby nowe lub oczekujące żądania przerwania wątku powodowały przerwania wątku w bieżącym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HOST_E_INVALIDOPERATION|Metoda została wywołana w wątku, który nie jest bieżącym wątkiem.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody zmniejsza licznik Opóźnij wątek-Abort dla bieżącego wątku o jeden.  
  
 Wywołania [ICLRTask2:: BeginPreventAsyncAbort —](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) i `EndPreventAsyncAbort` mogą być zagnieżdżane. Tak długo, jak licznik jest większy od zera, przerwania wątku dla bieżącego wątku są opóźnione.  
  
 Funkcja, która jest udostępniona przez tę funkcję, jest używana wewnętrznie przez maszynę wirtualną (VM). Użycie tych metod może spowodować nieokreślone zachowanie maszyny wirtualnej. Na przykład wywoływanie `EndPreventAsyncAbort` bez uprzedniego wywołania `BeginPreventAsyncAbort` może spowodować, że licznik ma wartość zero, gdy maszyna wirtualna została wcześniej zwiększona. Podobnie licznik wewnętrzny nie jest sprawdzany pod kątem przepełnienia. W przypadku przekroczenia limitu całkowitego, ponieważ jest zwiększana przez zarówno hosta, jak i maszynę wirtualną, zachowanie nie zostanie określone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [BeginPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
