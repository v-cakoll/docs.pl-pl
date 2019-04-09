---
title: IHostThreadPoolManager::GetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4dce4efeb82f44e2c0d19e95551696b16e9f07ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157550"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a>IHostThreadPoolManager::GetMaxThreads — Metoda
Pobiera maksymalną liczbę wątków, które przechowuje hosta jednocześnie w puli wątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwMaxWorkerThreads`  
 [out] Wskaźnik do maksymalną liczbę wątków, które host przechowuje w puli wątków.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetMaxThreads` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR (nie został załadowany do procesu lub środowiska CLR jest w stanie, w której nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Host nie zawiera implementacji `GetMaxThreads`.|  
  
## <a name="remarks"></a>Uwagi  
 CLR wywołuje `GetMaxThreads` ustalenie, łączna liczba wątków w puli wątków. [Getavailablethreads —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) metoda pobiera liczbę wątków, które nie są obecnie przetwarza elementy robocze. Wszystkie żądania nad wartością zwróconą `pdwMaxWorkerThreads` parametru pozostają w kolejce do momentu wątków stają się dostępne.  
  
 Jeśli host nie dostarcza implementację `GetMaxThreads`, powinna zwrócić wartość HRESULT E_NOTIMPL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
