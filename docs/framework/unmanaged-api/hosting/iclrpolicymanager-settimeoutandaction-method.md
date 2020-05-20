---
title: ICLRPolicyManager::SetTimeoutAndAction — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: efd30ef04c148d5e098110efcb37e50f143884e4
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703429"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a>ICLRPolicyManager::SetTimeoutAndAction — Metoda
Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasad, którą powinien wykonać środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi operacja.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `operation`  
 podczas Jedna z wartości [EClrOperation —](eclroperation-enumeration.md) , wskazująca na operację, dla której ma zostać ustawiony limit czasu i zasady `action` . Obsługiwane są następujące wartości:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 podczas Nowa wartość limitu czasu (w milisekundach). Wartość NIESKOŃCZONości `operation` nigdy nie przekracza limitu czasu.  
  
 `action`  
 podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję zasad, która powinna zostać podjęta przez środowisko CLR, gdy `operation` wystąpi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nie można ustawić limitu czasu dla określonego elementu `operation` lub podano nieprawidłową wartość dla elementu `action` .|  
  
## <a name="remarks"></a>Uwagi  
 `SetTimeoutAndAction`hermetyzuje możliwości metod [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) i [ICLRPolicyManager:: SetActionOnTimeout —](iclrpolicymanager-setactionontimeout-method.md) i można je wywołać zamiast wywołań sekwencyjnych do tych dwóch metod.  
  
> [!IMPORTANT]
> Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu dla operacji CLR. Zapoznaj się z sekcjami uwagi dla tych dwóch metod w celu uzyskania prawidłowych wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrOperation — Wyliczenie](eclroperation-enumeration.md)
- [EPolicyAction — Wyliczenie](epolicyaction-enumeration.md)
- [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)
- [SetActionOnTimeout, metoda](iclrpolicymanager-setactionontimeout-method.md)
- [ICLRPolicyManager:: SetTimeoutAndAction —](iclrpolicymanager-settimeoutandaction-method.md)
