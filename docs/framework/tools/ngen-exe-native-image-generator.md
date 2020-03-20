---
title: Ngen.exe (Generator obrazu natywnego)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
ms.openlocfilehash: 297bc3f9182e76523eda4d4be3112f4d1d7e3fee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741793"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Generator obrazu natywnego)

Generator obrazów natywnych (Ngen.exe) jest narzędziem, które poprawia wydajność zarządzanych aplikacji. Program Ngen.exe tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.

> [!NOTE]
> Program Ngen.exe kompiluje obrazy macierzyste dla zestawów przeznaczonych tylko dla programu .NET Framework. Równoważnym natywnym generatorem obrazu dla .NET Core jest [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).

Zmiany w pliku Ngen.exe w .NET Framework 4:

- Program Ngen.exe obecnie kompiluje zestawy w trybie pełnego zaufania, a zasady zabezpieczeń dostępu kodu (CAS) nie są już uwzględniane.

- Obrazy natywne generowane przez program Ngen.exe nie mogą już być ładowane do aplikacji, które działają w trybie częściowego zaufania.

Zmiany w programie Ngen.exe wprowadzone w programie .NET Framework w wersji 2.0:

- Instalacja zestawu powoduje także instalację jego zależności, co upraszcza składnię programu Ngen.exe.

- Obrazy natywne mogą być współużytkowane w różnych domenach aplikacji.

- Nowa akcja `update`, ponownie tworzy obrazy, które zostały unieważnione.

- Akcje mogą być odraczane w celu wykonania przez usługę, która korzysta z czasu bezczynności komputera, aby generować i instalować obrazy.

- Niektóre przyczyny unieważnienia obrazu zostały wyeliminowane.

