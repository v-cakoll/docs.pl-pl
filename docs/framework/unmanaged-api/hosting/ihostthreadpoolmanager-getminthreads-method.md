---
title: IHostThreadPoolManager::GetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: ce1abb75c5135a9bb23f1ad2d2acbd40d9111b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122065"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a>IHostThreadPoolManager::GetMinThreads — Metoda
Pobiera minimalną liczbę bezczynnych wątków, które Host przechowuje w puli wątków w oczekiwaniu na żądania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `MinThreads`  
 określoną Wskaźnik do minimalnej liczby bezczynnych wątków roboczych, które aktualnie przechowuje host.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetMinThreads` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Host nie dostarcza implementacji `GetMinThreads`.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagany do zapewnienia implementacji `GetMinThreads`. W takim przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
