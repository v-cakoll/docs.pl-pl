---
title: ICLRPolicyManager::SetActionOnFailure — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 143052febe136e969987c35bc06f6c3b3356aedf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140784"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure — Metoda
Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku wystąpienia określonego błędu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `failure`  
 podczas Jedna z wartości [EClrFailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) , wskazująca typ błędu, dla którego należy podjąć działania.  
  
 `action`  
 podczas Jedna z wartości [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , wskazująca akcję do wykonania w przypadku wystąpienia błędu. Aby zapoznać się z listą obsługiwanych wartości, zobacz sekcję Uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nie można ustawić akcji zasad dla określonej operacji lub określono nieprawidłową akcję zasad dla tej operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko CLR zgłasza wyjątek, gdy nie może przydzielić zasobu, takiego jak pamięć. `SetActionOnFailure` umożliwia hostowi przesłonięcie tego zachowania, określając akcję zasad, która ma zostać podjęta po awarii. W poniższej tabeli przedstawiono kombinacje obsługiwanych wartości [EClrFailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) i [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) . (Prefiks FAIL_ został pominięty z wartości [EClrFailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) ).  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||Brak||  
|eThrowException|X|X||||Brak||  
|`eAbortThread`|X|X||||Brak|X|  
|`eRudeAbortThread`|X|X||||Brak|X|  
|`eUnloadAppDomain`|X|X||X||Brak|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|Brak|X|  
|`eExitProcess`|X|X||X|X|Brak|X|  
|eFastExitProcess|X|X||X|X|Brak||  
|`eRudeExitProcess`|X|X|X|X|X|Brak||  
|`eDisableRuntime`|X|X|X|X|X|Brak||  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
