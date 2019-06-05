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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b45efb634ca9b88768d6e30884085f28ad17b7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490589"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx — Funkcja
Włącza niezarządzane hosty do załadowania środowisko uruchomieniowe języka wspólnego (CLR) do procesu. [CorBindToRuntime —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) i `CorBindToRuntimeEx` funkcje wykonują tę samą operację, ale `CorBindToRuntimeEx` funkcja pozwala na ustawienie flagi, aby określić zachowanie środowiska CLR.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
 Ta funkcja pobiera zestaw parametrów, zezwalających na hoście, wykonaj następujące czynności:  
  
- Określ wersję środowiska uruchomieniowego, które będą ładowane.  
  
- Wskazuje, czy serwer lub stacja robocza kompilacji powinny być załadowane.  
  
- Kontrolowanie, czy współbieżne wyrzucanie elementów bezużytecznych lub niewspółbieżnym wyrzucaniem elementów bezużytecznych jest wykonywane.  
  
> [!NOTE]
>  Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwana w aplikacjach działających w emulatorze WOW64 x86 emulatora w systemach 64-bitowych, które implementują architekturę Intel Itanium (wcześniej noszącą nazwę IA-64). Aby uzyskać więcej informacji o używaniu WOW64 w 64-bitowych systemach Windows, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Kontrolowanie, czy zestawy są ładowane jako niezależne od domeny.  
  
- Wskaźnik interfejsu do uzyskania [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) można ustawić dodatkowe opcje dotyczące konfigurowania wystąpienia środowiska CLR, przed jej ponownym uruchomieniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Ciąg opisujący wersję środowiska CLR chcesz załadować.  
  
 Numer wersji w programie .NET Framework składa się z czterech części oddzielonych kropkami: *główna.pomocnicza.kompilacja.poprawka*. Ciąg przekazany jako `pwszVersion` musi zaczynać się od znaków "v", następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z deklaracji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie, uruchomienie podkładki programowej ocenia `pwszVersion` wobec deklaracji i obciążeń najnowszej wersji środowiska uruchomieniowego, jest zgodny z żądaną wersją. Host może wymusić podkładkę, aby pominąć zasady oceny i załadować dokładną wersję określoną w `pwszVersion` , przekazując wartość `STARTUP_LOADER_SAFEMODE` dla `startupFlags` parametru, zgodnie z poniższym opisem.  
  
 Jeśli obiekt wywołujący określa wartość null w przypadku `pwszVersion`, `CorBindToRuntimeEx` identyfikuje zestaw zainstalowanego środowiska uruchomieniowe, których numery wersji są niższe niż w środowisku uruchomieniowym .NET Framework 4 i ładuje najnowszą wersję środowiska uruchomieniowego z tego zbioru. Nie będzie on ładować .NET Framework 4 lub nowszy, a kończy się niepowodzeniem, jeśli zainstalowano nie wcześniejszej wersji. Należy zauważyć, że przekazywanie wartości null daje hosta bez kontroli nad tym, którzy wersja środowiska uruchomieniowego jest załadowana. Mimo że takie podejście może być odpowiedni w niektórych scenariuszach, zdecydowanie zaleca się że host podać do załadowania określonej wersji.  
  
 `pwszBuildFlavor`  
 [in] Ciąg, który określa, czy ładować serwer czy stację roboczą kompilacji środowiska CLR. Prawidłowe wartości to `svr` i `wks`. Server kompilacji jest zoptymalizowany, aby móc korzystać z wielu procesorów do wyrzucania elementów bezużytecznych, a stacja robocza kompilacji jest zoptymalizowany dla aplikacji klienckich działających na komputerze jednoprocesorowym.  
  
 Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, stacja robocza kompilacji jest ładowany. Podczas uruchamiania na komputerze jednoprocesorowym, stacja robocza kompilacji będzie zawsze ładowana, nawet jeśli `pwszBuildFlavor` ustawiono `svr`. Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i współbieżne wyrzucanie elementów bezużytecznych zostało określone (zobacz opis `startupFlags` parametru), ładowana jest kompilacja serwera.  
  
 `startupFlags`  
 [in] Kombinacja wartości [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia. Te flagi kontrolować współbieżne wyrzucanie elementów bezużytecznych, kodem domeny neutralnej i zachowaniem `pwszVersion` parametru. Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona. Następujące wartości są prawidłowe:  
  
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
  
 Aby uzyskać opis tych flag, zobacz [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.  
  
 `rclsid`  
 [in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu. Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Żądanego interfejsu z `rclsid`. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Wskaźnik interfejsu zwrócone do `riid`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pwszVersion` Określa wersję środowiska uruchomieniowego, który nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontekstu wykonywania i przepływ tożsamości Windows  
 W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> obiektu nie przepływać przez punkty asynchroniczne, takie jak nowe wątki, pul wątków lub czasomierza wywołania zwrotne. W wersji 2.0 środowisko CLR <xref:System.Threading.ExecutionContext> obiektu otacza pewne informacje o aktualnie wykonywany wątek i przepływy go między kiedykolwiek asynchronicznego, ale nie granice domeny aplikacji. Podobnie <xref:System.Security.Principal.WindowsIdentity> obiektu również odbywa się za pośrednictwem dowolnego punktu asynchronicznego. W związku z tym bieżący personifikacji w wątku, ewentualnie przepływów zbyt.  
  
 Można zmienić przepływ na dwa sposoby:  
  
1. Modyfikując <xref:System.Threading.ExecutionContext> ustawienia, aby wstrzymać przepływ na podstawie na wątek (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).  
  
2. Po zmianie procesu domyślny tryb na tryb zgodności w wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu w dowolnym momencie asynchronicznego niezależnie od wartości <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku. Jak zmienić domyślny tryb, zależy od tego, czy używać zarządzanego pliku wykonywalnego lub niezarządzanego interfejsu hostingu do ładowania CLR:  
  
    1. Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.  
  
    2. W przypadku niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` znacznik w `startupFlags` parametru podczas wywoływania `CorBindToRuntimeEx` funkcji.  
  
     Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i wszystkie domeny aplikacji w procesie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
