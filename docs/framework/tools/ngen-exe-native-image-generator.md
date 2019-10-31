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
ms.openlocfilehash: e6c4baae854e5997b153e1363ca8ed4204e10e2b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085207"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Generator obrazu natywnego)

Generator obrazów natywnych (Ngen.exe) jest narzędziem, które poprawia wydajność zarządzanych aplikacji. Program Ngen.exe tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.

> [!NOTE]
> Ngen. exe kompiluje obrazy natywne dla zestawów, które są przeznaczone tylko dla .NET Framework. Równoważny Generator obrazu natywnego dla platformy .NET Core to [CrossGen](https://github.com/dotnet/coreclr/blob/master/Documentation/building/crossgen.md). 

Zmiany w programie Ngen. exe w .NET Framework 4:

- Program Ngen.exe obecnie kompiluje zestawy w trybie pełnego zaufania, a zasady zabezpieczeń dostępu kodu (CAS) nie są już uwzględniane.

- Obrazy natywne generowane przez program Ngen.exe nie mogą już być ładowane do aplikacji, które działają w trybie częściowego zaufania.

Zmiany w programie Ngen.exe wprowadzone w programie .NET Framework w wersji 2.0:

- Instalacja zestawu powoduje także instalację jego zależności, co upraszcza składnię programu Ngen.exe.

- Obrazy natywne mogą być współużytkowane w różnych domenach aplikacji.

- Nowa akcja `update`ponownie tworzy obrazy, które zostały unieważnione.

- Akcje mogą być odraczane w celu wykonania przez usługę, która korzysta z czasu bezczynności komputera, aby generować i instalować obrazy.

- Niektóre przyczyny unieważnienia obrazu zostały wyeliminowane.

W systemie Windows 8 zobacz [zadania obrazu natywnego](#native-image-task).

Aby uzyskać dodatkowe informacje na temat korzystania z programu Ngen. exe i usługi obrazów natywnych, zobacz [Native Image Service](#native-image-service).

> [!NOTE]
> Składnię programu Ngen. exe dla wersji 1,0 i 1,1 .NET Framework można znaleźć w [starszej składni generatora obrazów natywnych (Ngen. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a>Akcje

W poniższej tabeli przedstawiono składnię poszczególnych `action`. Aby uzyskać opisy poszczególnych części `action`, zobacz [argumenty](#ArgumentTable), [poziomy priorytetów](#PriorityTable), [scenariusze](#ScenarioTable)i tabele [konfiguracyjne](#ConfigTable) . W tabeli [Options](#OptionTable) opisano `options` i przełączenia pomocy.

|Akcja|Opis|
|------------|-----------------|
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Generuje obrazy natywne dla zestawu i jego zależności, a także instaluje obrazy w pamięci podręcznej obrazów natywnych.<br /><br /> Jeśli `/queue` jest określona, akcja zostanie umieszczona w kolejce dla usługi obrazów natywnych. Domyślnym priorytetem jest 3. Zobacz tabelę [poziomów priorytetów](#PriorityTable) .|
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Usuwa obrazy natywne zestawu i jego zależności z pamięci podręcznej obrazów natywnych.<br /><br /> Aby odinstalować pojedynczy obraz i jego zależności, należy użyć tych samych argumentów wiersza polecenia, które zostały użyte podczas instalacji obrazu. **Uwaga:**  Począwszy od .NET Framework 4, Akcja `uninstall` * nie jest już obsługiwana.|
|`update` [`/queue`]|Aktualizuje obrazy natywne, które stały się nieprawidłowe.<br /><br /> Jeśli określono `/queue`, aktualizacje są umieszczane w kolejce dla usługi obrazów natywnych. Aktualizacje są zawsze planowane z priorytetem 3, więc są uruchamiane, gdy komputer znajduje się w stanie bezczynności.|
|`display` [`assemblyName` &#124; `assemblyPath`]|Wyświetla stan obrazów natywnych dla zestawu i jego zależności.<br /><br /> Jeśli nie zostaną dostarczone argumenty, będą wyświetlane wszystkie dane z pamięci podręcznej obrazów natywnych.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> —lub—<br /><br /> `eqi` [1&#124;2&#124;3]|Wykonuje umieszczone w kolejce zadania kompilacji.<br /><br /> Jeśli określono priorytet, wykonywane są zadania kompilacji z większym lub równym priorytetem. Jeśli nie określono priorytetu, wykonywane są wszystkie skolejkowane zadania kompilacji.|
|`queue` {`pause` &#124; `continue` &#124; `status`}|Wstrzymuje usługę obrazów natywnych, zezwala wstrzymanej usłudze na kontynuowanie działania lub bada stan usługi.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`assemblyName`|Pełna nazwa wyświetlana zestawu. Na przykład `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Uwaga:**  Dla akcji `display` i `uninstall` można podać częściową nazwę zestawu, taką jak `myAssembly`. <br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|
|`assemblyPath`|Jawna ścieżka zestawu. Można określić pełną lub względną ścieżkę.<br /><br /> Jeśli użytkownik określi nazwę pliku bez ścieżki, zestaw musi znajdować się w bieżącym katalogu.<br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Poziomy priorytetów

|Priorytet|Opis|
|--------------|-----------------|
|`1`|Obrazy natywne są generowane i instalowane natychmiast, bez czekania na okres bezczynności.|
|`2`|Obrazy natywne są generowane i instalowane bez czekania na okres bezczynności, ale po zakończeniu wszystkich akcji z priorytetem 1 (i ich zależności).|
|`3`|Obrazy natywne są instalowane, gdy usługa obrazów natywnych wykryje, że komputer jest w stanie bezczynności. Zobacz [Native Image Service](#native-image-service).|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a>Scenariusze

|Scenariusz|Opis|
|--------------|-----------------|
|`/Debug`|Generuje obrazy natywne, których można używać w debugerze.|
|`/Profile`|Generuje obrazy natywne, które mogą być używane w profilerze.|
|`/NoDependencies`|Generuje minimalną liczbę obrazów natywnych wymaganą przez opcje określonego scenariusza.|

<a name="ConfigTable"></a>

## <a name="config"></a>Konfiguracja

|Konfiguracja|Opis|
|-------------------|-----------------|
|`/ExeConfig:``exePath`|Używa konfiguracji określonego zestawu wykonywalnego.<br /><br /> Program Ngen.exe musi podjąć te same decyzje, co moduł ładowania podczas tworzenia powiązania z zależnościami. Gdy składnik współużytkowany jest ładowany w czasie wykonywania, przy użyciu metody <xref:System.Reflection.Assembly.Load%2A>, plik konfiguracyjny aplikacji określa zależności, które są ładowane dla składnika współużytkowanego — na przykład wersję załadowanej zależności. Przełącznik `/ExeConfig` zapewnia wskazówki dotyczące programu Ngen. exe, na których zależności zostałyby załadowane w czasie wykonywania.|
|`/AppBase:``directoryPath`|Podczas lokalizowania zależności należy użyć określonego katalogu jako podstawy aplikacji.|

<a name="OptionTable"></a>

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|`/silent`|Pomija wyświetlanie komunikatów o sukcesie.|
|`/verbose`|Wyświetla szczegółowe informacje na potrzeby debugowania. **Uwaga:**  Ze względu na ograniczenia systemu operacyjnego ta opcja nie wyświetla więcej informacji o systemach Windows 98 i Windows Millennium Edition.|
|`/help`, `/?`|Wyświetla składnię polecenia i opcje dla aktualnego wydania.|

## <a name="remarks"></a>Uwagi

Użytkownik musi mieć uprawnienia administracyjne, aby uruchomić program Ngen.exe.

> [!CAUTION]
> Nie należy uruchamiać programu Ngen.exe dla zestawów, które nie są w pełni zaufane. Począwszy od .NET Framework 4, Ngen. exe kompiluje zestawy z pełnym zaufaniem, a zasady zabezpieczeń dostępu kodu (CAS) nie są już oceniane.

Począwszy od .NET Framework 4, obrazy natywne, które są generowane przy użyciu programu Ngen. exe, nie mogą być już ładowane do aplikacji, które działają w częściowej relacji zaufania. Zamiast tego wywoływany jest kompilator JIT (Just-In-Time).

Program Ngen. exe generuje obrazy natywne dla zestawu określonego przez argument `assemblyname` do akcji `install` i wszystkich jej zależności. Zależności są ustalane na podstawie odwołań w manifeście zestawu. Jedyny scenariusz, w którym należy zainstalować zależność osobno, to kiedy aplikacja ładuje ją przy użyciu odbicia, na przykład przez wywołanie metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.

> [!IMPORTANT]
> Nie należy używać metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> z obrazami natywnymi. Obraz załadowany za pomocą tej metody nie może być używany przez inne zestawy w kontekście wykonywania.

Program Ngen.exe utrzymuje licznik zależności. Załóżmy na przykład, że `MyAssembly.exe` i `YourAssembly.exe` są zainstalowane w pamięci podręcznej obrazów natywnych, a obydwie zawierają odwołania do `OurDependency.dll`. Jeśli `MyAssembly.exe` zostanie odinstalowany, `OurDependency.dll` nie zostanie odinstalowany. Jest on usuwany tylko wtedy, gdy `YourAssembly.exe` również zostanie odinstalowany.

Jeśli jest generowany obraz natywny dla zestawu przechowywanego w globalnej pamięci podręcznej zestawów, należy określić jego nazwę wyświetlaną. Zobacz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Obrazy natywne, które generuje program Ngen.exe, mogą być współużytkowane w różnych domenach aplikacji. Oznacza to, że można używać programu Ngen.exe w scenariuszach aplikacji, które wymagają współużytkowania zestawów w różnych domenach aplikacji. Aby określić neutralność domeny:

- Zastosuj atrybut <xref:System.LoaderOptimizationAttribute> do aplikacji.

- Ustaw właściwość <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> podczas tworzenia informacji o konfiguracji dla nowej domeny aplikacji.

Zawsze należy używać kodu neutralnego względem domeny podczas ładowania jego zestawu do wielu domen aplikacji. Jeśli obraz natywny zostanie załadowany do niewspółużytkowanej domeny aplikacji po załadowaniu do domeny współużytkowanej, nie będzie można go użyć.

> [!NOTE]
> Kod neutralny względem domeny nie może zostać zwolniony i wydajność może być nieco niższa, szczególnie w przypadku uzyskiwania dostępu do statycznych elementów członkowskich.

W tej sekcji uwag:

- [Generowanie obrazów dla różnych scenariuszy](#Scenarios)

- [Ustalanie, kiedy należy używać obrazów natywnych](#WhenToUse)

  - [Ulepszone użycie pamięci](#Memory)

  - [Szybsze uruchamianie aplikacji](#Startup)

  - [Podsumowanie zagadnień dotyczących użycia](#UsageSummary)

- [Ważność adresów podstawowych zestawu](#BaseAddresses)

- [Twarde powiązanie](#HardBinding)

  - [Określanie wskazówki dotyczącej powiązań dla zależności](#DependencyHint)

  - [Określanie domyślnej wskazówki dotyczącej powiązań dla zestawu](#AssemblyHint)

- [Przetwarzanie Odroczone](#Deferred)

- [Obrazy natywne i kompilacja JIT](#JITCompilation)

  - [Nieprawidłowe obrazy](#InvalidImages)

- [Rozwiązywanie problemów](#Troubleshooting)

  - [Podgląd dziennika powiązań zestawów](#Fusion)

  - [Asystent debugowania zarządzanego JITCompilationStart](#MDA)

  - [Rezygnacja z generowania obrazu natywnego](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Generowanie obrazów dla różnych scenariuszy

Po wygenerowaniu obrazu natywnego zestawu środowisko uruchomieniowe automatycznie próbuje zlokalizować i używać tego obrazu natywnego przy każdym uruchomieniu zestawu. W zależności od scenariuszy użycia można generować wiele obrazów.

Na przykład w przypadku uruchomienia zestawu w scenariuszu debugowania lub profilowania środowisko uruchomieniowe szuka obrazu natywnego, który został wygenerowany przy użyciu opcji `/Debug` lub `/Profile`. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca standardową kompilację JIT. Jedynym sposobem debugowania obrazów natywnych jest utworzenie obrazu natywnego z opcją `/Debug`.

Akcja `uninstall` rozpoznaje również scenariusze, dzięki czemu można odinstalować wszystkie scenariusze lub tylko wybrane scenariusze.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Ustalanie, kiedy należy używać obrazów natywnych

Obrazy natywne zapewniają poprawę wydajności w dwóch obszarach: ulepszone wykorzystanie pamięci i skrócenie czasu uruchamiania.

> [!NOTE]
> Wydajność obrazów natywnych zależy od kilku czynników, które utrudniają analizę, takich jak wzorce dostępu kodu i danych, liczba wywołań, jakie miały miejsce między granicami modułów, a także liczba zależności, które zostały już załadowane przez inne aplikacje. Jedynym sposobem ustalenia, czy obrazy natywne przynoszą korzyść aplikacji, są dokładne pomiary wydajności w kluczowych scenariuszach wdrażania.

<a name="Memory"></a>

### <a name="improved-memory-use"></a>Ulepszone użycie pamięci

Obrazy natywne mogą znacznie poprawić wykorzystanie pamięci, gdy kod jest współużytkowany w różnych procesach. Obrazy natywne są plikami środowiska Windows PE, więc pojedyncza kopia pliku dll może być współużytkowana przez wiele procesów, natomiast kod natywny wytworzony przez kompilator JIT jest przechowywany w pamięci prywatnej i nie może być współużytkowany.

Aplikacje uruchamiane w ramach usług terminalowych również mogą korzystać z udostępnionych stron kodowych.

Ponadto rezygnacja z ładowania kompilatora JIT umożliwia oszczędzenie określonej ilości pamięci dla każdego wystąpienia aplikacji.

<a name="Startup"></a>

### <a name="faster-application-startup"></a>Szybsze uruchamianie aplikacji

Wstępna kompilacja zestawów przy użyciu programu Ngen.exe może poprawić czas uruchamiania niektórych aplikacji. Ogólnie rzecz biorąc, współużytkowanie zestawów składnika przez aplikacje przynosi zyski, ponieważ po uruchomieniu pierwszej aplikacji składniki współużytkowane są już załadowane dla kolejnych aplikacji. Podczas zimnego uruchamiania nie występują takie zyski z wykorzystania obrazów natywnych, ponieważ każdy zestaw aplikacji musi zostać załadowany z dysku twardego, przez co czas dostępu do dysku twardego przeważa zyski ze współużytkowania.

Trwałe powiązania mogą wpływać na czas uruchamiania, ponieważ wszystkie obrazy trwale powiązane z głównym zestawem aplikacji muszą zostać załadowane w tym samym czasie.

> [!NOTE]
> Przed .NET Framework 3,5 z dodatkiem Service Pack 1 należy umieścić udostępnione, silnie nazwane składniki w globalnej pamięci podręcznej zestawów, ponieważ moduł ładujący wykonuje dodatkową weryfikację dla zestawów o silnych nazwach, które nie znajdują się w globalnej pamięci podręcznej zestawów, co skutecznie eliminuje Poprawa czasu uruchamiania uzyskana przy użyciu obrazów natywnych. Optymalizacje wprowadzone w .NET Framework 3,5 z dodatkiem SP1 spowodowały usunięcie dodatkowej weryfikacji.

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

## <a name="importance-of-assembly-base-addresses"></a>Ważność adresów podstawowych zestawu

Obrazy natywne są plikami środowiska Windows PE, więc dotyczą ich te same problemy zmiany podstawy, co innych plików wykonywalnych. Spadek wydajności przy relokacji jest jeszcze bardziej widoczny, jeśli są stosowane powiązania trwałe.

Aby ustawić adres podstawowy dla obrazu natywnego, należy użyć odpowiedniej opcji kompilatora, aby ustawić adres podstawowy dla zestawu. Program Ngen.exe używa tego adresu podstawowego dla obrazu natywnego.

> [!NOTE]
> Obrazy natywne są większe niż zestawy zarządzane, na podstawie których zostały utworzone. Adresy podstawowe muszą być obliczane tak, aby zezwalały na te większe rozmiary.

Można użyć narzędzia, takiego jak dumpbin.exe, aby wyświetlić preferowany adres podstawowy obrazu natywnego.

<a name="HardBinding"></a>

## <a name="hard-binding"></a>Twarde powiązanie

Trwałe powiązania zwiększają przepustowość i zmniejszają rozmiar zestawu roboczego dla obrazów natywnych. Wadą trwałych powiązań jest fakt, że wszystkie obrazy, które są trwale powiązane z zestawem, muszą być ładowane razem z zestawem. Może to znacznie zwiększyć czas uruchamiania dużych aplikacji.

Trwałe powiązanie jest odpowiednie dla zależności, które są ładowane we wszystkich krytycznych pod względem wydajności scenariuszach aplikacji. Podobnie jak w przypadku każdego aspektu wykorzystania obrazu natywnego, staranne wykonywanie pomiarów wydajności jest jedynym sposobem ustalenia, czy trwałe powiązanie zwiększa wydajność aplikacji.

Atrybuty <xref:System.Runtime.CompilerServices.DependencyAttribute> i <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> umożliwiają udostępnianie twardych wskazówek do programu Ngen. exe.

> [!NOTE]
> Te atrybuty są wskazówkami dla programu Ngen.exe, a nie poleceniami. Użycie ich nie gwarantuje uzyskania trwałego powiązania. Znaczenie tych atrybutów może się zmieniać w przyszłych wersjach.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Określanie wskazówki dotyczącej powiązań dla zależności

Zastosuj <xref:System.Runtime.CompilerServices.DependencyAttribute> do zestawu, aby wskazać prawdopodobieństwo załadowania określonej zależności. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> wskazuje, że stałe powiązanie jest odpowiednie, <xref:System.Runtime.CompilerServices.LoadHint.Default> wskazuje, że wartość domyślna dla zależności powinna być używana, a <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> wskazuje, że twarde powiązanie nie jest odpowiednie.

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

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Określanie domyślnej wskazówki dotyczącej powiązań dla zestawu

Domyślne wskazówki powiązania potrzebne są tylko zestawom, które będą stosowane natychmiastowo i często przez dowolną aplikację, która jest od nich zależna. Zastosuj <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> z <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> do takich zestawów, aby określić, że ma zostać użyte twarde powiązanie.

> [!NOTE]
> Nie istnieje powód, aby zastosować <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do zestawów dll, które nie należą do tej kategorii, ponieważ zastosowanie atrybutu z jakąkolwiek wartością inną niż <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> ma ten sam skutek, co w ogóle nie stosuje atrybutu.

Firma Microsoft używa <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute>, aby określić, że stałe powiązanie jest wartością domyślną dla bardzo niewielkiej liczby zestawów w .NET Framework, takiej jak mscorlib. dll.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Przetwarzanie Odroczone

Generowanie obrazów natywnych dla bardzo dużych aplikacji może zająć znaczną ilość czasu. Podobnie zmiany składnika współużytkowanego lub zmiany w ustawieniach komputera mogą wymagać aktualizacji wielu obrazów natywnych. Akcje `install` i `update` mają `/queue` opcję, która kolejkuje operację dla odroczonego wykonania przez usługę obrazu natywnego. Ponadto program Ngen. exe ma `queue` i `executeQueuedItems` akcje, które zapewniają kontrolę nad usługą. Aby uzyskać więcej informacji, zobacz [Native Image Service](#native-image-service).

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Obrazy natywne i kompilacja JIT

Jeśli program Ngen.exe napotka w zestawie jakiekolwiek metody, których nie może wygenerować, wyklucza je z obrazu natywnego. Gdy środowisko uruchomieniowe wykonuje zestaw, przywraca kompilację JIT dla metod, które nie zostały uwzględnione w obrazie natywnym.

Ponadto obrazy natywne nie są używane, jeśli zestaw został uaktualniony lub jeśli obraz został unieważniony z jakiegokolwiek powodu.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Nieprawidłowe obrazy

Użycie programu Ngen.exe w celu utworzenia obrazu natywnego zestawu powoduje, że dane wyjściowe zależą od opcji wiersza polecenia, które można określić, i niektórych ustawień na komputerze. Są to m.in. następujące ustawienia:

- Wersja programu .NET Framework.

- Wersja systemu operacyjnego, jeśli zmiana pochodzi z rodziny Windows 9X do rodziny systemu Windows NT.

- Dokładna tożsamość zestawu (ponowna kompilacja zmienia tożsamość).

- Dokładna tożsamość wszystkich zestawów, do których odwołuje się zestaw (ponowna kompilacja zmienia tożsamość).

- Czynniki związane z zabezpieczeniami.

Program Ngen.exe rejestruje te informacje podczas generowania obrazu natywnego. Podczas wykonywania zestawu środowisko uruchomieniowe poszukuje obrazu natywnego wygenerowanego z użyciem opcji i ustawień, które odpowiadają bieżącemu środowisku komputera. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca kompilację JIT zestawu. Następujące zmiany w ustawieniach komputera i środowiska powodują, że obrazy natywne stają się nieprawidłowe:

- Wersja programu .NET Framework.

     Jeśli zastosowano aktualizację programu .NET Framework, wszystkie obrazy natywne utworzone przy użyciu programu Ngen.exe stają się nieprawidłowe. Z tego powodu wszystkie aktualizacje .NET Framework wykonać polecenie `Ngen Update`, aby upewnić się, że wszystkie obrazy natywne zostaną ponownie wygenerowane. Program .NET Framework automatycznie tworzy nowe obrazy natywne dla bibliotek programu .NET Framework, które instaluje.

- Wersja systemu operacyjnego, jeśli zmiana pochodzi z rodziny Windows 9X do rodziny systemu Windows NT.

     Na przykład jeśli wersja systemu operacyjnego działającego na komputerze zmienia się z systemu Windows 98 na system Windows XP, wszystkie obrazy natywne przechowywane w pamięci podręcznej obrazów natywnych staną się nieprawidłowe. Jeśli jednak system operacyjny ulegnie zmianie z systemu Windows 2000 do systemu Windows XP, obrazy nie zostaną unieważnione.

- Dokładna tożsamość zestawu.

     Jeśli zestaw zostanie ponownie skompilowany, obraz natywny odpowiadający zestawowi staje się nieprawidłowy.

- Dokładna tożsamość jakichkolwiek zestawów, do których odwołuje się zestaw.

     Jeżeli zestaw zarządzany zostanie zaktualizowany, wszystkie obrazy natywne zależne bezpośrednio lub pośrednio od tego zestawu stają się nieprawidłowe i muszą zostać wygenerowane ponownie. Obejmuje to zarówno zwykłe odwołania, jak i trwale powiązane zależności. Za każdym razem, gdy aktualizacja oprogramowania zostanie zastosowana, program instalacyjny powinien wykonać polecenie `Ngen Update`, aby upewnić się, że wszystkie zależne obrazy natywne zostaną ponownie wygenerowane.

- Czynniki związane z zabezpieczeniami.

     Zmiana zasad zabezpieczeń komputera ograniczająca uprawnienia udzielone uprzednio zestawowi może spowodować, że poprzednio skompilowane obrazy natywne dla tego zestawu staną się nieprawidłowe.

     Aby uzyskać szczegółowe informacje na temat sposobu, w jaki środowisko uruchomieniowe języka wspólnego administruje zabezpieczeniami dostępu kodu i jak korzystać z uprawnień, zobacz [zabezpieczenia dostępu kodu](../misc/code-access-security.md).

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Poniższe tematy dotyczące rozwiązywania problemów umożliwiają sprawdzenie, które obrazy natywne są używane i które nie mogą być używane przez aplikację, aby określić, kiedy kompilator JIT zaczyna kompilować metodę, i pokazuje, jak zrezygnować z kompilacji obrazu natywnego określonego form.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>podgląd dziennika powiązań zestawów

Aby potwierdzić, że obrazy natywne są używane przez aplikację, można użyć [Fuslogvw. exe (Podgląd dziennika powiązań zestawów)](fuslogvw-exe-assembly-binding-log-viewer.md). Wybierz opcję **obrazy natywne** w polu **kategorie dzienników** w oknie Przeglądarka dzienników powiązań. Program Fuslogvw.exe dostarcza informacje o tym, dlaczego obraz natywny został odrzucony.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>Asystent debugowania zarządzanego JITCompilationStart

Za pomocą asystenta debugowania zarządzanego [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) (MDA) można określić, kiedy kompilator JIT zacznie kompilować funkcję.

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Rezygnacja z generowania obrazu natywnego

W niektórych przypadkach program NGen. exe może mieć problemy z generowaniem obrazu natywnego dla określonej metody lub można preferować, aby Metoda była skompilowana JIT, a następnie skompilowana do obrazu natywnego. W takim przypadku można użyć atrybutu `System.Runtime.BypassNGenAttribute`, aby zapobiec generowaniu przez program NGen. exe obrazu natywnego dla określonej metody. Ten atrybut musi być zastosowany indywidualnie dla każdej metody, której kod nie ma być dołączony do obrazu natywnego. Program NGen. exe rozpoznaje atrybut i nie generuje kodu w obrazie natywnym dla odpowiadającej metody.

Należy jednak pamiętać, że `BypassNGenAttribute` nie jest zdefiniowany jako typ w bibliotece klas .NET Framework. Aby można było użyć atrybutu w kodzie, należy najpierw zdefiniować go w następujący sposób:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Następnie można zastosować atrybut dla poszczególnych metod. Poniższy przykład instruuje Generator obrazu natywnego, że nie powinien generować obrazu natywnego dla metody `ExampleClass.ToJITCompile`.

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Przykłady

Następujące polecenie generuje obraz natywny dla `ClientApp.exe`, znajdujący się w bieżącym katalogu, i instaluje go w pamięci podręcznej obrazów natywnych. Jeśli istnieje plik konfiguracji zestawu, program Ngen.exe go użyje. Ponadto w przypadku plików DLL, do których od`ClientApp.exe` się odwołania, są generowane obrazy natywne.

```console
ngen install ClientApp.exe
```

Obraz instalowany za pomocą programu Ngen.exe jest również nazywany elementem głównym. Elementem głównym może być aplikacja albo składnik współużytkowany.

Następujące polecenie generuje obraz natywny dla `MyAssembly.exe` z określoną ścieżką.

```console
ngen install c:\myfiles\MyAssembly.exe
```

Podczas lokalizowania zestawów i ich zależności program Ngen.exe używa tej samej logiki badania, co środowisko uruchomieniowe języka wspólnego (CLR). Domyślnie katalog zawierający `ClientApp.exe` jest używany jako katalog podstawowy aplikacji, a wszystkie sondy zestawu zaczynają się w tym katalogu. To zachowanie można zastąpić przy użyciu opcji `/AppBase`.

> [!NOTE]
> Zachowanie to różni się od zachowania programu Ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, gdzie podstawa aplikacji znajduje się w bieżącym katalogu.

Zestaw może mieć zależność bez odwołania, na przykład jeśli ładuje plik DLL za pomocą metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>. Można utworzyć obraz natywny dla takiego pliku dll przy użyciu informacji konfiguracyjnych dla zestawu aplikacji z opcją `/ExeConfig`. Następujące polecenie generuje obraz natywny dla `MyLib.dll,` przy użyciu informacji o konfiguracji z `MyApp.exe`.

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Zestawy instalowane w ten sposób nie są usuwane, gdy jest usuwana aplikacja.

Aby odinstalować zależność, należy użyć tych samych opcji wiersza polecenia, które zostały użyte podczas jej instalowania. Poniższe polecenie Odinstalowuje `MyLib.dll` z poprzedniego przykładu.

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Aby utworzyć obraz natywny dla zestawu w globalnej pamięci podręcznej zestawów, należy użyć nazwy wyświetlanej zestawu. Na przykład:

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

Akcja `display` najpierw wyświetla listę wszystkich zestawów głównych, a następnie listę wszystkich obrazów natywnych na komputerze.

Prosta nazwa zestawu służy do wyświetlania informacji dotyczących tylko tego zestawu. Następujące polecenie wyświetla wszystkie obrazy natywne w pamięci podręcznej obrazów natywnych, które pasują do nazwy częściowej `MyAssembly`, ich zależności i wszystkich katalogów głównych, które mają zależność od `MyAssembly`:

```console
ngen display MyAssembly
```

Informacje o tym, które elementy główne są zależne od zestawu współużytkowanego składnika, są przydatne w ocenyie wpływu akcji `update` po uaktualnieniu składnika współużytkowanego.

Aby określić rozszerzenie pliku zestawu, należy określić ścieżkę lub wykonać program Ngen.exe z katalogu zawierającego zestaw:

```console
ngen display c:\myApps\MyAssembly.exe
```

Następujące polecenie wyświetla wszystkie obrazy natywne w pamięci podręcznej obrazów natywnych o nazwie `MyAssembly` i wersji 1.0.0.0.

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Aktualizacja obrazów

Obrazy są zazwyczaj aktualizowane po uaktualnieniu składnika współużytkowanego. Aby zaktualizować wszystkie obrazy natywne, które uległy zmianie lub których zależności uległy zmianie, użyj akcji `update` bez argumentów.

```console
ngen update
```

Aktualizacja wszystkich obrazów może być długotrwałym procesem. Można kolejkować aktualizacje do wykonania przez usługę obrazu macierzystego przy użyciu opcji `/queue`. Aby uzyskać więcej informacji na temat `/queue` opcji i priorytetów instalacji, zobacz [Native Image Service](#native-image-service).

```console
ngen update /queue
```

### <a name="uninstalling-images"></a>Odinstalowywanie obrazów

Program Ngen.exe utrzymuje listę zależności, aby składniki współużytkowane były usuwane tylko wtedy, gdy wszystkie zestawy, które od nich zależą, zostały usunięte. Ponadto współużytkowany składnik nie zostanie usunięty, jeśli został zainstalowany jako element główny.

Następujące polecenie Odinstalowuje wszystkie scenariusze dla `ClientApp.exe`głównej:

```console
ngen uninstall ClientApp
```

Akcja `uninstall` może służyć do usuwania konkretnych scenariuszy. Następujące polecenie Odinstalowuje wszystkie scenariusze debugowania dla `ClientApp.exe`:

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> Odinstalowanie scenariuszy `/debug` nie powoduje odinstalowania scenariusza, w którym znajdują się zarówno `/profile`, jak i `/debug.`

Następujące polecenie Odinstalowuje wszystkie scenariusze dla określonej wersji `ClientApp.exe`:

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

Następujące polecenia Odinstalowuje wszystkie scenariusze dla `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` lub tylko scenariusza debugowania dla tego zestawu:

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

Podobnie jak w przypadku akcji `install`, dostarczenie rozszerzenia wymaga wykonania programu Ngen. exe z katalogu zawierającego zestaw lub określenia pełnej ścieżki.

Aby zapoznać się z przykładami dotyczącymi usługi obrazów natywnych, zobacz [Native Image Service](#native-image-service).

## <a name="native-image-task"></a>Obraz macierzysty — zadanie

Zadanie obrazu natywnego to zadanie systemu Windows, które generuje i utrzymuje obrazy natywne. Zadanie obrazu natywnego generuje i automatycznie przejmuje obrazy natywne dla obsługiwanych scenariuszy. Umożliwia także instalatorom używanie programu [Ngen. exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md) do tworzenia i aktualizowania obrazów natywnych w odłożonym czasie.

Zadanie obrazu natywnego jest rejestrowane raz dla każdej architektury procesora obsługiwanej na komputerze, aby umożliwić kompilację dla aplikacji przeznaczonych dla każdej architektury:

|Nazwa zadania|32-bitowy komputer|64-bitowy komputer|
|---------------|----------------------|----------------------|
|.NET Framework NGEN v 4.0.30319|Tak|Tak|
|.NET Framework NGEN v 4.0.30319 64|Nie|Tak|

Zadanie obrazu natywnego jest dostępne w .NET Framework 4,5 i nowszych wersjach, gdy działa w systemie Windows 8 lub nowszym. We wcześniejszych wersjach systemu Windows .NET Framework używa [usługi obrazów natywnych](#native-image-service).

### <a name="task-lifetime"></a>Okres istnienia zadania

Ogólnie rzecz biorąc, Harmonogram zadań systemu Windows uruchamia zadanie obrazu natywnego co noc, gdy komputer jest w stanie bezczynności. Zadanie sprawdza wszystkie odroczone zadania, które są umieszczane w kolejce przez instalatorów aplikacji, wszystkie odroczone żądania aktualizacji obrazów natywnych i wszelkie automatyczne tworzenie obrazu. Zadanie kończy zaległe elementy robocze, a następnie zamyka. Jeśli komputer przestanie być bezczynny, gdy zadanie jest uruchomione, zadanie zostanie zatrzymane.

Możesz również ręcznie uruchomić zadanie natywnego obrazu za pomocą interfejsu użytkownika Harmonogram zadań lub ręcznie wywołania programu NGen. exe. Jeśli zadanie zostało rozpoczęte za pomocą jednej z tych metod, będzie ono nadal działać, gdy komputer nie będzie już w stanie bezczynności. Obrazy tworzone ręcznie przy użyciu programu NGen. exe są priorytetowe w celu włączenia przewidywalnego zachowania dla instalatorów aplikacji.

## <a name="native-image-service"></a>Usługa obrazu macierzystego

Natywna usługa obrazów to usługa systemu Windows, która generuje i utrzymuje obrazy natywne. Usługa obrazów natywnych umożliwia deweloperom odroczenie instalacji i aktualizacji obrazów natywnych na okresy, gdy komputer jest w stanie bezczynności.

Zwykle usługa obrazów natywnych jest inicjowana przez program instalacyjny (Instalator) dla aplikacji lub aktualizacji. W przypadku akcji o priorytecie 3 usługa jest wykonywana w czasie bezczynności na komputerze. Usługa zapisuje swój stan i umożliwia kontynuowanie wielu ponownych uruchomień, jeśli jest to konieczne. Kompilacja wielu obrazów może być umieszczona w kolejce.

Usługa również współdziała z ręcznym poleceniem Ngen. exe. Polecenia ręczne mają pierwszeństwo przed działaniami w tle.

> [!NOTE]
> W systemie Windows Vista Nazwa wyświetlana dla usługi obrazów natywnych to "Microsoft.NET Framework NGEN v 2.0.50727 _X86" lub "Microsoft.NET Framework NGEN v 2.0.50727 _X64". We wszystkich wcześniejszych wersjach systemu Microsoft Windows nazwa to "Optymalizacja środowiska uruchomieniowego platformy .NET w usłudze 2.0.50727 _X86" lub "środowisko optymalizacji środowiska uruchomieniowego platformy .NET w 2.0.50727 _X64".

### <a name="launching-deferred-operations"></a>Uruchamianie odroczonych operacji

Przed rozpoczęciem instalacji lub uaktualnienia zaleca się wstrzymywanie usługi. Gwarantuje to, że usługa nie zostanie wykonana, podczas gdy Instalator kopiuje pliki lub umieszcza zestawy w globalnej pamięci podręcznej zestawów. Następujący wiersz polecenia Ngen. exe wstrzymuje usługę:

```console
ngen queue pause
```

Po dodaniu wszystkich odroczonych operacji do kolejki następujące polecenie umożliwia wznowienie działania usługi:

```console
ngen queue continue
```

Aby odroczyć generowanie obrazu natywnego podczas instalowania nowej aplikacji lub podczas aktualizowania składnika współużytkowanego, użyj opcji `/queue` z akcjami `install` lub `update`. Poniższe wiersze poleceń Ngen. exe instalują obraz macierzysty dla składnika współużytkowanego i przeprowadzają aktualizację wszystkich katalogów głównych, które mogły mieć to oddziaływać:

```console
ngen install MyComponent /queue
ngen update /queue
```

Akcja `update` ponownie generuje wszystkie obrazy natywne, które zostały unieważnione, a nie tylko te, które używają `MyComponent`.

Jeśli aplikacja składa się z wielu katalogów głównych, można kontrolować priorytet akcji odroczonych. Następujące polecenia kolejką instalację trzech katalogów głównych. `Assembly1` jest zainstalowany jako pierwszy, bez czekania na czas bezczynności. `Assembly2` jest również instalowany bez oczekiwania na czas bezczynności, ale po zakończeniu wszystkich akcji o priorytecie 1. `Assembly3` jest instalowany, gdy usługa wykryje, że komputer jest w stanie bezczynności.

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Można wymusić, aby kolejkowane akcje były wykonywane synchronicznie za pomocą akcji `executeQueuedItems`. W przypadku podania opcjonalnego priorytetu ta akcja ma wpływ tylko na akcje znajdujące się w kolejce, które mają równy lub niższy priorytet. Domyślny priorytet to 3, dlatego następujące polecenie Ngen. exe natychmiast przetwarza wszystkie akcje w kolejce i nie zwraca do momentu zakończenia:

```console
ngen executeQueuedItems
```

Polecenia synchroniczne są wykonywane przez program Ngen. exe i nie używają usługi obrazów natywnych. Akcje można wykonywać przy użyciu programu Ngen. exe, gdy jest uruchomiona usługa obrazów natywnych.

### <a name="service-shutdown"></a>Zamykanie usługi

Po zainicjowaniu przez wykonanie polecenia Ngen. exe zawierającego opcję `/queue` usługa zostanie uruchomiona w tle do momentu zakończenia wszystkich akcji. Usługa zapisuje swój stan, aby umożliwić kontynuowanie wielu ponownych uruchomień, jeśli jest to konieczne. Gdy usługa wykryje, że nie ma więcej akcji w kolejce, resetuje jej stan tak, aby nie był uruchamiany ponownie przy następnym uruchomieniu komputera, a następnie zostanie zamknięty.

### <a name="service-interaction-with-clients"></a>Interakcja z klientami usługi

W .NET Framework w wersji 2,0 jedyną interakcją z usługą obrazów natywnych jest użycie narzędzia wiersza polecenia Ngen. exe. Użyj narzędzia wiersza polecenia w skryptach instalacyjnych, aby kolejkować akcje dla usługi obrazów natywnych i współdziałać z usługą.

## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Proces zarządzanego wykonania](../../standard/managed-execution-process.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
