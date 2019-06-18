---
title: Schemat ustawień środowiska uruchomieniowego
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d22046393b22683b961f5da7a5623f5dfa6a702e
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170031"
---
# <a name="runtime-settings-schema"></a>Schemat ustawień środowiska uruchomieniowego

Ustawienia środowiska uruchomieniowego są używane przez środowisko uruchomieniowe języka wspólnego do konfigurowania aplikacji środowiska .NET Framework.

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>\<Runtime > sekcji i jego elementy nadrzędne i podrzędne

[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblybinding — >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp >](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;\<\runtime > \
\<\configuration >

## <a name="alphabetical-list-of-runtime-elements"></a>Alfabetyczna lista \<runtime > elementy

|Element|Opis|
|-------------|-----------------|
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Dodaje nazwaną pamięć podręczną do `namedCaches` kolekcji w pamięci podręcznej.|
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Określa, że tożsamość Windows zawsze odbywa się za pośrednictwem punkty asynchroniczne, niezależnie od tego, jak zostało wykonane personifikacji.|
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definiuje co najmniej jeden przełączniki posługują się <xref:System.AppContext> Aby klasa zapewniała mechanizm rezygnacji z nowych funkcji.|
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Określa zestaw, który zapewnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.|
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Powoduje, że środowisko uruchomieniowe w celu zbierania statystyk na wszystkie domeny aplikacji, w trakcie trwania procesu.|
|[\<assemblybinding — >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|
|[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)|Zawiera informacje identyfikujące zestaw.|
|[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)|Przekierowuje jedną wersję zestawu do innej.|
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Określa, czy pominąć weryfikacją silnych nazw dla zaufanych zestawów.|
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Czyści `namedCaches` kolekcji w pamięci podręcznej.|
|[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)|Określa, gdzie środowisko uruchomieniowe można znaleźć zestawu.|
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Określa, że środowisko uruchomieniowe powinno używać starsze zachowanie sortowania podczas porównywania ciągów|
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.|
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.|
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Określa, czy buforowanie niepowodzenia powiązania, który jest zachowaniem domyślnym w programie .NET Framework 2.0, jest wyłączona.|
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Określa, czy podczas uruchamiania wątku zatwierdzone stos pełnego wątku.|
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Określa, czy należy wyłączyć zachowanie domyślne, które jest, aby zezwolić na host środowiska uruchomieniowego w celu zastąpienia ustawień konfiguracji domeny aplikacji.|
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Określa, czy data i godzina metod analizowania użyć skorygowany zbiór reguł do analizowania ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.|
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Określa, czy do wymuszania wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardów FIPS (Federal Information).|
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Określa, czy włączyć śledzenie zdarzeń dla Windows (ETW) dla typowych zdarzeń środowiska wykonawczego języka.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Określa, czy PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 do określenia, czy można załadować danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci.|
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.|
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Określa, czy środowisko uruchomieniowe jednocześnie uruchamia wyrzucanie elementów bezużytecznych.|
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup CPU.|
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych serwera.|
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Określa, czy środowisko wykonawcze używa zasady wydawcy zabezpieczenia dostępu kodu.|
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Określa, czy środowisko wykonawcze umożliwia kodu zarządzanego wykryć naruszenia zasad dostępu i inne wyjątki uszkodzony.|
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Określa, że tożsamość Windows nie przepływać przez punkty asynchroniczne, na niezależnie od ustawień przepływu kontekstu wykonania dla bieżącego wątku.|
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Określa, czy zestawy od źródła zdalnego są ładowane jako pełne zaufanie.|
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy.|
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji `namedCache` wystąpienia.|
|[\<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Określa, czy środowisko wykonawcze używa starszego kodu zasady zabezpieczeń dostępu (CAS).|
|[\<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Określa, czy środowisko wykonawcze automatycznie poprawki nieprawidłowa platforma wywołania deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między zarządzane, a kod niezarządzany.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania kodów wartości skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|
|[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Określa środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast usług zdalnych, poza granice domeny aplikacji.|
|[\<sondowanie >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Określa podkatalogów, które środowisko uruchomieniowe wyszukuje podczas ładowania zestawów.|
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy.|
|[\<qualifyassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy część nazwy jest używany.|
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optymalizuje sondy dla zestawów satelickich.|
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Usuwa wpis nazwaną pamięć podręczną z `namedCaches` kolekcji w pamięci podręcznej.|
|[\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Zawiera informacje dotyczące powiązania zestawu i zachowanie wyrzucania elementów bezużytecznych.|
|[\<shadowCopyTimeStampVerification>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzone w .NET Framework 4 lub powraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.|
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Określa, czy aplikacja może odwołać się tego samego zestawu w dwóch różnych implementacjach systemu .NET Framework, wyłączając zachowania domyślne, które traktuje zestawy za równorzędne do celów przenoszenia aplikacji.|
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Informacje dotyczące konfiguracji pamięci podręcznej domyślnego obiektu w pamięci.|
|[\<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.|
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.|
|[\<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Określa, czy środowisko wykonawcze używa starszego formatowania <xref:System.TimeSpan> wartości.|
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji 64-bitowy kompilator JIT dla kompilacji just in time.|
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Określa, czy środowisko uruchomieniowe oblicza kody skrótów dla ciągów na podstawie domeny aplikacji.|
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Środowisko uruchomieniowe używać stosu jawnych rozmiarów, podczas tworzenia niektórych wątków, żądań używa wewnętrznie, zamiast domyślnego rozmiaru stosu.|

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
