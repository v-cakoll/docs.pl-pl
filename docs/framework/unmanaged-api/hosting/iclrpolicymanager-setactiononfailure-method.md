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
ms.openlocfilehash: fb2ecc80f272a3fc9b63b20c5956e7a28f117784
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703461"
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
 podczas Jedna z wartości [EClrFailure —](eclrfailure-enumeration.md) , wskazująca typ błędu, dla którego należy podjąć działania.  
  
 `action`  
 podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję do wykonania w przypadku wystąpienia błędu. Aby zapoznać się z listą obsługiwanych wartości, zobacz sekcję Uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nie można ustawić akcji zasad dla określonej operacji lub określono nieprawidłową akcję zasad dla tej operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko CLR zgłasza wyjątek, gdy nie może przydzielić zasobu, takiego jak pamięć. `SetActionOnFailure`umożliwia hostowi przesłonięcie tego zachowania przez określenie akcji zasad, która ma zostać podjęta po awarii. W poniższej tabeli przedstawiono kombinacje obsługiwanych wartości [EClrFailure —](eclrfailure-enumeration.md) i [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) . (Prefiks FAIL_ został pominięty z wartości [EClrFailure —](eclrfailure-enumeration.md) ).  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|Witryna StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||Nie dotyczy||  
|eThrowException|X|X||||Nie dotyczy||  
|`eAbortThread`|X|X||||Nie dotyczy|X|  
|`eRudeAbortThread`|X|X||||Nie dotyczy|X|  
|`eUnloadAppDomain`|X|X||X||Nie dotyczy|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|Nie dotyczy|X|  
|`eExitProcess`|X|X||X|X|Nie dotyczy|X|  
|eFastExitProcess|X|X||X|X|Nie dotyczy||  
|`eRudeExitProcess`|X|X|X|X|X|Nie dotyczy||  
|`eDisableRuntime`|X|X|X|X|X|Nie dotyczy||  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure — Wyliczenie](eclrfailure-enumeration.md)
- [EPolicyAction — Wyliczenie](epolicyaction-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)
