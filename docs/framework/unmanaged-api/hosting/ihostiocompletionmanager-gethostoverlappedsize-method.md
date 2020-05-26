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
ms.openlocfilehash: a97009a4ebc834d867dddcc350033c550364ea42
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804749"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize — Metoda
Pobiera rozmiar danych niestandardowych, które Host zamierza dołączyć do żądań we/wy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcbSize`  
 określoną Wskaźnik do liczby bajtów, które powinny być przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR) oprócz rozmiaru `OVERLAPPED` obiektu Win32.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie asynchroniczne wywołania we/wy do interfejsów API platformy Windows przyjmują `OVERLAPPED` obiekt Win32, który zawiera informacje, takie jak położenie wskaźnika pliku. W celu utrzymania stanu aplikacje, które powodują asynchroniczne wywołania we/wy zwykle dodają niestandardowe dane do struktury. `GetHostOverlappedSize`i [IHostIoCompletionManager:: InitializeHostOverlapped —](ihostiocompletionmanager-initializehostoverlapped-method.md) umożliwiają hostowi uwzględnienie takich danych niestandardowych.  
  
 Środowisko CLR wywołuje `GetHostOverlappedSize` metodę w celu określenia rozmiaru danych niestandardowych, które Host zamierza dołączyć do `OVERLAPPED` obiektu.  
  
> [!NOTE]
> `GetHostOverlappedSize`jest wywoływana tylko raz. Dane niestandardowe hosta muszą mieć taki sam rozmiar dla każdego żądania we/wy.  
  
> [!IMPORTANT]
> Rozmiar `OVERLAPPED` samego obiektu nie jest uwzględniony w wartości `pcbSize` .  
  
 Więcej informacji o `OVERLAPPED` strukturze znajduje się w dokumentacji platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager, interfejs](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interfejs](ihostiocompletionmanager-interface.md)
