---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 369c74d2d8e82f157de0eec4294a5ee50542292b
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169785"
---
# <a name="whats-new-in-net-core-30-preview-5"></a>What's new in .NET Core 3.0 (wersja zapoznawcza 5)

W tym artykule opisano nowości w programie .NET Core 3.0 (za pośrednictwem wersja zapoznawcza 5). Jedną z największych ulepszenia to obsługa aplikacji klasycznych Windows (tylko Windows). Za pomocą zestawu .NET Core 3.0 SDK składnika Windows Desktop, można przenosić aplikacje Windows Forms i Windows Presentation Foundation (WPF). Było jasne, składnik Windows Desktop jest tylko obsługiwana i uwzględniane na Windows. Aby uzyskać więcej informacji, zobacz [pulpitu Windows](#windows-desktop) sekcję w dalszej części tego artykułu.

.NET core 3.0 dodaje obsługę C# 8.0. Zdecydowanie zaleca się używać najnowszej wersji programu Visual Studio 2019 Update 1 (wersja zapoznawcza) lub programu VSCode z rozszerzeniem technologię OmniSharp.

[Pobierz i rozpoczynanie pracy z usługą .NET Core 3.0 w wersji zapoznawczej 6](https://aka.ms/netcore3download) teraz na Windows, Mac i Linux.

Aby uzyskać więcej informacji na temat poszczególnych wersji zapoznawczej zobacz następujące komunikaty:

- [Ogłoszenie .NET core 3.0 w wersji zapoznawczej 6](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [Ogłoszenie .NET core 3.0 w wersji zapoznawczej 5](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [Ogłoszenie .NET core 3.0 w wersji zapoznawczej 4](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [Ogłoszenie .NET core 3.0 w wersji zapoznawczej 3](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [Ogłoszenie .NET core 3.0 w wersji zapoznawczej 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [Ogłoszenie .NET core 3.0 w wersji zapoznawczej 1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a>Instalator Windows zestawu SDK programu .NET core

Instalator MSI dla Windows został zmieniony, począwszy od programu .NET Core 3.0. Instalatory SDK uaktualni teraz zestaw SDK funkcji harmonogramem w miejscu. Paski funkcji są definiowane w *setki* grup w *poprawki* część numeru wersji. Na przykład **3.0. * 101*** i **3.0. * 201*** są wersje w dwóch grup różnych funkcji podczas **3.0. * 101*** i **3.0. * 199*** znajdują się w tej samej funkcji poza pasmem. I kiedy zestawu .NET Core SDK **3.0. * 101*** jest zainstalowany zestaw .NET Core SDK **3.0. * 100*** zostaną usunięte z komputera, jeśli taki istnieje. Gdy zestaw .NET Core SDK **3.0. * 200*** jest zainstalowany na tym samym komputerze, .NET Core SDK **3.0. * 101*** nie zostaną usunięte.

Aby uzyskać więcej informacji dotyczących wersjonowania, zobacz [omówienie sposobu platformy .NET Core jest wersjonowany](../versions/index.md).

## <a name="c-80-preview"></a>C#8.0 (wersja zapoznawcza)

Obsługuje platformy .NET core 3.0 C# 8 (wersja zapoznawcza). Aby uzyskać więcej informacji na temat C# funkcje 8.0, zobacz [nowości C# 8.0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET Standard 2.1

Mimo że program .NET Core 3.0 obsługuje **platformy .NET Standard 2.1**, domyślnie `dotnet new classlib` szablon generuje projekt, który jest przeznaczony dla **.NET Standard 2.0**. Do obiektu docelowego **platformy .NET Standard 2.1**, Edycja pliku projektu i zmień `TargetFramework` właściwości `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

Jeśli używasz programu Visual Studio należy Visual Studio 2019 r, jak program Visual Studio 2017 nie obsługuje **platformy .NET Standard 2.1** lub **.NET Core 3.0 to**. Zdecydowanie zaleca się używanie [Visual Studio 2019 aktualizacja 1 — wersja zapoznawcza](https://visualstudio.microsoft.com/vs/preview/).

## <a name="improved-net-core-version-apis"></a>Ulepszone .NET Core wersje interfejsów API

Począwszy od .NET Core 3.0 to wersja, podane interfejsów API za pomocą programu .NET Core teraz zwracane informacje oczekujesz. Na przykład:

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
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Zmiana powodująca niezgodność. Jest to technicznie istotnej zmiany, ponieważ zmienił się schemat przechowywania wersji.

## <a name="net-platform-dependent-intrinsics"></a>Funkcje wewnętrzne zależny od platformy .NET

Dodano interfejsy API, takich jak zezwalające na dostęp do niektórych instrukcji zorientowane na wydajności procesora CPU **SIMD** lub **instrukcji manipulowania Bit** ustawia. Te instrukcje może pomóc osiągnąć znaczne zwiększenie wydajności w niektórych scenariuszach, takich jak przetwarzanie danych, efektywnie równolegle. 

Gdzie jest to odpowiednie, do bibliotek .NET rozpoczęły przy użyciu tych instrukcji, aby zwiększyć wydajność.

Aby uzyskać więcej informacji, zobacz [wewnętrzne zależne platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Domyślne pliki wykonywalne

.NET core teraz kompilacje [zależny od struktury plików wykonywalnych](../deploying/index.md#framework-dependent-executables-fde) domyślnie. To zachowanie jest nowa dla aplikacji, które używają globalnie zainstalowaną wersję platformy .NET Core. Wcześniej tylko [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) dałby w efekcie plik wykonywalny.

Podczas `dotnet build` lub `dotnet publish`, tworzony jest plik wykonywalny, który pasuje do środowiska i platformy zestawu SDK jest używany. Mogą spodziewać się tego samego rzeczy, korzystając z tych plików wykonywalnych, tak jak w innych natywnych plików wykonywalnych, takich jak:

* Możesz kliknąć dwukrotnie plik wykonywalny.
* Można uruchomić aplikacji z poziomu wiersza polecenia, takie jak `myapp.exe` na Windows, i `./myapp` w systemie Linux i macOS.

## <a name="single-file-executables"></a>Pliki wykonywalne pojedynczego pliku

`dotnet publish` Polecenie obsługuje pakowanie aplikacji do wykonywalnej pojedynczego pliku specyficzne dla platformy. Plik wykonywalny jest samowyodrębniający i zawiera wszystkie zależności (w tym natywne), które są wymagane do uruchamiania aplikacji. Po uruchomieniu aplikacji aplikacja jest wyodrębniany do katalogu na jej podstawie nazwy i identyfikatora kompilacji. Autostart jest szybsza, kiedy aplikacja jest uruchamiana ponownie. Aplikacja nie musi wyodrębnić sam po raz drugi, o ile nie użyto nowej wersji.

Aby opublikować wykonywalnej pojedynczego pliku, należy ustawić `PublishSingleFile` w projekcie lub w wierszu polecenia za pomocą `dotnet publish` polecenia:

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Aby uzyskać więcej informacji dotyczących publikowania w jednym pliku, zobacz [narzędzia bundler pojedynczy plik, dokument projektowy](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Łączenie zestawu

.NET core 3.0 SDK jest powiązana z narzędziem, które można zmniejszyć rozmiar aplikacji, analizując IL i przycinanie nieużywane zestawów.

Aplikacje samodzielne zawierają wszystkie elementy potrzebne do uruchomienia kodu, bez konieczności .NET do zainstalowania na komputerze-hoście. Jednak wiele razy aplikacja wymaga tylko mały podzbiór platformę, by funkcji i innych nieużywane biblioteki można usunąć.

.NET core zawiera teraz ustawienie, który będzie używał [konsolidatora IL](https://github.com/mono/linker) narzędzie do skanowania IL Twojej aplikacji. to narzędzie wykrywa, jaki kod jest wymagana, a następnie przycina nieużywane biblioteki. To narzędzie może znacznie zmniejszyć rozmiar wdrażania niektórych aplikacji.

Aby włączyć to narzędzie `<PublishTrimmed>` ustawienie w projekcie i Opublikuj aplikację samodzielną:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

Na przykład podstawowa "hello world" nowej konsoli szablonu projektu jest uwzględniony, podczas publikowania osiąga około 70 MB. Za pomocą `<PublishTrimmed>`, zmniejszeniu rozmiaru do około 30 MB.

Należy wziąć pod uwagę, że aplikacje lub struktur (łącznie z platformą ASP.NET Core i WPF), które używają odbicia lub powiązanych funkcji dynamicznych, często przerywał działanie po przycięciu. Uszkodzenie ten występuje, ponieważ konsolidator nie wiedzieć o to dynamiczne zachowanie i nie można określić, jakie typy framework są wymagane w celu odbicia. Należy pamiętać o tym scenariuszu można skonfigurować narzędzia konsolidatora IL.

Przede wszystkim w przeciwnym wypadku upewnij się przetestować aplikację po przycięciu.

Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zobacz [dokumentacji](https://aka.ms/dotnet-illink) lub odwiedź [mono/konsolidatora]( https://github.com/mono/linker) repozytorium.

## <a name="tiered-compilation"></a>Warstwowe kompilacji

[Warstwowe kompilacji](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) jest domyślnie przy użyciu platformy .NET Core 3.0. Ta funkcja umożliwia bardziej adaptacyjnie Użyj kompilator just in Time (JIT), aby uzyskać lepszą wydajność.

Główną zaletą TC jest aby jitting metody powrotnego wolniejsze — ale — szybsze do tworzenia kodu lub wyższej jakości — ale wolniejsze do tworzenia kodu. Pomaga to zwiększyć wydajność aplikacji, ponieważ przechodzi ona przez różne etapy wykonywania z uruchamiania za pośrednictwem stabilnym stanem. To zachowanie różni się od podejścia-TC, gdzie każda metoda jest kompilowana pojedynczego sposób (taka sama jak w warstwie wysokiej jakości), jest obciążona do stabilnego kosztem wydajności uruchamiania.

Aby włączyć szybkie JIT (warstwy 0 w trybie JIT kodu), należy użyć tego ustawienia w pliku projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

Aby całkowicie wyłączyć TC, użyj tego ustawienia w pliku projektu:

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a>Obrazy ReadyToRun

Aby poprawić czas uruchamiania aplikacji .NET Core, należy kompilowanie zestawów aplikacji w formacie ReadyToRun (R2R). R2R jest formą ahead of time (AOT) kompilacji.

Pliki binarne R2R zwiększeniu wydajności uruchamiania, co zmniejsza ilość pracy wykonywanej przez kompilator just-in-time (JIT), które musi wykonać jak ładowanie aplikacji. Pliki binarne zawiera podobne kodu natywnego w porównaniu do czego dałby w efekcie kompilator JIT.

Pliki binarne R2R są większe, ponieważ zawierają one zarówno kod języka pośredniego (IL), który nadal jest wymagany dla niektórych scenariuszy i natywną wersję tego samego kodu. R2R jest dostępna tylko po opublikowaniu aplikacja samodzielna przeznaczonego środowiska uruchomieniowe określonych (RID), takie jak x64 w systemie Linux lub Windows x64.

Aby skompilować aplikację jako R2R, należy dodać `<PublishReadyToRun>` ustawienia:

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

Opublikuj aplikację samodzielną. Na przykład to polecenie tworzy aplikację samodzielną dla 64-bitowej wersji systemu Windows:

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a>Obejmujące wiele platform/architecture ograniczenia

Kompilator ReadyToRun nie obsługuje obecnie przeznaczonych dla wielu. Należy skompilować w danym elemencie docelowym. Na przykład chcąc R2R obrazy dla Windows x64, należy do uruchomienia polecenia Opublikuj w tym środowisku.

Wyjątki dla wielu odwołujących:

- Windows x64 może służyć do kompilowania Windows ARM32, ARM64 i x86 obrazów.
- Windows x86 może służyć do kompilowania Windows ARM32 obrazów.
- Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.

## <a name="build-copies-dependencies"></a>Kopiuje zależności kompilacji

`dotnet build` Polecenia teraz kopiuje zależności NuGet dla aplikacji z pamięcią podręczną programu NuGet do folderu wyjściowego kompilacji. Wcześniej zależności zostały skopiowane tylko jako część `dotnet publish`.

Istnieją pewne operacje takie jak łączenie i razor strony publikowania, który nadal będzie wymagać publikowania.

## <a name="local-tools"></a>Narzędzia do lokalnego

.NET core 3.0 wprowadzono lokalne narzędzia. Lokalne narzędzia są podobne do [globalnego narzędzia](../tools/global-tools.md) , ale są skojarzone z określonej lokalizacji na dysku. Lokalne narzędzia nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.

> [!WARNING]
> Jeśli próbujesz lokalne narzędzia .NET Core 3.0 w wersji zapoznawczej 1, takie jak uruchamianie `dotnet tool restore` lub `dotnet tool install`, usuń folder pamięci podręcznej narzędzia lokalnego. W przeciwnym razie lokalne narzędzia nie będą działać na dowolnym nowszą wersją. Ten folder znajduje się w:
>
> W systemie macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Na Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Lokalne narzędzia opierają się na nazwę pliku manifestu `dotnet-tools.json` w bieżącym katalogu. Ten plik manifestu definiuje narzędzia była dostępna, w tym folderze, jak i poniżej. Plik manifestu można rozpowszechniać w kodzie, aby upewnić się, że każdy, kto pracuje z kodem można przywrócić i używać tych samych narzędzi.

Globalne i lokalne narzędzi zgodna wersja środowiska uruchomieniowego jest wymagana. Wiele narzędzi, obecnie w witrynie NuGet.org docelowej platformy .NET Core środowiska uruchomieniowego 2.1. Aby zainstalować te narzędzia, globalnie lub lokalnie, czy nadal należy zainstalować [środowisko uruchomieniowe programu NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Wersja główna przenoszenia do przodu

.NET core 3.0 wprowadzono to opcjonalna funkcja, która umożliwia aplikacji uaktualniane do najnowszej wersji głównej programu .NET Core. Ponadto dodano nowe ustawienie do kontrolowania sposobu przenoszenia do przodu jest stosowany do swojej aplikacji. Można to skonfigurować w następujący sposób:

- Właściwości pliku projektu: `RollForward`
- Właściwość pliku konfiguracji środowiska uruchomieniowego: `rollForward`
- Zmienna środowiskowa: `DOTNET_ROLL_FORWARD`
- Argument wiersza polecenia: `--roll-forward`

Należy określić jedną z następujących wartości. Jeśli ustawienie zostanie pominięty, **pomocnicza** jest ustawieniem domyślnym.

- **LatestPatch**\
Uaktualniane najwyższa wersja poprawki. Powoduje to wyłączenie wersja pomocnicza przenoszenia do przodu.
- **Pomocnicza**\
Uaktualniane do najniższego wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej. Jeśli żądana wersja pomocnicza jest obecna, a następnie **LatestPatch** zasady są używane.
- **Główne**\
Uaktualniane do najniższego wyższej wersji głównej i najniższa wersja pomocnicza, jeśli brakuje żądanej wersji głównej. Jeśli żądana wersja główna jest obecny, a następnie **pomocnicza** zasady są używane.
- **LatestMinor**\
Uaktualniane do najwyższej wersji pomocniczej, nawet jeśli żądana wersja pomocnicza jest obecny. Przeznaczony dla składnika w scenariuszach hostingu.
- **latestMajor**\
Przywracanie do przodu najwyższą główne i najwyższą wersję pomocniczą, nawet jeśli żądana głównych znajduje się. Przeznaczony dla składnika w scenariuszach hostingu.
- **Wyłącz**\
Nie przejdą do przodu. Powiązać tylko z określonej wersji. Ta zasada nie jest zalecane do użytku ogólnego, ponieważ wyłącza możliwość uaktualniane najnowsze poprawki. Ta wartość jest zalecane tylko do testowania.

Oprócz **wyłączyć** ustawienie wszystkich ustawień użyje najwyższa wersja dostępna poprawka.

## <a name="windows-desktop"></a>Pulpit systemu Windows

.NET core 3.0 obsługuje aplikacje pulpitu Windows za pomocą formularzy Windows i Windows Presentation Foundation (WPF). Następujące struktury obsługi, za pomocą nowoczesnych kontrolek i Fluent stylów z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [Wyspy XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Składnik Windows Desktop jest częścią Windows zestaw SDK programu .NET Core 3.0.

Można utworzyć nowej aplikacji WPF i Windows Forms z następującymi `dotnet` poleceń:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 dodaje **nowy projekt** szablonów dla platformy .NET Core 3.0 Windows Forms i WPF.

Aby uzyskać więcej informacji na temat portów istniejącej aplikacji .NET Framework, zobacz [projekty WPF portu](../porting/wpf.md) i [projektów portu Windows Forms](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>Składniki COM wywoływalnej — Windows Desktop

Na Windows można teraz utworzyć składniki COM-wywoływalnej zarządzane. Ta możliwość jest krytyczna, .NET Core za pomocą modelu COM dodatku modeli, a także zapewnić zgodność z programem .NET Framework.

W odróżnieniu od .NET Framework gdzie *mscoree.dll* został użyty jako serwer COM, .NET Core doda uruchamianie natywnej biblioteki dll do *bin* katalogu podczas tworzenia składnika COM.

Na przykład sposobu tworzenia składnika modelu COM i używanie go zobacz [pokaz COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>Wdrażanie MSIX — Windows Desktop

[MSIX](https://docs.microsoft.com/windows/msix/) jest nowy format pakietu aplikacji Windows. Może służyć do wdrażania aplikacji klasycznych .NET Core 3.0 dla systemu Windows 10.

[Projekt pakietu aplikacji Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępne w programie Visual Studio 2019 r, pozwala na tworzenie pakietów MSIX [niezależna](../deploying/index.md#self-contained-deployments-scd) aplikacji .NET Core.

Plik projektu .NET Core, musisz określić obsługiwane środowiska uruchomieniowe w `<RuntimeIdentifiers>` właściwości:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

Aplikacje .NET core Windows Forms można ustawić trybu wysokiej rozdzielczości, przy użyciu <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. `SetHighDpiMode` Metoda ustawia odpowiedni tryb wysokiej rozdzielczości, chyba że ustawienie została ustawiona za pomocą innych środków, takich jak `App.Manifest` lub P/Invoke przed `Application.Run`.

Możliwe `highDpiMode` wartości, wyrażonych w <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> wyliczenia są:

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości, zobacz [wysokiej rozdzielczości DPI aplikacji programowanie aplikacji klasycznych na Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy <xref:System.Index?displayProperty=nameWithType> typ może być używany do indeksowania. Można utworzyć jeden z `int` , jest liczona od początku lub z prefiksem `^` — operator (C#), jest liczona od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa się z dwóch `Index` wartości, jeden dla początkowego i jeden dla elementu end i mogą być zapisywane z `x..y` zakres wyrażenia (C#). Następnie można zaindeksować z `Range`, która generuje wycinek:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Aby uzyskać więcej informacji, zobacz [samouczek zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Asynchroniczne strumienie

<xref:System.Collections.Generic.IAsyncEnumerable%601> Typu jest nowa wersja asynchroniczne <xref:System.Collections.Generic.IEnumerable%601>. Język umożliwia `await foreach` za pośrednictwem `IAsyncEnumerable<T>` używanie ich elementy i używać `yield return` do ich do produkcji elementów.

Poniższy przykład ilustruje środowiska produkcyjnego i zużycia strumieni asynchronicznych. `foreach` Instrukcja jest asynchroniczne, a sam używa `yield return` do produkcji strumienia asynchronicznego dla obiektów wywołujących. Ten wzorzec (przy użyciu `yield return`) to zalecany model do produkcji strumieni asynchronicznych.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

Oprócz możliwości `await foreach`, można również utworzyć async Iteratory, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator` można zarówno `await` i `yield` w. W przypadku obiektów, które muszą zostać zlikwidowany, można użyć `IAsyncDisposable`, który implementuje różnych typów BCL, takich jak `Stream` i `Timer`.

Aby uzyskać więcej informacji, zobacz [samouczek strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>Ulepszenia zmiennoprzecinkowej IEEE

Liczb zmiennoprzecinkowych punktu interfejsy API są aktualizowane do wykonania [poprawki 754-2008 IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Celem tych zmian jest do udostępnienia wszystkich **wymagane** operacji i upewnij się, że są one behaviorally zgodne ze specyfikacji IEEE. Aby uzyskać więcej informacji na temat ulepszenia zmiennoprzecinkowych zobacz [ulepszenia zmiennopozycyjna analizowania i formatowanie w .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) wpis w blogu.

Formatowanie z poprawkami i analizowanie obejmują:

* Poprawnie przeanalizować i zaokrąglanie danych wejściowych o dowolnej długości.
* Poprawnie przeanalizować i sformatować ujemna zero.
* Poprawnie przeanalizować `Infinity` i `NaN` poprzez sposób wyboru bez uwzględniania wielkości liter, dzięki czemu, opcjonalny poprzedzających `+` jeśli ma to zastosowanie.

Nowe <xref:System.Math?displayProperty=nameWithType> obejmują interfejsy API:

* <xref:System.Math.BitIncrement(System.Double)> i <xref:System.Math.BitDecrement(System.Double)>\
Odnosi się do `nextUp` i `nextDown` IEEE operacji. Zwracają najmniejsza liczba zmiennoprzecinkowa porównuje w mniejszym lub większym niż dane wejściowe (odpowiednio). Na przykład `Math.BitIncrement(0.0)` zwróci `double.Epsilon`.

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)> i <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odnosi się do `maxNumMag` i `minNumMag` operacje IEEE zwracają wartość, która jest większy lub mniejszy w wielkości dwóch danych wejściowych (odpowiednio). Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwróci `-3.0`.

* <xref:System.Math.ILogB(System.Double)>\
Odnosi się do `logB` IEEE operacji, która zwraca wartość całkowitą, zwraca całkowitą dziennik base 2 parametr wejściowy. Ta metoda skutecznie jest taka sama jak `floor(log2(x))`, ale pracy z minimalnym błąd zaokrąglania.

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odnosi się do `scaleB` IEEE operacji, która przyjmuje wartość całkowitą, funkcja zwraca skutecznie `x * pow(2, n)`, ale odbywa się przy użyciu minimalnego błąd zaokrąglania.

* <xref:System.Math.Log2(System.Double)>\
Odnosi się do `log2` operacji IEEE Zwraca logarytm o podstawie 2 dla podanego. Minimalizuje błędów zaokrąglania.

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odnosi się do `fma` wykonuje operację IEEE kolei wielokrotnie dodać. Oznacza to robi `(x * y) + z` jako pojedyncza operacja,-, minimalizując błąd zaokrąglania. Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` co powoduje zwrócenie `1e308`. Regularne `(1e308 * 2.0) - 1e308` zwraca `double.PositiveInfinity`.

* <xref:System.Math.CopySign(System.Double,System.Double)>\
Odnosi się do `copySign` IEEE operację, zwraca wartość `x`, ale przy użyciu konta z `y`.

## <a name="fast-built-in-json-support"></a>Szybkie wbudowanej obsługi formatu JSON

Użytkownicy platformy .NET ma dużym stopniu polegać [ **Json.NET** ](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal dobrych wyborów. **Program Json.NET** używa ciągów .NET jako jej podstawowy typ danych, który jest pod maską UTF-16.

Nowa funkcja wbudowanej obsługi JSON to alokacji o wysokiej wydajności, niski i oparte na `Span<byte>`. Trzy nowe główne powiązane JSON typy zostały dodane do platformy .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> przestrzeni nazw. Te typy nie *jeszcze* obsługuje zwykłe stare CLR obiektu (POCO) serializacji i deserializacji.

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> jest o wysokiej wydajności, niski alokacji, tylko do przodu czytnik UTF-8 kodowany w formacie JSON tekst odczytywane `ReadOnlySpan<byte>`. `Utf8JsonReader` Jest typem podstawowe, niskiego poziomu, który może służyć do tworzenia niestandardowych analizatory i deserializers. Odczytywanie za pośrednictwem ładunek w formacie JSON za pomocą nowego `Utf8JsonReader` wynosi 2 x szybciej niż przy użyciu czytnika, z **Json.NET**. Go nie przydzielić, dopóki nie trzeba actualize tokenów JSON jako ciągi (UTF-16).

Oto przykład przeczytanie [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) plik utworzony przez Visual Studio Code:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> zapewnia wysoce wydajnych niebuforowanym, tylko do zapisu kodowany w formacie UTF-8 do przodu tekstu JSON z popularnych typów .NET, takich jak `String`, `Int32`, i `DateTime`. Podobnie jak czytelnik moduł zapisujący jest typem podstawowe, niskiego poziomu, który może służyć do tworzenia niestandardowych serializatory. Zapis ładunku JSON za pomocą nowego `Utf8JsonWriter` wynosi 30-80% szybciej niż przy użyciu składnika zapisywania z **Json.NET** i nie alokować.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> jest wbudowana w górnej części `Utf8JsonReader`. `JsonDocument` Zapewnia możliwość analizowania danych JSON i dokonać jego kompilacji tylko do odczytu modelu DOM (Document Object) można wykonywać zapytania do obsługi dostępu losowego i wyliczenia. Elementy JSON, które tworzą dane można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typ, który jest udostępniany przez `JsonDocument` jako właściwość o nazwie `RootElement`. `JsonElement` Zawiera wyliczenia tablicy i obiektów JSON, wraz z interfejsów API do konwertowania tekstu JSON do popularnych typów .NET. Analizowanie typowe ładunek w formacie JSON i uzyskiwania dostępu do wszystkich jej członków przy użyciu `JsonDocument` jest szybsza niż x 2 – 3 **Json.NET** z przydziałem niewielkie ilości danych, które stosowne o rozmiarze (czyli < 1 MB).

Poniżej przedstawiono przykładowe zastosowanie `JsonDocument` i `JsonElement` mogą służyć jako punkt początkowy:

Oto C# 8.0 przykład przeczytanie [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) plik utworzony przez Visual Studio Code:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> jest wbudowana w górnej części <xref:System.Text.Json.Utf8JsonReader> i <xref:System.Text.Json.Utf8JsonWriter> zapewnienie opcję szeregowania szybko małej ilości pamięci, pracując z dokumentów JSON i fragmenty.

Sprawdź: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md na przykład do portu na w tym artykule

Oto przykład serializacji obiektu do formatu JSON:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Oto przykład deserializacji ciągu JSON na obiekt. Można użyć ciągu JSON utworzony w poprzednim przykładzie:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Ulepszenia międzyoperacyjności

.NET core 3.0 to zwiększa natywnych międzyoperacyjności interfejsu API.

### <a name="type-nativelibrary"></a>Wpisz: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> zapewnia hermetyzację ładowania natywnej biblioteki (przy użyciu tej samej logiki obciążenia jako .NET Core P/Invoke) i podając takie jak funkcje pomocnicze odpowiednie `getSymbol`. Dla przykładu kodu zobacz [pokaz DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).

### <a name="windows-native-interop"></a>Współdziałanie natywne Windows

Windows oferuje rozbudowane natywnych interfejsów API w formie płaskiej interfejsów API języka C, COM i WinRT. Podczas gdy platformy .NET Core obsługuje **P/Invoke**, .NET Core 3.0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywować interfejsów API WinRT**. Dla przykładu kodu zobacz [wersji demonstracyjnej programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>Obsługa protokołu HTTP/2

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typu obsługuje protokół HTTP/2. Włączenie protokołu HTTP/2 za pośrednictwem protokołu TLS/ALPN negocjowane jest wersji protokołu HTTP i protokołu HTTP/2 jest używany, gdy serwer wybiera z niej korzystać.

Domyślnym protokołem pozostają HTTP/1.1, ale można włączyć protokołu HTTP/2 na dwa różne sposoby. Po pierwsze można ustawić komunikat żądania HTTP do użycia protokołu HTTP/2:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Po drugie, można zmienić <xref:System.Net.Http.HttpClient> do domyślnie używają protokołu HTTP/2:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Wiele razy, gdy tworzysz aplikację, chcesz korzystanie z połączenia nieszyfrowanego. Jeśli wiesz, że docelowy punkt końcowy będzie korzystać z protokołu HTTP/2, można włączyć połączenia nieszyfrowanego protokołu HTTP/2. Można ją włączyć, ustawiając `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` zmiennej środowiskowej, aby `1` lub, włączając je w kontekście aplikacji:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 w systemie Linux

.NET core korzysta z zalet [Obsługa protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy będzie ona dostępna w danym środowisku. Za pomocą protokołu TLS 1.3:

* Zwiększona czasy połączeń z ograniczoną liczbę rund wymagane między klientem i serwerem.
* Ulepszone zabezpieczenia ze względu na usunięcie rozmaite algorytmy kryptograficzne przestarzały i niebezpieczne.

Jeśli są dostępne, korzysta z platformy .NET Core 3.0 **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, lub **OpenSSL 1.0.2** w systemie Linux. Gdy **OpenSSL 1.1.1** jest dostępny, zarówno <xref:System.Net.Security.SslStream?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> użyje typy **TLS 1.3** (zakładając, że obsługa klienta i serwera **TLS 1.3**).

>[!IMPORTANT]
>Windows i macOS nie jest jeszcze obsługiwany **TLS 1.3**. .NET core 3.0 to będzie obsługiwać **TLS 1.3** w tych systemach operacyjnych po udostępnieniu Pomocy technicznej.

Następujące C# .NET Core 3.0 w 18.10 Ubuntu nawiązywania połączenia z przykładowym 8.0 <https://www.cloudflare.com>:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Szyfry kryptografii

.NET 3.0 dodaje obsługę **AES-GCM** i **AES-CCM** szyfrów, implementowane za pomocą <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> odpowiednio. Te algorytmy są [uwierzytelnione szyfrowanie za pomocą algorytmów skojarzenia danych (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Poniższy kod demonstruje użycie `AesGcm` szyfrowania do szyfrowania i odszyfrowywania danych losowych.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Kryptograficznych kluczy importu/eksportu

.NET core 3.0 obsługuje importowanie i eksportowanie kluczy asymetrycznych publicznych i prywatnych z standardowych formatów. Nie należy używać certyfikatu X.509.

Wszystkie klucza typów, takich jak *RSA*, *DSA*, *ECDsa*, i *ECDiffieHellman*, obsługuje następujące formaty:

* **Klucz publiczny**
  * X.509 SubjectPublicKeyInfo

* **klucz prywatny**
  * PKCS #8 PrivateKeyInfo
  * PKCS#8 EncryptedPrivateKeyInfo

RSA również klucze pomocy technicznej:

* **Klucz publiczny**
  * PKCS#1 RSAPublicKey

* **klucz prywatny**
  * PKCS #1 RSAPrivateKey

Metody eksportowania generuje dane binarne zakodowane w formacie DER i metod import oczekiwać takie same. Jeśli klucz jest przechowywany w formacie PEM przyjaznego tekstu, obiekt wywołujący, będą musieli base64 — dekodowanie zawartości przed wywołaniem metody importu.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS #8** pliki mogą być kontrolowane za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> i **PFX/PKCS #12** pliki mogą być kontrolowane za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. **Plik PFX/PKCS #12** pliki mogą być zmieniane za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>Portu SerialPort dla systemu Linux

Obsługuje platformy .NET core 3.0 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.

Wcześniej, .NET Core obsługiwana tylko przy użyciu `SerialPort` na Windows.

## <a name="docker-and-cgroup-memory-limits"></a>Ogranicza platformy docker i cgroup pamięci

Począwszy od wersji zapoznawczej 3 działającej platformy .NET Core 3.0 w systemie Linux przy użyciu rozwiązania Docker działa lepiej z cgroup limity pamięci. Uruchomiony kontener platformy Docker z limitami pamięci, takich jak z `docker run -m`, zmienia sposób działania platformy .NET Core.

* Domyślny rozmiar sterty modułu odśmiecania pamięci (GC): Maksymalna liczba o rozmiarze 20 mb lub 75% limitu pamięci dla kontenera.
* Jawny rozmiar można ustawić jako wartość bezwzględna liczby lub wartości procentowej cgroup limitu.
* Rozmiar minimalny zastrzeżonego segmentu na stercie GC to 16 mb. Ten rozmiar zmniejsza liczbę stosów, które są tworzone na maszynach.

## <a name="smaller-garbage-collection-heap-sizes"></a>Mniejsze rozmiary stercie wyrzucania elementów bezużytecznych

Rozmiar sterty domyślny moduł Garbage Collector została zmniejszona skutkuje platformy .NET Core przy użyciu mniejszej ilości pamięci. Ta zmiana lepszego dopasowania z budżetem generacji 0 alokacji o rozmiarze pamięci podręcznej nowoczesny procesor.

## <a name="garbage-collection-large-page-support"></a>Obsługa dużych stron kolekcji wyrzucania elementów

Dużych stron (nazywanego także ogromny stron w systemie Linux) jest funkcją, w którym system operacyjny jest możliwość ustanowienia regionami pamięci jest większy niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądanie te dużych stron.

Teraz można skonfigurować moduł zbierający elementy bezużyteczne **GCLargePages** ustawienie jako opcjonalna funkcja alokować dużych stron na Windows.

## <a name="gpio-support-for-raspberry-pi"></a>Interfejs GPIO obsługa urządzenia Raspberry Pi

Zostały wydane dwa pakiety NuGet, używanej do programowania GPIO:

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Pakiety GPIO zawierają interfejsy API dla *GPIO*, *SPI*, *I2C*, i *PWM* urządzeń. Pakiet IoT powiązania zawiera powiązania urządzenia. Aby uzyskać więcej informacji, zobacz [repozytorium GitHub urządzeń](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>Obsługa systemu Linux ARM64

.NET core 3.0 dodaje obsługę systemu Linux dla architektury ARM64. Głównym zastosowaniem dla architektury ARM64 jest obecnie używany w scenariuszach IoT. Aby uzyskać więcej informacji, zobacz [stanu programu .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).

[Obrazy platformy docker dla platformy .NET Core dla procesorów ARM64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.

> [!NOTE]
> **ARM64** pomocy technicznej Windows nie jest jeszcze dostępna.
