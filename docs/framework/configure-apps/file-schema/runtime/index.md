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
ms.openlocfilehash: 5b340ef99b489b66c62971cacedccdfe609d0b1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252522"
---
# <a name="runtime-settings-schema"></a>Schemat ustawień środowiska uruchomieniowego

Ustawienia środowiska uruchomieniowego są używane przez środowisko uruchomieniowe języka wspólnego do konfigurowania aplikacji przeznaczonych dla .NET Framework.

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>Sekcja \<> środowiska uruchomieniowego i jej elementy nadrzędne i podrzędne

[\<> konfiguracji](../configuration-element.md)\
&nbsp;&nbsp;[\<> środowiska uruchomieniowego](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides >](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<> zestawubinding](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> dependentAssembly](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity >](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect >](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy Apply >](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> sondowania](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly >](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Tag supportportability >](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion >](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<> developmentmode](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures >](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment >](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable >](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer >](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy >](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience >](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp >](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;[\<System. Runtime. buforowanie >](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Elemencie MemoryCache >](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches >](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Dodaj >](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Wyczyść >](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Usuń >](remove-element-for-namedcaches.md)  

## <a name="alphabetical-list-of-runtime-elements"></a>Alfabetyczna lista \<elementów > środowiska uruchomieniowego

|Element|Opis|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|Dodaje nazwaną pamięć podręczną `namedCaches` do kolekcji dla pamięci podręcznej pamięci.|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Określa, że tożsamość systemu Windows jest zawsze przepływów między punktami asynchronicznymi, niezależnie od tego, jak personifikacja została wykonana.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Definiuje jeden lub więcej przełączników używanych przez <xref:System.AppContext> klasę, aby zapewnić mechanizm rezygnacji dla nowych funkcji.|
|[\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)|Określa zestaw, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Powoduje, że środowisko uruchomieniowe zbiera statystyki dotyczące wszystkich domen aplikacji w procesie przez cały czas trwania procesu.|
|[\<> zestawubinding](assemblybinding-element-for-runtime.md)|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|Zawiera informacje identyfikacyjne dotyczące zestawu.|
|[\<bindingRedirect >](bindingredirect-element.md)|Przekierowuje jedną wersję zestawu do innej.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Określa, czy należy pominąć weryfikację silnej nazwy dla zaufanych zestawów.|
|[\<Wyczyść >](clear-element-for-namedcaches.md)|`namedCaches` Czyści kolekcję dla pamięci podręcznej pamięci.|
|[\<codeBase>](codebase-element.md)|Określa, gdzie środowisko uruchomieniowe może znaleźć zestaw.|
|[\<CompatSortNLSVersion >](compatsortnlsversion-element.md)|Określa, że środowisko uruchomieniowe ma używać starszego zachowania sortowania podczas wykonywania porównań ciągów|
|[\<> dependentAssembly](dependentassembly-element.md)|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.|
|[\<> developmentmode](developmentmode-element.md)|Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Określa, czy buforowanie błędów powiązań, które jest domyślnym zachowaniem w .NET Framework 2,0, jest wyłączone.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Określa, czy pełny stos wątków jest zatwierdzany podczas uruchamiania wątku.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Określa, czy domyślne zachowanie, które umożliwia hostowi środowiska uruchomieniowego przesłonięcie ustawień konfiguracji dla domeny aplikacji, jest wyłączone.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Określa, czy metody analizowania dat i godzin używają skorygowanego zestawu reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Określa, czy należy wymusić wymaganie konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne z FIPS (Federal Information Processing Standards).|
|[\<etwEnable>](etwenable-element.md)|Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Określa, czy funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1,1, aby określić, czy ładować dane liczników wydajności z pamięci współdzielonej określonej dla kategorii, czy z pamięci globalnej.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Na platformach 64-bitowych program umożliwia korzystanie z tablic o rozmiarze większym niż 2 gigabajty (GB).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci jednocześnie.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.|
|[\<gcServer>](gcserver-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci serwera.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Określa, czy środowisko uruchomieniowe używa zasad wydawcy zabezpieczeń dostępu kodu (CAS).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Określa, czy środowisko uruchomieniowe umożliwia kodowi zarządzanemu przechwytywanie naruszeń dostępu i innych wyjątków uszkodzonych Stanów.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Określa, że tożsamość systemu Windows nie przepływa między punktami asynchronicznymi, niezależnie od ustawień przepływu dla kontekstu wykonywania w bieżącym wątku.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Określa, czy zestawy ze źródeł zdalnych są ładowane jako pełne zaufanie.|
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji dla tego `namedCache` wystąpienia.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Określa, czy środowisko uruchomieniowe korzysta ze starszych zasad zabezpieczeń dostępu kodu (CAS).|
|[\<NetFx40_PInvokeStackResilience >](netfx40-pinvokestackresilience-element.md)|Określa, czy środowisko uruchomieniowe automatycznie naprawia nieprawidłowe deklaracje wywołania platformy w czasie wykonywania, kosztem wolniejszych przejść między zarządzanym i niezarządzanym kodem.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczenia kodów skrótów dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|Określa, że środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.|
|[\<> sondowania](probing-element.md)|Określa podkatalogi, które środowisko uruchomieniowe wyszukuje podczas ładowania zestawów.|
|[\<publisherPolicy>](publisherpolicy-element.md)|Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy.|
|[\<qualifyAssembly >](qualifyassembly-element.md)|Określa pełną nazwę zestawu, który ma być dynamicznie ładowany, gdy zostanie użyta nazwa częściowa.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Optymalizuje sondę dla zestawów satelickich.|
|[\<remove>](remove-element-for-namedcaches.md)|Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.|
|[\<runtime>](runtime-element.md)|Zawiera informacje o powiązaniu zestawu i zachowaniu wyrzucania elementów bezużytecznych.|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|Określa, czy kopiowanie w tle używa domyślnego zachowania uruchamiania wprowadzonego w .NET Framework 4, czy przywraca zachowanie uruchamiania wcześniejszych wersji .NET Framework.|
|[\<Tag supportportability >](supportportability-element.md)|Określa, że aplikacja może odwoływać się do tego samego zestawu w dwóch różnych implementacjach .NET Framework, przez wyłączenie domyślnego zachowania, które traktuje zestawy jako równoważne do celów przenośności aplikacji.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Zawiera informacje o konfiguracji domyślnej pamięci podręcznej obiektów w pamięci.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|Określa, czy środowisko uruchomieniowe używa starszej wersji formatowania dla <xref:System.TimeSpan> wartości.|
|[\<useLegacyJit>](uselegacyjit-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego korzysta ze starszego 64-bitowego kompilatora JIT dla kompilacji just in Time.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Określa, czy środowisko uruchomieniowe oblicza kody skrótów dla ciągów na podstawie poszczególnych domen aplikacji.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|Żąda, aby środowisko uruchomieniowe używało jawnych rozmiarów stosu, gdy tworzy pewne wątki używane wewnętrznie, zamiast domyślnego rozmiaru stosu.|

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)
