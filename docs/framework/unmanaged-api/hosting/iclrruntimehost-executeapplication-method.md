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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ce7e9ff4041abd1e89330bd3a565b755875d3b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194230"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication — Metoda
Używane w oparte na manifeście scenariusze wdrażania technologii ClickOnce do określenia aplikacji zostanie uaktywniony w nowej domenie. Aby uzyskać więcej informacji na temat tych scenariuszy, zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Pełna nazwa aplikacji, zgodnie z definicją <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 [in] Liczbę ciągów zawartych w `ppwzManifestPaths` tablicy.  
  
 `ppwzManifestPaths`  
 [in] Opcjonalnie. Tablica ciągu, który zawiera ścieżki manifestu dla aplikacji.  
  
 `dwActivationData`  
 [in] Liczbę ciągów zawartych w `ppwzActivationData` tablicy.  
  
 `ppwzActivationData`  
 [in] Opcjonalnie. Tablica ciągu, który zawiera dane aktywacji aplikacji, takich jak część ciągu zapytania adresu URL dla aplikacji wdrożonych w sieci Web.  
  
 `pReturnValue`  
 [out] Wartość zwrócona z punktu wejścia aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ExecuteApplication` Służy do aktywowania aplikacji ClickOnce w domenie nowo utworzonej aplikacji.  
  
 `pReturnValue` Parametr wyjściowy jest ustawiona na wartość zwracaną przez aplikację. Jeśli podasz wartość null dla `pReturnValue`, `ExecuteApplication` nie kończy się niepowodzeniem, ale nie zwraca wartości.  
  
> [!IMPORTANT]
>  Nie wywołuj [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem `ExecuteApplication` metodę, aby aktywować manifestu aplikacji. Jeśli `Start` najpierw jest wywoływana metoda `ExecuteApplication` wywołania metody zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [SetAppDomainManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [Przewodnik: Pobieranie zestawów na żądanie przy użyciu interfejsu API wdrażania ClickOnce za pomocą Projektanta](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
