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
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176295"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook — Metoda
Umożliwia hostowi określenie, czy środowisko uruchomieniowe języka wspólnego (CLR) może wbudowane określone wywołanie funkcji niezarządzanej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `target`  
 [w] Adres w mapowanym pliku wykonywalnego przenośnego (PE) niezarządzanej funkcji, która ma być wywoływana.  
  
 `pbCallNeedsHostHook`  
 [na zewnątrz] Wskaźnik do wartości logicznej, który wskazuje, czy host wymaga połączenia, które mają być podłączone.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zoptymalizować wykonanie kodu, CLR wykonuje analizę każdej platformy wywołać wywołanie podczas kompilacji, aby ustalić, czy wywołanie może być inlined. `CallNeedsHostHook`umożliwia hostowi zastąpienie tej decyzji, wymagając podłączenia wywołania funkcji niezarządzanej. Jeśli host wymaga haka, środowisko wykonawcze nie inline wywołania.  
  
 Host zazwyczaj wymaga haka, gdzie musi dostosować stan zmiennoprzecinkowe lub po otrzymaniu powiadomienia, że wywołanie jest wprowadzenie stanu, w którym host nie może śledzić żądania środowiska wykonawczego dla pamięci lub blokady podjęte. Gdy host wymaga, aby wywołanie zostało podłączona, środowisko wykonawcze powiadamia o wielu przejściach do i z kodu zarządzanego przy użyciu wywołań [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)i [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
