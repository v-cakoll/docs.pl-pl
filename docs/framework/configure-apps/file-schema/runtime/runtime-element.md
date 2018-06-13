---
title: '&lt;środowisko uruchomieniowe&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fb050a8d73c42094caf83ba00c5dfc2e4d472723
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748675"
---
# <a name="ltruntimegt-element"></a>&lt;środowisko uruchomieniowe&gt; — Element
Zawiera informacje używane przez środowisko uruchomieniowe języka wspólnego do konfigurowania aplikacji.  
  
 \<Konfiguracja >  
\<runtime>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Określa, czy tożsamość systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definiuje co najmniej jeden przełącznik używany przez <xref:System.AppContext> klasy, aby zapewnić mechanizm rezygnacji z nowych funkcji.|  
|[\<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Określa zestaw, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Powoduje, że środowiska uruchomieniowego w celu zbierania statystyk we wszystkich domenach aplikacji w trakcie cyklu życia procesu.|  
|[\<assemblybinding — >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Określa, czy pominąć weryfikacja jednoznacznych nazw dla zaufanych zestawów.|  
|[\<Compatsortnlsversion — >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Określa, czy podczas porównywania ciągów środowiska uruchomieniowego należy używać starszych sortowania.|  
|[\<developmentmode — >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Określa, czy środowisko uruchomieniowe wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Określa, czy jest wyłączone buforowanie niepowodzenia powiązań, czyli domyślne zachowanie w programie .NET Framework w wersji 2.0.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Określa, czy po uruchomieniu wątku zatwierdzone stosu wątku pełna.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Określa, czy zachowanie domyślne, czyli aby umożliwić host czasu wykonywania w celu zastąpienia ustawień konfiguracji dla domeny aplikacji jest wyłączone.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Określa, czy data i czas przetwarzania metody użyć skorygowaną zbiór reguł do analizowania ciągi daty, które zawierają tylko dzień, miesiąc, godzinę i oznaczenie AM/PM.|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Określa, czy można wymusić wymagania konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardami FIPS (Federal Information).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzenia środowiska uruchomieniowego języka wspólnego.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Określa, czy PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 do określenia, czy ładowanie danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub pamięci globalnej.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego działa jednocześnie wyrzucanie elementów bezużytecznych.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego Uruchamia odzyskiwanie pamięci na serwerze.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Określa, czy środowisko uruchomieniowe używa zasad wydawcy (CAS) zabezpieczeń dostępu kodu.|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Określa, czy środowisko uruchomieniowe umożliwia kodu zarządzanego do wychwytywania naruszenia zasad dostępu i innych wyjątków uszkodzony.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Określa, że tożsamość systemu Windows nie przepływ między punktami asynchroniczne, niezależnie od ustawień przepływu kontekstu wykonywania w bieżącym wątku.|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Określa, czy zestawy z zdalnych źródeł, są ładowane przy pełnym zaufaniu.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Określa, czy środowisko uruchomieniowe używa zasady zabezpieczeń (CAS) starszego kodu dostępu.|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Określa, czy środowisko uruchomieniowe platformy niepoprawne wywołanie deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między poprawki zarządzane automatycznie i kodu niezarządzanego.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Określa środowisko wykonawcze będzie używać usługa międzyoperacyjna modelu COM zamiast usług zdalnych, poza granice domeny aplikacji.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optymalizuje sondy zestawów satelickich.|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzone w systemie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], lub wraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.|  
|[\<supportPortability >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Określa, aplikacja może odwoływać tego samego zestawu w dwóch różnych implementacji programu .NET Framework, wyłączając domyślne zachowanie, która traktuje zestawy jako równoważne do celów przenośność aplikacji.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Informacje dotyczące konfiguracji pamięci podręcznej w pamięci obiekt domyślny.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Określa, czy środowisko uruchomieniowe dystrybuuje zarządzanych wątków we wszystkich grupach procesora CPU.|  
|[\<Throwunobservedtaskexceptions — >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Określa, czy zadanie nieobsługiwanych wyjątków powinny przerwanie uruchomiony proces.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Określa, czy środowisko uruchomieniowe używa starszej wersji formatowanie <xref:System.TimeSpan> wartości.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji kompilatora JIT 64-bitowej w czasie kompilacji.|  
|[\<Userandomizedstringhashalgorithm — >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Określa, czy środowisko uruchomieniowe oblicza skrótu dla ciągów na poszczególnych domen aplikacji.|  
|[\<Usesmallinternalthreadstacks — >](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Żądania, że środowisko uruchomieniowe stwarza niektórych wątków, użyj rozmiarów jawne stosu jest używana wewnętrznie, zamiast domyślny rozmiar stosu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy podrzędne w [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji są używane przez środowisko uruchomieniowe języka wspólnego do konfigurowania, jak wykonuje aplikacji. Na przykład [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element określa, czy korzysta z modułu zbierającego elementy bezużyteczne stacji roboczej wyrzucanie elementów bezużytecznych lub odzyskiwanie pamięci na serwerze, [ \< Userandomizedstringhashalgorithm — >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) element określa, czy środowisko uruchomieniowe języka wspólnego obliczania skrótu ciągu w każdej aplikacji lub zasadach domeny dla każdej aplikacji i `AppContextSwitchOverrides` element umożliwia użytkownikom biblioteki Aby zgłosić się lub zrezygnować z zmienione funkcje udostępniane przez bibliotekę.  
  
 Elementy w [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji odczytywanych automatycznie przez środowisko uruchomieniowe języka wspólnego podczas uruchamiania aplikacji. Można również zdefiniować pliku konfiguracji dla domeny aplikacji innych niż domyślne, podając jego nazwę, aby <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> właściwości; jego ustawienia są odczytywane automatycznie po załadowaniu domeny aplikacji. Rzadko, jeśli w ogóle, masz potrzeba bezpośrednio odczytywać z ustawieniami [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracyjnym aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
