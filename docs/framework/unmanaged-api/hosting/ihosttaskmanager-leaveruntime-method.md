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
ms.openlocfilehash: 959cb541013ca0a26557e849874dbb329489d855
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749531"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime — Metoda
Powiadamia hosta, że aktualnie wykonywane zadanie zostanie pozostaw środowisko uruchomieniowe języka wspólnego (CLR), a następnie wprowadź kod niezarządzany.  
  
> [!IMPORTANT]
>  Do odpowiedniego wywołania [ihosttaskmanager::enterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) powiadamia hosta, że aktualnie wykonywane zadanie ponownego wprowadzania kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `target`  
 [in] Adres w ramach zamapowanego przenośny plik wykonywalny niezarządzanej funkcji do wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nie ma wystarczającej ilości pamięci jest dostępny w celu zakończenia żądanej alokacji.|  
  
## <a name="remarks"></a>Uwagi  
 Może być zagnieżdżona sekwencji wywołań do i z kodem niezarządzanym. Na przykład poniższa lista zawiera hipotetyczny sytuacji, w którym Sekwencja wywołań `LeaveRuntime`, [ihosttaskmanager::reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager::reverseleaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), i `IHostTaskManager::EnterRuntime` Zezwalaj hostowi na określenie zagnieżdżonych warstw.  
  
|Akcja|Odpowiedniego wywołania metody|  
|------------|-------------------------------|  
|Wywołaj niezarządzanej funkcji w języku C za pomocą platformy zarządzane wywołania pliku wykonywalnego języka Visual Basic.|`IHostTaskManager::LeaveRuntime`|  
|Niezarządzanej funkcji C wywołuje metodę w zarządzanej biblioteki DLL, napisany w C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Zarządzany C# funkcja wywołuje innej niezarządzanej funkcji w języku C, również przy użyciu platformy wywołania.|`IHostTaskManager::LeaveRuntime`|  
|Druga funkcja niezarządzanych zwraca wykonanie do C# funkcji.|`IHostTaskManager::EnterRuntime`|  
|C# Funkcja zwraca wykonanie do pierwszej funkcji niezarządzanych.|`IHostTaskManager::ReverseLeaveRuntime`|  
|Pierwszy niezarządzanej funkcji zwraca wykonanie do programu Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
