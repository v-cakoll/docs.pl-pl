---
title: ICLRPolicyManager::SetActionOnTimeout — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 0b8e7dfbe377e60b548003af10fb11392b514030
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703456"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a>ICLRPolicyManager::SetActionOnTimeout — Metoda
Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR), gdy określona operacja przeprowadzi limit czasu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `operation`  
 podczas Jedna z wartości [EClrOperation —](eclroperation-enumeration.md) , wskazująca na operację, dla której ma zostać określona akcja limitu czasu. Obsługiwane są następujące wartości:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `action`  
 podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca akcję zasad, która ma zostać podjęta po przełączeniu operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetActionOnTimeout`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nie można ustawić limitu czasu dla określonego elementu `operation` lub podano nieprawidłową wartość dla elementu `operation` .|  
  
## <a name="remarks"></a>Uwagi  
 Wartość limitu czasu może być domyślnym limitem czasu ustawionym przez środowisko CLR lub wartość określoną przez hosta w wywołaniu metody [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) .  
  
 Nie wszystkie wartości akcji zasad można określić jako zachowanie limitu czasu dla operacji CLR. `SetActionOnTimeout`jest zazwyczaj używany tylko w celu eskalacji zachowań. Na przykład host może określić, że przerwania wątku są włączane do przerwania wątku prosta, ale nie można określić przeciwieństwa. W poniższej tabeli opisano prawidłowe `action` wartości prawidłowych wartości `operation` .  
  
|Wartość dla`operation`|Prawidłowe wartości dla`action`|  
|---------------------------|-------------------------------|  
|OPR_ThreadRudeAbortInNonCriticalRegion<br /><br /> OPR_ThreadRudeAbortInCriticalRegion|- eRudeAbortThread<br />- eUnloadAppDomain<br />- eRudeUnloadAppDomain<br />- eExitProcess<br />- eFastExitProcess<br />- eRudeExitProcess<br />- eDisableRuntime|  
|OPR_AppDomainUnload|- eUnloadAppDomain<br />- eRudeUnloadAppDomain<br />- eExitProcess<br />- eFastExitProcess<br />- eRudeExitProcess<br />- eDisableRuntime|  
|OPR_ProcessExit|- eExitProcess<br />- eFastExitProcess<br />- eRudeExitProcess<br />- eDisableRuntime|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrOperation — Wyliczenie](eclroperation-enumeration.md)
- [EPolicyAction — Wyliczenie](epolicyaction-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)
