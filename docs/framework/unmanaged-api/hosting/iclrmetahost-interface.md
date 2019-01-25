---
title: ICLRMetaHost — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52b12df9953dbafaeebfe223313288de0e559b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584051"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost — Interfejs
Udostępnia metody, które zwracają określonej wersji środowiska uruchomieniowego języka wspólnego (CLR) na podstawie jego numeru wersji, listę wszystkich zainstalowanych CLRs, listy wszystkie środowiska uruchomieniowe, które są ładowane w określonym procesie, odnajdź wersję środowiska CLR używane do kompilowania zestawu, Zakończ proces Zamknięcie czyste środowisko uruchomieniowe i powiązań dla zapytań dotyczących starszej wersji interfejsu API.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji środowiska CLR, który jest zainstalowany na komputerze.|  
|[EnumerateLoadedRuntimes, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdego środowiska CLR, który jest ładowany w danym procesie. Ta metoda zastępuje [getversionfromprocess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[ExitProcess, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Próbuje zamknięcie wszystkie załadowane środowisk wykonawczych, a następnie kończy proces. Zastępuje [corexitprocess —](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkcji.|  
|[GetRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odnosi się do określonej wersji środowiska CLR. Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.|  
|[GetVersionFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Pobiera zestaw oryginalna wersja programu .NET Framework kompilacji (przechowywany w metadanych) podanej ścieżki pliku. Ta metoda zastępuje [getfileversion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Zwraca interfejs, który reprezentuje środowiska uruchomieniowego, do którego zasady starszych aktywacji została powiązana, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu na [ \<uruchamiania > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis w pliku konfiguracji, przy użyciu bezpośredniego Aktywacja starszych interfejsów API lub przez wywołanie metody [iclrruntimeinfo::bindaslegacyv2runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.|  
|[RequestRuntimeLoadedNotification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Gwarantuje wywołanie zwrotne do wskaźnika określonej funkcji, gdy jest ładowana jako pierwsza wersja środowiska CLR, ale jeszcze nie rozpoczęty. Ta metoda zastępuje [lockclrversion —](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Uwagi  
 Jedynym sposobem, aby pobrać wystąpienie ten interfejs jest wywołanie [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji w następujący sposób:  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
