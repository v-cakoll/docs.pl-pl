---
title: IHostControl::SetAppDomainManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 74ffc5c92402808ae566d7cb014d9d920c384ae8
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804948"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager — Metoda
Powiadamia hosta o utworzeniu domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainID`  
 podczas Liczbowy identyfikator wybranego elementu <xref:System.AppDomain> .  
  
 `pUnkAppDomainManager`  
 podczas Wskaźnik do <xref:System.AppDomainManager> obiektu, który jest implementowany przez hosta `IUnknown` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.AppDomainManager>Zapewnia host z mechanizmem ładowania do kodu zarządzanego i kontrolowania tworzenia i ustawień każdego z nich <xref:System.AppDomain> . <xref:System.AppDomainManager>Jest ładowany do każdego <xref:System.AppDomain> , kiedy <xref:System.AppDomain> jest tworzony. W przypadku wybrania tej opcji środowisko CLR powiadamia hosta o utworzeniu domeny aplikacji przez ustawienie wartości `pUnkAppDomainManager` parametru.  
  
 We wdrożeniu `SetAppDomainManager` metody, host może ustawić nazwę zestawu i typ dla Menedżera domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl, interfejs](ihostcontrol-interface.md)
