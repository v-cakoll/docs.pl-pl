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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3d714e83eb0b75b31b08e7a356eb9ea699e1794
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689198"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime — Funkcja
Włącza niezarządzane hosty do załadowania środowisko uruchomieniowe języka wspólnego (CLR) do procesu.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [in] Ciąg opisujący wersję środowiska CLR chcesz załadować.  
  
 Numer wersji w programie .NET Framework składa się z czterech części oddzielonych kropkami: *główna.pomocnicza.kompilacja.poprawka*. Ciąg przekazany jako `pwszVersion` musi zaczynać się od znaków "v", następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z deklaracji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie, uruchomienie podkładki programowej ocenia `pwszVersion` wobec deklaracji i obciążeń najnowszej wersji środowiska uruchomieniowego, jest zgodny z żądaną wersją. Host może wymusić podkładkę, aby pominąć zasady oceny i załadować dokładną wersję określoną w `pwszVersion` , przekazując wartość `STARTUP_LOADER_SAFEMODE` dla `flags` parametru, zgodnie z poniższym opisem.  
  
 Jeśli obiekt wywołujący określa wartość null w przypadku `pwszVersion`, najnowszą wersję środowiska wykonawczego jest załadowana. Przekazanie wartości null zapewnia hosta bez kontroli nad tym, którzy wersja środowiska uruchomieniowego jest załadowana. Mimo że takie podejście może być odpowiedni w niektórych scenariuszach, zdecydowanie zaleca się że host podać do załadowania określonej wersji.  
  
 `pwszBuildFlavor`  
 [in] Ciąg, który określa, czy ładować serwer czy stację roboczą kompilacji środowiska CLR. Prawidłowe wartości to `svr` i `wks`. Server kompilacji jest zoptymalizowany, aby móc korzystać z wielu procesorów do wyrzucania elementów bezużytecznych, a stacja robocza kompilacji jest zoptymalizowany dla aplikacji klienckich działających na komputerze jednoprocesorowym.  
  
 Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, stacja robocza kompilacji jest ładowany. Podczas uruchamiania na komputerze jednoprocesorowym, stacja robocza kompilacji będzie zawsze ładowana, nawet jeśli `pwszBuildFlavor` ustawiono `svr`. Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i współbieżne wyrzucanie elementów bezużytecznych zostało określone (zobacz opis `flags` parametru), ładowana jest kompilacja serwera.  
  
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
  
1.  Modyfikując <xref:System.Threading.ExecutionContext> ustawienia, aby wstrzymać przepływ na podstawie na wątek (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).  
  
2.  Po zmianie procesu domyślny tryb na tryb zgodności w wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu w dowolnym momencie asynchronicznego niezależnie od wartości <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku. Jak zmienić domyślny tryb, zależy od tego, czy używać zarządzanego pliku wykonywalnego lub niezarządzanego interfejsu hostingu do ładowania CLR:  
  
    1.  Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.  
  
    2.  W przypadku niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` znacznik w `flags` parametru podczas wywoływania `CorBindToRuntimeEx` funkcji.  
  
     Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i wszystkie domeny aplikacji w procesie.  
  
## <a name="remarks"></a>Uwagi  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i `CorBindToRuntime` wykonanie tej samej operacji, ale `CorBindToRuntimeEx` funkcja pozwala na ustawienie flagi, aby określić zachowanie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
