---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach, które można znaleźć w .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 6e85c2c3e796ae59a13f944bd4913e4b7316c56a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398812"
---
# <a name="whats-new-in-net-core-30"></a>Co nowego w programie .NET Core 3.0

W tym artykule opisano nowości w .NET Core 3.0. Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko windows). Korzystając ze składnika SDK .NET Core 3.0 Z systemem Windows Desktop, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF). Aby było jasne, składnik Pulpit systemu Windows jest obsługiwany i uwzględniany tylko w systemie Windows. Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.

.NET Core 3.0 dodaje obsługę języka C# 8.0. Zdecydowanie zaleca się używanie programu [Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej, [programu Visual Studio dla komputerów Mac 8.3](/visualstudio/mac/install-preview) lub nowszych lub [kodu programu Visual Studio](https://code.visualstudio.com/) z najnowszym **rozszerzeniem języka C#.**

[Pobierz i zacznij korzystać z .NET Core 3.0](https://aka.ms/netcore3download) już teraz w systemie Windows, macOS lub Linux.

Aby uzyskać więcej informacji na temat wydania, zobacz [anons .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1 został uznany przez firmę Microsoft za gotowy do produkcji i był w pełni obsługiwany. Jeśli używasz wersji zapoznawczej, musisz przejść do wersji RTM, aby kontynuować obsługę.

## <a name="language-improvements-c-80"></a>Ulepszenia języka C# 8.0

C# 8.0 jest również częścią tej wersji, która zawiera funkcję [typów odwołań z możliwością null,](../../csharp/tutorials/nullable-reference-types.md) [strumienia asynchronicznego](../../csharp/tutorials/generate-consume-asynchronous-stream.md)i [więcej wzorców](../../csharp/tutorials/pattern-matching.md). Aby uzyskać więcej informacji na temat funkcji języka C# 8.0, zobacz [Co nowego w języku C# 8.0](../../csharp/whats-new/csharp-8.md).

Dodano ulepszenia języka do obsługi następujących funkcji interfejsu API wyszczególnionych poniżej:

- [Zakresy i indeksy](#ranges-and-indices)
- [Strumienie asynchroniczne](#async-streams)

## <a name="net-standard-21"></a>Standard .NET 2.1

.NET Core 3.0 implementuje **.NET Standard 2.1**. Jednak domyślny `dotnet new classlib` szablon generuje projekt, który nadal jest przeznaczony dla **.NET Standard 2.0**. Aby kierować program **.NET Standard 2.1,** należy `TargetFramework` edytować plik projektu i zmienić właściwość `netstandard2.1`na:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program Visual Studio 2017 nie obsługuje **programu .NET Standard 2.1** lub **.NET Core 3.0**.

## <a name="compiledeploy"></a>Kompilowanie/wdrażanie

### <a name="default-executables"></a>Domyślne pliki wykonywalne

Program .NET Core domyślnie tworzy [pliki wykonywalne zależne od czasu wykonywania.](../deploying/index.md#publish-runtime-dependent) To zachowanie jest nowe dla aplikacji, które używają globalnie zainstalowanej wersji programu .NET Core. Wcześniej tylko [niezależne wdrożenia](../deploying/index.md#publish-self-contained) będą produkować plik wykonywalny.

Podczas `dotnet build` `dotnet publish`lub plik wykonywalny (znany jako **appHost**) jest tworzony, który pasuje do środowiska i platformy sdk używasz. Można oczekiwać tych samych rzeczy z tych plików wykonywalnych, jak inne natywne pliki wykonywalne, takie jak:

- Możesz kliknąć dwukrotnie plik wykonywalny.
- Aplikację można uruchomić bezpośrednio z wiersza `myapp.exe` polecenia, na `./myapp` przykład w systemie Windows, a także w systemie Linux i macOS.

### <a name="macos-apphost-and-notarization"></a>aplikacja macOSHost i notarialnie

*Tylko system macOS*

Począwszy od notarialnie .NET Core SDK 3.0 dla systemu macOS, ustawienie do produkcji domyślnego pliku wykonywalnego (znany jako appHost) jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [notarialnie Catalina w systemie macOS oraz wpływ na pobieranie i projekty programu .NET Core](../install/macos-notarization-issues.md).

Gdy ustawienie appHost jest włączone, program .NET Core generuje natywny plik wykonywalny Mach-O podczas tworzenia lub publikowania. Aplikacja jest uruchamiana w kontekście appHost, gdy jest `dotnet run` uruchamiany z kodu źródłowego za pomocą polecenia lub przez bezpośrednie uruchomienie pliku wykonywalnego Mach-O.

Bez appHost, jedynym sposobem użytkownik może uruchomić aplikację zależną od `dotnet <filename.dll>` środowiska [uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest z poleceniem. AppHost jest zawsze tworzony podczas publikowania aplikacji [niezależne .](../deploying/index.md#publish-self-contained)

Możesz skonfigurować appHost na poziomie projektu lub przełączyć appHost dla `dotnet` określonego `-p:UseAppHost` polecenia z parametrem:

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

Aby uzyskać więcej `UseAppHost` informacji o tym ustawieniu, zobacz [WŁAŚCIWOŚCI MSBuild dla programu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="single-file-executables"></a>Pliki wykonywalne dla jednego pliku

Polecenie `dotnet publish` obsługuje pakowanie aplikacji do pliku wykonywalnego dla danego pliku specyficznego dla platformy. Plik wykonywalny jest samowyodrębnianie i zawiera wszystkie zależności (w tym natywnych), które są wymagane do uruchomienia aplikacji. Po pierwszym uruchomieniu aplikacji aplikacja jest wyodrębniana do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji. Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie. Aplikacja nie musi wyodrębniać się po raz drugi, chyba że nowa wersja została użyta.

Aby opublikować plik wykonywalny dla pojedynczego pliku, ustaw je `PublishSingleFile` w projekcie lub w wierszu `dotnet publish` polecenia za pomocą polecenia:

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

Aby uzyskać więcej informacji na temat publikowania pojedynczych plików, zobacz [dokument projektowy pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

### <a name="assembly-linking"></a>Łączenie zestawów

Zestaw SDK .NET core 3.0 jest dostarczany z narzędziem, które może zmniejszyć rozmiar aplikacji, analizując il i przycinając nieużywane zestawy.

Niezależne aplikacje zawierają wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania .NET na komputerze-hoście. Jednak wiele razy aplikacja wymaga tylko mały podzbiór struktury do działania i inne nieużywane biblioteki mogą zostać usunięte.

.NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora IL](https://github.com/mono/linker) do skanowania il aplikacji. To narzędzie wykrywa, jaki kod jest wymagany, a następnie przycina nieużywane biblioteki. To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.

Aby włączyć to narzędzie, dodaj `<PublishTrimmed>` ustawienie w projekcie i opublikuj niezależną aplikację:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Na przykład podstawowy "hello world" nowy szablon projektu konsoli, który jest uwzględniony, po opublikowaniu, osiąga około 70 MB w rozmiarze. Za `<PublishTrimmed>`pomocą , ten rozmiar jest zmniejszona do około 30 MB.

Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które używają odbicia lub powiązanych funkcji dynamicznych, często zostaną zerwane po przycięciu. To pęknięcie występuje, ponieważ konsolidator nie wie o tym zachowanie dynamiczne i nie można określić, które typy struktury są wymagane do odbicia. Narzędzie IL Linker można skonfigurować tak, aby zdawać sobie sprawę z tego scenariusza.

Przede wszystkim należy przetestować aplikację po przycinaniu.

Aby uzyskać więcej informacji na temat narzędzia IL Linker, zobacz [dokumentację](https://aka.ms/dotnet-illink) lub odwiedź repówkę [mono/linker.]( https://github.com/mono/linker)

### <a name="tiered-compilation"></a>Kompilacja warstwowa

[Kompilacja warstwowa](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) jest domyślnie włączone z .NET Core 3.0. Ta funkcja umożliwia programowi uruchomieniowemu bardziej adaptacyjne korzystanie z kompilatora just-in-time (JIT), aby osiągnąć lepszą wydajność.

Główną zaletą kompilacji warstwowej jest zapewnienie dwóch sposobów metody wysięgnika: w niższej jakości, ale szybciej warstwy lub wyższej jakości, ale wolniej warstwy. Jakość odnosi się do tego, jak dobrze metoda jest zoptymalizowana. TC pomaga poprawić wydajność aplikacji, ponieważ przechodzi przez różne etapy wykonywania, od uruchamiania przez stan stały. Gdy kompilacja warstwowa jest wyłączona, każda metoda jest kompilowana w jeden sposób, który jest stronniczy do wydajności w stanie stacjonarnym nad wydajnością uruchamiania.

Po włączeniu tc, następujące zachowanie ma zastosowanie do kompilacji metod podczas uruchamiania aplikacji:

- Jeśli metoda ma kod skompilowany z wyprzedzeniem lub [ReadyToRun](#readytorun-images), pregenerowany kod jest używany.
- W przeciwnym razie metoda jest wyjmowany. Zazwyczaj te metody są ogólne typy wartości.
  - *Szybki JIT* szybciej wytwarza kod niższej jakości (lub mniej zoptymalizowany). W .NET Core 3.0 Szybkie JIT jest domyślnie włączona dla metod, które nie zawierają pętli i jest preferowana podczas uruchamiania.
  - W pełni optymalizujący kod JIT wytwarza kod wyższej jakości (lub bardziej zoptymalizowany) wolniej. W przypadku metod, w których szybki jit nie będzie używany <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>(na przykład, jeśli metoda jest przypisana za pomocą), w pełni optymalizujący JIT jest używany.

W przypadku często nazywanych metod kompilator just-in-time ostatecznie tworzy w pełni zoptymalizowany kod w tle. Zoptymalizowany kod zastępuje następnie wstępnie skompilowany kod dla tej metody.

Kod generowany przez Szybki JIT może działać wolniej, przydzielać więcej pamięci lub używać więcej miejsca na stosie. Jeśli występują problemy, można wyłączyć Szybki JIT przy użyciu tej właściwości MSBuild w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

Aby całkowicie wyłączyć tc, użyj tej właściwości MSBuild w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Jeśli te ustawienia zostaną zmienić w pliku projektu, może być konieczne wykonanie czystej kompilacji, aby nowe ustawienia zostały odzwierciedlone (usuń `obj` katalogi i `bin` przebuduj).

Aby uzyskać więcej informacji na temat konfigurowania kompilacji w czasie wykonywania, zobacz [Opcje konfiguracji czasu wykonywania kompilacji](../run-time-config/compilation.md).

### <a name="readytorun-images"></a>Obrazy ReadyToRun

Czas uruchamiania aplikacji .NET Core można skrócić, kompilując zestawy aplikacji w formacie ReadyToRun (R2R). R2R jest formą kompilacji z wyprzedzeniem (AOT).

Pliki binarne R2R zwiększyć wydajność uruchamiania poprzez zmniejszenie ilości pracy kompilator just-in-time (JIT) musi wykonać podczas ładowania aplikacji. Pliki binarne zawierają podobny kod macierzysty w porównaniu do tego, co jit będzie produkować. Jednak pliki binarne R2R są większe, ponieważ zawierają zarówno kod języka pośredniego (IL), który jest nadal potrzebny w niektórych scenariuszach, jak i natywnej wersji tego samego kodu. R2R jest dostępna tylko podczas publikowania niezależnej aplikacji, która jest przeznaczona dla określonych środowisk środowiska uruchomieniowego (RID), takich jak Linux x64 lub Windows x64.

Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:

01. Dodaj `<PublishReadyToRun>` to ustawienie do projektu:

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Publikowanie niezależnej aplikacji. Na przykład to polecenie tworzy niezależną aplikację dla 64-bitowej wersji systemu Windows:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Ograniczenia między platformami/architekturą

Kompilator ReadyToRun nie obsługuje obecnie cross-targeting. Należy skompilować na danym celu. Na przykład, jeśli chcesz obrazy R2R dla systemu Windows x64, należy uruchomić polecenie publikowania w tym środowisku.

Wyjątki od kierowania krzyżowego:

- System Windows x64 może służyć do kompilowania obrazów z systemami Windows ARM32, ARM64 i x86.
- System Windows x86 może służyć do kompilowania obrazów arm32 systemu Windows.
- Linux x64 może być używany do kompilowania obrazów Linux ARM32 i ARM64.

## <a name="runtimesdk"></a>Czas wykonywania/zestaw SDK

### <a name="major-version-runtime-roll-forward"></a>Sposób wykonywania wersji głównej do przodu

.NET Core 3.0 wprowadza funkcję opt-in, która umożliwia aplikacji przewijanie do najnowszej wersji głównej programu .NET Core. Ponadto dodano nowe ustawienie, aby kontrolować sposób stosowania rolowania do przodu w aplikacji. Można to skonfigurować w następujący sposób:

- Właściwość pliku projektu:`RollForward`
- Właściwość pliku konfiguracyjnego w czasie wykonywania:`rollForward`
- Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`
- Argument wiersza polecenia:`--roll-forward`

Należy określić jedną z następujących wartości. Jeśli ustawienie zostanie pominięte, domyślnie domyślnym elementem **jest wartość Pomocnica.**

- **Najnowsza łata**\
Przewiń do przodu do najwyższej wersji poprawki. Spowoduje to wyłączenie pomocniczej wersji przewijania do przodu.
- **Drobne**\
Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanych wersji pomocniczej. Jeśli występuje żądana wersja pomocnicza, używana jest zasada **LatestPatch.**
- **Głównych**\
Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli nie ma żądanej wersji głównej. Jeśli występuje żądana wersja główna, używana jest zasada **pomocnicza.**
- **NajnowszaDrobna**\
Przewiń do przodu do najwyższej wersji pomocniczej, nawet jeśli żądana wersja pomocnicza jest obecna. Przeznaczone dla scenariuszy hostingu składników.
- **NajnowszaMajor**\
Przewiń do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane jest główne. Przeznaczone dla scenariuszy hostingu składników.
- **Wyłączyć**\
Nie przewiń do przodu. Powiąż tylko określoną wersję. Ta zasada nie jest zalecane do ogólnego użytku, ponieważ wyłącza możliwość przewijania do przodu do najnowszych poprawek. Ta wartość jest zalecana tylko do testowania.

Oprócz ustawienia **Wyłącz,** wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.

### <a name="build-copies-dependencies"></a>Tworzenie kopii zależności

Polecenie `dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu wyjściowego kompilacji. Wcześniej zależności były kopiowane tylko `dotnet publish`jako część pliku .

Istnieją pewne operacje, takie jak łączenie i publikowanie stron brzytwy, które nadal będą wymagały publikowania.

### <a name="local-tools"></a>Narzędzia lokalne

.NET Core 3.0 wprowadza narzędzia lokalne. Narzędzia lokalne są podobne do [narzędzi globalnych,](../tools/global-tools.md) ale są skojarzone z określoną lokalizacją na dysku. Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.

> [!WARNING]
> Jeśli w wersji .NET Core 3.0 Preview 1 `dotnet tool restore` `dotnet tool install`wypróbowano narzędzia lokalne, takie jak uruchamianie lub usuwanie folderu pamięci podręcznej narzędzi lokalnych. W przeciwnym razie narzędzia lokalne nie będą działać w żadnej nowszej wersji. Ten folder znajduje się pod adresem:
>
> W systemie macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`
>
> W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Narzędzia lokalne opierają się `dotnet-tools.json` na oczywistej nazwie pliku w bieżącym katalogu. Ten plik manifestu definiuje narzędzia, które mają być dostępne w tym folderze i poniżej. Można rozpowszechniać plik manifestu z kodem, aby upewnić się, że każdy, kto pracuje z kodem można przywrócić i używać tych samych narzędzi.

W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego. Wiele narzędzi, które są obecnie dostępne w NuGet.org celu .NET Core Runtime 2.1. Aby zainstalować te narzędzia globalnie lub lokalnie, nadal należy zainstalować [program NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).

### <a name="new-globaljson-options"></a>Nowe opcje global.json

Plik *global.json* ma nowe opcje, które zapewniają większą elastyczność podczas próby zdefiniowania, która wersja .NET Core SDK jest używana. Nowe opcje to:

- `allowPrerelease`: Wskazuje, czy program rozpoznawania nazw zestawów SDK powinien uwzględniać wersje wstępne podczas wybierania wersji sdk do użycia.
- `rollForward`: Wskazuje zasady przekazywania do przodu, które mają być używane podczas wybierania wersji sdk, albo jako rezerwowy, gdy brakuje określonej wersji sdk, albo jako dyrektywa do używania wyższej wersji.

Aby uzyskać więcej informacji na temat zmian, w tym wartości domyślnych, obsługiwanych wartości i nowych reguł dopasowywania, zobacz [global.json overview](../tools/global-json.md).

### <a name="smaller-garbage-collection-heap-sizes"></a>Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych

Domyślny rozmiar sterty modułu zbierającego elementy bezużyteczne został zmniejszony, co spowodowało użycie programu .NET Core przy użyciu mniejszej ilości pamięci. Ta zmiana lepiej dopasowuje się do budżetu alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej procesora.

### <a name="garbage-collection-large-page-support"></a>Obsługa dużych stron wyrzucania elementów bezużytecznych

Duże strony (znane również jako Ogromne strony w systemie Linux) to funkcja, w której system operacyjny jest w stanie ustanowić regiony pamięci większe niż rozmiar strony macierzystej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.

Moduł zbierający elementy bezużyteczne można teraz skonfigurować za pomocą ustawienia **GCLargePages** jako funkcję opt-in, aby przydzielić duże strony w systemie Windows.

## <a name="windows-desktop--com"></a>Środowisko com & dla komputerów stacjonarnych z systemem Windows

### <a name="net-core-sdk-windows-installer"></a>Instalator sdk programu .NET Core systemu Windows

Instalator MSI dla systemu Windows został zmieniony począwszy od .NET Core 3.0. Instalatorzy sdk będą teraz uaktualniać wersje pasma funkcji SDK w miejscu. Pasma funkcji są zdefiniowane w *setkach* grup w sekcji *poprawek* numeru wersji. Na przykład **3.0._ 101_ ** i **3,0._ 201_ ** to wersje w dwóch różnych zespołach fabularnych, podczas gdy **3.0._ 101_ ** i **3,0._ 199_ ** są w tym samym zespole fabularnym. I, gdy .NET Core SDK **3.0._ 101_ ** jest zainstalowany, .NET Core SDK **3.0._ 100_ ** zostanie usunięty chorąna z urządzenia, jeśli istnieje. Gdy .NET Core SDK **3.0._ 200_ ** jest zainstalowany na tym samym komputerze, .NET Core SDK **3.0._ 101_ ** nie zostanie usunięty.

Aby uzyskać więcej informacji na temat wersji, zobacz [Omówienie wersji programu .NET Core](../versions/index.md).

### <a name="windows-desktop"></a>Pulpit systemu Windows

Program .NET Core 3.0 obsługuje aplikacje klasyczne systemu Windows przy użyciu programu Windows Presentation Foundation (WPF) i formularzy systemu Windows. Te struktury obsługują również przy użyciu nowoczesnych formantów i płynnego stylu z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Składnik Pulpit systemu Windows jest częścią sdk windows .NET Core 3.0.

Można utworzyć nową aplikację WPF lub Formularze systemu Windows za pomocą następujących `dotnet` poleceń:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Program Visual Studio 2019 dodaje nowe szablony **projektów** dla formularzy systemu Windows .NET Core 3.0 i WPF.

Aby uzyskać więcej informacji na temat przenoszenia istniejącej aplikacji .NET Framework, zobacz [Projekty Port WPF](../../desktop-wpf/migration/convert-project-from-net-framework.md) i [Port Windows Forms .](../porting/winforms.md)

#### <a name="winforms-high-dpi"></a>WinForms wysoki DPI

Aplikacje .NET Core Windows Forms można <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>ustawić tryb wysokiej dpi za pomocą . Metoda `SetHighDpiMode` ustawia odpowiedni tryb wysokiego DPI, chyba że ustawienie `App.Manifest` zostało ustawione w `Application.Run`inny sposób, taki jak p/invoke przed .

Możliwe `highDpiMode` wartości, wyrażone w <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> wyliczeniu są następujące:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Aby uzyskać więcej informacji na temat trybów wysokiej dpi, zobacz [Programowanie aplikacji pulpitu o wysokiej dpi w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="create-com-components"></a>Tworzenie składników COM

W systemie Windows można teraz tworzyć składniki zarządzane wywoływane przez com. Ta funkcja ma kluczowe znaczenie dla używania .NET Core z modelami dodatku COM, a także w celu zapewnienia parzystości z .NET Framework.

W przeciwieństwie do platformy .NET Framework, w której jako serwera COM był używany *plik mscoree.dll,* program .NET Core doda do katalogu *bin* serwer natywnej dll wyrzutni.

Aby zapoznać się z przykładem sposobu tworzenia składnika COM i używania go, zobacz [pokaz modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Windows Native Interop

System Windows oferuje bogaty natywny interfejs API w postaci płaskich interfejsów API C, COM i WinRT. Podczas gdy .NET Core obsługuje **P/Invoke**, .NET Core 3.0 dodaje możliwość **współtworzenia interfejsów API COM** i **aktywowania interfejsów API WinRT**. Na przykład kodu zobacz [Pokaz programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>Wdrożenie MSIX

[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows. Może służyć do wdrażania aplikacji komputerowych .NET Core 3.0 w systemie Windows 10.

[Projekt pakowania aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX z [samodzielnymi](../deploying/index.md#publish-self-contained) aplikacjami .NET Core.

Plik projektu .NET Core musi określać obsługiwane `<RuntimeIdentifiers>` działania uruchomieniowe we właściwości:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Ulepszenia Linuksa

### <a name="serialport-for-linux"></a>SerialPort dla systemu Linux

.NET Core 3.0 zapewnia <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> podstawową obsługę w systemie Linux.

Wcześniej program .NET Core `SerialPort` był obsługiwany tylko w systemie Windows.

Aby uzyskać więcej informacji na temat ograniczonej obsługi portu szeregowego w systemie Linux, zobacz [Problem usługi GitHub #33146](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Limity pamięci docker i cgroup

Uruchamianie .NET Core 3.0 w systemie Linux z platformą Docker działa lepiej z limitami pamięci grupy cgroup. Uruchamianie kontenera platformy Docker `docker run -m`z limitami pamięci, na przykład z , zmienia sposób działania programu .NET Core.

- Domyślny rozmiar sterty modułu zbierającego elementy bezużyteczne (GC): maksymalnie 20 mb lub 75% limitu pamięci w kontenerze.
- Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu grupy.
- Minimalny zarezerwowany rozmiar segmentu na stertę GC wynosi 16 mb. Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.

### <a name="gpio-support-for-raspberry-pi"></a>Obsługa GPIO dla Raspberry Pi

Dwa pakiety zostały wydane do NuGet, które można użyć do programowania GPIO:

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [Wiązania iot.Device.bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Pakiety GPIO zawierają interfejsy API dla urządzeń *GPIO,* *SPI,* *I2C*i *PWM.* Pakiet powiązań IoT zawiera powiązania urządzeń. Aby uzyskać więcej informacji, zobacz [urządzenia GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).

### <a name="arm64-linux-support"></a>Obsługa systemu ARM64 Linux

.NET Core 3.0 dodaje obsługę arm64 dla systemu Linux. Głównym przypadkiem użycia dla ARM64 jest obecnie ze scenariuszami IoT. Aby uzyskać więcej informacji, zobacz [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

[Obrazy docker dla .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debiana i Ubuntu.

> [!NOTE]
> **ARM64 ( ARM64 )** Pomoc techniczna systemu Windows nie jest jeszcze dostępna.

## <a name="security"></a>Zabezpieczenia

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 w systemie Linux

Program .NET Core korzysta teraz z [obsługi protokołu TLS 1.3 w openssl 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest dostępny w danym środowisku. Z TLS 1.3:

- Czasy połączenia są poprawiane dzięki ograniczeniu liczby przejazdów w obie strony między klientem a serwerem.
- Poprawiono bezpieczeństwo dzięki usunięciu różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.

Jeśli jest dostępny, .NET Core 3.0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux. Gdy **openssl 1.1.1** jest <xref:System.Net.Security.SslStream?displayProperty=nameWithType> <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> dostępny, oba i typy będą używać **TLS 1.3** (przy założeniu, że zarówno klient, jak i serwer obsługują **TLS 1.3).**

> [!IMPORTANT]
> Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1.3**. .NET Core 3.0 będzie obsługiwać **protokół TLS 1.3** w tych systemach operacyjnych, gdy pomoc techniczna stanie się dostępna.

Poniższy przykład języka C# 8.0 pokazuje ,NET Core 3.0 na <https://www.cloudflare.com>Ubuntu 18.10 łączącsię z:

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Szyfry kryptograficzne

.NET 3.0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM,** zaimplementowanych odpowiednio z <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> odpowiednio. Algorytmy te są zarówno [uwierzytelnione szyfrowanie z danymi skojarzenia (AEAD) algorytmy](https://en.wikipedia.org/wiki/Authenticated_encryption).

Poniższy kod demonstruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania losowych danych.

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Import/eksport kluczy kryptograficznych

.NET Core 3.0 obsługuje import i eksport asymetrycznych kluczy publicznych i prywatnych ze standardowych formatów. Nie musisz używać certyfikatu X.509.

Wszystkie typy kluczy, takie jak *RSA,* *DSA,* *ECDsa*i *ECDiffieHellman,* obsługują następujące formaty:

- **Klucz publiczny**
  - X.509 SubjectPublicKeyInfo

- **Klucz prywatny**
  - PKCS#8 PrivateKeyInfo
  - PKCS#8 EncryptedPrivateKeyInfo

Klawisze RSA obsługują również:

- **Klucz publiczny**
  - PKCS#1 RSAPublicKey

- **Klucz prywatny**
  - PKCS#1 RSAPrivateKey

Metody eksportu produkują dane binarne zakodowane w formacie DER, a metody importu oczekują tego samego. Jeśli klucz jest przechowywany w formacie PEM przyjazny dla tekstu, obiekt wywołujący będzie musiał base64-dekodować zawartość przed wywołaniem metody importu.

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**Pliki PKCS#8** można sprawdzić, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> a pliki **PFX/PKCS#12** <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>można sprawdzić za pomocą . **Pliki PFX/PKCS#12** można manipulować za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="net-core-30-api-changes"></a>Zmiany interfejsu API .NET Core 3.0

### <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy <xref:System.Index?displayProperty=nameWithType> typ może służyć do indeksowania. Można utworzyć jeden `int` z tego, który liczy się `^` od początku lub z operatorem prefiksu (C#), który liczy się od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa `Index` się z dwóch wartości, jeden dla początku i jeden `x..y` na koniec i mogą być zapisywane z wyrażeniem zakresu (C#). Następnie można indeksować `Range`za pomocą , który tworzy plasterek:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Aby uzyskać więcej informacji, zobacz [zakresy i indeksy samouczek](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Strumienie asynchroniczne

Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> jest nową asynchroniczną <xref:System.Collections.Generic.IEnumerable%601>wersją programu . Język pozwala `await foreach` na `IAsyncEnumerable<T>` korzystanie z ich `yield return` elementów i używać do nich do tworzenia elementów.

W poniższym przykładzie przedstawiono zarówno produkcję, jak i zużycie strumieni asynchronii. Instrukcja `foreach` jest async `yield return` i sam używa do tworzenia strumienia asynchronicznego dla wywołań. Ten wzorzec (za pomocą `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznego.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Oprócz możliwości `await foreach`, można również utworzyć iteratory asynchroniczne, na przykład iterator, który `await` `yield` `IAsyncEnumerable/IAsyncEnumerator` zwraca, że można zarówno i w. W przypadku obiektów, które muszą zostać `IAsyncDisposable`usunięte, można użyć , `Stream` które `Timer`różne typy BCL implementują, takie jak i .

Aby uzyskać więcej informacji, zobacz [samouczek strumieni asynchroniczych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>Zmiennoprzecinkowy punkt pływatowy IEEE

Interfejsy API zmiennoprzecinkowych są aktualizowane zgodnie z [wersją IEEE 754-2008.](https://en.wikipedia.org/wiki/IEEE_754-2008_revision) Celem tych zmian jest udostępnienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne behawioralnie ze specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [ulepszenia analizy i formatowania zmiennoprzecinkowego w blogu .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

Poprawki dotyczące analiz owania i formatowania obejmują:

- Poprawnie analizować i okrągłe dane wejściowe o dowolnej długości.
- Poprawnie przeanalizować i sformatować ujemne zero.
- Poprawnie przeanalizować `Infinity` i `NaN` wykonując sprawdzanie bez uwzględniania wielkości liter `+` i pozwalając opcjonalne poprzedzające w stosownych przypadkach.

Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:

- <xref:System.Math.BitIncrement(System.Double)>I<xref:System.Math.BitDecrement(System.Double)>\
Odpowiada operacjom `nextUp` `nextDown` ieee i IEEE. Zwracają najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio). Na przykład, `Math.BitIncrement(0.0)` `double.Epsilon`zwróci .

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)>I<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odpowiada `maxNumMag` i `minNumMag` IEEE operacji, zwracają wartość, która jest większa lub mniejsza wielkości dwóch danych wejściowych (odpowiednio). Na przykład, `Math.MaxMagnitude(2.0, -3.0)` `-3.0`zwróci .

- <xref:System.Math.ILogB(System.Double)>\
Odpowiada operacji `logB` IEEE, która zwraca wartość integralną, zwraca integralną dziennika base-2 parametru wejściowego. Ta metoda jest skutecznie `floor(log2(x))`taka sama jak , ale wykonane z minimalnym błędem zaokrąglania.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odpowiada operacji `scaleB` IEEE, która przyjmuje wartość integralną, `x * pow(2, n)`zwraca skutecznie , ale odbywa się przy minimalnym błędzie zaokrąglania.

- <xref:System.Math.Log2(System.Double)>\
Odpowiada operacji `log2` IEEE, zwraca logarytm base-2. Minimalizuje błąd zaokrąglania.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odpowiada operacji `fma` IEEE, wykonuje posmarowywany dodają mnożenie. Oznacza to, `(x * y) + z` że robi to jako pojedyncza operacja, minimalizując w ten sposób błąd zaokrąglania. Przykładem jest `FusedMultiplyAdd(1e308, 2.0, -1e308)`, `1e308`który zwraca . Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Odpowiada operacji `copySign` IEEE, zwraca wartość `x`, ale ze znakiem `y`.

### <a name="net-platform-dependent-intrinsics"></a>Wewnętrzne elementy zależne od platformy .NET

Dodano interfejsy API, które umożliwiają dostęp do niektórych instrukcji procesora cpu zorientowanych na perf, takich jak zestawy instrukcji **SIMD** lub **Bit Manipulation.** Te instrukcje mogą pomóc osiągnąć znaczną poprawę wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych równolegle.

W stosownych przypadkach biblioteki .NET zaczęły używać tych instrukcji w celu zwiększenia wydajności.

Aby uzyskać więcej informacji, zobacz [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

### <a name="improved-net-core-version-apis"></a>Ulepszone interfejsy API wersji podstawowej .NET

Począwszy od .NET Core 3.0, interfejsy API wersji dostarczane z .NET Core zwracają teraz informacje, których oczekujesz. Przykład:

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
> Przełomowa zmiana. Jest to technicznie przełomowa zmiana, ponieważ schemat wersji uległ zmianie.

### <a name="fast-built-in-json-support"></a>Szybka wbudowana obsługa JSON

Użytkownicy .NET w dużej mierze polegali na [Newtonsoft.Json](https://www.newtonsoft.com/json) i innych popularnych bibliotekach JSON, które nadal są dobrym wyborem. `Newtonsoft.Json`używa ciągów .NET jako podstawowego typu danych, którym jest UTF-16 pod maską.

Nowa wbudowana obsługa JSON jest wysoka wydajność, niska alokacja i współpracuje z UTF-8 zakodowany tekst JSON. Aby uzyskać więcej <xref:System.Text.Json> informacji na temat obszaru nazw i typów, zobacz następujące artykuły:

* [Serializacja JSON w .NET — omówienie](../../standard/serialization/system-text-json-overview.md)
* [Jak serializować i deserializować JSON w .NET](../../standard/serialization/system-text-json-how-to.md).
* [Jak przenieść z Newtonsoft.Json do System.Text.Json](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>Obsługa protokołu HTTP/2

Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> obsługuje protokół HTTP/2. Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się z niej korzystać.

Domyślnym protokołem pozostaje HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby. Najpierw można ustawić komunikat żądania HTTP, aby użyć protokołu HTTP/2:

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Po drugie, <xref:System.Net.Http.HttpClient> domyślnie można zmienić sposób używania protokołu HTTP/2:

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Wiele razy podczas tworzenia aplikacji, chcesz użyć połączenia niezaszyfrowanego. Jeśli wiesz, że docelowy punkt końcowy będzie używał protokołu HTTP/2, możesz włączyć połączenia niezaszyfrowane dla protokołu HTTP/2. Można go włączyć, ustawiając zmienną środowiskową `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` `1` lub włączając ją w kontekście aplikacji:

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Następne kroki

- [Przejrzyj zmiany dotyczące podziału między programami .NET Core 2.2 i 3.0.](../compatibility/2.2-3.0.md)
- [Przejrzyj zmiany dotyczące łamania zasad w aplikacji .NET Core 3.0 dla formularzy systemu Windows.](../compatibility/winforms.md#net-core-30)
