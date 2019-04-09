---
title: IHostIoCompletionManager::InitializeHostOverlapped — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dea19a13cd2c741a24695b293ae1c8621ad5688
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157673"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped — Metoda
Zapewnia możliwość zainicjowania wszelkie niestandardowe dane do dołączenia do systemu Win32 hosta `OVERLAPPED` strukturę, która jest używana dla żądań asynchronicznych We/Wy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pvOverlapped`  
 [in] Wskaźnik do Win32 `OVERLAPPED` struktury, które mają zostać dołączone do żądania We/Wy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci na przydzielić żądanego zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Platforma Windows funkcji Użyj `OVERLAPPED` struktura do przechowywania stanu dla żądań asynchronicznych We/Wy. CLR wywołuje `InitializeHostOverlapped` metody, aby zapewnić możliwość dołączenia niestandardowe dane do hosta `OVERLAPPED` wystąpienia.  
  
> [!IMPORTANT]
>  Aby przejść do początku ich bloku danych niestandardowych, hosty należy ustawić przesunięcie do rozmiaru `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).  
  
 Zwracana wartość wynosząca E_OUTOFMEMORY wskazuje, że host nie może zainicjować swoich danych niestandardowych. W tym przypadku CLR zgłasza błąd i nie powiedzie się wywołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRIoCompletionManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
