---
title: ICLRSyncManager::CreateRWLockOwnerIterator — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: 9eace3e7330d3f8c0c9762e0b1b456ad1bf8a3ac
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763192"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator — Metoda
Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) tworzy iterator dla hosta do użycia w celu określenia zestawu zadań oczekujących na blokadę modułu odczytującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 podczas Plik cookie skojarzony z wymaganą blokadą czytnika czytników.  
  
 `pIterator`  
 określoną Wskaźnik do iteratora, który może być przesłany do metod [GetRWLockOwnerNext —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) i [DeleteRWLockOwnerIterator —](iclrsyncmanager-deleterwlockowneriterator-method.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`został wywołany w wątku, w którym aktualnie działa kod zarządzany.|  
  
## <a name="remarks"></a>Uwagi  
 Hosty zwykle wywołują `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` metody,, i `GetRWLockOwnerNext` podczas wykrywania zakleszczenia. Host jest odpowiedzialny za zapewnienie, że blokada czytnika czytników jest nadal prawidłowa, ponieważ środowisko CLR nie podejmuje próby utrzymania aktywności blokady czytnika. Dla hosta jest dostępnych kilka strategii zapewniających prawidłowość blokady:  
  
- Host może blokować wywołania wydania na blokadzie czytnika czytników (na przykład [IHostSemaphore:: ReleaseSemaphore —](ihostsemaphore-releasesemaphore-method.md)), a jednocześnie upewniając się, że ten blok nie powoduje zakleszczenia.  
  
- Host może zablokować wyjście przed oczekiwaniem na obiekt zdarzenia skojarzony z blokadą modułu odczytującego czytnika i ponownie upewniając się, że ten blok nie powoduje zakleszczenia.  
  
> [!NOTE]
> `CreateRWLockOwnerIterator`musi być wywoływana tylko w wątkach, które aktualnie wykonuje kod niezarządzany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
