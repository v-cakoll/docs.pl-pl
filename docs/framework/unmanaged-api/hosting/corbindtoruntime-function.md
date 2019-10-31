---
title: CorBindToRuntime — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138307"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime — Funkcja
Umożliwia niezarządzanym hostom ładowanie środowiska uruchomieniowego języka wspólnego (CLR) do procesu.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszVersion`  
 podczas Ciąg opisujący wersję środowiska CLR, które chcesz załadować.  
  
 Numer wersji w .NET Framework składa się z czterech części oddzielonych kropkami: *główna. pomocnicza. kompilacja. poprawka*. Ciąg przesłany jako `pwszVersion` musi rozpoczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v 1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z instrukcją zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie podkładka uruchamiania szacuje `pwszVersion` względem instrukcji zasad i ładuje najnowszą wersję środowiska uruchomieniowego, która jest zgodna z żądaną wersją. Host może zmusić podkładkę do pominięcia oceny zasad i załadowania dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości `STARTUP_LOADER_SAFEMODE` parametru `flags`, zgodnie z poniższym opisem.  
  
 Jeśli obiekt wywołujący określa wartość null dla `pwszVersion`, zostanie załadowana Najnowsza wersja środowiska uruchomieniowego. Przekazanie wartości null powoduje, że host nie kontroluje, która wersja środowiska uruchomieniowego jest załadowana. Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby Host dostarczał określoną wersję do załadowania.  
  
 `pwszBuildFlavor`  
 podczas Ciąg określający, czy załadować serwer lub kompilację stacji roboczej środowiska CLR. Prawidłowe wartości to `svr` i `wks`. Kompilacja serwera jest zoptymalizowana pod kątem wykorzystania wielu procesorów na potrzeby wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.  
  
 Jeśli `pwszBuildFlavor` ma wartość null, zostanie załadowana kompilacja stacji roboczej. W przypadku uruchamiania na komputerze z jednym procesorem kompilacja stacji roboczej jest zawsze ładowana, nawet jeśli `pwszBuildFlavor` jest ustawiona na `svr`. Jeśli jednak `pwszBuildFlavor` jest ustawiona na `svr` i zostanie określone współbieżne wyrzucanie elementów bezużytecznych (zobacz opis parametru `flags`), kompilacja serwera zostanie załadowana.  
  
 `rclsid`  
 podczas `CLSID` klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) . Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 podczas `IID` żądanego interfejsu z `rclsid`. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 określoną Zwrócony wskaźnik interfejsu do `riid`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pwszVersion` określa wersję środowiska uruchomieniowego, która nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT równą CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontekst wykonywania i przepływ tożsamości systemu Windows  
 W wersji 1 środowiska CLR obiekt <xref:System.Security.Principal.WindowsIdentity> nie przepływów między punktami asynchronicznymi, takimi jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza. W wersji 2,0 środowiska CLR obiekt <xref:System.Threading.ExecutionContext> otacza niektóre informacje o aktualnie wykonywanym wątku i przepływa go w dowolnym punkcie asynchronicznym, ale nie między granicami domeny aplikacji. Podobnie obiekt <xref:System.Security.Principal.WindowsIdentity> jest również przepływów w każdym punkcie asynchronicznym. W związku z tym bieżąca personifikacja w wątku, jeśli istnieje, również przepływów.  
  
 Przepływ można zmienić na dwa sposoby:  
  
1. Modyfikując ustawienia <xref:System.Threading.ExecutionContext>, aby pominąć przepływ dla poszczególnych wątków (zobacz Metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>).  
  
2. Przez zmianę trybu domyślnego procesu na tryb zgodności w wersji 1, gdzie obiekt <xref:System.Security.Principal.WindowsIdentity> nie przepływa przez żaden punkt asynchroniczny, niezależnie od ustawień <xref:System.Threading.ExecutionContext> w bieżącym wątku. Sposób zmiany trybu domyślnego zależy od tego, czy do załadowania środowiska CLR jest używany zarządzany plik wykonywalny, czy niezarządzany interfejs hostingu:  
  
    1. W przypadku zarządzanych plików wykonywalnych należy ustawić atrybut `enabled` elementu [\<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.  
  
    2. W przypadku niezarządzanych interfejsów hostingu Ustaw flagę `STARTUP_LEGACY_IMPERSONATION` w parametrze `flags` podczas wywoływania funkcji `CorBindToRuntimeEx`.  
  
     Tryb zgodności w wersji 1 dotyczy całego procesu i wszystkich domen aplikacji w procesie.  
  
## <a name="remarks"></a>Uwagi  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i `CorBindToRuntime` wykonać tę samą operację, ale funkcja `CorBindToRuntimeEx` pozwala ustawić flagi, aby określić zachowanie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
