---
title: "IHostIoCompletionManager::InitializeHostOverlapped — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.InitializeHostOverlapped
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26e8f9d963e6924a8c6abd73c3e025543c7d5b83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
|S_OK|`InitializeHostOverlapped`zwrócona pomyślnie.|  
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRIoCompletionManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [GetHostOverlappedSize — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [IHostIoCompletionManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
