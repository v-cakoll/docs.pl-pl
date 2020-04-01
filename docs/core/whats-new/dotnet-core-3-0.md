---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 7e879a44bd8056ac8753c1e86464fe14fd6b9e50
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523578"
---
# <a name="whats-new-in-net-core-30"></a>Co nowego w programie .NET Core 3.0

W tym artykule opisano nowości w .NET Core 3.0. Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko dla systemu Windows). Korzystając ze składnika .NET Core 3.0 SDK Windows Desktop, można przenosić aplikacje Windows Forms i Windows Presentation Foundation (WPF). Aby było jasne, składnik Pulpit systemu Windows jest obsługiwany i dołączony tylko w systemie Windows. Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.

.NET Core 3.0 dodaje obsługę języka C# 8.0. Zdecydowanie zaleca się używanie [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej, [programu Visual Studio dla komputerów Mac 8.3](/visualstudio/mac/install-preview) lub nowszych lub [programu Visual Studio Code](https://code.visualstudio.com/) z najnowszym **rozszerzeniem języka C#.**

[Pobierz i zacznij ować korzystanie z platformy .NET Core 3.0](https://aka.ms/netcore3download) już teraz w systemie Windows, macOS lub Linux.

Aby uzyskać więcej informacji na temat wydania, zobacz [komunikat .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1 został uznany za gotowy do produkcji przez firmę Microsoft i był w pełni obsługiwany. Jeśli używasz wersji zapoznawczej, musisz przejść do wersji RTM, aby uzyskać ciągłą pomoc techniczną.

## <a name="language-improvements-c-80"></a>Ulepszenia językowe C# 8.0

C# 8.0 jest również częścią tej wersji, która zawiera funkcję [typów odwołań nullable,](../../csharp/tutorials/nullable-reference-types.md) [strumienie asynchroniowe](../../csharp/tutorials/generate-consume-asynchronous-stream.md)i [więcej wzorców](../../csharp/tutorials/pattern-matching.md). Aby uzyskać więcej informacji na temat funkcji języka C# 8.0, zobacz [Co nowego w języku C# 8.0](../../csharp/whats-new/csharp-8.md).

Dodano ulepszenia języka w celu obsługi następujących funkcji interfejsu API wyszczególnionych poniżej:

- [Zakresy i indeksy](#ranges-and-indices)
- [Strumienie asynchronizowe](#async-streams)

## <a name="net-standard-21"></a>.NET Standard 2.1

.NET Core 3.0 implementuje **.NET Standard 2.1**. Jednak szablon `dotnet new classlib` domyślny generuje projekt, który nadal jest przeznaczony dla **platformy .NET Standard 2.0**. Aby kierować reklamy na **program .NET Standard 2.1,** edytuj plik projektu i zmień właściwość `TargetFramework` `netstandard2.1`na:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual Studio 2019,](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ponieważ program Visual Studio 2017 nie obsługuje **programu .NET Standard 2.1** lub **.NET Core 3.0.**

## <a name="compiledeploy"></a>Kompilowanie/wdrażanie

### <a name="default-executables"></a>Domyślne pliki wykonywalne

Program .NET Core domyślnie tworzy [pliki wykonywalne zależne od środowiska uruchomieniowego.](../deploying/index.md#publish-runtime-dependent) To zachowanie jest nowe dla aplikacji, które używają globalnie zainstalowanej wersji programu .NET Core. Wcześniej tylko [samodzielne wdrożenia](../deploying/index.md#publish-self-contained) tworzyły plik wykonywalny.

Podczas `dotnet build` `dotnet publish`lub , plik wykonywalny (znany jako **appHost**) jest tworzony, który pasuje do środowiska i platformy SDK, którego używasz. Można oczekiwać tych samych rzeczy z tymi plikami wykonywalnymi, jak inne natywne pliki wykonywalne, takie jak:

- Możesz dwukrotnie kliknąć plik wykonywalny.
- Aplikację można uruchomić bezpośrednio z wiersza polecenia, na `myapp.exe` `./myapp` przykład w systemie Windows oraz w systemach Linux i macOS.

### <a name="macos-apphost-and-notarization"></a>aplikacja macOSHost i notarization

*Tylko system macOS*

Począwszy od nota poś nieposłusznego .NET Core SDK 3.0 dla systemu macOS, ustawienie do tworzenia domyślnego pliku wykonywalnego (znanego jako appHost) jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [system notarization systemu macOS Catalina i wpływ na pliki do pobrania i projekty .NET Core](../install/macos-notarization-issues.md).

Gdy ustawienie appHost jest włączone, .NET Core generuje natywny plik wykonywalny Mach-O podczas tworzenia lub publikowania. Aplikacja jest uruchamiana w kontekście appHost, gdy jest `dotnet run` uruchamiana z kodu źródłowego za pomocą polecenia lub uruchamiając plik wykonywalny Mach-O bezpośrednio.

Bez appHost, jedynym sposobem, w jaki użytkownik może uruchomić `dotnet <filename.dll>` aplikację [zależną od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest za pomocą polecenia. AplikacjaHost jest zawsze tworzony podczas publikowania aplikacji [samodzielny](../deploying/index.md#publish-self-contained).

Można skonfigurować appHost na poziomie projektu lub przełączyć appHost dla `dotnet` określonego `-p:UseAppHost` polecenia z parametrem:

- Plik projektu

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parametr wiersza polecenia

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Aby uzyskać więcej `UseAppHost` informacji na temat tego ustawienia, zobacz [Właściwości msbuild dla pliku Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="single-file-executables"></a>Pliki wykonywalne z jednym plikiem plików

Polecenie `dotnet publish` obsługuje pakowanie aplikacji do pliku wykonywalnego z pojedynczym plikiem specyficznym dla platformy. Plik wykonywalny jest samorozwiązywania i zawiera wszystkie zależności (w tym natywnych), które są wymagane do uruchomienia aplikacji. Po pierwszym uruchomieniu aplikacji jest wyodrębniany do katalogu na podstawie nazwy aplikacji i identyfikator kompilacji. Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie. Aplikacja nie musi wyodrębniać się po raz drugi, chyba że użyto nowej wersji.

Aby opublikować plik wykonywalny z jednym plikiem, ustaw `PublishSingleFile` w projekcie lub w wierszu polecenia poleceniem: `dotnet publish`

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

— lub —

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

Aby uzyskać więcej informacji na temat publikowania pojedynczego pliku, zobacz [dokument projektowy pakietu z pojedynczym plikiem](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

### <a name="assembly-linking"></a>Łączenie zmontowania

Zestaw SDK .NET core 3.0 jest dostarczany z narzędziem, które może zmniejszyć rozmiar aplikacji, analizując il i przycinanie nieużywanych zestawów.

Samodzielne aplikacje zawierają wszystko, co potrzebne do uruchomienia kodu, bez konieczności instalowania platformy .NET na komputerze-hoście. Jednak wiele razy aplikacja wymaga tylko niewielki podzbiór struktury do działania i innych nieużywanych bibliotek może zostać usunięty.

Program .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [do konsolidowania IL](https://github.com/mono/linker) do skanowania il aplikacji. To narzędzie wykrywa, jaki kod jest wymagany, a następnie przycina nieużywane biblioteki. To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.

Aby włączyć to narzędzie, dodaj `<PublishTrimmed>` ustawienie w projekcie i opublikuj samodzielną aplikację:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Na przykład podstawowy szablon nowego projektu konsoli "hello world", który jest uwzględniony po opublikowaniu, osiągnie rozmiar około 70 MB. Za `<PublishTrimmed>`pomocą , ten rozmiar jest zmniejszona do około 30 MB.

Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które używają odbicia lub powiązanych funkcji dynamicznych, często pęknie po przycięciu. To pęknięcie występuje, ponieważ konsolidator nie wie o tym dynamicznym zachowaniu i nie można określić, które typy struktury są wymagane do odbicia. Narzędzie IL Linker można skonfigurować tak, aby było świadome tego scenariusza.

Przede wszystkim należy przetestować aplikację po przycięciu.

Aby uzyskać więcej informacji na temat narzędzia IL Linker, zobacz [dokumentację](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/linker.]( https://github.com/mono/linker)

### <a name="tiered-compilation"></a>Kompilacja warstwowa

[Kompilacja warstwowa](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) jest domyślnie włączona z .NET Core 3.0. Ta funkcja umożliwia środowisko wykonawcze bardziej adaptacyjnie używać kompilatora just-in-time (JIT), aby osiągnąć lepszą wydajność.

Główną zaletą kompilacji warstwowej jest zapewnienie dwóch sposobów jitting metody: w niższej jakości, ale szybciej warstwy lub wyższej jakości, ale wolniej warstwy. Jakość odnosi się do tego, jak dobrze metoda jest zoptymalizowana. TC pomaga poprawić wydajność aplikacji, ponieważ przechodzi przez różne etapy wykonywania, od uruchamiania do stanu ustalonego. Gdy kompilacja warstwowa jest wyłączona, każda metoda jest kompilowana w jeden sposób, który jest stronniczy do wydajności w stanie ustalonym w porównaniu z wydajnością uruchamiania.

Gdy TC jest włączona, następujące zachowanie ma zastosowanie do kompilacji metody podczas uruchamiania aplikacji:

- Jeśli metoda ma przed czasem skompilowany kod lub [ReadyToRun](#readytorun-images), używany jest wstępnie generowany kod.
- W przeciwnym razie metoda jest jitted. Zazwyczaj te metody są rodzajowe za generyczne typy wartości.
  - *Quick JIT* szybciej wytwarza kod niższej jakości (lub mniej zoptymalizowany). W .NET Core 3.0 Quick JIT jest domyślnie włączona dla metod, które nie zawierają pętli i jest preferowana podczas uruchamiania.
  - W pełni optymalizujący JIT wytwarza wolniej kod wyższej jakości (lub bardziej zoptymalizowany). W przypadku metod, w których quick JIT nie byłoby <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>używane (na przykład, jeśli metoda jest przypisana z), w pełni optymalizacji JIT jest używany.

Dla często wywoływanych metod kompilator just-in-time ostatecznie tworzy w pełni zoptymalizowany kod w tle. Zoptymalizowany kod następnie zastępuje wstępnie skompilowany kod dla tej metody.

Kod generowany przez Szybkie JIT może działać wolniej, przydzielić więcej pamięci lub użyć więcej miejsca na stosie. Jeśli występują problemy, można wyłączyć Szybkie JIT przy użyciu tej właściwości MSBuild w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

Aby całkowicie wyłączyć TC, użyj tej właściwości MSBuild w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Jeśli zmienisz te ustawienia w pliku projektu, może być konieczne wykonanie czystej kompilacji `obj` dla `bin` nowych ustawień, które mają być odzwierciedlone (usuń katalogi i i odbuduj).

Aby uzyskać więcej informacji na temat konfigurowania kompilacji w czasie wykonywania, zobacz [Opcje konfiguracji w czasie wykonywania kompilacji](../run-time-config/compilation.md).

### <a name="readytorun-images"></a>Obrazy ReadyToRun

Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji w formacie ReadyToRun (R2R). R2R jest formą kompilacji z wyprzedzeniem (AOT).

Pliki binarne R2R zwiększają wydajność uruchamiania, zmniejszając ilość pracy, jaką kompilator just-in-time (JIT) musi wykonać w miarę ładowania aplikacji. Pliki binarne zawierają podobny kod macierzysty w porównaniu do tego, co JIT będzie produkować. Jednak pliki binarne R2R są większe, ponieważ zawierają zarówno kod języka pośredniego (IL), który jest nadal potrzebny w niektórych scenariuszach, jak i natywną wersję tego samego kodu. R2R jest dostępny tylko podczas publikowania samodzielnej aplikacji przeznaczonej dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.

Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:

01. Dodaj `<PublishReadyToRun>` ustawienie do projektu:

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Opublikuj niezależną aplikację. Na przykład to polecenie tworzy niezależną aplikację dla 64-bitowej wersji systemu Windows:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Ograniczenia między platformami/architekturą

Kompilator ReadyToRun obecnie nie obsługuje kierowania krzyżowego. Należy skompilować na danym celu. Na przykład, jeśli chcesz obrazy R2R dla systemu Windows x64, należy uruchomić polecenie publikowania w tym środowisku.

Wyjątki od kierowania krzyżowego:

- System Windows x64 może być używany do kompilowania obrazów windows ARM32, ARM64 i x86.
- System Windows x86 może być używany do kompilowania obrazów systemu Windows ARM32.
- Linux x64 może być używany do kompilowania obrazów Linux ARM32 i ARM64.

## <a name="runtimesdk"></a>Środowisko wykonawcze/SDK

### <a name="major-version-runtime-roll-forward"></a>Rzut środowiska uruchomieniowego w wersji głównej do przodu

Program .NET Core 3.0 wprowadza funkcję opt-in, która umożliwia aplikacji przewija się do najnowszej głównej wersji programu .NET Core. Ponadto dodano nowe ustawienie, aby kontrolować sposób przekazywania do przodu jest stosowany do aplikacji. Można to skonfigurować w następujący sposób:

- Właściwość pliku projektu:`RollForward`
- Właściwość pliku konfiguracji w czasie wykonywania:`rollForward`
- Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`
- Argument wiersza polecenia:`--roll-forward`

Należy określić jedną z następujących wartości. Jeśli ustawienie zostanie pominięte, wartość domyślna jest **wartośćą minor.**

- **NajnowszePatch**\
Przewiń do przodu do najwyższej wersji poprawki. Spowoduje to wyłączenie wersji pomocniczej do przodu.
- **Drobne**\
Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej. Jeśli żądana wersja pomocnicza jest obecna, używana jest zasada **LatestPatch.**
- **Głównych**\
Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje żądanej wersji głównej. Jeśli żądana wersja główna jest obecny, a następnie **drobne** zasady są używane.
- **NajnowszyMinor**\
Przewiń do przodu do najwyższej wersji pomocniczej, nawet jeśli wymagana wersja pomocnicza jest obecna. Przeznaczone do scenariuszy hostingu składników.
- **NajnowszeMajor**\
Przewiń do przodu do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli jest wymagana major. Przeznaczone do scenariuszy hostingu składników.
- **Wyłączyć**\
Nie przewracaj się do przodu. Tylko powiązanie z określoną wersją. Ta zasada nie jest zalecana do ogólnego użytku, ponieważ wyłącza możliwość przekazywania do najnowszych poprawek. Ta wartość jest zalecana tylko do testowania.

Oprócz ustawienia **Wyłącz,** wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.

### <a name="build-copies-dependencies"></a>Tworzenie zależności kopii

Polecenie `dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu wyjściowego kompilacji. Wcześniej zależności były kopiowane tylko w `dotnet publish`ramach .

Istnieje kilka operacji, takich jak łączenie i publikowanie stron maszynki do golenia, które nadal będą wymagały publikowania.

### <a name="local-tools"></a>Narzędzia lokalne

Program .NET Core 3.0 wprowadza narzędzia lokalne. Narzędzia lokalne są podobne do [narzędzi globalnych,](../tools/global-tools.md) ale są skojarzone z określoną lokalizacją na dysku. Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.

> [!WARNING]
> Jeśli wypróbowano narzędzia lokalne w wersji zapoznawczej `dotnet tool restore` 3.0 core 1, takie jak uruchamianie lub `dotnet tool install`usuwanie folderu pamięci podręcznej narzędzi lokalnych. W przeciwnym razie narzędzia lokalne nie będą działać w żadnej nowszej wersji. Ten folder znajduje się pod adresem:
>
> Na macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`
>
> W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Narzędzia lokalne opierają się `dotnet-tools.json` na nazwie pliku manifestu w bieżącym katalogu. Ten plik manifestu definiuje narzędzia, które mają być dostępne w tym folderze i poniżej. Można rozpowszechniać plik manifestu z kodem, aby upewnić się, że każdy, kto pracuje z kodem można przywrócić i korzystać z tych samych narzędzi.

W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska wykonawczego. Wiele narzędzi obecnie na NuGet.org docelowym .NET Core Runtime 2.1. Aby zainstalować te narzędzia globalnie lub lokalnie, należy zainstalować [środowisko wykonawcze NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

### <a name="new-globaljson-options"></a>Nowe opcje global.json

Plik *global.json* ma nowe opcje, które zapewniają większą elastyczność podczas próby zdefiniowania, która wersja .NET Core SDK jest używana. Nowe opcje to:

- `allowPrerelease`: Wskazuje, czy program rozpoznawania nazw SDK powinien uwzględniać wersje wersji wstępnej podczas wybierania wersji SDK do użycia.
- `rollForward`: Wskazuje zasady do przodu rolki do użycia podczas wybierania wersji SDK, jako rezerwowy, gdy brakuje określonej wersji SDK lub jako dyrektywy do korzystania z wyższej wersji.

Aby uzyskać więcej informacji na temat zmian, w tym wartości domyślnych, obsługiwanych wartości i nowych reguł dopasowywania, zobacz [global.json overview](../tools/global-json.md).

### <a name="smaller-garbage-collection-heap-sizes"></a>Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych

Domyślny rozmiar sterty modułu zbierającego elementy bezużyteczne został zmniejszony, co spowodowało, że program .NET Core zużywa mniej pamięci. Ta zmiana lepiej dostosowuje się do budżetu alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej procesora.

### <a name="garbage-collection-large-page-support"></a>Obsługa dużych stron wyrzucania elementów bezużytecznych

Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny jest w stanie ustanowić regiony pamięci większe niż rozmiar strony macierzystej (często 4K), aby poprawić wydajność aplikacji żądającej tych dużych stron.

Moduł zbierający elementy bezużyteczne można teraz skonfigurować za pomocą ustawienia **GCLargePages** jako funkcji opt-in, aby wybrać przydzielenie dużych stron w systemie Windows.

## <a name="windows-desktop--com"></a>Komputer & windows

### <a name="net-core-sdk-windows-installer"></a>Instalator windowsowy pakietu NET Core SDK

Instalator MSI dla systemu Windows zmienił się począwszy od .NET Core 3.0. Instalatorzy SDK będą teraz uaktualniać wersje pasma funkcji SDK w miejscu. Pasma funkcji są definiowane w *setkach* grup w sekcji *poprawek* numeru wersji. Na przykład **3.0._ 101_ ** i **3.0._ 201_ ** to wersje w dwóch różnych pasmach fabularnych, podczas gdy **3.0._ 101_ ** i **3.0._ 199_ ** są w tym samym paśmie fabularnym. I kiedy .NET Core SDK **3.0._ 101_ ** jest zainstalowany, .NET Core SDK **3.0._ 100_ ** zostanie usunięty z urządzenia, jeśli istnieje. Kiedy .NET Core SDK **3.0._ 200_ ** jest zainstalowany na tym samym komputerze, .NET Core SDK **3.0._ 101_ ** nie zostanie usunięty.

Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie sposobu wersjowania programu .NET Core](../versions/index.md).

### <a name="windows-desktop"></a>Pulpit systemu Windows

Program .NET Core 3.0 obsługuje aplikacje klasyczne systemu Windows przy użyciu programu Windows Presentation Foundation (WPF) i Windows Forms. Te struktury obsługują również korzystanie z nowoczesnych formantów i płynnego stylu z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML.](/windows/uwp/xaml-platform/xaml-host-controls)

Składnik Pulpit systemu Windows jest częścią pakietu Windows .NET Core 3.0 SDK.

Można utworzyć nową aplikację WPF lub Formularze systemu Windows z następującymi `dotnet` poleceniami:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 dodaje nowe szablony **projektu** dla .NET Core 3.0 Windows Forms i WPF.

Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [Projekty WPF portu](../../desktop-wpf/migration/convert-project-from-net-framework.md) i [projekty formularzy portów systemu Windows](../porting/winforms.md).

#### <a name="winforms-high-dpi"></a>WinForms wysoka rozdzielczość DPI

Aplikacje .NET Core Windows Forms można <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>ustawić tryb wysokiej rozdzielczości DPI za pomocą programu . Metoda `SetHighDpiMode` ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że `App.Manifest` ustawienie zostało ustawione `Application.Run`za pomocą innych środków, takich jak p/invoke przed .

Możliwe `highDpiMode` wartości wyrażone w <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> wyliczenia są następujące:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji pulpitu o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="create-com-components"></a>Tworzenie składników COM

W systemie Windows można teraz tworzyć składniki zarządzane wywoływane przez jednostkę COM. Ta funkcja ma kluczowe znaczenie dla korzystania z programu .NET Core z modelami dodatków COM, a także w celu zapewnienia parzystości z programem .NET Framework.

W przeciwieństwie do programu .NET Framework, w którym *mscoree.dll* był używany jako serwer COM, program .NET Core doda natywną bibliotekę dll programu launcher do katalogu *pojemnika* podczas tworzenia składnika COM.

Na przykład, jak utworzyć składnik COM i z niego korzystać, zobacz [com demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Natywny interop systemu Windows

System Windows oferuje bogaty natywny interfejs API w postaci płaskich interfejsów API C, COM i WinRT. Podczas gdy program .NET Core obsługuje **p/invoke,**.NET Core 3.0 dodaje możliwość **tworzenia interfejsów API COM** i **aktywowania interfejsów API winrt**. Przykładowy kod można znaleźć w wersji [Demonstracyjnej programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>Wdrażanie msix

[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows. Może być używany do wdrażania aplikacji komputerowych .NET Core 3.0 w systemie Windows 10.

[Projekt pakowania aplikacji systemu Windows,](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX z [samodzielnymi aplikacjami](../deploying/index.md#publish-self-contained) .NET Core.

Plik projektu .NET Core musi określać obsługiwane `<RuntimeIdentifiers>` środowiska wykonawcze we właściwości:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Ulepszenia systemu Linux

### <a name="serialport-for-linux"></a>SerialPort dla Linuksa

.NET Core 3.0 zapewnia <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> podstawową obsługę systemu Linux.

Wcześniej program .NET Core był `SerialPort` obsługiwany tylko w systemie Windows.

Aby uzyskać więcej informacji na temat ograniczonej obsługi portu szeregowego w systemie Linux, zobacz [#33146 problem gitHub](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Limity pamięci platformy Docker i cgroup

Uruchamianie .NET Core 3.0 na Linuksie z docker działa lepiej z limitami pamięci cgroup. Uruchamianie kontenera platformy Docker z `docker run -m`limitami pamięci, na przykład z , zmienia zachowanie .NET Core.

- Domyślny rozmiar sterty modułu zbierającego elementy bezużyteczne (GC): maksymalnie 20 mb lub 75% limitu pamięci w kontenerze.
- Jawny rozmiar można ustawić jako bezwzględną liczbę lub procent limitu cgroup.
- Minimalny zarezerwowany rozmiar segmentu na stertę GC wynosi 16 mb. Ten rozmiar zmniejsza liczbę stert, które są tworzone na komputerach.

### <a name="gpio-support-for-raspberry-pi"></a>Obsługa GPIO dla Raspberry Pi

Dwa pakiety zostały wydane do NuGet, który można użyć do programowania GPIO:

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [Iot.Device.Powiązania](https://www.nuget.org/packages/Iot.Device.Bindings)

Pakiety GPIO zawierają interfejsy API dla urządzeń *GPIO,* *SPI,* *I2C*i *PWM.* Pakiet powiązań IoT zawiera powiązania urządzeń. Aby uzyskać więcej informacji, zobacz [urządzenia GitHub repozytorium](https://github.com/dotnet/iot/blob/master/src/devices/).

### <a name="arm64-linux-support"></a>Obsługa systemu ARM64 Linux

.NET Core 3.0 dodaje obsługę ARM64 dla Linuksa. Podstawowym przypadkiem użycia arm64 jest obecnie ze scenariuszami IoT. Aby uzyskać więcej informacji, zobacz [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

[Obrazy platformy Docker dla .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.

> [!NOTE]
> **ARM64 ( ARM64 )** Pomoc techniczna systemu Windows nie jest jeszcze dostępna.

## <a name="security"></a>Zabezpieczenia

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 w systemie Linux

Program .NET Core korzysta teraz z [obsługi protokołu TLS 1.3 w openssl 1.1.1,](https://www.openssl.org/blog/blog/2018/09/11/release111/)gdy jest on dostępny w danym środowisku. Z TLS 1.3:

- Czas połączenia jest lepszy dzięki zmniejszeniu liczby rund między klientem a serwerem.
- Większe bezpieczeństwo dzięki usunięciu różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.

Jeśli jest dostępna, .NET Core 3.0 używa **OpenSSL 1.1.1,** **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux. Gdy **OpenSSL 1.1.1** jest <xref:System.Net.Security.SslStream?displayProperty=nameWithType> <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> dostępny, oba typy będą używać **protokołu TLS 1.3** (przy założeniu, że zarówno klient, jak i serwer obsługują **TLS 1.3).**

> [!IMPORTANT]
> Windows i macOS nie obsługują jeszcze **protokołu TLS 1.3**. Program .NET Core 3.0 będzie obsługiwał **tls 1.3** w tych systemach operacyjnych, gdy pomoc techniczna stanie się dostępna.

W poniższym przykładzie C# 8.0 pokazano .NET Core 3.0 na Ubuntu 18.10 łącząc się <https://www.cloudflare.com>z:

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Szyfry kryptograficzne

.NET 3.0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM,** zaimplementowanych odpowiednio z <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> odpowiednio. Algorytmy te są zarówno [uwierzytelnionym szyfrowaniem z algorytmami skojarzenia danych (AEAD).](https://en.wikipedia.org/wiki/Authenticated_encryption)

Poniższy kod demonstruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania losowych danych.

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Import/eksport klucza kryptograficznego

Program .NET Core 3.0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych ze standardowych formatów. Nie trzeba używać certyfikatu X.509.

Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDsa*i *ECDiffieHellman,* obsługują następujące formaty:

- **Klucz publiczny**
  - X.509 TematPublicKeyInfo

- **Klucz prywatny**
  - PKCS #8 PrivateKeyInfo
  - PKCS #8 EncryptedPrivateKeyInfo

Klucze RSA obsługują również:

- **Klucz publiczny**
  - PKCS #1 RSAPublicKey

- **Klucz prywatny**
  - PKCS#1 RSAPrivateKey

Metody eksportu generują dane binarne zakodowane w formacie DER, a metody importu oczekują tego samego. Jeśli klucz jest przechowywany w formacie PEM przyjazny dla tekstu, obiekt wywołujący będzie musiał base64-dekodować zawartość przed wywołaniem metody importu.

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**Pliki PKCS#8** można sprawdzić <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> za pomocą plików **PFX/PKCS#12** za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>pliku . **Pliki PFX/PKCS#12** można manipulować za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>pliku .

## <a name="net-core-30-api-changes"></a>Zmiany interfejsu API programu .NET Core 3.0

### <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy <xref:System.Index?displayProperty=nameWithType> typ może służyć do indeksowania. Można utworzyć jeden `int` z, który liczy się od początku `^` lub z prefiksu operatora (C#), który liczy się od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa `Index` się z dwóch wartości, jeden dla początku i jeden `x..y` na końcu i mogą być zapisywane z wyrażeniem zakresu (C#). Następnie można indeksować `Range`za pomocą , który tworzy plasterek:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Aby uzyskać więcej informacji, zobacz [zakresy i indeksy samouczka](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Strumienie asynchroniczne

Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> jest nową asynchroniką <xref:System.Collections.Generic.IEnumerable%601>wersją programu . Język pozwala `await foreach` na `IAsyncEnumerable<T>` korzystanie z ich `yield return` elementów i używać do nich do tworzenia elementów.

Poniższy przykład pokazuje zarówno produkcji i zużycia strumieni asynchronii. Instrukcja `foreach` jest async i `yield return` sama używa do produkcji strumienia asynchronii dla wywołań. Ten wzorzec (przy użyciu) `yield return`jest zalecanym modelem do wytwarzania strumieni asynchronii.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

`await foreach`Oprócz możliwości , można również utworzyć iteratory asynchronii, na przykład iterator, który `yield` `IAsyncEnumerable/IAsyncEnumerator` zwraca, że można zarówno `await` i w. W przypadku obiektów, które muszą zostać `IAsyncDisposable`usunięte, można użyć , `Stream` które `Timer`implementują różne typy BCL, takie jak i .

Aby uzyskać więcej informacji, zobacz [samouczek strumieni asynchronii](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>IEEE Zmiennoprzecinka

Interfejsy API zmiennoprzecinowe są aktualizowane zgodnie z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Celem tych zmian jest udostępnienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z zachowaniem specyfikacji IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [zmiennoprzecinające się i formatowanie ulepszeń w blogu .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

Poprawki do analizowania i formatowania obejmują:

- Poprawnie analizuj i okrąglaj wejścia o dowolnej długości.
- Poprawnie przeanalizować i sformatować ujemne zero.
- Poprawnie przeanalizować `Infinity` `NaN` i wykonując kontrolę bez uwzględniania wielkości liter i `+` zezwalając na opcjonalne poprzedzające, w stosownych przypadkach.

Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:

- <xref:System.Math.BitIncrement(System.Double)>I<xref:System.Math.BitDecrement(System.Double)>\
Odpowiada operacjom `nextUp` `nextDown` IEEE. Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większą lub mniejszą niż dane wejściowe (odpowiednio). Na przykład, `Math.BitIncrement(0.0)` `double.Epsilon`zwróci .

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)>I<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odpowiada operacji `maxNumMag` i `minNumMag` IEEE, zwracają wartość, która jest większa lub mniejsza wielkość dwóch wejść (odpowiednio). Na przykład, `Math.MaxMagnitude(2.0, -3.0)` `-3.0`zwróci .

- <xref:System.Math.ILogB(System.Double)>\
Odpowiada operacji `logB` IEEE, która zwraca wartość integralną, zwraca całka base-2 dziennika parametru wejściowego. Ta metoda jest skutecznie `floor(log2(x))`taka sama jak , ale odbywa się z minimalnym błędem zaokrąglania.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odpowiada operacji `scaleB` IEEE, która przyjmuje wartość całkowitą, `x * pow(2, n)`zwraca skutecznie , ale odbywa się z minimalnym błędem zaokrąglania.

- <xref:System.Math.Log2(System.Double)>\
Odpowiada operacji `log2` IEEE, zwraca logarytm base-2. Minimalizuje błąd zaokrąglania.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odpowiada operacji `fma` IEEE, wykonuje połączone multiply add. Oznacza to, `(x * y) + z` że wykonuje jako pojedynczą operację, minimalizując w ten sposób błąd zaokrąglania. Przykładem `FusedMultiplyAdd(1e308, 2.0, -1e308)`jest , `1e308`który zwraca . Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Odpowiada operacji `copySign` IEEE, zwraca wartość `x`, ale ze znakiem `y`.

### <a name="net-platform-dependent-intrinsics"></a>Elementy wewnętrzne zależne od platformy .NET

Dodano interfejsy API, które umożliwiają dostęp do niektórych instrukcji procesora zorientowanych na procesor, takich jak zestawy instrukcji **SIMD** lub **Bit Manipulation.** Te instrukcje mogą pomóc w osiągnięciu znaczącej poprawy wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych równolegle.

W stosownych przypadkach biblioteki platformy .NET zaczęły używać tych instrukcji w celu zwiększenia wydajności.

Aby uzyskać więcej informacji, zobacz [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

### <a name="improved-net-core-version-apis"></a>Ulepszone interfejsy API wersji .NET Core

Począwszy od platformy .NET Core 3.0, interfejsy API wersji dostarczone z programem .NET Core zwracają teraz oczekiwane informacje. Przykład:

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Przełomowa zmiana. Jest to technicznie przełomowa zmiana, ponieważ schemat przechowywania wersji uległ zmianie.

### <a name="fast-built-in-json-support"></a>Szybka wbudowana obsługa JSON

Użytkownicy platformy .NET w dużej mierze polegali na [Newtonsoft.Json](https://www.newtonsoft.com/json) i innych popularnych bibliotekach JSON, które nadal są dobrym wyborem. `Newtonsoft.Json`używa ciągów .NET jako podstawowego typu danych, który jest UTF-16 pod maską.

Nowa wbudowana obsługa JSON jest wysokowydajna, niska alokacja i współpracuje z UTF-8 zakodowany tekst JSON. Aby uzyskać więcej <xref:System.Text.Json> informacji na temat obszaru nazw i typów, zobacz następujące artykuły:

* [Serializacja JSON w .NET - omówienie](../../standard/serialization/system-text-json-overview.md)
* [Jak serializować i deserialize JSON w .NET](../../standard/serialization/system-text-json-how-to.md).
* [Jak przeprowadzić migrację z Newtonsoft.Json do System.Text.Json](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>Obsługa protokołu HTTP/2

Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> obsługuje protokół HTTP/2. Jeśli http/2 jest włączona, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się z niej korzystać.

Domyślny protokół pozostaje HTTP/1.1, ale PROTOKÓŁ HTTP/2 można włączyć na dwa różne sposoby. Najpierw można ustawić komunikat żądania HTTP na http/2:

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Po drugie, <xref:System.Net.Http.HttpClient> można zmienić, aby domyślnie używać protokołu HTTP/2:

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Wiele razy podczas tworzenia aplikacji, chcesz użyć połączenia niezaszyfrowanego. Jeśli wiesz, że docelowy punkt końcowy będzie używał protokołu HTTP/2, możesz włączyć połączenia niezaszyfrowane dla protokołu HTTP/2. Można ją włączyć, ustawiając zmienną środowiskową `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` na `1` lub włączając ją w kontekście aplikacji:

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Następne kroki

- [Przejrzyj przełomowe zmiany między .NET Core 2.2 i 3.0.](../compatibility/2.2-3.0.md)
- [Przejrzyj przełomowe zmiany w aplikacjach .NET Core 3.0 dla formularzy systemu Windows.](../compatibility/winforms.md#net-core-30)
