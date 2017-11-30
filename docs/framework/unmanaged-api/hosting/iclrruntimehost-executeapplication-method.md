---
title: "ICLRRuntimeHost::ExecuteApplication — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteApplication
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3b43365ad208dae5b28b31cf494de37ca670d791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication — Metoda
Używane w na podstawie manifestu scenariuszy wdrażania ClickOnce do określenia aplikacji do aktywacji w nowej domenie. Aby uzyskać więcej informacji na temat tych scenariuszy, zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment).  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pwzAppFullName`  
 [in] Pełna nazwa aplikacji, zgodnie z definicją <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 [in] Liczbę ciągów zawartych w `ppwzManifestPaths` tablicy.  
  
 `ppwzManifestPaths`  
 [in] Opcjonalne. Tablica ciągów, zawierająca ścieżek manifestu dla aplikacji.  
  
 `dwActivationData`  
 [in] Liczbę ciągów zawartych w `ppwzActivationData` tablicy.  
  
 `ppwzActivationData`  
 [in] Opcjonalne. Tablica ciąg zawierający dane aktywacji aplikacji, takich jak część ciągu zapytania adres URL aplikacje wdrożone za pośrednictwem sieci Web.  
  
 `pReturnValue`  
 [out] Wartość zwrócona z punktu wejścia aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ExecuteApplication`Służy do aktywowania aplikacji ClickOnce w domenie nowo utworzonej aplikacji.  
  
 `pReturnValue` Parametr wyjściowy ma ustawioną wartość zwrócona przez aplikację. Jeśli zostanie podana wartość null dla `pReturnValue`, `ExecuteApplication` nie kończy się niepowodzeniem, ale nie zwraca wartości.  
  
> [!IMPORTANT]
>  Nie wywołuj [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem `ExecuteApplication` metodę, aby aktywować manifest aplikacji. Jeśli `Start` metoda jest wywoływana po pierwsze, `ExecuteApplication` wywołanie metody zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [ICLRRuntimeHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [SetAppDomainManager — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [Wskazówki: Pobieranie zestawów na żądanie przy użyciu interfejsu API przy użyciu narzędzia Projektant wdrażania ClickOnce](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
