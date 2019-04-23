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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f988084310b920907bb7f212e7d40ca0d1c91db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197519"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a>ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda
Określa zachowanie środowiska uruchomieniowego języka wspólnego (CLR), po wystąpieniu nieobsługiwanego wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `policy`  
 [in] Jedną z [eclrunhandledexception —](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) wartości, wskazującą, czy zachowanie jest ustawiony przez środowisko CLR lub hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetUnhandledExceptionPolicy` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko CLR jest ostatnim Obsługa wszystkie nieobsłużone wyjątki, a jej zachowanie domyślne jest zrywać proces. Hosta można zmienić to zachowanie przez ustawienie `policy` wartość eHostDeterminedPolicy. Ta wartość umożliwia hosta zaimplementować własną zachowanie domyślne, podobnie jak w przypadku wcześniejszych wersji środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrUnhandledException, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
