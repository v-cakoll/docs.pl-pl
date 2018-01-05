---
title: "ICLRTask2::EndPreventAsyncAbort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2.EndPreventAsyncAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b18f6b8f6768c0a2980489cf8b84e16a9dd31350
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort — Metoda
Zezwala na nowe lub oczekujące żądania przerwania wątku w wątku przerywa w bieżącym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HOST_E_INVALIDOPERATION|Metoda została wywołana w wątku, który nie jest bieżący wątek.|  
  
## <a name="remarks"></a>Uwagi  
 Ten licznik zmniejsza przerwania wątku opóźnienie — metoda podczas wywoływania bieżącego wątku o jeden.  
  
 Wywołuje się [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) i `EndPreventAsyncAbort` mogą być zagnieżdżone. Tak długo, jak wartość licznika jest większa niż zero, opóźnienia przerwania wątku dla bieżącego wątku.  
  
 Funkcje, które jest udostępniane przez tę funkcję jest używana wewnętrznie przez maszynę wirtualną (VM). Nieprawidłowe użycie tych metod może spowodować nieokreślony zachowanie w maszynie Wirtualnej. Na przykład wywołanie elementu `EndPreventAsyncAbort` bez wywoływania pierwszego elementu `BeginPreventAsyncAbort` można ustawić licznik do zera, gdy maszyna wirtualna wcześniej ma zwiększany. Podobnie wewnętrzny licznik nie jest sprawdzany pod kątem przepełnienia. W razie przekroczenia limitu całkowitej, ponieważ jest zwiększany przez hosta i maszyny Wirtualnej, efekty jest nieokreślony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [BeginPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)  
 [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
