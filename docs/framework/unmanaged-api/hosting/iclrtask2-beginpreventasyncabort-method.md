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
ms.openlocfilehash: 0da18c6850f393808d05dff8b1f19ac12b05bb86
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762893"
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
  
 Wywołania `BeginPreventAsyncAbort` i [ICLRTask2:: EndPreventAsyncAbort —](iclrtask2-endpreventasyncabort-method.md) mogą być zagnieżdżane. Tak długo, jak licznik jest większy od zera, przerwania wątku dla bieżącego wątku są opóźnione. Jeśli to wywołanie nie jest sparowane z wywołaniem `EndPreventAsyncAbort` metody, można dotrzeć do stanu, w którym przerwania wątku nie można dostarczyć do bieżącego wątku.  
  
 Opóźnienie nie jest uznawane za wątek, który przerywa siebie.  
  
 Funkcja, która jest udostępniona przez tę funkcję, jest używana wewnętrznie przez maszynę wirtualną (VM). Użycie tych metod może spowodować nieokreślone zachowanie maszyny wirtualnej. Na przykład wywołanie `EndPreventAsyncAbort` bez pierwszego wywołania `BeginPreventAsyncAbort` może spowodować ustawienie wartości zero dla licznika, gdy maszyna wirtualna została wcześniej zwiększona. Podobnie licznik wewnętrzny nie jest sprawdzany pod kątem przepełnienia. W przypadku przekroczenia limitu całkowitego, ponieważ jest zwiększana przez zarówno hosta, jak i maszynę wirtualną, zachowanie nie zostanie określone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [EndPreventAsyncAbort, metoda](iclrtask2-endpreventasyncabort-method.md)
- [ICLRTask2 — Interfejs](iclrtask2-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
