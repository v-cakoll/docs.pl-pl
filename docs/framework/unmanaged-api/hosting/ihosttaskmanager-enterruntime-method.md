---
title: IHostTaskManager::EnterRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a01779e6203ddfea32e72838b7e02996fd868c2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749612"
---
# <a name="ihosttaskmanagerenterruntime-method"></a>IHostTaskManager::EnterRuntime — Metoda
Powiadamia hosta, że wywołanie metody niezarządzanego, takie jak metody wywołania platformy zwraca Kontrola wykonywania na środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`EnterRuntime` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci była dostępna do wykonania żądanej alokacji.|  
  
## <a name="remarks"></a>Uwagi  
 `EnterRuntime` jest wywoływana w celu powiadomienia hosta, niezarządzanej funkcji, dla którego podczas wcześniejszego wywołania [leaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) metoda została wprowadzona, zakończenia i zwraca Kontrola wykonywania do środowiska uruchomieniowego.  
  
> [!NOTE]
>  [Reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) jest wywoływana w celu powiadomienia hosta, niezarządzanej funkcji, dla którego podczas wcześniejszego wywołania `LeaveRuntime` została wprowadzona, wywołuje element kodu zarządzanego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [Instrukcje: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [LeaveRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
