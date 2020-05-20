---
title: ICLRRuntimeHost::SetHostControl — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 8d6a4e1ca934c748352b0c4f5120536a4dd24e0b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703960"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl — Metoda
Ustawia wskaźnik interfejsu, który może być używany przez środowisko uruchomieniowe języka wspólnego (CLR), aby uzyskać implementację [interfejsu IHostControl](ihostcontrol-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pHostControl`  
 podczas Wskaźnik interfejsu do implementacji [interfejsu IHostControl](ihostcontrol-interface.md)hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetHostControl`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_CLR_ALREADY_STARTED|Środowisko CLR zostało już zainicjowane.|  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać `SetHostControl` przed zainicjowaniem środowiska CLR, czyli przed wywołaniem [metody Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub użyciem dowolnego [interfejsu metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). Zaleca się wywołanie `SetHostControl` natychmiast po wywołaniu [funkcji CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [funkcji CorBindToRuntimeEx](corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeHost, interfejs](iclrruntimehost-interface.md)
- [IHostControl, interfejs](ihostcontrol-interface.md)
