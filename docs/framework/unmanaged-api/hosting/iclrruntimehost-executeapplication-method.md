---
title: ICLRRuntimeHost::ExecuteApplication — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
ms.openlocfilehash: 924d032c42dca95b253acea167d55dd6e2b811e5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703336"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication — Metoda
Używany w scenariuszach wdrażania ClickOnce opartych na manifestach, aby określić aplikację, która ma zostać aktywowana w nowej domenie. Aby uzyskać więcej informacji na temat tych scenariuszy, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzAppFullName`  
 podczas Pełna nazwa aplikacji zgodnie z definicją dla <xref:System.ApplicationIdentity> .  
  
 `dwManifestPaths`  
 podczas Liczba ciągów zawartych w `ppwzManifestPaths` tablicy.  
  
 `ppwzManifestPaths`  
 podczas Obowiązkowe. Tablica ciągów zawierająca ścieżki manifestu dla aplikacji.  
  
 `dwActivationData`  
 podczas Liczba ciągów zawartych w `ppwzActivationData` tablicy.  
  
 `ppwzActivationData`  
 podczas Obowiązkowe. Tablica ciągów zawierająca dane aktywacji aplikacji, na przykład część ciągu zapytania w adresie URL dla aplikacji wdrożonych za pośrednictwem sieci Web.  
  
 `pReturnValue`  
 określoną Wartość zwracana z punktu wejścia aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ExecuteApplication`służy do uaktywniania aplikacji ClickOnce w nowo utworzonej domenie aplikacji.  
  
 `pReturnValue`Parametr wyjściowy jest ustawiany na wartość zwracaną przez aplikację. Jeśli podasz wartość null dla, nie `pReturnValue` `ExecuteApplication` powiedzie się, ale nie zwróci wartości.  
  
> [!IMPORTANT]
> Nie wywołuj metody [startowej](iclrruntimehost-start-method.md) przed wywołaniem `ExecuteApplication` metody w celu aktywowania aplikacji opartej na manifeście. Jeśli `Start` Metoda jest wywoływana jako pierwsza, `ExecuteApplication` wywołanie metody zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost, interfejs](iclrruntimehost-interface.md)
- [SetAppDomainManager, metoda](ihostcontrol-setappdomainmanager-method.md)
- [Wskazówki: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce za pomocą Projektanta](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
