---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 7fa02c4c79da118543117aada7d1b9cca09c4cae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703403"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a>ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda
Określa zachowanie środowiska uruchomieniowego języka wspólnego (CLR) w przypadku wystąpienia nieobsługiwanego wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `policy`  
 podczas Jedna z wartości [EClrUnhandledException —](eclrunhandledexception-enumeration.md) , wskazująca, czy zachowanie jest ustawione przez środowisko CLR czy hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetUnhandledExceptionPolicy`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko CLR jest ostatnim programem obsługi dla wszystkich nieobsłużonych wyjątków, a jego domyślne zachowanie polega na rozdzieleniu tego procesu. Na hoście można zmienić to zachowanie, ustawiając `policy` wartość na eHostDeterminedPolicy. Ta wartość umożliwia hostowi wdrożenie własnego zachowania domyślnego, tak jak w przypadku wcześniejszych wersji środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrUnhandledException — Wyliczenie](eclrunhandledexception-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)
- [IHostPolicyManager, interfejs](ihostpolicymanager-interface.md)
