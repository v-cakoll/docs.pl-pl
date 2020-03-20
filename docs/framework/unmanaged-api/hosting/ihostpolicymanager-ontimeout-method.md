---
title: IHostPolicyManager::OnTimeout — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178002"
---
# <a name="ihostpolicymanagerontimeout-method"></a>IHostPolicyManager::OnTimeout — Metoda
Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma zamiar podjąć akcję określoną przez wywołanie [do metody ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na limit czasu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `operation`  
 [w] Jedna z wartości [EClrOperation,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wskazująca rodzaj operacji, która się przesunęła.  
  
 `action`  
 [w] Jedną z wartości [EPolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wskazując akcję, którą clr podejmuje w odpowiedzi na limit czasu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OnTimeout`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [EClrOperation — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
