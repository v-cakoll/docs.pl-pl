---
title: IHostTaskManager::LeaveRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d31c5c1b95d250f90b202b391d908f9c12afb84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime — Metoda
Powiadamia hosta aktualnie wykonywanego zadania o zbliżającym się pozostaw środowisko uruchomieniowe języka wspólnego (CLR), a następnie wprowadź kod niezarządzany.  
  
> [!IMPORTANT]
>  Do odpowiedniego wywołania [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) powiadamia hosta, czy aktualnie wykonywanego zadania ponownego wprowadzania kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `target`  
 [in] Adres w mapowanej przenośny plik wykonywalny niezarządzanej funkcji do wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Do zakończenia żądanej alokacji jest za mało pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Może być zagnieżdżone sekwencje wywołania do i z kodu niezarządzanego. Na przykład na poniższej liście opisano fikcyjnej sytuacji, w którym sekwencję wywołań `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), i `IHostTaskManager::EnterRuntime` umożliwia hosta do identyfikowania zagnieżdżone warstwy.  
  
|Akcja|Odpowiedniego wywołania — metoda|  
|------------|-------------------------------|  
|Wywołania funkcji niezarządzanej napisana w języku C przy użyciu platformy zarządzanych wywołania wykonywalne języka Visual Basic.|`IHostTaskManager::LeaveRuntime`|  
|Niezarządzanej funkcji C wywołuje metodę w zarządzanej biblioteki DLL napisane w języku C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Zarządzane C# wywołań funkcji wywołanie innego niezarządzanej funkcji napisane w języku C, również przy użyciu platformy.|`IHostTaskManager::LeaveRuntime`|  
|Drugi niezarządzanej funkcji zwraca wykonanie funkcji języka C#.|`IHostTaskManager::EnterRuntime`|  
|Funkcja języka C# zwraca wykonanie pierwszej funkcji niezarządzanej.|`IHostTaskManager::ReverseLeaveRuntime`|  
|Pierwszy niezarządzanej funkcji zwraca wykonanie do programu Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
