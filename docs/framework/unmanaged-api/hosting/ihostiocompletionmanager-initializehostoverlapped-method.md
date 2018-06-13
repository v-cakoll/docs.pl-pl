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
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438971"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped — Metoda
Zapewnia możliwość zainicjować wszelkie niestandardowe dane mają zostać dołączone do systemu Win32 hosta `OVERLAPPED` struktury, która jest używana dla żądań asynchronicznych We/Wy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvOverlapped`  
 [in] Wskaźnik do środowiska Win32 `OVERLAPPED` struktury, które zostaną dołączone do żądania operacji We/Wy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci nie była dostępna do przydzielenia do żądanego zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj funkcji platformy Windows `OVERLAPPED` struktury do przechowywania stanu dla żądań asynchronicznych We/Wy. Wywołania CLR `InitializeHostOverlapped` metody daje możliwość dołączenia danych niestandardowych do hosta `OVERLAPPED` wystąpienia.  
  
> [!IMPORTANT]
>  Aby uzyskać na początku bloku ich danych niestandardowych, hosty ustawić przesunięcie rozmiar `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).  
  
 Zwracana wartość E_OUTOFMEMORY wskazuje, że host nie może zainicjować swoich danych niestandardowych. W takim przypadku CLR zgłasza błąd i nie powiodło się wywołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [GetHostOverlappedSize, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [IHostIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
