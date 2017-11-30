---
title: "CorBindToRuntime — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a833be39f93082e8d2c0cb28f435f754143721f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime — Funkcja
Umożliwia niezarządzane hosty załadować środowisko uruchomieniowe języka wspólnego (CLR) do procesu.  
  
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
  
 Numer wersji w programie .NET Framework składa się z czterech części oddzielone kropkami: *główna.pomocnicza.kompilacja.poprawka*. Ciąg przekazany jako `pwszVersion` musi rozpoczynać się od znaku "v" następuje pierwsze trzy części numer wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z instrukcji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie, ocenia podkładki uruchamiania `pwszVersion` przed deklaracji zasad i obciążeń najnowszą wersję środowiska uruchomieniowego który jest zgodny z wersją żądanej. Hosta można wymusić podkładki, aby pominąć oceny zasad i załadować dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości `STARTUP_LOADER_SAFEMODE` dla `flags` parametru, zgodnie z poniższym opisem.  
  
 Jeśli element wywołujący określa wartość null dla `pwszVersion`, najnowszą wersję środowiska wykonawczego został załadowany. Przekazywanie null daje hosta bez kontroli, w którym jest załadowana wersja środowiska uruchomieniowego. Chociaż w niektórych scenariuszach może być to rozwiązanie, zaleca się że host podać do ładowania określonej wersji.  
  
 `pwszBuildFlavor`  
 [in] Ciąg, który określa, czy ładowanie serwera lub stacji roboczej kompilacji środowiska CLR. Prawidłowe wartości to `svr` i `wks`. Zoptymalizowano kompilacji serwera mógł korzystać z wielu procesorów do wyrzucania i kompilacji stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich działających na maszynie jeden procesor.  
  
 Jeśli `pwszBuildFlavor` ma wartość null, jest ładowany kompilacji stacji roboczej. Podczas uruchamiania na maszynie jeden procesor, zawsze jest ładowany kompilacji stacji roboczej, nawet jeśli `pwszBuildFlavor` ma ustawioną wartość `svr`. Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i określono współbieżne odzyskiwanie pamięci (w opisie `flags` parametru), serwer kompilacji został załadowany.  
  
 `rclsid`  
 [in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu. Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Żądanego interfejsu z `rclsid`. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Wskaźnik interfejsu zwrócony do `riid`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pwszVersion` Określa wersję środowiska uruchomieniowego, który nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontekstu wykonywania i przepływu tożsamości systemu Windows  
 W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> między punktami asynchronicznego, takie jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza nie przepływ obiektu. W wersji 2.0 CLR <xref:System.Threading.ExecutionContext> obiekt opakowuje niektóre informacje o obecnie wykonywanym wątku i przepływa go w dowolnym punkcie asynchroniczne, ale nie poza granice domeny aplikacji. Podobnie <xref:System.Security.Principal.WindowsIdentity> obiektu przepływa również dla dowolnego punktu asynchronicznego. W związku z tym bieżącego personifikacji w wątku, jeśli przepływy zbyt.  
  
 Można zmienić przepływu na dwa sposoby:  
  
1.  Zmieniając <xref:System.Threading.ExecutionContext> ustawienia, aby pominąć przepływem na podstawie dla każdego wątku (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).  
  
2.  Zmieniając to tryb domyślny proces do trybu zgodności wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu dla dowolnego punktu asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku. Jak zmienić domyślny tryb, zależy od tego, przy użyciu zarządzanego pliku wykonywalnego lub niezarządzane interfejs hostingu można załadować środowiska CLR:  
  
    1.  Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.  
  
    2.  Niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` oflagowane w `flags` parametr podczas wywoływania metody `CorBindToRuntimeEx` funkcji.  
  
     Tryb zgodności wersji 1 dotyczy całego procesu i wszystkich domen aplikacji w procesie.  
  
## <a name="remarks"></a>Uwagi  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i `CorBindToRuntime` wykonać operację, ale `CorBindToRuntimeEx` funkcji można ustawić flagi, aby określić zachowanie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CorBindToCurrentRuntime — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeByCfg — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
