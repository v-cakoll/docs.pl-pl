---
title: CorBindToRuntimeEx — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176503"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx — Funkcja
Umożliwia hostów niezarządzanych załadować środowiska uruchomieniowego języka wspólnego (CLR) do procesu. [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) i `CorBindToRuntimeEx` funkcje wykonują tę `CorBindToRuntimeEx` samą operację, ale funkcja umożliwia ustawienie flagi, aby określić zachowanie CLR.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
 Ta funkcja przyjmuje zestaw parametrów, które umożliwiają hostowi wykonać następujące czynności:  
  
- Określ wersję środowiska wykonawczego, który zostanie załadowany.  
  
- Wskazać, czy ma zostać załadowana kompilacja serwera lub stacji roboczej.  
  
- Kontrolować, czy równoczesnych wyrzucania elementów bezużytecznych lub nie jednocześnie wyrzucania elementów bezużytecznych jest wykonywana.  
  
> [!NOTE]
> Równoczesne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach z emulatorem WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej nazywaną IA-64). Aby uzyskać więcej informacji na temat używania WOW64 w 64-bitowych systemach Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Osłanianie, czy zestawy są ładowane jako neutralne dla domeny.  
  
- Uzyskaj wskaźnik interfejsu do [ICorRuntimeHost,](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) który może służyć do ustawiania dodatkowych opcji konfigurowania wystąpienia CLR przed jego uruchomieniem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [w] Ciąg opisujący wersję clr, który chcesz załadować.  
  
 Numer wersji w ramach .NET Framework składa się z czterech części oddzielonych kropkami: *major.minor.build.revision*. Ciąg przeszedł `pwszVersion` zgodnie z musi zaczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje programu CLR są instalowane z instrukcją zasad określającą zgodność z poprzednimi wersjami programu CLR. Domyślnie podkładka uruchamiania `pwszVersion` ocenia instrukcje zasad i ładuje najnowszą wersję środowiska wykonawczego, która jest zgodna z żądaną wersją. Host może wymusić podkładkę do pominięcia oceny zasad `pwszVersion` i załadować `STARTUP_LOADER_SAFEMODE` dokładną wersję określoną przez przekazanie wartości parametru, `startupFlags` jak opisano poniżej.  
  
 Jeśli wywołujący określa wartość `pwszVersion` `CorBindToRuntimeEx` null dla , identyfikuje zestaw zainstalowanych runtimes których numery wersji są niższe niż .NET Framework 4 środowiska uruchomieniowego i ładuje najnowszą wersję środowiska wykonawczego z tego zestawu. Nie ładuje programu .NET Framework 4 lub nowszego i kończy się niepowodzeniem, jeśli nie zainstalowano żadnej wcześniejszej wersji. Należy zauważyć, że przekazywanie null daje hosta nie kontroli nad tym, która wersja środowiska wykonawczego jest ładowany. Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby host dostarczał określoną wersję do załadowania.  
  
 `pwszBuildFlavor`  
 [w] Ciąg, który określa, czy załadować serwer lub kompilacji stacji roboczej CLR. Prawidłowe `svr` wartości `wks`są i . Kompilacja serwera jest zoptymalizowana pod kątem korzystania z wielu procesorów do wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.  
  
 Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej jest ładowana. Podczas pracy na komputerze z jednym procesorem kompilacja stacji `pwszBuildFlavor` roboczej `svr`jest zawsze ładowana, nawet jeśli jest ustawiona na . Jednak jeśli `pwszBuildFlavor` jest `svr` ustawiona i równoczesnych wyrzucania elementów `startupFlags` bezużytecznych jest określony (zobacz opis parametru), kompilacja serwera jest ładowany.  
  
 `startupFlags`  
 [w] Kombinacja wartości wyliczenia [STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) Flagi te kontrolują równoczesnych wyrzucania elementów bezużytecznych, `pwszVersion` kod neutralny dla domeny i zachowanie parametru. Wartość domyślna to pojedyncza domena, jeśli nie ustawiono żadnej flagi. Prawidłowe są następujące wartości:  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Opisy tych flag można znaleźć w [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.  
  
 `rclsid`  
 [w] Coclass, `CLSID` który implementuje interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Obsługiwane wartości są CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [w] Wymagany `IID` interfejs z . `rclsid` Obsługiwane wartości są IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [na zewnątrz] Zwrócony wskaźnik `riid`interfejsu do .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pwszVersion` określa wersję środowiska uruchomieniowego, `CorBindToRuntimeEx` która nie istnieje, zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontekst wykonywania i przepływ tożsamości systemu Windows  
 W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> obiekt nie przepływa przez punkty asynchroniczne, takie jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza. W wersji 2.0 środowiska CLR obiekt zawija <xref:System.Threading.ExecutionContext> niektóre informacje o aktualnie wykonywanym wątku i przepływa przez dowolny punkt asynchroniczne, ale nie przez granice domeny aplikacji. Podobnie obiekt <xref:System.Security.Principal.WindowsIdentity> przepływa również przez dowolny punkt asynchroniczne. W związku z tym bieżącej personifikacji w wątku, jeśli istnieje, przepływa zbyt.  
  
 Przepływ można zmienić na dwa sposoby:  
  
1. Modyfikując <xref:System.Threading.ExecutionContext> ustawienia w celu wygaszenia przepływu <xref:System.Threading.ExecutionContext.SuppressFlow%2A>na <xref:System.Security.SecurityContext.SuppressFlow%2A>podstawie <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> wątku (patrz , i metody).  
  
2. Zmieniając domyślny tryb procesu na tryb zgodności w wersji <xref:System.Security.Principal.WindowsIdentity> 1, w którym obiekt nie przepływa przez <xref:System.Threading.ExecutionContext> żaden punkt asynchroniczne, niezależnie od ustawień w bieżącym wątku. Sposób zmiany trybu domyślnego zależy od tego, czy do załadowania programu CLR używasz zarządzanego pliku wykonywalnego, czy niezarządzanego interfejsu hostingu:  
  
    1. W przypadku zarządzanych plików wykonywalnych należy ustawić `enabled` atrybut [ \<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element na `true`.  
  
    2. W przypadku niezarządzanych interfejsów hostingu ustaw flagę `STARTUP_LEGACY_IMPERSONATION` w parametrze `startupFlags` podczas wywoływania `CorBindToRuntimeEx` funkcji.  
  
     Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i do wszystkich domen aplikacji w procesie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg — Funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost — Funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
