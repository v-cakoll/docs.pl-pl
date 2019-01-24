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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3554d351512f48aad65872dd9ae82d084552d518
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600248"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator — Metoda
Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) Utwórz iterator dla hosta na potrzeby określania zestawu zadań, oczekiwania na blokadę zapisu czytnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cookie`  
 [in] Plik cookie skojarzonego z blokadą żądany czytnik składnika zapisywania.  
  
 `pIterator`  
 [out] Wskaźnik do iteratora, który może być przekazywany do [getrwlockownernext —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) i [deleterwlockowneriterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator` został wywołany w wątku, który jest obecnie uruchomiona kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Hosty zwykle wywołują `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, i `GetRWLockOwnerNext` metody podczas wykrywania zakleszczeń. Host jest odpowiedzialny za zapewnienie, że czytnik blokadę jest nadal ważny, CLR sprawia, że próba podtrzymywania czytnika blokadę. Kilka strategii są dostępne dla hosta zapewnić poprawność blokady:  
  
-   Hosta można zablokować wywołań wersji na blokadę reader (na przykład [ihostsemaphore::releasesemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) przy jednoczesnym zapewnieniu, że ten blok nie spowoduje zakleszczenia.  
  
-   Host może zablokować opuszczenia oczekiwanie na obiekt zdarzenia skojarzone z czytnika blokadę ponownie zapewnienie, że ten blok nie spowoduje zakleszczenia.  
  
> [!NOTE]
>  `CreateRWLockOwnerIterator` musi zostać wywołany tylko na wątki, które są aktualnie wykonuje kod niezarządzany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
