---
title: IHostSyncManager::CreateRWLockWriterEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: f00d166541f7955516e9d5c1dce2a4342c08ad0a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803146"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a>IHostSyncManager::CreateRWLockWriterEvent — Metoda
Tworzy obiekt zdarzenia autoresetowania dla implementacji blokady składnika zapisywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 podczas Plik cookie, który ma zostać skojarzony ze zdarzeniem resetowania.  
  
 `ppEvent`  
 określoną Wskaźnik do adresu wystąpienia [IHostAutoEvent](ihostautoevent-interface.md) lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateRWLockWriterEvent`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje `CreateRWLockWriterEvent` metodę, aby uzyskać odwołanie do wystąpienia, `IHostAutoEvent` które ma być używane w jego implementacji blokady składnika zapisywania. Host może użyć określonego pliku cookie, aby określić, które zadania oczekują na blokadę, wywołując metody iteracji interfejsu [ICLRSyncManager](iclrsyncmanager-interface.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)
- [IHostAutoEvent — Interfejs](ihostautoevent-interface.md)
- [IHostManualEvent, interfejs](ihostmanualevent-interface.md)
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
