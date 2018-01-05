---
title: "ICLRMetaHost — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost
helpviewer_keywords: ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a12635e14b694b361e2877041588d7d9f08a4102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost — Interfejs
Udostępnia metody, które zwraca określoną wersję środowisko uruchomieniowe języka wspólnego (CLR) na podstawie jego numeru wersji, wyświetlić listę wszystkich zainstalowanych CLRs, listy wszystkich środowisk uruchomieniowych, które są ładowane w określonym procesie, wersji środowiska CLR, używanej do kompilacji zestawu, Zakończ proces odnajdywania Zamknięcie czyste środowiska uruchomieniowego i powiązań dla zapytań starszej wersji interfejsu API.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Zwraca wyliczenie, który zawiera prawidłowy [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji środowiska CLR, który jest zainstalowany na komputerze.|  
|[EnumerateLoadedRuntimes, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Zwraca wyliczenie, który zawiera prawidłowy [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdego środowiska CLR, który jest ładowany w danym procesie. Ta metoda zastępuje [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[ExitProcess, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Podejmuje próbę prawidłowe zamknięcie wszystkich załadowanych środowisk uruchomieniowych, a następnie kończy proces. Zastępuje [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkcji.|  
|[GetRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu, który odpowiada określonej wersji środowiska CLR. Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.|  
|[GetVersionFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Pobiera zestawu oryginalna wersja programu .NET Framework kompilacji (przechowywane w metadanych) podanej ścieżki pliku. Ta metoda zastępuje [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Zwraca interfejs, który reprezentuje runtime, do którego zasad aktywacji starszych wersji został powiązany, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<uruchamiania > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis pliku konfiguracji, używając bezpośredniego aktywacji starszych interfejsów API, przez wywołanie [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.|  
|[RequestRuntimeLoadedNotification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Gwarantuje wywołania zwrotnego do wskaźnika funkcji określonej wersji środowiska CLR jest ładowana jako pierwsza, ale jeszcze nie uruchomiono. Ta metoda zastępuje [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Uwagi  
 Jedynym sposobem na pobranie wystąpienia tego interfejsu jest wywołując [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) działają w następujący sposób:  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
