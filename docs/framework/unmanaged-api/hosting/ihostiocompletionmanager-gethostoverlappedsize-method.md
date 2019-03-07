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
ms.openlocfilehash: e1482baf1a5ac951ce94ce55e50de2562597bdb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490726"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize — Metoda
Pobiera rozmiar danych niestandardowych, aby dołączyć do żądań We/Wy przez hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcbSize`  
 [out] Wskaźnik do liczby bajtów, które środowisko uruchomieniowe języka wspólnego (CLR) należy przydzielić oprócz rozmiaru Win32 `OVERLAPPED` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Asynchroniczne wywołania operacji We/Wy do interfejsów API platformy Windows zająć Win32 `OVERLAPPED` obiektu, który zawiera informacje, takie jak pozycja wskaźnika pliku. Do zarządzania stanem, aplikacje, które zwykle wywołania asynchroniczne operacje We/Wy, należy dodać niestandardowe dane do struktury. `GetHostOverlappedSize` i [ihostiocompletionmanager::initializehostoverlapped —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) zapewnienia możliwości dla hosta, obejmujący takie dane niestandardowe.  
  
 CLR wywołuje `GetHostOverlappedSize` metodę, aby określić rozmiar danych niestandardowych, że host nie chce dołączyć do `OVERLAPPED` obiektu.  
  
> [!NOTE]
>  `GetHostOverlappedSize` zostanie wywołana tylko raz. Niestandardowe dane hosta musi być taki sam rozmiar dla każdego żądania We/Wy.  
  
> [!IMPORTANT]
>  Rozmiar `OVERLAPPED` sam obiekt nie znajduje się w wartości `pcbSize`.  
  
 Aby uzyskać więcej informacji na temat `OVERLAPPED` struktury, można znaleźć w dokumentacji platformy Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
