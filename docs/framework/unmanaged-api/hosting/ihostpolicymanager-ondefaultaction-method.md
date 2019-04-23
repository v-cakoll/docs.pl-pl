---
title: IHostPolicyManager::OnDefaultAction — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45167a2b358b9a7a39390c07f552aa3f3dabce4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108657"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a>IHostPolicyManager::OnDefaultAction — Metoda
Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma mieć domyślną akcję, która została ustawiona przez wywołanie [iclrpolicymanager::setdefaultaction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metody w odpowiedzi na przerwanie wątku lub <xref:System.AppDomain> zwolnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `operation`  
 [in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazujący rodzaj zdarzeń, do którego odpowiada środowiska CLR.  
  
 `action`  
 [in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazując akcję, która zajmuje środowisko CLR w odpowiedzi na zdarzenie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OnDefaultAction` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetwarzania wywołania. pomyślnie|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrOperation, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
