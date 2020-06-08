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
ms.openlocfilehash: bb7c3659930f308328cba121c06a88cb6a95eb26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504163"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost — Interfejs
Dostarcza metody, które zwracają określoną wersję środowiska uruchomieniowego języka wspólnego (CLR) na podstawie jego numeru wersji, wyświetla listę wszystkich zainstalowanych CLRs, wyświetla wszystkie środowiska uruchomieniowe, które są ładowane w określonym procesie, wykrywają wersję środowiska CLR używaną do kompilowania zestawu, opuszczają proces z zamknięciem czystego środowiska uruchomieniowego i powiążą się z kwerendą ze starszej wersji interfejsu API.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes, metoda](iclrmetahost-enumerateinstalledruntimes-method.md)|Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) dla każdej wersji środowiska CLR zainstalowanej na komputerze.|  
|[EnumerateLoadedRuntimes, metoda](iclrmetahost-enumerateloadedruntimes-method.md)|Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) dla każdego środowiska CLR, które jest załadowane w danym procesie. Ta metoda zastępuje [GetVersionFromProcess —](getversionfromprocess-function.md).|  
|[ExitProcess — Metoda](iclrmetahost-exitprocess-method.md)|Próbuje bezpiecznie zamknąć wszystkie ładowane środowiska uruchomieniowe, a następnie kończy proces. Zastępuje funkcję [CorExitProcess —](corexitprocess-function.md) .|  
|[GetRuntime, metoda](iclrmetahost-getruntime-method.md)|Pobiera Interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , który odpowiada określonej wersji środowiska CLR. Ta metoda zastępuje funkcję [CorBindToRuntimeEx](corbindtoruntimeex-function.md) używaną z flagą [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .|  
|[GetVersionFromFile, metoda](iclrmetahost-getversionfromfile-method.md)|Pobiera oryginalną wersję kompilacji .NET Framework zestawu (przechowywaną w metadanych), uwzględniając ścieżkę pliku. Ta metoda zastępuje [GetFileVersion —](getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding, metoda](iclrmetahost-querylegacyv2runtimebinding-method.md)|Zwraca interfejs reprezentujący środowisko uruchomieniowe, do którego powiązano starsze zasady aktywacji, na przykład przy użyciu `useLegacyV2RuntimeActivationPolicy` atrybutu w wpisie pliku konfiguracji [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md) , bezpośrednio wykorzystując starsze interfejsy API aktywacji lub wywołując metodę [ICLRRuntimeInfo:: BindAsLegacyV2Runtime —](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .|  
|[RequestRuntimeLoadedNotification, metoda](iclrmetahost-requestruntimeloadednotification-method.md)|Gwarantuje wywołanie zwrotne do określonego wskaźnika funkcji podczas pierwszego ładowania wersji środowiska CLR, ale nie zostało jeszcze uruchomione. Ta metoda zastępuje [LockClrVersion —](lockclrversion-function.md)|  
  
## <a name="remarks"></a>Uwagi  
 Jedynym sposobem, aby uzyskać wystąpienie tego interfejsu, jest wywołanie funkcji [CLRCreateInstance](clrcreateinstance-function.md) w następujący sposób:  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
