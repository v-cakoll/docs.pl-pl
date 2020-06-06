---
title: <runtime> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3825ae7c3e35193cb835981600fe1ef83097cd2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430459"
---
# <a name="runtime-element"></a>\<runtime> Element

Zawiera informacje używane przez środowisko uruchomieniowe języka wspólnego do konfigurowania aplikacji.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

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
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Określa, że tożsamość systemu Windows jest zawsze przepływów między punktami asynchronicznymi, niezależnie od tego, jak personifikacja została wykonana.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Definiuje jeden lub więcej przełączników używanych przez <xref:System.AppContext> klasę, aby zapewnić mechanizm rezygnacji dla nowych funkcji.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Określa zestaw, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Powoduje, że środowisko uruchomieniowe zbiera statystyki dotyczące wszystkich domen aplikacji w procesie przez cały czas trwania procesu.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Określa, czy należy pominąć weryfikację silnej nazwy dla zaufanych zestawów.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Określa, że środowisko uruchomieniowe ma używać starszego zachowania sortowania podczas porównywania ciągów.|
|[\<developmentMode>](developmentmode-element.md)|Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Określa, czy buforowanie błędów powiązań, które jest domyślnym zachowaniem w .NET Framework w wersji 2,0, jest wyłączone.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Określa, czy pełny stos wątków jest zatwierdzany podczas uruchamiania wątku.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Określa, czy domyślne zachowanie, które umożliwia hostowi środowiska uruchomieniowego przesłonięcie ustawień konfiguracji dla domeny aplikacji, jest wyłączone.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Określa, czy metody analizowania dat i godzin używają skorygowanego zestawu reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Określa, czy należy wymusić wymaganie konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne z FIPS (Federal Information Processing Standards).|
|[\<etwEnable>](etwenable-element.md)|Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Określa, czy funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1,1, aby określić, czy ładować dane liczników wydajności z pamięci współdzielonej określonej dla kategorii, czy z pamięci globalnej.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Na platformach 64-bitowych program umożliwia korzystanie z tablic o rozmiarze większym niż 2 gigabajty (GB).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci jednocześnie.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Definiuje koligację między stertami odzyskiwania pamięci i procesorami indywidualnymi.|
|[\<GCHeapCount>](gcheapcount-element.md)|Określa liczbę stert/wątków, które mają być używane do wyrzucania elementów bezużytecznych serwera.|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Określa rozmiar progu, który powoduje, że moduł zbierający elementy bezużyteczne umieszcza obiekty na stertie dużego obiektu.|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Określa, czy koligacji wątki odzyskiwania pamięci serwera z procesorami CPU.|
|[\<gcServer>](gcserver-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci serwera.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Określa, czy środowisko uruchomieniowe używa zasad wydawcy zabezpieczeń dostępu kodu (CAS).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Określa, czy środowisko uruchomieniowe umożliwia kodowi zarządzanemu przechwytywanie naruszeń dostępu i innych wyjątków uszkodzonych Stanów.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Określa, że tożsamość systemu Windows nie przepływa między punktami asynchronicznymi, niezależnie od ustawień przepływu dla kontekstu wykonywania w bieżącym wątku.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Określa, czy zestawy ze źródeł zdalnych są ładowane jako pełne zaufanie.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Określa, czy środowisko uruchomieniowe korzysta ze starszych zasad zabezpieczeń dostępu kodu (CAS).|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Określa, czy środowisko uruchomieniowe automatycznie naprawia nieprawidłowe deklaracje wywołania platformy w czasie wykonywania, kosztem wolniejszych przejść między zarządzanym i niezarządzanym kodem.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczenia kodów skrótów dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|Określa, że środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Optymalizuje sondę dla zestawów satelickich.|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Określa, czy kopiowanie w tle używa domyślnego zachowania uruchamiania wprowadzonego w .NET Framework 4, czy przywraca zachowanie uruchamiania wcześniejszych wersji .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Określa, że aplikacja może odwoływać się do tego samego zestawu w dwóch różnych implementacjach .NET Framework, przez wyłączenie domyślnego zachowania, które traktuje zestawy jako równoważne do celów przenośności aplikacji.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Zawiera informacje o konfiguracji domyślnej pamięci podręcznej obiektów w pamięci.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|Określa, czy środowisko uruchomieniowe używa starszej wersji formatowania dla <xref:System.TimeSpan> wartości.|
|[\<useLegacyJit>](uselegacyjit-element.md)|Określa, czy środowisko uruchomieniowe języka wspólnego korzysta ze starszego 64-bitowego kompilatora JIT dla kompilacji just in Time.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Określa, czy środowisko uruchomieniowe oblicza kody skrótów dla ciągów na podstawie poszczególnych domen aplikacji.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|Żąda, aby środowisko uruchomieniowe używało jawnych rozmiarów stosu, gdy tworzy pewne wątki używane wewnętrznie, zamiast domyślnego rozmiaru stosu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|

## <a name="remarks"></a>Uwagi

Elementy podrzędne w [\<runtime>](runtime-element.md) sekcji pliku konfiguracji są używane przez środowisko uruchomieniowe języka wspólnego do konfigurowania sposobu działania aplikacji. Na przykład [\<gcServer>](gcserver-element.md) element określa, czy moduł wyrzucania elementów bezużytecznych używa odzyskiwania pamięci stacji roboczej lub wyrzucania elementów bezużytecznych serwera, [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów dla poszczególnych aplikacji lub domen dla poszczególnych aplikacji, a `AppContextSwitchOverrides` element pozwala użytkownikom biblioteki na wybór lub rezygnację z zmiany funkcjonalności udostępnionej przez bibliotekę.

Elementy w [\<runtime>](runtime-element.md) sekcji są odczytywane automatycznie przez środowisko uruchomieniowe języka wspólnego podczas uruchamiania aplikacji. Możesz również zdefiniować plik konfiguracyjny dla domeny aplikacji innej niż domyślna, dostarczając jej nazwę do <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> właściwości; jej ustawienia są odczytywane automatycznie podczas ładowania domeny aplikacji. Jeśli kiedykolwiek wcześniej, koniecznie należy bezpośrednio odczytać ustawienia w [\<runtime>](runtime-element.md) sekcji w pliku konfiguracji aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
