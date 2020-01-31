---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 10/22/2019
ms.openlocfilehash: b8aa19a1d422fe7d6accd2b095f15843446599cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789891"
---
# <a name="whats-new-in-net-core-30"></a>Co nowego w programie .NET Core 3.0

W tym artykule opisano nowości w programie .NET Core 3.0. Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko system Windows). Korzystając z pulpitu systemu Windows składnika zestawu SDK platformy .NET Core 3.0, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF). Aby można było wyczyścić, składnik pulpitu systemu Windows jest obsługiwany i uwzględniany w systemie Windows. Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.

Program .NET Core 3.0 dodaje obsługę C# 8.0. Zdecydowanie zaleca się używanie [programu Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej, [Visual Studio dla komputerów Mac 8,3](/visualstudio/mac/install-preview) lub nowszego lub [Visual Studio Code](https://code.visualstudio.com/) z najnowszym  **C# rozszerzeniem**.

[Pobierz i Rozpocznij pracę z platformą .NET Core 3.0](https://aka.ms/netcore3download) teraz w systemie Windows, MacOS lub Linux.

Aby uzyskać więcej informacji o wersji, zobacz [anons programu .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

Środowisko .NET Core RC1 zostało uznane za gotowe do produkcji przez firmę Microsoft i zostało w pełni obsługiwane. Jeśli korzystasz z wersji zapoznawczej, musisz przejść do wersji RTM, aby uzyskać pomoc techniczną.

## <a name="language-improvements-c-80"></a>Udoskonalenia C# języka 8,0

C#8,0 jest również częścią tej wersji, która obejmuje funkcję [typów referencyjnych dopuszczających wartość null](../../csharp/tutorials/nullable-reference-types.md) , [strumienie asynchroniczne](../../csharp/tutorials/generate-consume-asynchronous-stream.md)i [więcej wzorców](../../csharp/tutorials/pattern-matching.md). Aby uzyskać więcej informacji C# o funkcjach 8.0, zobacz [co nowego C# w programie 8.0](../../csharp/whats-new/csharp-8.md).

Wprowadzono ulepszenia dotyczące języka w celu obsługi następujących funkcji API poniżej:

- [Zakresy i indeksy](#ranges-and-indices)
- [Strumienie asynchroniczne](#async-streams)

## <a name="net-standard-21"></a>.NET Standard 2.1

Platforma .NET Core 3,0 implementuje **.NET Standard 2,1**. Jednak domyślny szablon `dotnet new classlib` generuje projekt, który nadal jest przeznaczony dla **.NET Standard 2,0**. Aby docelowa **.NET Standard 2.1**, edytuj plik projektu i Zmień `TargetFramework` właściwość na `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program visual Studio 2017 nie obsługuje **.NET Standard 2.1** ani **.NET Core 3.0**.

## <a name="compiledeploy"></a>Kompiluj/Wdróż

### <a name="default-executables"></a>Domyślne pliki wykonywalne

Platforma .NET Core teraz domyślnie kompiluje [pliki wykonywalne zależne od platformy](../deploying/index.md#framework-dependent-executables-fde) . To zachowanie jest nowe w przypadku aplikacji korzystających z zainstalowanej globalnie wersji platformy .NET Core. Wcześniej tylko [wstępnie zawarte wdrożenia](../deploying/index.md#self-contained-deployments-scd) spowodują utworzenie pliku wykonywalnego.

W trakcie `dotnet build` lub `dotnet publish`, tworzony jest plik wykonywalny zgodny ze środowiskiem i platformą używanego zestawu SDK. Można oczekiwać, że te same elementy wykonywalne są takie same jak w przypadku innych natywnych plików wykonywalnych, takich jak:

- Możesz kliknąć dwukrotnie plik wykonywalny.
- Aplikację można uruchomić bezpośrednio z poziomu wiersza polecenia, na przykład `myapp.exe` w systemie Windows i `./myapp` w systemie Linux i macOS.

### <a name="single-file-executables"></a>Pliki wykonywalne pojedynczego pliku

Polecenie `dotnet publish` obsługuje pakowanie aplikacji do pliku wykonywalnego określonego dla konkretnej platformy. Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji. Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji. Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie. Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że została użyta Nowa wersja.

Aby opublikować plik wykonywalny pojedynczego pliku, ustaw `PublishSingleFile` w projekcie lub w wierszu polecenia za pomocą polecenia `dotnet publish`:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

lub

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

### <a name="assembly-linking"></a>Łączenie zestawów

Zestaw SDK platformy .NET Core 3.0 zawiera narzędzie, które pozwala zmniejszyć rozmiar aplikacji przez analizowanie IL i przycinanie nieużywanych zestawów.

Aplikacje samodzielne obejmują wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania programu .NET na komputerze-hoście. Jednak wiele razy aplikacja wymaga tylko małego podzestawu platformy do działania, a inne nieużywane biblioteki mogą zostać usunięte.

Platforma .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora Il](https://github.com/mono/linker) do skanowania Il aplikacji. To narzędzie wykrywa wymagany kod, a następnie przycina nieużywane biblioteki. To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.

Aby włączyć to narzędzie, należy dodać ustawienie `<PublishTrimmed>` w projekcie i opublikować samodzielną aplikację:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Na przykład podstawowy "Hello World" nowy szablon projektu konsoli, który jest dostępny po opublikowaniu, trafień o rozmiarze 70 MB. Przy użyciu `<PublishTrimmed>`rozmiar jest zmniejszany do około 30 MB.

Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które wykorzystują odbicie lub powiązane funkcje dynamiczne, często będą przerywane po przycięciu. To uszkodzenie występuje, ponieważ konsolidator nie wie o tym zachowaniu dynamicznym i nie może określić, które typy struktur są wymagane do odbicia. Narzędzie konsolidatora IL można skonfigurować pod kątem tego scenariusza.

Przed przycinaniem upewnij się, że aplikacja została przetestowana.

Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zapoznaj się z [dokumentacją](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/konsolidatora]( https://github.com/mono/linker) .

### <a name="tiered-compilation"></a>Kompilacja warstwowa

[Kompilacja warstwowa](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) jest domyślnie włączona z platformą .NET Core 3.0. Ta funkcja umożliwia środowisku uruchomieniowemu wydajniejsze używanie kompilatora just-in-Time (JIT) w celu uzyskania lepszej wydajności.

Główną zaletą kompilacji warstwowej jest zapewnienie dwóch sposobów jitting metod: w warstwach o niższej jakości lub szybszych lub wyższych warstwach. Jakość odnosi się do tego, jak dobrze jest zoptymalizowana Metoda. TC ułatwia zwiększenie wydajności aplikacji w miarę przechodzenia przez różne etapy wykonywania — od uruchomienia do stanu stałego. Gdy kompilacja warstwowa jest wyłączona, każda metoda jest kompilowana w jednym ze sposobów, która jest obciążona wydajnością o stałej kondycji w porównaniu z wydajnością uruchamiania.

Po włączeniu TC następujące zachowanie ma zastosowanie do kompilacji metody podczas uruchamiania aplikacji:

- Jeśli metoda zawiera kod skompilowany z wyprzedzeniem lub [ReadyToRun](#readytorun-images), używany jest wygenerowany kod.
- W przeciwnym razie metoda jest trybie JIT. Zazwyczaj te metody są ogólne względem typów wartościowych.
  - *Szybkie kompilatory* umożliwiają szybsze generowanie kodu o niższej jakości (lub mniej zoptymalizowanym). W przypadku programu .NET Core 3,0, szybkie JIT jest domyślnie włączone dla metod, które nie zawierają pętli i są preferowane podczas uruchamiania.
  - W pełni Optymalizacja JIT powoduje szybsze generowanie kodu o wyższej jakości (lub bardziej zoptymalizowany). W przypadku metod, w których nie można użyć metody szybkiej JIT (na przykład jeśli metoda ma atrybut <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), używana jest pełna optymalizacja JIT.

W przypadku często wywoływanych metod kompilator just in Time w końcu tworzy w tle w pełni zoptymalizowany kod. Zoptymalizowany kod zastępuje wstępnie skompilowany kod dla tej metody.

Kod wygenerowany przez szybką JIT może działać wolniej, przydzielać więcej pamięci lub używać większej ilości miejsca na stosie. Jeśli występują problemy, można wyłączyć szybkie JIT przy użyciu tej właściwości programu MSBuild w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

Aby całkowicie wyłączyć TC, Użyj tej właściwości programu MSBuild w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Jeśli zmienisz te ustawienia w pliku projektu, może być konieczne wykonanie czystej kompilacji w celu odzwierciedlenia nowych ustawień (Usuń `obj` i `bin` katalogi i Skompiluj ponownie).

Aby uzyskać więcej informacji o konfigurowaniu kompilacji w czasie wykonywania, zobacz [Opcje konfiguracji czasu wykonywania dla kompilacji](../run-time-config/compilation.md).

### <a name="readytorun-images"></a>Obrazy ReadyToRun

Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji jako ReadyToRun (R2R). R2R to forma kompilacji z wyprzedzeniem (AOT).

Pliki binarne R2R zwiększają wydajność uruchamiania przez zmniejszenie ilości pracy kompilatora, który jest potrzebny do załadowania aplikacji. Pliki binarne zawierają podobny kod natywny w porównaniu z przeznaczeniem JIT. R2R pliki binarne są jednak większe, ponieważ zawierają kod języka pośredniego (IL), który jest nadal wymagany w niektórych scenariuszach i natywną wersję tego samego kodu. R2R jest dostępna tylko w przypadku publikowania aplikacji samodzielnej, która jest przeznaczona dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.

Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:

01. Dodaj do projektu ustawienie `<PublishReadyToRun>`:

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Publikowanie aplikacji samodzielnej. Na przykład to polecenie tworzy samodzielną aplikację dla 64-bitowej wersji systemu Windows:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Ograniczenia dotyczące wielu platform/architektury

Kompilator ReadyToRun nie obsługuje obecnie określania wartości docelowej. Należy skompilować na danym miejscu docelowym. Na przykład jeśli chcesz, aby obrazy R2R dla systemu Windows x64 zostały wykonane, należy uruchomić polecenie Publikuj w tym środowisku.

Wyjątki dla wielu elementów docelowych:

- System Windows x64 może służyć do kompilowania obrazów systemów Windows ARM32, ARM64 i x86.
- System Windows x86 może służyć do kompilowania obrazów ARM32 systemu Windows.
- System Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.

## <a name="runtimesdk"></a>Środowisko uruchomieniowe/zestaw SDK

### <a name="major-version-roll-forward"></a>Wersja główna — przekazanie do przodu

W programie .NET Core 3.0 wprowadzono funkcję wyboru, która pozwala aplikacji na przewinięcie do najnowszej wersji programu .NET Core. Ponadto zostało dodane nowe ustawienie służące do kontrolowania sposobu, w jaki przenoszone do przodu jest stosowane do aplikacji. Tę konfigurację można skonfigurować w następujący sposób:

- Właściwość pliku projektu: `RollForward`
- Właściwość pliku konfiguracji czasu wykonywania: `rollForward`
- Zmienna środowiskowa: `DOTNET_ROLL_FORWARD`
- Argument wiersza polecenia: `--roll-forward`

Należy określić jedną z następujących wartości. Jeśli ustawienie zostanie pominięte, wartością domyślną jest wartość **pomocnicza** .

- **LatestPatch**\
Przewinięcie do najwyższej wersji poprawki. Spowoduje to wyłączenie wycofywania wersji pomocniczej.
- \ **pomocnicze**
Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej. Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady **LatestPatch** .
- \ **Główne**
Zaczekaj na najmniejszą wyższą wersję główną i najniższą wersję pomocniczą, jeśli brakuje żądanej wersji głównej. Jeśli jest obecna żądana wersja główna, są używane zasady **pomocnicze** .
- **LatestMinor**\
Przewinięcie do przodu do najwyższej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza. Przeznaczone do scenariuszy hostingu składników.
- **LatestMajor**\
Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli jest obecny żądany główny. Przeznaczone do scenariuszy hostingu składników.
- **Wyłącz**\
Nie przetaczaj dalej. Powiąż tylko z określoną wersją. Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek. Ta wartość jest zalecana tylko do celów testowych.

Oprócz ustawienia **Wyłącz** wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.

### <a name="build-copies-dependencies"></a>Zależności kompilacji kopii

Polecenie `dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu danych wyjściowych kompilacji. Wcześniej zależności były kopiowane tylko jako część `dotnet publish`.

Istnieją pewne operacje, takie jak łączenie i publikowanie stron Razor, które nadal wymagają publikacji.

### <a name="local-tools"></a>Narzędzia lokalne

Środowisko .NET Core 3.0 zawiera wprowadzenie do narzędzi lokalnych. Narzędzia lokalne są podobne do [narzędzi globalnych](../tools/global-tools.md) , ale są skojarzone z konkretną lokalizacją na dysku. Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.

> [!WARNING]
> Jeśli podjęto próbę skorzystania z narzędzi lokalnych w programie .NET Core 3.0 `dotnet tool restore` w `dotnet tool install`wersji zapoznawczej 1, takiej jak uruchamianie lub, Usuń folder pamięci podręcznej narzędzi lokalnych W przeciwnym razie narzędzia lokalne nie będą działały w żadnej nowszej wersji. Ten folder znajduje się w lokalizacji:
>
> W systemie macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> W systemie Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Narzędzia lokalne są zależne od nazwy pliku manifestu `dotnet-tools.json` w bieżącym katalogu. Ten plik manifestu definiuje narzędzia do udostępnienia w tym folderze i poniżej. Plik manifestu można dystrybuować z kodem, aby upewnić się, że każda osoba, która współpracuje z kodem, będzie mogła przywrócić i korzystać z tych samych narzędzi.

W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego. Wiele narzędzi obecnie na NuGet.org docelowym środowiska uruchomieniowego .NET Core 2.1. Aby zainstalować te narzędzia globalnie lub lokalnie, nadal trzeba zainstalować [środowisko uruchomieniowe NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

### <a name="smaller-garbage-collection-heap-sizes"></a>Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych

Rozmiar sterty domyślnej modułu wyrzucania elementów bezużytecznych został zmniejszony z powodu mniejszej ilości pamięci w programie .NET Core. Ta zmiana jest lepsza w porównaniu z budżetem alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej.

### <a name="garbage-collection-large-page-support"></a>Obsługa dużej strony odzyskiwania pamięci

Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny może ustalić obszary pamięci większe niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.

Moduł wyrzucania elementów bezużytecznych można teraz skonfigurować przy użyciu ustawienia **GCLargePages** jako funkcji wyboru do przydzielania dużych stron w systemie Windows.

## <a name="windows-desktop--com"></a>Windows Desktop & COM

### <a name="net-core-sdk-windows-installer"></a>Zestaw .NET Core SDK Instalator Windows

Instalator MSI dla systemu Windows został zmieniony począwszy od platformy .NET Core 3.0. Instalatorzy zestawu SDK teraz uaktualniają wersje funkcji zestawu SDK na miejscu. Paski funkcji są zdefiniowane w grupach *setek* w sekcji *poprawka* numeru wersji. Na przykład **3.0. _101_**  i **3.0. _201_**  są wersje w dwóch różnych warstwach funkcji podczas **3.0. _101_**  i **3.0. _199_**  znajdują się w tej samej paśmie funkcji. I, w przypadku zestaw .NET Core SDK **3.0. _101_**  jest zainstalowana, zestaw .NET Core SDK **3.0. _100_**  zostanie usunięta z komputera, jeśli istnieje. Gdy zestaw .NET Core SDK **3.0. _200_**  jest zainstalowana na tym samym komputerze, zestaw .NET Core SDK **3.0. _101_**  nie zostanie usunięta.

Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).

### <a name="windows-desktop"></a>Pulpit systemu Windows

Program .NET Core 3.0 obsługuje aplikacje klasyczne systemu Windows przy użyciu Windows Presentation Foundation (WPF) i Windows Forms. Te struktury obsługują również korzystanie z nowoczesnych kontrolek i stylów Fluent z poziomu biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Składnik pulpitu systemu Windows jest częścią zestawu SDK systemu Windows .NET Core 3.0.

Nową aplikację WPF lub Windows Forms można utworzyć przy użyciu następujących poleceń `dotnet`:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Program Visual Studio 2019 dodaje **nowe szablony projektów** dla platformy .NET Core 3.0 Windows Forms i WPF.

Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [port WPF projekty](../../desktop-wpf/migration/convert-project-from-net-framework.md) i [projekty Windows Forms portów](../porting/winforms.md).

#### <a name="winforms-high-dpi"></a>Bardzo wysokie wartości DPI

Aplikacje .NET Core Windows Forms mogą ustawiać tryb wysokiej rozdzielczości DPI z <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. Metoda `SetHighDpiMode` ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że ustawienie zostało ustawione za pomocą innych metod, takich jak `App.Manifest` lub P/Invoke przed `Application.Run`.

Możliwe wartości `highDpiMode` wyrażone przez Wyliczenie <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> są następujące:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="create-com-components"></a>Tworzenie składników COM

W systemie Windows można teraz tworzyć zarządzane składniki COM. Ta funkcja ma kluczowe znaczenie dla korzystania z platformy .NET Core z modelami dodatków COM, a także do zapewnienia parzystości .NET Framework.

W przeciwieństwie do .NET Framework, w którym *Biblioteka mscoree. dll* była używana jako serwer com, podczas kompilowania składnika com program .NET Core doda natywną bibliotekę DLL uruchamiania do katalogu *bin* .

Przykład sposobu tworzenia składnika modelu COM i korzystania z niego można znaleźć w [demonstracji modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Windows Native Interop

System Windows oferuje bogaty natywny interfejs API w postaci prostych interfejsów API języka C, COM i WinRT. Podczas gdy platforma .NET Core obsługuje funkcję **P/Invoke**, program .NET Core 3.0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywowania interfejsów API WinRT**. Aby zapoznać się z przykładem kodu, zobacz [Demonstracja programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>Wdrożenie MSIX

[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows. Można go użyć do wdrożenia aplikacji klasycznych platformy .NET Core 3.0 w systemie Windows 10.

[Projekt pakietu aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX przy użyciu [samodzielnych](../deploying/index.md#self-contained-deployments-scd) aplikacji .NET Core.

Plik projektu .NET Core musi określać obsługiwane środowiska uruchomieniowe we właściwości `<RuntimeIdentifiers>`:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Udoskonalenia systemu Linux

### <a name="serialport-for-linux"></a>Klasy SerialPort dla systemu Linux

Program .NET Core 3.0 zapewnia podstawową pomoc <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> techniczną dla systemu Linux.

Wcześniej platforma .NET Core była obsługiwana tylko przy użyciu `SerialPort` w systemie Windows.

Aby uzyskać więcej informacji o ograniczonej obsłudze portu szeregowego w systemie Linux, zobacz artykuł [dotyczący usługi GitHub #33146](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Limity pamięci Docker i cgroup

Uruchamianie programu .NET Core 3.0 w systemie Linux przy użyciu platformy Docker działa lepiej z limitami pamięci cgroup. Uruchamianie kontenera Docker z limitami pamięci, na przykład z `docker run -m`, zmienia sposób działania programu .NET Core.

- Domyślny rozmiar sterty modułu wyrzucania elementów bezużytecznych (GC): maksymalnie 20 MB lub 75% limitu pamięci w kontenerze.
- Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu cgroup.
- Minimalny zarezerwowany rozmiar segmentu na stos GC to 16 MB. Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.

### <a name="gpio-support-for-raspberry-pi"></a>Obsługa interfejsu GPIO dla Raspberry Pi

Do programu NuGet zostały wydane dwa pakiety, których można użyć do programowania interfejsu GPIO:

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [IoT. Device. bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Pakiety GPIO obejmują interfejsy API dla urządzeń z interfejsem *GPIO*, *SPI*, *I2C*i *PWM* . Pakiet powiązań IoT obejmuje powiązania urządzeń. Aby uzyskać więcej informacji, zobacz [repozytorium GitHub](https://github.com/dotnet/iot/blob/master/src/devices/).

### <a name="arm64-linux-support"></a>Obsługa systemu Linux ARM64

Program .NET Core 3.0 dodaje obsługę ARM64 dla systemu Linux. Podstawowy przypadek użycia dla ARM64 jest obecnie z scenariuszami IoT. Aby uzyskać więcej informacji, zobacz temat [stan arm64 programu .NET Core](https://github.com/dotnet/announcements/issues/82).

[Obrazy Docker dla platformy .NET Core w systemie arm64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.

> [!NOTE]
> **Arm64** Obsługa systemu Windows nie jest jeszcze dostępna.

## <a name="security"></a>Zabezpieczenia

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 w systemie Linux

Platforma .NET Core wykorzystuje teraz zalety [protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest on dostępny w danym środowisku. Z protokołem TLS 1.3:

- Czas połączenia jest ulepszony ze zredukowanymi przedziałami rundy między klientem i serwerem.
- Ulepszone zabezpieczenia spowodowane usuwaniem różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.

Jeśli jest dostępny, program .NET Core 3.0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux. Gdy **OpenSSL 1.1.1** jest dostępny, oba <xref:System.Net.Security.SslStream?displayProperty=nameWithType> typy <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i używają **protokołu TLS 1.3** (przy założeniu, że zarówno klient, jak i serwer obsługują **protokół TLS 1.3**).

> [!IMPORTANT]
> Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1.3**. Platforma .NET Core 3.0 będzie obsługiwać **protokół TLS 1.3** w tych systemach operacyjnych, gdy będzie dostępna pomoc techniczna.

Poniższy C# przykład 8,0 ilustruje platformę .NET Core 3.0 na Ubuntu 18.10 <https://www.cloudflare.com>z:

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Szyfrowanie kryptografii

Program .NET 3.0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM** , implementowanych <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> za <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> pomocą i odpowiednio. Te algorytmy są [uwierzytelnianiem uwierzytelnianym przy użyciu algorytmów danych skojarzenia (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Poniższy kod ilustruje użycie szyfru `AesGcm` do szyfrowania i odszyfrowywania danych losowych.

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Import/Eksport klucza kryptograficznego

Program .NET Core 3.0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych z formatów standardowych. Nie musisz używać certyfikatu X. 509.

Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDSA*i *ECDiffieHellman*, obsługują następujące formaty:

- **Klucz publiczny**
  - SubjectPublicKeyInfo X. 509

- **Klucz prywatny**
  - PrivateKeyInfo PKCS # 8
  - EncryptedPrivateKeyInfo PKCS # 8

Klucze RSA obsługują również:

- **Klucz publiczny**
  - RSAPublicKey PKCS # 1

- **Klucz prywatny**
  - RSAPrivateKey PKCS # 1

Metody eksportowania generują dane binarne kodowane algorytmem DER, a metody importowe oczekują na to samo. Jeśli klucz jest przechowywany w formacie PEM przyjaznym dla tekstu, wywołujący będzie musiał odkodować zawartość przed wywołaniem metody Import.

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

Pliki **PKCS # 8** można sprawdzić za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, a pliki **PFX/PKCS # 12** można sprawdzić przy użyciu <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. Pliki **PFX/PKCS # 12** można manipulować przy użyciu <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="net-core-30-api-changes"></a>Zmiany interfejsu API programu .NET Core 3,0

### <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy typ <xref:System.Index?displayProperty=nameWithType> może służyć do indeksowania. Można utworzyć jeden z `int`, który liczy od początku lub z prefiksem `^` (C#), który liczy się od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również typ <xref:System.Range?displayProperty=nameWithType>, który składa się z dwóch `Index` wartości, jeden dla początku i jeden dla końca, i może być zapisany z wyrażeniem zakresu `x..y` (C#). Następnie można indeksować za pomocą `Range`, co spowoduje utworzenie wycinka:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Strumienie asynchroniczne

Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> to nowa asynchroniczna wersja <xref:System.Collections.Generic.IEnumerable%601>. Język pozwala `await foreach` za pośrednictwem `IAsyncEnumerable<T>` do korzystania z ich elementów, a następnie używać `yield return` do tworzenia elementów.

Poniższy przykład ilustruje produkcję i zużycie strumieni asynchronicznych. Instrukcja `foreach` jest asynchroniczna i sama używa `yield return` do tworzenia strumienia asynchronicznego dla obiektów wywołujących. Ten wzorzec (przy użyciu `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznych.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Poza możliwością `await foreach`można także tworzyć Iteratory asynchroniczne, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator`, które można `await` i `yield` w. W przypadku obiektów, które muszą zostać usunięte, można użyć `IAsyncDisposable`, które mają różne implementacje typów BCL, takie jak `Stream` i `Timer`.

Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>Liczba zmiennoprzecinkowa IEEE

Interfejsy API zmiennoprzecinkowe są aktualizowane w celu zapewnienia zgodności z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Celem tych zmian jest uwidocznienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [udoskonalenia analizy i formatowania zmiennoprzecinkowe w wpisie na blogu programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

Poprawki dotyczące analizowania i formatowania obejmują:

- Poprawnie Analizuj i Zaokrąglij dane wejściowe o dowolnej długości.
- Prawidłowo Przeanalizuj i sformatuj ujemną wartość zero.
- Prawidłowo Przeanalizuj `Infinity` i `NaN`, wykonując kontrolę bez uwzględniania wielkości liter i zezwalając na opcjonalne, poprzednia `+`, jeśli ma to zastosowanie.

Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:

- <xref:System.Math.BitIncrement(System.Double)> i <xref:System.Math.BitDecrement(System.Double)>\
Odnosi się do `nextUp` i `nextDown` operacji IEEE. Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio). Na przykład `Math.BitIncrement(0.0)` zwróci `double.Epsilon`.

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)> i <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odnosi się do `maxNumMag` i `minNumMag` operacji IEEE, zwracają wartość, która jest większa lub mniejsza o wielkości dwóch danych wejściowych (odpowiednio). Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwróci `-3.0`.

- <xref:System.Math.ILogB(System.Double)>\
Odnosi się do `logB` operacji IEEE, która zwraca wartość całkowitą, zwracająca podstawowy dziennik Base-2 parametru wejściowego. Ta metoda jest efektywnie taka sama jak `floor(log2(x))`, ale została wykonana z minimalnym błędem zaokrąglania.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odnosi się do `scaleB` operacji IEEE, która przyjmuje wartość całkowitą, która zwraca efektywnie `x * pow(2, n)`, ale jest wykonywana z minimalnym błędem zaokrąglania.

- <xref:System.Math.Log2(System.Double)>\
Odnosi się do `log2` operacji IEEE, która zwraca logarytm o podstawie 2. Minimalizuje błąd zaokrąglania.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odnosi się do `fma` operacji IEEE, dlatego wykonuje odrzucane, wielokrotne Dodawanie. Oznacza to, że `(x * y) + z` w ramach jednej operacji, co minimalizuje błąd zaokrąglania. Przykładem jest `FusedMultiplyAdd(1e308, 2.0, -1e308)`, która zwraca `1e308`. Regularne `(1e308 * 2.0) - 1e308` zwraca `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Odnosi się do `copySign` operacji IEEE, która zwraca wartość `x`, ale ze znakiem `y`.

### <a name="net-platform-dependent-intrinsics"></a>Elementy wewnętrzne zależne od platformy .NET

Dodano interfejsy API, które umożliwiają dostęp do pewnych instrukcji procesora CPU zorientowanych na wydajność, takich jak **SIMD** lub **bitowe zestawy instrukcji manipulowania** . Te instrukcje mogą pomóc w osiągnięciu znaczących ulepszeń wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych.

W odpowiednich przypadkach biblioteki .NET zaczęły korzystać z tych instrukcji w celu zwiększenia wydajności.

Aby uzyskać więcej informacji, zobacz elementy [wewnętrzne zależne od platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

### <a name="improved-net-core-version-apis"></a>Ulepszone interfejsy API wersji platformy .NET Core

Począwszy od platformy .NET Core 3.0, interfejsy API wersji dostarczone z platformą .NET Core teraz zwracają oczekiwane informacje. Na przykład:

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
> Istotna zmiana. Jest to technicznie istotna zmiana, ponieważ schemat przechowywania wersji został zmieniony.

### <a name="fast-built-in-json-support"></a>Szybka Wbudowana obsługa JSON

Użytkownicy platformy .NET w dużym stopniu opierają się na [Newtonsoft. JSON](https://www.newtonsoft.com/json) i innych popularnych bibliotekach JSON, które nadal są dobrym wybórem. `Newtonsoft.Json` używa ciągów .NET jako podstawowego elementu DataType, który jest UTF-16 pod okapem.

Nowa Wbudowana obsługa JSON to wysoka wydajność, niska alokacja i współpracuje z tekstem JSON zakodowanym w formacie UTF-8. Więcej informacji o przestrzeni nazw i typach <xref:System.Text.Json> można znaleźć w następujących artykułach:

* [Serializacja kodu JSON w programie .NET — Omówienie](../../standard/serialization/system-text-json-overview.md)
* [Jak serializować i deserializować kod JSON w programie .NET](../../standard/serialization/system-text-json-how-to.md).
* [Jak przeprowadzić migrację z Newtonsoft. JSON do System. Text. JSON](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>Obsługa protokołu HTTP/2

Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> obsługuje protokół HTTP/2. Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/CLIENTHELLO ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się go użyć.

Domyślnym protokołem jest protokół HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby. Najpierw można ustawić komunikat żądania HTTP na potrzeby używania protokołu HTTP/2:

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Następnie można zmienić <xref:System.Net.Http.HttpClient>, aby domyślnie używać protokołu HTTP/2:

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

W wielu przypadkach podczas tworzenia aplikacji chcesz użyć nieszyfrowanego połączenia. Jeśli wiesz, że docelowy punkt końcowy będzie używać protokołu HTTP/2, możesz włączyć nieszyfrowane połączenia dla protokołu HTTP/2. Można ją włączyć, ustawiając zmienną środowiskową `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` na `1` lub włączając ją w kontekście aplikacji:

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Następne kroki

- [Zapoznaj się z istotnymi zmianami między programem .NET Core 2,2 i 3,0.](../compatibility/2.2-3.0.md)
- [Zapoznaj się z istotnymi zmianami w programie .NET Core 3,0 dla aplikacji Windows Forms.](../compatibility/winforms.md#net-core-30)
