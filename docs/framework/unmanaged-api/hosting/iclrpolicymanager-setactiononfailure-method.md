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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504111"
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
 Domyślnie środowisko CLR zgłasza wyjątek, gdy nie może przydzielić zasobu, takiego jak pamięć. `SetActionOnFailure`umożliwia hostowi przesłonięcie tego zachowania przez określenie akcji zasad, która ma zostać podjęta po awarii. W poniższej tabeli przedstawiono kombinacje obsługiwanych wartości [EClrFailure —](eclrfailure-enumeration.md) i [EPolicyAction —](epolicyaction-enumeration.md) . (Prefiks FAIL_ został pominięty z wartości [EClrFailure —](eclrfailure-enumeration.md) ).  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|Witryna StackOverflow|AccessViolation|CodeContract|  
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
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure — Wyliczenie](eclrfailure-enumeration.md)
- [EPolicyAction — Wyliczenie](epolicyaction-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)
