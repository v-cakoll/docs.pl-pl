---
title: IHostSyncManager::CreateCrst — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
ms.openlocfilehash: 03c0f94d10629b677cca4c4c456cdaab344cfcdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139432"
---
# <a name="ihostsyncmanagercreatecrst-method"></a>IHostSyncManager::CreateCrst — Metoda
Tworzy obiekt sekcji krytycznej do synchronizacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppCrst`  
 określoną Wskaźnik do adresu wystąpienia [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) zaimplementowanego przez hosta lub wartość null, jeśli nie można utworzyć sekcji krytycznej.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateCrst` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci, aby utworzyć żądaną sekcję krytyczną.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekty sekcji krytycznej zapewniają synchronizację podobną do tej, która jest dostarczana przez obiekt mutex, z tą różnicą, że sekcje krytyczne mogą być używane tylko przez wątki pojedynczego procesu. `CreateCrst` odzwierciedla funkcję Win32 `InitializeCriticalSection`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostCrst, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [Muteksy](../../../standard/threading/mutexes.md)
- [Semaphore i SemaphoreSlim](../../../standard/threading/semaphore-and-semaphoreslim.md)
