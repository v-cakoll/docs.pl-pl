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
ms.openlocfilehash: 0dc2f625da7f4e37583f198c8d6dba86f6dcdb10
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805064"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda
Pobiera wskaźnik interfejsu do [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , który reprezentuje listę zestawów, które host oczekuje na załadowanie środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReferenceList`  
 określoną Wskaźnik do adresu zawierającego `ICLRAssemblyReferenceList` listę odwołań do zestawów, które host oczekuje na załadowanie środowiska CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci, aby utworzyć listę odwołań dla żądanego elementu `ICLRAssemblyReferenceList` .|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR rozpoznaje odwołania przy użyciu następującego zestawu wytycznych:  
  
- Najpierw sprawdza listę odwołań do zestawów zwracanych przez `GetNonHostStoreAssemblies` .  
  
- Jeśli zestaw znajduje się na liście, środowisko CLR tworzy je w normalny sposób.  
  
- Jeśli zestaw nie znajduje się na liście, a host dostarczył implementację [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), środowisko CLR wywołuje [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) , aby umożliwić hostowi powiązanie z zestawem.  
  
- W przeciwnym razie środowisko CLR nie zostanie powiązane z zestawem.  
  
 Jeśli host `ppReferenceList` ma wartość null, środowisko CLR najpierw sonduje globalną pamięć podręczną zestawów, wywołuje `ProvideAssembly` , a następnie sonduje bazę aplikacji w celu rozpoznania odwołania do zestawu.  
  
> [!NOTE]
> Po inicjacji, środowisko CLR wywołuje `GetNonHostStoreAssemblies` tylko raz. Metoda nie jest ponownie wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](ihostassemblystore-interface.md)
