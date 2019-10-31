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
ms.openlocfilehash: bb760f4923cc3530a28bc68180db743ee468b51d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140914"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost — Interfejs
Dostarcza metody, które zwracają określoną wersję środowiska uruchomieniowego języka wspólnego (CLR) na podstawie jego numeru wersji, wyświetla listę wszystkich zainstalowanych CLRs, wyświetla listę wszystkich środowisk uruchomieniowych ładowanych w określonym procesie, Odnajdywanie wersji środowiska CLR użytej do skompilowania zestawu, wyjście z procesu przy zamykaniu czystego środowiska uruchomieniowego i przeszukiwaniu starszych powiązań interfejsu API.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) dla każdej wersji środowiska CLR zainstalowanej na komputerze.|  
|[EnumerateLoadedRuntimes, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) dla każdego środowiska CLR, które jest załadowane w danym procesie. Ta metoda zastępuje [GetVersionFromProcess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[ExitProcess, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Próbuje bezpiecznie zamknąć wszystkie ładowane środowiska uruchomieniowe, a następnie kończy proces. Zastępuje funkcję [CorExitProcess —](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) .|  
|[GetRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Pobiera Interfejs [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który odpowiada określonej wersji środowiska CLR. Ta metoda zastępuje funkcję [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) używaną z flagą [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .|  
|[GetVersionFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Pobiera oryginalną wersję kompilacji .NET Framework zestawu (przechowywaną w metadanych), uwzględniając ścieżkę pliku. Ta metoda zastępuje [GetFileVersion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Zwraca interfejs reprezentujący środowisko uruchomieniowe, do którego powiązano starsze zasady aktywacji, na przykład przy użyciu atrybutu `useLegacyV2RuntimeActivationPolicy` w wpisie pliku konfiguracji [elementu > start\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , przez bezpośrednie użycie starszych interfejsów API aktywacji lub przez Wywoływanie metody [ICLRRuntimeInfo:: BindAsLegacyV2Runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .|  
|[RequestRuntimeLoadedNotification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Gwarantuje wywołanie zwrotne do określonego wskaźnika funkcji podczas pierwszego ładowania wersji środowiska CLR, ale nie zostało jeszcze uruchomione. Ta metoda zastępuje [LockClrVersion —](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Uwagi  
 Jedynym sposobem, aby uzyskać wystąpienie tego interfejsu, jest wywołanie funkcji [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) w następujący sposób:  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
