---
title: IHostControl::GetHostManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: 25e931ec17cad3508d548fb4ca7e53b0ade3f119
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804953"
---
# <a name="ihostcontrolgethostmanager-method"></a>IHostControl::GetHostManager — Metoda
Pobiera wskaźnik interfejsu do implementacji hosta interfejsu z określonym `IID` .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 podczas `IID`Interfejs, który jest wysyłany przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
 `ppObject`  
 określoną Wskaźnik do interfejsu zaimplementowanego przez hosta lub wartość null, Jeśli host nie obsługuje tego interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetHostManager`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Żądana `IID` jest nieprawidłowa.|  
|E_NOINTERFACE|Żądany interfejs nie jest obsługiwany.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wysyła zapytanie do hosta, aby określić, czy obsługuje jeden lub więcej z następujących interfejsów:  
  
- [IHostMemoryManager](ihostmemorymanager-interface.md)  
  
- [IHostTaskManager](ihosttaskmanager-interface.md)  
  
- [IHostThreadPoolManager](ihostthreadpoolmanager-interface.md)  
  
- [IHostIoCompletionManager](ihostiocompletionmanager-interface.md)  
  
- [IHostSyncManager](ihostsyncmanager-interface.md)  
  
- [IHostAssemblyManager](ihostassemblymanager-interface.md)  
  
- [IHostGCManager](ihostgcmanager-interface.md)  
  
- [IHostPolicyManager](ihostpolicymanager-interface.md)  
  
- [IHostSecurityManager](ihostsecuritymanager-interface.md)  
  
 Jeśli host obsługuje określony interfejs, ustawia on `ppObject` jego implementację. W przeciwnym razie ustawia `ppObject` wartość null.  
  
 Środowisko CLR nie wywołuje `Release` menedżerów hostów nawet po jego zamknięciu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IHostControl, interfejs](ihostcontrol-interface.md)
