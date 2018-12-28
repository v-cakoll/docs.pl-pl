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
ms.openlocfilehash: 5ab9fafeb6c836f1561752a8e2bdfddb97296399
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610681"
---
# <a name="ltruntimegt-element"></a>&lt;środowisko uruchomieniowe&gt; — Element
Zawiera informacje używane przez środowisko uruchomieniowe języka wspólnego, aby skonfigurować aplikacje.  
  
 \<Konfiguracja >  
\<runtime>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W następujących sekcjach opisano elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Określa, że tożsamość Windows zawsze odbywa się za pośrednictwem punkty asynchroniczne, niezależnie od tego, jak zostało wykonane personifikacji.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definiuje co najmniej jeden przełączniki posługują się <xref:System.AppContext> Aby klasa zapewniała mechanizm rezygnacji z nowych funkcji.|  
|[\<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Określa zestaw, który zapewnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Powoduje, że środowisko uruchomieniowe w celu zbierania statystyk na wszystkie domeny aplikacji, w trakcie trwania procesu.|  
|[\<assemblybinding — >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Określa, czy pominąć weryfikacją silnych nazw dla zaufanych zestawów.|  
|[\<CompatSortNLSVersion >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Określa, że środowisko uruchomieniowe powinno używać starsze zachowanie sortowania podczas porównywania ciągów.|  
|[\<developmentmode — >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Określa, czy buforowanie niepowodzenia powiązania, który jest to zachowanie domyślne w .NET Framework w wersji 2.0, jest wyłączona.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Określa, czy stos pełnego wątku jest zatwierdzona, gdy wątek jest uruchomiony.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Określa, czy należy wyłączyć zachowanie domyślne, które jest, aby zezwolić na host środowiska uruchomieniowego w celu zastąpienia ustawień konfiguracji domeny aplikacji.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Określa, czy data i godzina metod analizowania użyć skorygowany zbiór reguł do analizowania ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Określa, czy do wymuszania wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardów FIPS (Federal Information).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Określa, czy włączyć śledzenie zdarzeń dla Windows (ETW) dla typowych zdarzeń środowiska wykonawczego języka.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Określa, czy PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 do określenia, czy można załadować danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego jednocześnie uruchamia wyrzucanie elementów bezużytecznych.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup CPU.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych serwera.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Określa, czy środowisko wykonawcze używa zasady wydawcy zabezpieczenia dostępu kodu.|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Określa, czy środowisko wykonawcze umożliwia kodu zarządzanego wykryć naruszenia zasad dostępu i inne wyjątki uszkodzony.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Określa, że tożsamość Windows nie przepływać przez punkty asynchroniczne, na niezależnie od ustawień przepływu kontekstu wykonania dla bieżącego wątku.|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Określa, czy zestawy od źródła zdalnego są ładowane jako pełne zaufanie.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Określa, czy środowisko wykonawcze używa starszego kodu zasady zabezpieczeń dostępu (CAS).|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Określa, czy środowisko wykonawcze automatycznie poprawki nieprawidłowa platforma wywołania deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między zarządzane, a kod niezarządzany.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania kodów wartości skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Określa środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast usług zdalnych, poza granice domeny aplikacji.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optymalizuje sondy dla zestawów satelickich.|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzona w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], lub powraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.|  
|[\<supportportability — >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Określa, czy aplikacja może odwołać się tego samego zestawu w dwóch różnych implementacjach systemu .NET Framework, wyłączając zachowania domyślne, które traktuje zestawy za równorzędne do celów przenoszenia aplikacji.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Informacje dotyczące konfiguracji pamięci podręcznej domyślnego obiektu w pamięci.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.|  
|[\<Throwunobservedtaskexceptions — >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Określa, czy środowisko wykonawcze używa starszego formatowania <xref:System.TimeSpan> wartości.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji 64-bitowy kompilator JIT dla kompilacji just in time.|  
|[\<Userandomizedstringhashalgorithm — >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Określa, czy środowisko uruchomieniowe oblicza kody skrótów dla ciągów na podstawie domeny aplikacji.|  
|[\<Usesmallinternalthreadstacks — >](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Środowisko uruchomieniowe używać stosu jawnych rozmiarów, podczas tworzenia niektórych wątków, żądań używa wewnętrznie, zamiast domyślnego rozmiaru stosu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy podrzędne w [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji są używane przez środowisko uruchomieniowe języka wspólnego do skonfigurowania, jak aplikacja wykonuje. Na przykład [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element określa, czy moduł zbierający elementy bezużyteczne używa wyrzucania elementów bezużytecznych dla stacji roboczych lub wyrzucanie elementów bezużytecznych serwera [ \< Userandomizedstringhashalgorithm — >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) element określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągu w każdej aplikacji lub zasadach domeny dla aplikacji i `AppContextSwitchOverrides` element umożliwia użytkownikom biblioteki Aby zgodzić się na lub zrezygnować z zmienione funkcje udostępniane przez bibliotekę.  
  
 Elementy w [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji odczytywanych automatycznie przez środowisko uruchomieniowe języka wspólnego przy uruchamianiu aplikacji. Można również definiować plik konfiguracyjny dla domeny aplikacji innych niż domyślne, podając jego nazwę na <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> właściwości jego ustawienia są odczytywane automatycznie po załadowaniu do domeny aplikacji. Rzadko, jeśli w ogóle, należy potrzebę bezpośredniego odczytywania ustawień w [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracyjnym aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
