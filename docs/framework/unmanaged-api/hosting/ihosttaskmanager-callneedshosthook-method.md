---
title: IHostTaskManager::CallNeedsHostHook — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 5bc5752d4d2b772b1d18f438c4daaa1b8938da9e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842351"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook — Metoda
Umożliwia hostowi określenie, czy środowisko uruchomieniowe języka wspólnego (CLR) może być wbudowane w określone wywołanie do niezarządzanej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `target`  
 podczas Adres w zamapowanym przenośnym pliku wykonywalnym (PE) niezarządzanej funkcji, która ma zostać wywołana.  
  
 `pbCallNeedsHostHook`  
 określoną Wskaźnik do wartości logicznej wskazującej, czy host wymaga wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Aby ułatwić optymalizację wykonywania kodu, środowisko CLR wykonuje analizę każdego wywołania wywołania platformy podczas kompilacji, aby określić, czy wywołanie może być wbudowane. `CallNeedsHostHook`umożliwia hostowi przesłonięcie tej decyzji przez wymaganie wywołania niezarządzanej funkcji. Jeśli host wymaga elementu Hook, środowisko uruchomieniowe nie wywołuje wywołania.  
  
 Host zwykle wymaga punktu zaczepienia, w którym należy dostosować stan zmiennoprzecinkowy lub po odebraniu powiadomienia, że wywołanie przejdzie do stanu, w którym host nie może śledzić żądań dotyczących pamięci lub wszelkich wykonanych blokad. Gdy host wymaga, aby wywołanie było podłączane, środowisko uruchomieniowe powiadamia hosta przejść do i z kodu zarządzanego za pomocą wywołań do [EnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)i [ReverseLeaveRuntime —](ihosttaskmanager-reverseleaveruntime-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](iclrtask-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
