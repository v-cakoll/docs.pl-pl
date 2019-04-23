---
title: IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ae9a8e9e26f05675611ac4c6acd8ecfe5704b0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104458"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda
Pobiera wskaźnik interfejsu do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, które hosta oczekuje, że środowisko uruchomieniowe języka wspólnego (CLR) do załadowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReferenceList`  
 [out] Wskaźnik na adres `ICLRAssemblyReferenceList` zawierający listę odwołania do zestawów, do których host oczekuje środowiska CLR do załadowania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci była dostępna do utworzenia listy odwołań dla żądanego `ICLRAssemblyReferenceList`.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR rozwiązuje odwołań za pomocą zestawu następujących wytycznych:  
  
-   Po pierwsze, konsultacje dotyczące listy odwołania do zestawów, zwracany przez `GetNonHostStoreAssemblies`.  
  
-   Jeśli zestaw zostanie wyświetlone na liście, środowisko CLR zwykle wiąże do niego.  
  
-   Jeśli zestaw nie ma na liście, a host ma pod warunkiem implementację [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR wywołuje [ihostassemblystore::provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) zezwalająca na hoście do dostarczania zestaw można powiązać.  
  
-   W przeciwnym razie środowisko CLR nie może powiązać do zestawu.  
  
 Jeśli host ustawia `ppReferenceList` na wartość null, sondy pierwszego środowiska CLR wywołuje global assembly cache `ProvideAssembly`, a następnie sondy podstawy aplikacji, aby rozwiązać odwołania do zestawu.  
  
> [!NOTE]
>  Po zainicjowaniu, środowisko CLR wywołuje `GetNonHostStoreAssemblies` tylko raz. Metoda nie jest ponownie wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
