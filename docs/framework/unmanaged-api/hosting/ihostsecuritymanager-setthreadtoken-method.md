---
title: IHostSecurityManager::SetThreadToken — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf29b906d524138fdd78b7a4f0286d1c59adc8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622129"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a>IHostSecurityManager::SetThreadToken — Metoda
Ustawia obsługi do aktualnie wykonywany wątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hToken`  
 [in] Dojście do tokenu, aby ustawić aktualnie wykonywany wątek.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetThreadToken` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostSecurityManager::SetThreadToken` zachowuje się podobnie do odpowiednich funkcji Win32 o takiej samej nazwie, z tą różnicą, że funkcja Win32 pozwala na obiekt wywołujący, aby przekazać dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::SetThreadToken` tylko z aktualnie wykonywany Wątek można skojarzyć token.  
  
 `HANDLE` Typ nie jest zgodny z COM; oznacza to, jego rozmiar jest specyficzne dla systemu operacyjnego i potrzebny organizowanie niestandardowe. W związku z tym ten token jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
