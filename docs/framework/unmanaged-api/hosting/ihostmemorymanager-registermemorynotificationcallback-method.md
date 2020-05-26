---
title: IHostMemoryManager::RegisterMemoryNotificationCallback — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 0c20df85560f715e829fe02be599788854fcb0f1
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804479"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback — Metoda
Rejestruje wskaźnik do funkcji wywołania zwrotnego, którą Host wywołuje, aby powiadomić środowisko uruchomieniowe języka wspólnego (CLR) o bieżącym obciążeniu pamięci na komputerze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 podczas Wskaźnik interfejsu do wystąpienia [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) , który jest implementowany przez środowisko CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ `ICLRMemoryNotificationCallback` Interfejs definiuje tylko jedną metodę ([ICLRMemoryNotificationCallback:: OnMemoryNotification —](iclrmemorynotificationcallback-onmemorynotification-method.md)), a ponieważ `pCallback` jest wskaźnikiem do `ICLRMemoryNotificationCallback` wystąpienia dostarczonego przez środowisko CLR, rejestracja jest skuteczna dla samej funkcji wywołania zwrotnego. Host wywołuje `OnMemoryNotification` , aby zgłosić warunki ciśnienia pamięci zamiast używać standardowej `CreateMemoryResourceNotification` funkcji Win32. Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.  
  
> [!NOTE]
> Wywołania `OnMemoryNotification` nigdy nie blokują. Zawsze są zwracane natychmiast.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRMemoryNotificationCallback — Interfejs](iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager, interfejs](ihostmemorymanager-interface.md)
