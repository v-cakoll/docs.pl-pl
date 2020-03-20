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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176516"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime — Funkcja
Umożliwia hostów niezarządzanych załadować środowiska uruchomieniowego języka wspólnego (CLR) do procesu.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
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
 [w] Ciąg opisujący wersję clr, który chcesz załadować.  
  
 Numer wersji w ramach .NET Framework składa się z czterech części oddzielonych kropkami: *major.minor.build.revision*. Ciąg przeszedł `pwszVersion` zgodnie z musi zaczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje programu CLR są instalowane z instrukcją zasad określającą zgodność z poprzednimi wersjami programu CLR. Domyślnie podkładka uruchamiania `pwszVersion` ocenia instrukcje zasad i ładuje najnowszą wersję środowiska wykonawczego, która jest zgodna z żądaną wersją. Host może wymusić podkładkę do pominięcia oceny zasad `pwszVersion` i załadować `STARTUP_LOADER_SAFEMODE` dokładną wersję określoną przez przekazanie wartości parametru, `flags` jak opisano poniżej.  
  
 Jeśli wywołujący określa wartość `pwszVersion`null dla , jest ładowana najnowsza wersja środowiska wykonawczego. Przekazywanie null daje hostowi nie kontrolę nad tym, która wersja środowiska wykonawczego jest ładowana. Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby host dostarczał określoną wersję do załadowania.  
  
 `pwszBuildFlavor`  
 [w] Ciąg, który określa, czy załadować serwer lub kompilacji stacji roboczej CLR. Prawidłowe `svr` wartości `wks`są i . Kompilacja serwera jest zoptymalizowana pod kątem korzystania z wielu procesorów do wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.  
  
 Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej jest ładowana. Podczas pracy na komputerze z jednym procesorem kompilacja stacji `pwszBuildFlavor` roboczej `svr`jest zawsze ładowana, nawet jeśli jest ustawiona na . Jednak jeśli `pwszBuildFlavor` jest `svr` ustawiona i równoczesnych wyrzucania elementów `flags` bezużytecznych jest określony (zobacz opis parametru), kompilacja serwera jest ładowany.  
  
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
  
    2. W przypadku niezarządzanych interfejsów hostingu ustaw flagę `STARTUP_LEGACY_IMPERSONATION` w parametrze `flags` podczas wywoływania `CorBindToRuntimeEx` funkcji.  
  
     Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i do wszystkich domen aplikacji w procesie.  
  
## <a name="remarks"></a>Uwagi  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` i wykonać tę samą operację, ale `CorBindToRuntimeEx` funkcja umożliwia ustawienie flagi, aby określić zachowanie CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg — Funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost — Funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
