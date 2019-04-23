---
title: IHostThreadPoolManager::SetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e290f20feacc59944bb1cafded327f4316ab88d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174164"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a>IHostThreadPoolManager::SetMinThreads — Metoda
Ustawia minimalna liczba bezczynnych wątków, które hosta, musisz utrzymywać w oczekiwaniu żądań.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `MinThreads`  
 [in] Nowe minimalna liczba wątków, które należy zachować hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetMinThreads` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Host nie zawiera implementacji `SetMinThreads`.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie musi dostarczać implementację `SetMinThreads`. W tym przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
