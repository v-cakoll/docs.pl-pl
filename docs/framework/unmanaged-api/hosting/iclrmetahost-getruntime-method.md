---
title: ICLRMetaHost::GetRuntime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: eb305aaa18fcb8dc63e3090297aabc8defc3a401
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140933"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime — Metoda
Pobiera Interfejs [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który odnosi się do określonej wersji środowiska uruchomieniowego języka wspólnego (CLR). Ta metoda zastępuje funkcję [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) używaną z flagą [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzVersion`  
 podczas Wersja kompilacji .NET Framework przechowywana w metadanych w formacie "v*A*. *B*[. *X*] ". *A*, *B*i *X* to liczby dziesiętne, które odpowiadają wersji głównej, wersji pomocniczej i numer kompilacji.  
  
> [!NOTE]
> Ten parametr musi być zgodny z nazwą katalogu dla .NET Framework wersji, ponieważ pojawia się w obszarze C:\Windows\Microsoft.NET\Framework lub C:\Windows\Microsoft.NET\Framework64.  
  
 Przykładowe wartości to "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" i "v 4.0. *X*", gdzie *x* zależy od zainstalowanego numeru kompilacji. Prefiks "v" jest wymagany.  
  
 `riid`  
 podczas Identyfikator żądanego interfejsu. Obecnie jedyną prawidłową wartością tego parametru jest IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 określoną Wskaźnik do interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który odnosi się do żądanego środowiska uruchomieniowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzVersion` lub `ppRuntime` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda współdziała z starszymi interfejsami, takimi jak interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) i starsze funkcje, takie jak przestarzałe funkcje `CorBindTo*` (zobacz [przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) w interfejsie API hostingu .NET Framework 2,0). Oznacza to, że środowiska uruchomieniowe, które są ładowane ze starszym interfejsem API są widoczne dla nowego interfejsu API, a środowiska uruchomieniowe ładowane z nowym interfejsem API są widoczne dla starszego interfejsu API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
