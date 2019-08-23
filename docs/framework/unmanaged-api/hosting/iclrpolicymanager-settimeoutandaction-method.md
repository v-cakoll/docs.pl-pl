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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120dbfdc463a7441cce8ca7d87561998a8e28eda
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916950"
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
 podczas Jedna z wartości [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , wskazująca na operację, dla której ma zostać ustawiony limit czasu `action`i zasady. Obsługiwane są następujące wartości:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 podczas Nowa wartość limitu czasu (w milisekundach). Wartość nieskończoności `operation` nigdy nie przekracza limitu czasu.  
  
 `action`  
 podczas Jedna z wartości [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , wskazująca akcję zasad, która powinna zostać podjęta przez `operation` środowisko CLR, gdy wystąpi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nie można ustawić limitu czasu dla określonego `operation`elementu lub podano nieprawidłową wartość dla `action`elementu.|  
  
## <a name="remarks"></a>Uwagi  
 `SetTimeoutAndAction`hermetyzuje możliwości metod [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) i [ICLRPolicyManager:: SetActionOnTimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) i można je wywołać zamiast wywołań sekwencyjnych do tych dwóch metod.  
  
> [!IMPORTANT]
> Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu dla operacji CLR. Zapoznaj się z sekcjami uwagi dla tych dwóch metod w celu uzyskania prawidłowych wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MSCorEE. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrOperation, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnTimeout, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [ICLRPolicyManager:: SetTimeoutAndAction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
