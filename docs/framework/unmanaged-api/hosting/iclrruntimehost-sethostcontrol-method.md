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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8400f615f2fcdb847b398806fe4219ae709beebe
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495302"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl — Metoda
Ustawia wskaźnik interfejsu, używanego przez środowisko uruchomieniowe języka wspólnego (CLR) można pobrać wdrożenia hosta [ihostcontrol — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pHostControl`  
 [in] Wskaźnik interfejsu do wdrożenia hosta [ihostcontrol — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetHostControl` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_CLR_ALREADY_STARTED|Środowisko CLR został już zainicjowany.|  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać `SetHostControl` przed środowisko CLR jest inicjowany, oznacza to, zanim wywołasz [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub korzystających z [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). Zalecane jest, należy wywołać `SetHostControl` natychmiast po wywołaniu [corbindtocurrentruntime — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [corbindtoruntimeex — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
