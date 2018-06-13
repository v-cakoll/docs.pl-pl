---
title: IHostIoCompletionManager::GetHostOverlappedSize — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6713fdb822babf607752c1823a32dae43a7d567e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439609"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize — Metoda
Pobiera rozmiar niestandardowych danych, aby dołączyć do żądania operacji We/Wy przez hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcbSize`  
 [out] Wskaźnik do liczba bajtów, które środowisko uruchomieniowe języka wspólnego (CLR) należy przydzielić oprócz rozmiaru Win32 `OVERLAPPED` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania asynchroniczne We/Wy do interfejsów API platformy Windows zająć Win32 `OVERLAPPED` obiektu, który zawiera informacje, takie jak pozycję wskaźnika pliku. Aby zachować stan, aplikacje, które zwykle wywołania asynchroniczne We/Wy dodać niestandardowe dane do struktury. `GetHostOverlappedSize` i [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) możliwość hosta na obejmują takie dane niestandardowe.  
  
 Wywołania CLR `GetHostOverlappedSize` metodę, aby określić rozmiar danych niestandardowych, która hosta można dołączyć do `OVERLAPPED` obiektu.  
  
> [!NOTE]
>  `GetHostOverlappedSize` zostanie wywołana tylko raz. Niestandardowe dane hosta musi mieć taki sam rozmiar dla każdego żądania We/Wy.  
  
> [!IMPORTANT]
>  Rozmiar `OVERLAPPED` sam obiekt nie znajduje się w wartości `pcbSize`.  
  
 Aby uzyskać więcej informacji na temat `OVERLAPPED` struktury, zobacz dokumentację platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.NativeOverlapped>  
 [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [IHostIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
