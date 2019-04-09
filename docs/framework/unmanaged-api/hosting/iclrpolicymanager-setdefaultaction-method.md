---
title: ICLRPolicyManager::SetDefaultAction — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d339fbadc3260d20fac848ad7f1a9031c3443aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154664"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a>ICLRPolicyManager::SetDefaultAction — Metoda
Określa akcję zasad, które środowisko uruchomieniowe języka wspólnego (CLR) należy wykonać po wystąpieniu określonej operacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `operation`  
 [in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazując akcji, dla których CLR można dostosować zachowanie.  
  
 `action`  
 [in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazując działanie zasad CLR powinien wykonać, gdy `operation` występuje.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetDefaultAction` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nieprawidłowy `action` określono `operation`, lub podano nieprawidłową wartość dla `operation`.|  
  
## <a name="remarks"></a>Uwagi  
 Nie wszystkie wartości akcji zasad można określić jako zachowanie domyślne w operacjach aparatu CLR. `SetDefaultAction` Zazwyczaj można tylko przekazać zachowanie. Na przykład host można określić, czy przerwanie wątku przekształcone prosta wątku przerwań, ale nie można określić odwrotny. W poniższej tabeli opisano prawidłowe `action` wartości dla każdego możliwe `operation` wartość.  
  
|Wartość `operation`|Prawidłowe wartości `action`|  
|---------------------------|-------------------------------|  
|OPR_ThreadAbort|-eAbortThread<br />-eRudeAbortThread<br />-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_ThreadRudeAbortInNonCriticalRegion<br /><br /> OPR_ThreadRudeAbortInCriticalRegion|-eRudeAbortThread<br />-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_AppDomainUnload|-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_AppDomainRudeUnload|-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_ProcessExit|-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_FinalizerRun|-eNoAction<br />-eAbortThread<br />-eRudeAbortThread<br />-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrOperation — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