W systemie Windows 8 zobacz [Zadanie obrazu natywnego](#native-image-task).

Aby uzyskać dodatkowe informacje na temat korzystania z programu Ngen.exe i natywnej usługi obrazów, zobacz [Natywna usługa obrazów](#native-image-service).

> [!NOTE]
> Składnia Ngen.exe dla wersji 1.0 i 1.1 programu .NET Framework można znaleźć w [legacy syntax Generatora obrazów natywnych (Ngen.exe).](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100))

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a>Akcje

W poniższej tabeli przedstawiono `action`składnię każdego . Opisy poszczególnych części `action`tabel , zobacz [Argumenty](#ArgumentTable), Poziomy [priorytetów](#PriorityTable), [Scenariusze](#ScenarioTable)i [Konfiguracje.](#ConfigTable) W [Options](#OptionTable) tabeli `options` Opcje opisano przełączniki pomocy i pomocy.

|Akcja|Opis|
|------------|-----------------|
|`install`[`assemblyName` &#124; `assemblyPath`] [`scenarios`]`config`[`/queue``:`]`1` [ `2` [ [ `3`&#124;&#124;}]]|Generuje obrazy natywne dla zestawu i jego zależności, a także instaluje obrazy w pamięci podręcznej obrazów natywnych.<br /><br /> Jeśli `/queue` zostanie określona, akcja jest umieszczana w kolejce dla usługi obrazu macierzystego. Domyślnym priorytetem jest 3. Zobacz tabelę [Poziomy priorytetów.](#PriorityTable)|
|`uninstall`[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Usuwa obrazy natywne zestawu i jego zależności z pamięci podręcznej obrazów natywnych.<br /><br /> Aby odinstalować pojedynczy obraz i jego zależności, należy użyć tych samych argumentów wiersza polecenia, które zostały użyte podczas instalacji obrazu. **Uwaga:**  Począwszy od programu .NET Framework `uninstall` 4, akcja * nie jest już obsługiwana.|
|`update` [`/queue`]|Aktualizuje obrazy natywne, które stały się nieprawidłowe.<br /><br /> Jeśli `/queue` jest określony, aktualizacje są umieszczane w kolejce dla usługi obrazu macierzystego. Aktualizacje są zawsze planowane z priorytetem 3, więc są uruchamiane, gdy komputer znajduje się w stanie bezczynności.|
|`display`[`assemblyName` &#124; `assemblyPath`]|Wyświetla stan obrazów natywnych dla zestawu i jego zależności.<br /><br /> Jeśli nie zostaną dostarczone argumenty, będą wyświetlane wszystkie dane z pamięci podręcznej obrazów natywnych.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> — lub —<br /><br /> `eqi`[1&#124;2&#124;3]|Wykonuje umieszczone w kolejce zadania kompilacji.<br /><br /> Jeśli określono priorytet, wykonywane są zadania kompilacji z większym lub równym priorytetem. Jeśli nie określono priorytetu, wykonywane są wszystkie skolejkowane zadania kompilacji.|
|`queue`{`pause` &#124; `continue` &#124; `status`}|Wstrzymuje usługę obrazów natywnych, zezwala wstrzymanej usłudze na kontynuowanie działania lub bada stan usługi.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`assemblyName`|Pełna nazwa wyświetlana zestawu. Na przykład `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Uwaga:**  Można podać nazwę zestawu częściowego, na `display` `uninstall` przykład `myAssembly`dla i akcji. <br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|
|`assemblyPath`|Jawna ścieżka zestawu. Można określić pełną lub względną ścieżkę.<br /><br /> Jeśli użytkownik określi nazwę pliku bez ścieżki, zestaw musi znajdować się w bieżącym katalogu.<br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Poziomy priorytetów

|Priorytet|Opis|
|--------------|-----------------|
|`1`|Obrazy natywne są generowane i instalowane natychmiast, bez czekania na okres bezczynności.|
|`2`|Obrazy natywne są generowane i instalowane bez czekania na okres bezczynności, ale po zakończeniu wszystkich akcji z priorytetem 1 (i ich zależności).|
|`3`|Obrazy natywne są instalowane, gdy usługa obrazów natywnych wykryje, że komputer jest w stanie bezczynności. Zobacz [Natywna usługa obrazów](#native-image-service).|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a>Scenariusze

|Scenariusz|Opis|
|--------------|-----------------|
|`/Debug`|Generuje obrazy natywne, których można używać w debugerze.|
|`/Profile`|Generuje obrazy natywne, które mogą być używane w profilerze.|
|`/NoDependencies`|Generuje minimalną liczbę obrazów natywnych wymaganą przez opcje określonego scenariusza.|

<a name="ConfigTable"></a>

## <a name="config"></a>Config

|Konfigurowanie|Opis|
|-------------------|-----------------|
|`/ExeConfig:` `exePath`|Używa konfiguracji określonego zestawu wykonywalnego.<br /><br /> Program Ngen.exe musi podjąć te same decyzje, co moduł ładowania podczas tworzenia powiązania z zależnościami. Gdy składnik udostępniony jest ładowany <xref:System.Reflection.Assembly.Load%2A> w czasie wykonywania, przy użyciu metody, plik konfiguracyjny aplikacji określa zależności, które są ładowane dla składnika udostępnionego — na przykład wersja zależności, która jest ładowana. Przełącznik `/ExeConfig` daje Ngen.exe wskazówki, na których zależności będą ładowane w czasie wykonywania.|
|`/AppBase:` `directoryPath`|Podczas lokalizowania zależności należy użyć określonego katalogu jako podstawy aplikacji.|

<a name="OptionTable"></a>

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|`/silent`|Pomija wyświetlanie komunikatów o sukcesie.|
|`/verbose`|Wyświetla szczegółowe informacje na potrzeby debugowania. **Uwaga:**  Ze względu na ograniczenia systemu operacyjnego ta opcja nie wyświetla tyle dodatkowych informacji w systemach Windows 98 i Windows Millennium Edition.|
|`/help`, `/?`|Wyświetla składnię polecenia i opcje dla aktualnego wydania.|

## <a name="remarks"></a>Uwagi

Użytkownik musi mieć uprawnienia administracyjne, aby uruchomić program Ngen.exe.

> [!CAUTION]
> Nie należy uruchamiać programu Ngen.exe dla zestawów, które nie są w pełni zaufane. Począwszy od programu .NET Framework 4, Ngen.exe kompiluje zestawy z pełnym zaufaniem, a zasady zabezpieczeń dostępu do kodu (CAS) nie są już oceniane.

Począwszy od programu .NET Framework 4, natywnych obrazów, które są generowane z Ngen.exe nie można już ładować do aplikacji, które są uruchomione w częściowym zaufaniu. Zamiast tego wywoływany jest kompilator JIT (Just-In-Time).

Ngen.exe generuje obrazy macierzyste dla `assemblyname` zestawu określonego `install` przez argument do akcji i wszystkich jej zależności. Zależności są ustalane na podstawie odwołań w manifeście zestawu. Jedynym scenariuszem, w którym należy zainstalować zależność oddzielnie jest, gdy aplikacja ładuje <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> go przy użyciu odbicia, na przykład wywołując metodę.

> [!IMPORTANT]
> Nie należy <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> używać metody z obrazami macierzystymi. Obraz załadowany za pomocą tej metody nie może być używany przez inne zestawy w kontekście wykonywania.

Program Ngen.exe utrzymuje licznik zależności. Załóżmy `MyAssembly.exe` na `YourAssembly.exe` przykład, że oba są zainstalowane w rodzimej pamięci podręcznej obrazów, a oba mają odwołania do `OurDependency.dll`. Jeśli `MyAssembly.exe` zostanie odinstalowany, `OurDependency.dll` nie jest odinstalowywane. Jest usuwany `YourAssembly.exe` tylko wtedy, gdy jest również odinstalowany.

Jeśli jest generowany obraz natywny dla zestawu przechowywanego w globalnej pamięci podręcznej zestawów, należy określić jego nazwę wyświetlaną. Zobacz: <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Obrazy natywne, które generuje program Ngen.exe, mogą być współużytkowane w różnych domenach aplikacji. Oznacza to, że można używać programu Ngen.exe w scenariuszach aplikacji, które wymagają współużytkowania zestawów w różnych domenach aplikacji. Aby określić neutralność domeny:

- Zastosuj <xref:System.LoaderOptimizationAttribute> atrybut do aplikacji.

- Ustaw <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> właściwość podczas tworzenia informacji o konfiguracji dla nowej domeny aplikacji.

Zawsze należy używać kodu neutralnego względem domeny podczas ładowania jego zestawu do wielu domen aplikacji. Jeśli obraz natywny zostanie załadowany do niewspółużytkowanej domeny aplikacji po załadowaniu do domeny współużytkowanej, nie będzie można go użyć.

> [!NOTE]
> Kod neutralny względem domeny nie może zostać zwolniony i wydajność może być nieco niższa, szczególnie w przypadku uzyskiwania dostępu do statycznych elementów członkowskich.

W tej sekcji Uwagi:

- [Generowanie obrazów dla różnych scenariuszy](#Scenarios)

- [Określanie, kiedy używać obrazów natywnych](#WhenToUse)

  - [Lepsze wykorzystanie pamięci](#Memory)

  - [Szybsze uruchamianie aplikacji](#Startup)

  - [Podsumowanie zagadnień dotyczących użycia](#UsageSummary)

- [Znaczenie adresów bazy montażowej](#BaseAddresses)

- [Mocna oprawa](#HardBinding)

  - [Określanie wskazówki wiązania dla zależności](#DependencyHint)

  - [Określanie domyślnej wskazówki wiązania dla zestawu](#AssemblyHint)

- [Odroczone przetwarzanie](#Deferred)

- [Obrazy natywne i kompilacja JIT](#JITCompilation)

  - [Nieprawidłowe obrazy](#InvalidImages)

- [Rozwiązywanie problemów](#Troubleshooting)

  - [podgląd dziennika powiązań zestawów](#Fusion)

  - [Asystent debugowania zarządzany JITCompilationStart](#MDA)

  - [Rezygnacja z generowania obrazu natywnego](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Generowanie obrazów dla różnych scenariuszy

Po wygenerowaniu obrazu macierzystego dla zestawu środowisko wykonawcze automatycznie próbuje zlokalizować i użyć tego obrazu macierzystego przy każdym uruchomieniu zestawu. W zależności od scenariuszy użycia można generować wiele obrazów.

Na przykład po uruchomieniu zestawu w debugowaniu lub profilowania scenariusza, środowisko uruchomieniowe `/Debug` szuka `/Profile` obrazu macierzystego, który został wygenerowany z lub opcji. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca standardową kompilację JIT. Jedynym sposobem debugowania obrazów natywnych jest `/Debug` utworzenie obrazu natywnego z opcją.

Akcja `uninstall` rozpoznaje również scenariusze, dzięki czemu można odinstalować wszystkie scenariusze lub tylko wybrane scenariusze.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Określanie, kiedy używać obrazów natywnych

Obrazy natywne zapewniają poprawę wydajności w dwóch obszarach: ulepszone wykorzystanie pamięci i skrócenie czasu uruchamiania.

> [!NOTE]
> Wydajność obrazów natywnych zależy od kilku czynników, które utrudniają analizę, takich jak wzorce dostępu kodu i danych, liczba wywołań, jakie miały miejsce między granicami modułów, a także liczba zależności, które zostały już załadowane przez inne aplikacje. Jedynym sposobem ustalenia, czy obrazy natywne przynoszą korzyść aplikacji, są dokładne pomiary wydajności w kluczowych scenariuszach wdrażania.

<a name="Memory"></a>

### <a name="improved-memory-use"></a>Lepsze wykorzystanie pamięci

Obrazy natywne mogą znacznie poprawić wykorzystanie pamięci, gdy kod jest współużytkowany w różnych procesach. Obrazy natywne są plikami środowiska Windows PE, więc pojedyncza kopia pliku dll może być współużytkowana przez wiele procesów, natomiast kod natywny wytworzony przez kompilator JIT jest przechowywany w pamięci prywatnej i nie może być współużytkowany.

Aplikacje uruchamiane w ramach usług terminalowych również mogą korzystać z udostępnionych stron kodowych.

Ponadto rezygnacja z ładowania kompilatora JIT umożliwia oszczędzenie określonej ilości pamięci dla każdego wystąpienia aplikacji.

<a name="Startup"></a>

### <a name="faster-application-startup"></a>Szybsze uruchamianie aplikacji

Wstępna kompilacja zestawów przy użyciu programu Ngen.exe może poprawić czas uruchamiania niektórych aplikacji. Ogólnie rzecz biorąc, współużytkowanie zestawów składnika przez aplikacje przynosi zyski, ponieważ po uruchomieniu pierwszej aplikacji składniki współużytkowane są już załadowane dla kolejnych aplikacji. Podczas zimnego uruchamiania nie występują takie zyski z wykorzystania obrazów natywnych, ponieważ każdy zestaw aplikacji musi zostać załadowany z dysku twardego, przez co czas dostępu do dysku twardego przeważa zyski ze współużytkowania.

Trwałe powiązania mogą wpływać na czas uruchamiania, ponieważ wszystkie obrazy trwale powiązane z głównym zestawem aplikacji muszą zostać załadowane w tym samym czasie.

> [!NOTE]
> Przed dodatkiem Service Pack 1 programu .NET Framework 3.5 należy umieścić udostępnione komponenty o silnej nazwie w globalnej pamięci podręcznej zestawów, ponieważ moduł ładujący wykonuje dodatkowe sprawdzanie poprawności w zestawach o silnych nazwach, które nie znajdują się w globalnej pamięci podręcznej zestawów, skutecznie eliminując wszelkie ulepszenia w czasie uruchamiania uzyskane przy użyciu obrazów natywnych. Optymalizacje wprowadzone w pliku .NET Framework 3.5 z dodatkiem SP1 usunęły dodatkowe sprawdzanie poprawności.

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a>Podsumowanie zagadnień dotyczących użycia

Następujące zagadnienia ogólne i dotyczące aplikacji mogą pomóc zadecydować, czy warto używać obrazów natywnych dla swojej aplikacji:

- Obrazy natywne są ładowane szybciej niż pliki MSIL, ponieważ eliminują potrzebę wykonywania wielu działań podczas uruchamiania, takich jak kompilacja JIT i weryfikacja bezpieczeństwa typów.

- Obrazy natywne wymagają mniejszego początkowego zestawu roboczego, ponieważ nie ma potrzeby wczytywania kompilatora JIT.

- Obrazy natywne umożliwiają współużytkowanie kodu przez różne procesy.

- Obrazy natywne wymagają więcej miejsca na dysku twardym niż zestawy MSIL, a ich generowanie może długo trwać.

- Obrazy natywne muszą być obsługiwane.

  - Obrazy muszą być generowane ponownie, gdy oryginalny zestaw lub jedna z jego zależności jest zmieniana.

  - Pojedynczy zestaw może wymagać wielu obrazów natywnych, aby można było używać go w różnych aplikacjach lub scenariuszach. Na przykład informacje o konfiguracji w dwóch aplikacjach mogą powodować różne decyzje dotyczące powiązań dla tego samego zestawu zależnego.

  - Obrazy natywne muszą być generowane przez administratora, czyli za pomocą konta systemu Windows z grupy Administratorzy.

Podczas określania, czy obrazy natywne mogą spowodować poprawę wydajności, oprócz tych ogólnych zagadnień, należy też rozważyć naturę aplikacji.

- Jeśli aplikacja działa w środowisku, w którym jest używanych wiele współużytkowanych składników, obrazy natywne umożliwią współużytkowanie składników przez wiele procesów.

- Jeśli aplikacja używa wielu domen aplikacji, obrazy natywne umożliwią współużytkowanie stron kodu w różnych domenach.

    > [!NOTE]
    > W wersjach 1.0 i 1.1 programu .NET Framework obrazów natywnych nie można współużytkować w różnych domenach aplikacji. Inaczej jest w wersji 2.0 i późniejszych.

- Jeśli aplikacja będzie uruchamiana na serwerze terminali, obrazy natywne umożliwią współużytkowanie stron kodu.

- Zazwyczaj korzystne jest kompilowanie do obrazów natywnych dużych aplikacji. Taka kompilacja małych aplikacje zazwyczaj nie przynosi korzyści.

- W przypadku aplikacji działających przez długi czas kompilacja JIT w czasie wykonywania sprawdza się nieco lepiej niż obrazy natywne. (Trwałe powiązania mogą do pewnego stopnia złagodzić różnicę w wydajności).

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a>Znaczenie adresów bazy montażowej

Obrazy natywne są plikami środowiska Windows PE, więc dotyczą ich te same problemy zmiany podstawy, co innych plików wykonywalnych. Spadek wydajności przy relokacji jest jeszcze bardziej widoczny, jeśli są stosowane powiązania trwałe.

Aby ustawić adres podstawowy dla obrazu natywnego, należy użyć odpowiedniej opcji kompilatora, aby ustawić adres podstawowy dla zestawu. Program Ngen.exe używa tego adresu podstawowego dla obrazu natywnego.

> [!NOTE]
> Obrazy natywne są większe niż zestawy zarządzane, na podstawie których zostały utworzone. Adresy podstawowe muszą być obliczane tak, aby zezwalały na te większe rozmiary.

Można użyć narzędzia, takiego jak dumpbin.exe, aby wyświetlić preferowany adres podstawowy obrazu natywnego.

<a name="HardBinding"></a>

## <a name="hard-binding"></a>Mocna oprawa

Trwałe powiązania zwiększają przepustowość i zmniejszają rozmiar zestawu roboczego dla obrazów natywnych. Wadą trwałych powiązań jest fakt, że wszystkie obrazy, które są trwale powiązane z zestawem, muszą być ładowane razem z zestawem. Może to znacznie zwiększyć czas uruchamiania dużych aplikacji.

Trwałe powiązanie jest odpowiednie dla zależności, które są ładowane we wszystkich krytycznych pod względem wydajności scenariuszach aplikacji. Podobnie jak w przypadku każdego aspektu wykorzystania obrazu natywnego, staranne wykonywanie pomiarów wydajności jest jedynym sposobem ustalenia, czy trwałe powiązanie zwiększa wydajność aplikacji.

<xref:System.Runtime.CompilerServices.DependencyAttribute> Atrybuty <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> i umożliwiają dostarczanie twardych wskazówek dotyczących wiązania do pliku Ngen.exe.

> [!NOTE]
> Te atrybuty są wskazówkami dla programu Ngen.exe, a nie poleceniami. Użycie ich nie gwarantuje uzyskania trwałego powiązania. Znaczenie tych atrybutów może się zmieniać w przyszłych wersjach.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Określanie wskazówki wiązania dla zależności

Zastosuj <xref:System.Runtime.CompilerServices.DependencyAttribute> do zestawu, aby wskazać prawdopodobieństwo, że określona zależność zostanie załadowana. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>wskazuje, że wiązanie <xref:System.Runtime.CompilerServices.LoadHint.Default> twarde jest odpowiednie, wskazuje, że należy <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> użyć wartości domyślnej zależności i wskazuje, że wiązanie twarde nie jest odpowiednie.

Poniższy kod pokazuje atrybuty dla zestawu mającego dwie zależności. Pierwsza zależność (Assembly1) jest odpowiednim kandydatem dla trwałego powiązania, ale druga zależność (Assembly2) nie jest.

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

Nazwa zestawu nie zawiera rozszerzenia nazwy pliku. Można używać nazw wyświetlanych.

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Określanie domyślnej wskazówki wiązania dla zestawu

Domyślne wskazówki powiązania potrzebne są tylko zestawom, które będą stosowane natychmiastowo i często przez dowolną aplikację, która jest od nich zależna. Zastosuj <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> z <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> do takich zestawów, aby określić, że należy użyć wiązania twardego.

> [!NOTE]
> Nie ma powodu, <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> aby zastosować do .dll zestawy, które nie należą do tej kategorii, <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> ponieważ stosowanie atrybutu z dowolnej wartości innej niż ma taki sam efekt jak nie stosowanie atrybutu w ogóle.

Firma Microsoft <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> używa do określenia, że twarde powiązanie jest domyślne dla bardzo małej liczby zestawów w programie .NET Framework, takich jak mscorlib.dll.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Odroczone przetwarzanie

Generowanie obrazów natywnych dla bardzo dużych aplikacji może zająć znaczną ilość czasu. Podobnie zmiany składnika współużytkowanego lub zmiany w ustawieniach komputera mogą wymagać aktualizacji wielu obrazów natywnych. Akcje `install` `update` i akcje `/queue` mają opcję, która kolejkuje operację dla odroczonego wykonania przez natywną usługę obrazu. Ponadto Ngen.exe ma `queue` `executeQueuedItems` i akcje, które zapewniają pewną kontrolę nad usługą. Aby uzyskać więcej informacji, zobacz [Natywna usługa obrazów](#native-image-service).

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Obrazy natywne i kompilacja JIT

Jeśli program Ngen.exe napotka w zestawie jakiekolwiek metody, których nie może wygenerować, wyklucza je z obrazu natywnego. Gdy środowisko uruchomieniowe wykonuje zestaw, przywraca kompilację JIT dla metod, które nie zostały uwzględnione w obrazie natywnym.

Ponadto obrazy natywne nie są używane, jeśli zestaw został uaktualniony lub jeśli obraz został unieważniony z jakiegokolwiek powodu.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Nieprawidłowe obrazy

Użycie programu Ngen.exe w celu utworzenia obrazu natywnego zestawu powoduje, że dane wyjściowe zależą od opcji wiersza polecenia, które można określić, i niektórych ustawień na komputerze. Są to m.in. następujące ustawienia:

- Wersja programu .NET Framework.

- Wersja systemu operacyjnego, jeśli zmiana jest z rodziny Windows 9x do rodziny Windows NT.

- Dokładna tożsamość zestawu (ponowna kompilacja zmienia tożsamość).

- Dokładna tożsamość wszystkich zestawów, do których odwołuje się zestaw (ponowna kompilacja zmienia tożsamość).

- Czynniki związane z zabezpieczeniami.

Program Ngen.exe rejestruje te informacje podczas generowania obrazu natywnego. Podczas wykonywania zestawu środowisko uruchomieniowe poszukuje obrazu natywnego wygenerowanego z użyciem opcji i ustawień, które odpowiadają bieżącemu środowisku komputera. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca kompilację JIT zestawu. Następujące zmiany w ustawieniach komputera i środowiska powodują, że obrazy natywne stają się nieprawidłowe:

- Wersja programu .NET Framework.

     Jeśli zastosowano aktualizację programu .NET Framework, wszystkie obrazy natywne utworzone przy użyciu programu Ngen.exe stają się nieprawidłowe. Z tego powodu wszystkie aktualizacje programu `Ngen Update` .NET Framework wykonują polecenie, aby upewnić się, że wszystkie obrazy macierzyste są ponownie generowane. Program .NET Framework automatycznie tworzy nowe obrazy natywne dla bibliotek programu .NET Framework, które instaluje.

- Wersja systemu operacyjnego, jeśli zmiana jest z rodziny Windows 9x do rodziny Windows NT.

     Jeśli na przykład wersja systemu operacyjnego działającego na komputerze zmieni się z systemu Windows 98 na Windows XP, wszystkie obrazy macierzyste przechowywane w pamięci podręcznej obrazu macierzystego staną się nieprawidłowe. Jeśli jednak system operacyjny zmieni się z systemu Windows 2000 na Windows XP, obrazy nie zostaną unieważnione.

- Dokładna tożsamość zestawu.

     Jeśli zestaw zostanie ponownie skompilowany, obraz natywny odpowiadający zestawowi staje się nieprawidłowy.

- Dokładna tożsamość jakichkolwiek zestawów, do których odwołuje się zestaw.

     Jeżeli zestaw zarządzany zostanie zaktualizowany, wszystkie obrazy natywne zależne bezpośrednio lub pośrednio od tego zestawu stają się nieprawidłowe i muszą zostać wygenerowane ponownie. Obejmuje to zarówno zwykłe odwołania, jak i trwale powiązane zależności. Za każdym razem, gdy zastosowana jest `Ngen Update` aktualizacja oprogramowania, program instalacyjny powinien wykonać polecenie, aby upewnić się, że wszystkie zależne obrazy macierzyste są ponownie generowane.

- Czynniki związane z zabezpieczeniami.

     Zmiana zasad zabezpieczeń komputera ograniczająca uprawnienia udzielone uprzednio zestawowi może spowodować, że poprzednio skompilowane obrazy natywne dla tego zestawu staną się nieprawidłowe.

     Aby uzyskać szczegółowe informacje o tym, jak środowisko wykonawcze wspólnego języka administruje zabezpieczeniami dostępu do kodu i jak korzystać z uprawnień, zobacz [Zabezpieczenia dostępu do kodu](../misc/code-access-security.md).

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Poniższe tematy rozwiązywania problemów pozwalają zobaczyć, które obrazy natywne są używane, a które nie mogą być używane przez aplikację, aby określić, kiedy kompilator JIT rozpoczyna kompilowanie metody i pokazuje, jak zrezygnować z kompilacji obrazu natywnego określony Metody.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>podgląd dziennika powiązań zestawów

Aby potwierdzić, że obrazy natywne są używane przez aplikację, można użyć [pliku Fuslogvw.exe (Przeglądarka dzienników wiązania zestawu).](fuslogvw-exe-assembly-binding-log-viewer.md) Wybierz **pozycję Obrazy natywne** w polu **Kategorie dzienników** w oknie przeglądarki dzienników powiązań. Program Fuslogvw.exe dostarcza informacje o tym, dlaczego obraz natywny został odrzucony.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>Asystent debugowania zarządzany JITCompilationStart

Za pomocą [asystenta debugowania zarządzanego jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) (MDA) można określić, kiedy kompilator JIT rozpoczyna kompilowanie funkcji.

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Rezygnacja z generowania obrazu natywnego

W niektórych przypadkach NGen.exe może mieć trudności z generowaniem obrazu macierzystego dla określonej metody lub może wolisz, aby metoda była JIT skompilowana, a następnie skompilowana do obrazu macierzystego. W takim przypadku można `System.Runtime.BypassNGenAttribute` użyć atrybutu, aby zapobiec NGen.exe generowania obrazu macierzystego dla określonej metody. Atrybut musi być stosowany indywidualnie do każdej metody, której kod nie ma być uwzględnionych w obrazie macierzystym. Program NGen.exe rozpoznaje atrybut i nie generuje kodu w obrazie macierzystym dla odpowiedniej metody.

Należy jednak zauważyć, że `BypassNGenAttribute` nie jest zdefiniowany jako typ w bibliotece klas .NET Framework. Aby korzystać z atrybutu w kodzie, należy najpierw zdefiniować go w następujący sposób:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Następnie można zastosować atrybut na podstawie dla metody. Poniższy przykład instruuje generator obrazu macierzystego, że `ExampleClass.ToJITCompile` nie należy generować obrazu macierzystego dla metody.

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Przykłady

Następujące polecenie generuje obraz macierzysty dla `ClientApp.exe`programu , znajdującego się w bieżącym katalogu i instaluje obraz w pamięci podręcznej obrazu macierzystego. Jeśli istnieje plik konfiguracji zestawu, program Ngen.exe go użyje. Ponadto obrazy natywne są generowane dla `ClientApp.exe` wszystkich plików dll, które się odwołują.

```console
ngen install ClientApp.exe
```

Obraz instalowany za pomocą programu Ngen.exe jest również nazywany elementem głównym. Elementem głównym może być aplikacja albo składnik współużytkowany.

Następujące polecenie generuje obraz macierzysty dla `MyAssembly.exe` z określoną ścieżką.

```console
ngen install c:\myfiles\MyAssembly.exe
```

Podczas lokalizowania zestawów i ich zależności program Ngen.exe używa tej samej logiki badania, co środowisko uruchomieniowe języka wspólnego (CLR). Domyślnie katalog, który `ClientApp.exe` zawiera jest używany jako katalog podstawowy aplikacji i wszystkie sondowanie zestawu rozpoczyna się w tym katalogu. To zachowanie można zastąpić za `/AppBase` pomocą tej opcji.

> [!NOTE]
> Zachowanie to różni się od zachowania programu Ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, gdzie podstawa aplikacji znajduje się w bieżącym katalogu.

Zestaw może mieć zależność bez odwołania, na przykład jeśli ładuje plik <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .dll przy użyciu metody. Obraz macierzysty dla takiego pliku dll można utworzyć przy użyciu informacji `/ExeConfig` o konfiguracji dla złożenia aplikacji z opcją. Następujące polecenie generuje obraz macierzysty do `MyLib.dll,` korzystania `MyApp.exe`z informacji o konfiguracji z programu .

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Zestawy instalowane w ten sposób nie są usuwane, gdy jest usuwana aplikacja.

Aby odinstalować zależność, należy użyć tych samych opcji wiersza polecenia, które zostały użyte podczas jej instalowania. Następujące polecenie odinstalowuje `MyLib.dll` z poprzedniego przykładu.

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Aby utworzyć obraz natywny dla zestawu w globalnej pamięci podręcznej zestawów, należy użyć nazwy wyświetlanej zestawu. Przykład:

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

Program NGen.exe generuje oddzielny zestaw obrazów dla każdego instalowanego scenariusza. Na przykład poniższe polecenia instalują kompletny zestaw obrazów natywnych dla normalnych operacji, drugi kompletny zestaw na potrzeby debugowania i trzeci na potrzeby profilowania:

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a>Wyświetlanie pamięci podręcznej obrazów natywnych

Obrazy natywne zainstalowane w pamięci podręcznej można wyświetlić przy użyciu programu Ngen.exe. Poniższe polecenie wyświetla wszystkie obrazy natywne znajdujące się w pamięci podręcznej obrazów natywnych.

```console
ngen display
```

Akcja `display` zawiera najpierw listę wszystkich zestawów głównych, a następnie listę wszystkich obrazów natywnych na komputerze.

Prosta nazwa zestawu służy do wyświetlania informacji dotyczących tylko tego zestawu. Następujące polecenie wyświetla wszystkie obrazy natywne w `MyAssembly`pamięci podręcznej obrazu macierzystego, które pasują `MyAssembly`do nazwy częściowej, ich zależności i wszystkich katalogów głównych, które mają zależność od:

```console
ngen display MyAssembly
```

Wiedząc, jakie katalogi główne zależą od zestawu współużytkującego składnika jest przydatne w pomiarze wpływu `update` akcji po uaktualnieniu składnika udostępnionego.

Aby określić rozszerzenie pliku zestawu, należy określić ścieżkę lub wykonać program Ngen.exe z katalogu zawierającego zestaw:

```console
ngen display c:\myApps\MyAssembly.exe
```

Następujące polecenie wyświetla wszystkie obrazy natywne `MyAssembly` w pamięci podręcznej obrazu macierzystego z nazwą i wersją 1.0.0.0.

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Aktualizacja obrazów

Obrazy są zazwyczaj aktualizowane po uaktualnieniu składnika współużytkowanego. Aby zaktualizować wszystkie obrazy macierzyste, które uległy zmianie `update` lub których zależności uległy zmianie, użyj akcji bez argumentów.

```console
ngen update
```

Aktualizacja wszystkich obrazów może być długotrwałym procesem. Aktualizacje można kolejkować do wykonania przez `/queue` natywną usługę obrazu przy użyciu opcji. Aby uzyskać więcej `/queue` informacji na temat priorytetów opcji i instalacji, zobacz [Natywna usługa obrazów](#native-image-service).

```console
ngen update /queue
```

### <a name="uninstalling-images"></a>Odinstalowywanie obrazów

Program Ngen.exe utrzymuje listę zależności, aby składniki współużytkowane były usuwane tylko wtedy, gdy wszystkie zestawy, które od nich zależą, zostały usunięte. Ponadto współużytkowany składnik nie zostanie usunięty, jeśli został zainstalowany jako element główny.

Następujące polecenie odinstalowuje wszystkie scenariusze dla katalogu głównego: `ClientApp.exe`

```console
ngen uninstall ClientApp
```

Akcja `uninstall` może służyć do usuwania określonych scenariuszy. Następujące polecenie odinstalowuje wszystkie scenariusze debugowania dla: `ClientApp.exe`

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> Odinstalowanie `/debug` scenariuszy nie powoduje odinstalowania scenariusza, który obejmuje zarówno `/profile``/debug.`

Następujące polecenie odinstalowuje wszystkie scenariusze `ClientApp.exe`dla określonej wersji:

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

Następujące polecenia odinstalować wszystkie `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` scenariusze dla lub tylko scenariusz debugowania dla tego zestawu:

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

Podobnie jak `install` w odniesieniu do akcji, dostarczanie rozszerzenia wymaga wykonania pliku Ngen.exe z katalogu zawierającego zestaw lub określenia pełnej ścieżki.

Aby zapoznać się z przykładami dotyczącymi usługi obrazu natywnego, zobacz [Usługa obrazu natywnego](#native-image-service).

## <a name="native-image-task"></a>Obraz macierzysty — zadanie

Zadanie obrazu macierzystego jest zadaniem systemu Windows, które generuje i przechowuje obrazy natywne. Zadanie obrazu macierzystego generuje i odzyskuje obrazy natywne automatycznie dla obsługiwanych scenariuszy. Umożliwia również instalatorom użycie [pliku Ngen.exe (Generator natywnych obrazów)](ngen-exe-native-image-generator.md) do tworzenia i aktualizowania obrazów natywnych w odroczonym czasie.

Zadanie obrazu macierzystego jest rejestrowane raz dla każdej architektury procesora obsługiwanego na komputerze, aby umożliwić kompilację dla aplikacji przeznaczonych dla każdej architektury:

|Nazwa zadania|Komputer 32-bitowy|Komputer 64-bitowy|
|---------------|----------------------|----------------------|
|NET Framework NGEN v4.0.30319|Tak|Tak|
|NET Framework NGEN v4.0.30319 64|Nie|Tak|

Zadanie obrazu macierzystego jest dostępne w programie .NET Framework 4.5 i nowszych wersjach, gdy jest uruchomione w systemie Windows 8 lub nowszym. We wcześniejszych wersjach systemu Windows program .NET Framework używa [usługi obrazu macierzystego](#native-image-service).

### <a name="task-lifetime"></a>Okres istnienia zadania

Ogólnie rzecz biorąc harmonogram zadań systemu Windows uruchamia zadanie obrazu macierzystego każdej nocy, gdy komputer jest bezczynny. Zadanie sprawdza, czy nie ma odroczonej pracy, która jest umieszczana w kolejce przez instalatory aplikacji, wszelkich odroczonych żądań aktualizacji obrazu macierzystego i automatycznego tworzenia obrazu. Zadanie kończy zaległe elementy robocze, a następnie zamyka się. Jeśli komputer przestanie być bezczynny podczas pracy zadania, zadanie zostanie zatrzymane.

Zadanie obrazu macierzystego można również uruchomić ręcznie za pomocą interfejsu użytkownika harmonogramu zadań lub za pomocą ręcznych wywołań NGen.exe. Jeśli zadanie zostanie uruchomione za pomocą jednej z tych metod, będzie ono nadal działać, gdy komputer nie jest już bezczynny. Obrazy tworzone ręcznie przy użyciu programu NGen.exe mają priorytetowe priorytety, aby umożliwić przewidywalne zachowanie instalatorów aplikacji.

## <a name="native-image-service"></a>Usługa obrazu macierzystego

Natywna usługa obrazu to usługa systemu Windows, która generuje i przechowuje obrazy natywne. Natywna usługa obrazu umożliwia deweloperowi odroczenie instalacji i aktualizacji obrazów natywnych do okresów, gdy komputer jest bezczynny.

Zwykle natywna usługa obrazu jest inicjowana przez program instalacyjny (instalator) dla aplikacji lub aktualizacji. Dla akcji o priorytecie 3 usługa jest wykonywana w czasie bezczynnym na komputerze. Usługa zapisuje swój stan i jest w stanie kontynuować przez wiele ponownych rozruchów, jeśli to konieczne. Wiele kompilacji obrazów można umieszczać w kolejce.

Usługa współdziała również z instrukcją Ngen.exe polecenia. Polecenia ręczne mają pierwszeństwo przed aktywnością w tle.

> [!NOTE]
> W systemie Windows Vista nazwa wyświetlana dla natywnej usługi obrazów to "Microsoft.NET Framework NGEN v2.0.50727_X86" lub "Microsoft.NET Framework NGEN v2.0.50727_X64". We wszystkich wcześniejszych wersjach systemu Microsoft Windows nazwa to ".NET Runtime Optimization Service v2.0.50727_X86" lub ".NET Runtime Optimization Service v2.0.50727_X64".

### <a name="launching-deferred-operations"></a>Uruchamianie odroczonych operacji

Przed rozpoczęciem instalacji lub uaktualnienia zaleca się wstrzymanie usługi. Gwarantuje to, że usługa nie jest wykonywana, gdy instalator kopiuje pliki lub umieszcza zestawy w globalnej pamięci podręcznej zestawów. Następujący wiersz polecenia Ngen.exe wstrzymuje usługę:

```console
ngen queue pause
```

Gdy wszystkie odroczone operacje zostały umieszczone w kolejce, następujące polecenie umożliwia wznowienie usługi:

```console
ngen queue continue
```

Aby odroczyć generowanie obrazu natywnego podczas instalowania nowej `/queue` aplikacji `install` lub `update` podczas aktualizowania udostępnionego składnika, użyj opcji z lub akcji. Następujące wiersze polecenia Ngen.exe instalują obraz macierzysty dla udostępnionego składnika i wykonują aktualizację wszystkich katalogów głównych, których mogło to dotyczyć:

```console
ngen install MyComponent /queue
ngen update /queue
```

Akcja `update` regeneruje wszystkie obrazy natywne, które `MyComponent`zostały unieważnione, a nie tylko te, które używają .

Jeśli aplikacja składa się z wielu katalogów głównych, można kontrolować priorytet odroczonych akcji. Następujące polecenia kolejkują instalację trzech katalogów głównych. `Assembly1`jest zainstalowany jako pierwszy, bez czekania na czas bezczynny. `Assembly2`jest również zainstalowany bez oczekiwania na czas bezczynny, ale po zakończeniu wszystkich działań priorytetowych 1. `Assembly3`jest instalowany, gdy usługa wykryje, że komputer jest bezczynny.

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Można wymusić akcje w kolejce do wystąpienia `executeQueuedItems` synchronicznie przy użyciu akcji. Jeśli podasz opcjonalny priorytet, ta akcja dotyczy tylko akcji w kolejce, które mają równy lub niższy priorytet. Domyślny priorytet to 3, więc następujące polecenie Ngen.exe natychmiast przetwarza wszystkie akcje w kolejce i nie zwraca się, dopóki nie zostaną zakończone:

```console
ngen executeQueuedItems
```

Polecenia synchroniczne są wykonywane przez Ngen.exe i nie korzystają z natywnej usługi obrazu. Akcje można wykonywać przy użyciu programu Ngen.exe, gdy jest uruchomiona natywna usługa obrazu.

### <a name="service-shutdown"></a>Zamknięcie usługi

Po zainicjowaniu przez wykonanie polecenia Ngen.exe, `/queue` które zawiera opcję, usługa jest uruchamiana w tle, dopóki wszystkie akcje nie zostaną zakończone. Usługa zapisuje swój stan, dzięki czemu można kontynuować przez wiele ponownych rozruchów, jeśli to konieczne. Gdy usługa wykryje, że nie ma więcej akcji w kolejce, resetuje swój stan, tak aby nie można ponownie uruchomić następnym uruchomieniu komputera, a następnie zamyka się w dół.

### <a name="service-interaction-with-clients"></a>Interakcja z usługami z klientami

W wersji 2.0 programu .NET Framework jedyną interakcją z natywną usługą obrazu jest narzędzie wiersza polecenia Ngen.exe. Narzędzie wiersza polecenia w skryptach instalacyjnych umożliwia kolejkowanie akcji dla natywnej usługi obrazu i interakcję z usługą.

## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Proces zarządzanego wykonania](../../standard/managed-execution-process.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
