---
title: IHostSyncManager::CreateCrstWithSpinCount — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50f292ab39bcf77d49d8a363b43b9233f350974c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446771"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a>IHostSyncManager::CreateCrstWithSpinCount — Metoda
Tworzy obiekt sekcja krytyczna z licznikiem pokrętła do synchronizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSpinCount`  
 [in] Określa liczbę pokrętła dla obiekt sekcja krytyczna.  
  
 `ppCrst`  
 [out] Wskaźnik do adresu [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia, lub wartość null, jeśli nie można utworzyć sekcji krytycznych.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateCrstWithSpinCount` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci nie była dostępna, można utworzyć żądanego sekcja krytyczna.|  
  
## <a name="remarks"></a>Uwagi  
 Liczba pokrętła jest używana tylko w systemie wieloprocesorowym. Liczba pokrętła określa liczbę powtórzeń wątek wywołujący musi pokrętła przed przesłaniem operację oczekiwania na semafora skojarzony z sekcji krytycznej niedostępny. Jeśli sekcja krytyczna staje się wolnego podczas operacji pokrętła, wątek wywołujący pozwala uniknąć operacji oczekiwania. `CreateCrstWithSpinCount` odzwierciedla Win32 `InitializeCriticalSectionAndSpinCount` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
