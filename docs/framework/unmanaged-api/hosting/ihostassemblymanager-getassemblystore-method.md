---
title: IHostAssemblyManager::GetAssemblyStore — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805071"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a>IHostAssemblyManager::GetAssemblyStore — Metoda
Pobiera wskaźnik interfejsu do [IHostAssemblyStore](ihostassemblystore-interface.md) , który reprezentuje listę zestawów załadowanych przez hosta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssemblyStore`  
 określoną Wskaźnik funkcji do `IHostAssemblyStore` wystąpienia lub wartość null, Jeśli host nie implementuje `IHostAssemblyStore` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetAssemblyStore`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|Host nie oferuje implementacji programu `IHostAssemblyStore` .|  
  
## <a name="remarks"></a>Uwagi  
 `IHostAssemblyStore`dostarcza metody, które umożliwiają hostowi powiązanie z zestawami i modułami niezależnie od środowiska CLR. Hosty zwykle zapewniają magazyny zestawów pozwalające ładować zestawy z formatów innych niż system plików.  
  
> [!NOTE]
> Jeśli host nie jest zaimplementowany `IHostAssemblyStore` , `GetAssemblyStore` powinien zwrócić wartość HRESULT o wartości E_NOINTERFACE i powinien mieć ustawioną wartość `ppAssemblyStore` null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IHostAssemblyManager, interfejs](ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](ihostassemblystore-interface.md)
