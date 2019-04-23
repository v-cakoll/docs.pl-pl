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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117433"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure — Metoda
Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy wystąpi awaria określonej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `failure`  
 [in] Jedną z [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości, wskazujący typ awarii, do których chcesz podjąć działania.  
  
 `action`  
 [in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję do wykonania, kiedy wystąpi błąd. Aby uzyskać listę obsługiwanych wartości zobacz sekcję Uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Działanie zasad nie można ustawić dla określonej operacji lub nieprawidłowe zasady akcji została określona dla tej operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko CLR zgłasza wyjątek, gdy go nie powiedzie się do przydzielenia zasobu, takie jak pamięć. `SetActionOnFailure` Zezwalaj hostowi na zastąpienie tego zachowania, określając zasady działanie podejmowane w przypadku awarii. W poniższej tabeli przedstawiono kombinacje [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) i [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które są obsługiwane. (Prefiks FAIL_ pominięto w [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości.)  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|Naruszenie zasad dostępu|CodeContract|  
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
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
