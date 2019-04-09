---
title: IHostTaskManager::SetLocale — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79d4c5b2b2bbe821ff546324fd3af04cb3472e4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149828"
---
# <a name="ihosttaskmanagersetlocale-method"></a>IHostTaskManager::SetLocale — Metoda
Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) została zmieniona, ustawienia regionalne lub kultury na aktualnie przeprowadzane zadanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lcid`  
 [in] Wartość identyfikatora ustawień regionalnych, który jest mapowany do nowo przypisanej geograficzne kultury i języka.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetLocale` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Host nie zezwala na kodu zarządzanego użytkownika do modyfikowania ustawień regionalnych.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe wywołuje `SetLocale` po wartości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwość zostanie zmieniony przez kod zarządzany. Ta metoda zapewnia możliwość hosta do wykonywania jakichkolwiek mechanizmów środowiska użytkownika, który może mieć do synchronizacji ustawień regionalnych. Jeśli host nie zezwala na ustawienia regionalne, które można zmienić z poziomu kodu zarządzanego lub nie implementuje mechanizm do synchronizowania ustawień regionalnych, powinna zwrócić E_NOTIMPL z tej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [SetUILocale, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
