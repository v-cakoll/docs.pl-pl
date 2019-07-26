---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 06/14/2019
ms.openlocfilehash: b1dd243d754bfc3b682c084820547f6b7846f0ea
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484657"
---
# <a name="whats-new-in-net-core-30-preview-6"></a>Co nowego w programie .NET Core 3,0 (wersja zapoznawcza 6)

W tym artykule opisano nowości w programie .NET Core 3,0 (w wersji zapoznawczej 6). Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko system Windows). Korzystając z pulpitu systemu Windows składnika zestawu SDK platformy .NET Core 3,0, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF). Aby można było wyczyścić, składnik pulpitu systemu Windows jest obsługiwany i uwzględniany w systemie Windows. Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.

Program .NET Core 3,0 dodaje obsługę C# 8,0. Zdecydowanie zaleca się użycie [najnowszej wersji programu Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)lub Visual Studio Code z rozszerzeniem OmniSharp.

[Pobierz i zacznij korzystać z programu .NET Core 3,0 w wersji zapoznawczej 6](https://aka.ms/netcore3download) teraz w systemach Windows, Mac i Linux.

Aby uzyskać więcej informacji na temat każdej wersji zapoznawczej, zobacz następujące powiadomienia:

- [Anons programu .NET Core 3,0 w wersji 6](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [Anons programu .NET Core 3,0 Preview 5](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [Anons programu .NET Core 3,0 Preview 4](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [Anons programu .NET Core 3,0 Preview 3](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [Anons programu .NET Core 3,0 w wersji zapoznawczej 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [Powiadomienie dotyczące programu .NET Core 3,0 Preview 1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a>Zestaw .NET Core SDK Instalator Windows

Instalator MSI dla systemu Windows został zmieniony począwszy od platformy .NET Core 3,0. Instalatorzy zestawu SDK teraz uaktualniają wersje funkcji zestawu SDK na miejscu. Paski funkcji są zdefiniowane w grupach *setek* w sekcji *poprawka* numeru wersji. Na przykład **3,0. _101_**  i **3,0. _201_**  są wersje w dwóch różnych warstwach funkcji podczas **3,0. _101_**  i **3,0. _199_**  znajdują się w tej samej paśmie funkcji. I, w przypadku zestaw .NET Core SDK **3,0. _101_**  jest zainstalowana, zestaw .NET Core SDK **3,0. _100_**  zostanie usunięta z komputera, jeśli istnieje. Gdy zestaw .NET Core SDK **3,0. _200_**  jest zainstalowana na tym samym komputerze, zestaw .NET Core SDK **3,0. _101_**  nie zostanie usunięta.

Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).

## <a name="c-80-preview"></a>C#wersja zapoznawcza 8,0

Program .NET Core 3,0 C# obsługuje 8 wersji zapoznawczych. Aby uzyskać więcej informacji C# o funkcjach 8,0, zobacz [co nowego C# w programie 8,0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET Standard 2,1

Mimo że program .NET Core 3,0 obsługuje **.NET Standard 2,1**, szablon `dotnet new classlib` domyślny generuje projekt, który jest przeznaczony dla **.NET Standard 2,0**. Aby docelowa **.NET Standard 2,1**, edytuj plik projektu i Zmień `TargetFramework` właściwość na `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program visual Studio 2017 nie obsługuje **.NET Standard 2,1** ani **.NET Core 3,0**.

## <a name="improved-net-core-version-apis"></a>Ulepszone interfejsy API wersji platformy .NET Core

Począwszy od platformy .NET Core 3,0, interfejsy API wersji dostarczone z platformą .NET Core teraz zwracają oczekiwane informacje. Na przykład:

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
> Istotna zmiana. Jest to technicznie istotna zmiana, ponieważ schemat przechowywania wersji został zmieniony.

## <a name="net-platform-dependent-intrinsics"></a>Elementy wewnętrzne zależne od platformy .NET

Dodano interfejsy API, które umożliwiają dostęp do pewnych instrukcji procesora CPU zorientowanych na wydajność, takich jak **SIMD** lub **bitowe zestawy instrukcji manipulowania** . Te instrukcje mogą pomóc w osiągnięciu znaczących ulepszeń wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych. 

W odpowiednich przypadkach biblioteki .NET zaczęły korzystać z tych instrukcji w celu zwiększenia wydajności.

Aby uzyskać więcej informacji, zobacz elementy [wewnętrzne zależne od platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Domyślne pliki wykonywalne

Platforma .NET Core teraz domyślnie kompiluje [pliki wykonywalne zależne od platformy](../deploying/index.md#framework-dependent-executables-fde) . To zachowanie jest nowe w przypadku aplikacji korzystających z zainstalowanej globalnie wersji platformy .NET Core. Wcześniej tylko [wstępnie zawarte wdrożenia](../deploying/index.md#self-contained-deployments-scd) spowodują utworzenie pliku wykonywalnego.

W `dotnet build` trakcie `dotnet publish`lub, tworzony jest plik wykonywalny zgodny ze środowiskiem i platformą używanego zestawu SDK. Można oczekiwać, że te same elementy wykonywalne są takie same jak w przypadku innych natywnych plików wykonywalnych, takich jak:

* Możesz kliknąć dwukrotnie plik wykonywalny.
* Aplikację można uruchomić z poziomu wiersza polecenia bezpośrednio, na przykład `myapp.exe` w systemie Windows `./myapp` , w systemie Linux i macOS.

## <a name="single-file-executables"></a>Pliki wykonywalne pojedynczego pliku

`dotnet publish` Polecenie obsługuje pakowanie aplikacji do pliku wykonywalnego określonego dla konkretnej platformy. Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji. Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji. Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie. Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że została użyta Nowa wersja.

Aby opublikować plik wykonywalny pojedynczego pliku, ustaw `PublishSingleFile` w projekcie lub w wierszu `dotnet publish` polecenia polecenie:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

—lub—

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Łączenie zestawów

Zestaw SDK platformy .NET Core 3,0 zawiera narzędzie, które pozwala zmniejszyć rozmiar aplikacji przez analizowanie IL i przycinanie nieużywanych zestawów.

Aplikacje samodzielne obejmują wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania programu .NET na komputerze-hoście. Jednak wiele razy aplikacja wymaga tylko małego podzestawu platformy do działania, a inne nieużywane biblioteki mogą zostać usunięte.

Platforma .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora Il](https://github.com/mono/linker) do skanowania Il aplikacji. to narzędzie wykrywa wymagany kod, a następnie przycina nieużywane biblioteki. To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.

Aby włączyć to narzędzie, Dodaj `<PublishTrimmed>` ustawienie w projekcie i Opublikuj samodzielną aplikację:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

Na przykład podstawowy "Hello World" nowy szablon projektu konsoli, który jest dostępny po opublikowaniu, trafień o rozmiarze 70 MB. Przy użyciu `<PublishTrimmed>`, ten rozmiar jest zmniejszany do około 30 MB.

Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które wykorzystują odbicie lub powiązane funkcje dynamiczne, często będą przerywane po przycięciu. To uszkodzenie występuje, ponieważ konsolidator nie wie o tym zachowaniu dynamicznym i nie może określić, które typy struktur są wymagane do odbicia. Narzędzie konsolidatora IL można skonfigurować pod kątem tego scenariusza.

Przed przycinaniem upewnij się, że aplikacja została przetestowana.

Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zapoznaj się z [dokumentacją](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/konsolidatora]( https://github.com/mono/linker) .

## <a name="tiered-compilation"></a>Kompilacja warstwowa

[Kompilacja warstwowa](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) jest domyślnie włączona z platformą .NET Core 3,0. Ta funkcja umożliwia środowisku uruchomieniowemu wydajniejsze używanie kompilatora just-in-Time (JIT) w celu uzyskania lepszej wydajności.

Główną zaletą TC jest umożliwienie (ponownej) jitting metod z wolniejszym, ale szybszym użyciem kodu lub wyższej jakości, aby utworzyć kod. Pozwala to zwiększyć wydajność aplikacji, która przechodzi przez różne etapy wykonywania, od uruchamiania do stanu stałego. Jest to kontrast z podejściem innym niż TC, gdzie każda metoda jest skompilowana w jeden sposób (taka sama jak warstwa wysokiej jakości), która jest obciążona niestabilnym stanem w porównaniu z wydajnością uruchamiania.

Aby włączyć funkcję szybkiego JIT (kod 0 trybie JIT), użyj tego ustawienia w pliku projektu:

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

Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji jako ReadyToRun (R2R). R2R to forma kompilacji z wyprzedzeniem (AOT).

Pliki binarne R2R zwiększają wydajność uruchamiania przez zmniejszenie ilości pracy kompilatora, który jest potrzebny do załadowania aplikacji. Pliki binarne zawierają podobny kod natywny w porównaniu z przeznaczeniem JIT.

Pliki binarne R2R są większe, ponieważ zawierają kod języka pośredniego (IL), który jest nadal wymagany w niektórych scenariuszach i natywną wersję tego samego kodu. R2R jest dostępna tylko w przypadku publikowania aplikacji samodzielnej, która jest przeznaczona dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.

Aby skompilować aplikację jako R2R, Dodaj `<PublishReadyToRun>` ustawienie:

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

Publikowanie aplikacji samodzielnej. Na przykład to polecenie tworzy samodzielną aplikację dla 64-bitowej wersji systemu Windows:

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a>Ograniczenia dotyczące wielu platform/architektury

Kompilator ReadyToRun nie obsługuje obecnie określania wartości docelowej. Należy skompilować na danym miejscu docelowym. Na przykład jeśli chcesz, aby obrazy R2R dla systemu Windows x64 zostały wykonane, należy uruchomić polecenie Publikuj w tym środowisku.

Wyjątki dla wielu elementów docelowych:

- System Windows x64 może służyć do kompilowania obrazów systemów Windows ARM32, ARM64 i x86.
- System Windows x86 może służyć do kompilowania obrazów ARM32 systemu Windows.
- System Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.

## <a name="build-copies-dependencies"></a>Zależności kompilacji kopii

`dotnet build` Polecenie teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu danych wyjściowych kompilacji. Wcześniej zależności były kopiowane tylko w ramach programu `dotnet publish`.

Istnieją pewne operacje, takie jak łączenie i publikowanie stron Razor, które nadal wymagają publikacji.

## <a name="local-tools"></a>Narzędzia lokalne

Środowisko .NET Core 3,0 zawiera wprowadzenie do narzędzi lokalnych. Narzędzia lokalne są podobne do [narzędzi globalnych](../tools/global-tools.md) , ale są skojarzone z konkretną lokalizacją na dysku. Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.

> [!WARNING]
> Jeśli podjęto próbę skorzystania z narzędzi lokalnych w programie .NET Core 3,0 `dotnet tool restore` w `dotnet tool install`wersji zapoznawczej 1, takiej jak uruchamianie lub, Usuń folder pamięci podręcznej narzędzi lokalnych W przeciwnym razie narzędzia lokalne nie będą działały w żadnej nowszej wersji. Ten folder znajduje się w lokalizacji:
>
> W systemie macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`
>
> W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Narzędzia lokalne są zależne od nazwy `dotnet-tools.json` pliku manifestu w bieżącym katalogu. Ten plik manifestu definiuje narzędzia do udostępnienia w tym folderze i poniżej. Plik manifestu można dystrybuować z kodem, aby upewnić się, że każda osoba, która współpracuje z kodem, będzie mogła przywrócić i korzystać z tych samych narzędzi.

W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego. Wiele narzędzi obecnie na NuGet.org docelowym środowiska uruchomieniowego .NET Core 2,1. Aby zainstalować te narzędzia globalnie lub lokalnie, nadal trzeba zainstalować [środowisko uruchomieniowe NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Wersja główna — przekazanie do przodu

W programie .NET Core 3,0 wprowadzono funkcję wyboru, która pozwala aplikacji na przewinięcie do najnowszej wersji programu .NET Core. Ponadto zostało dodane nowe ustawienie służące do kontrolowania sposobu, w jaki przenoszone do przodu jest stosowane do aplikacji. Tę konfigurację można skonfigurować w następujący sposób:

- Właściwość pliku projektu:`RollForward`
- Właściwość pliku konfiguracji środowiska uruchomieniowego:`rollForward`
- Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`
- Argument wiersza polecenia:`--roll-forward`

Należy określić jedną z następujących wartości. Jeśli ustawienie zostanie pominięte, wartością  domyślną jest wartość pomocnicza.

- **LatestPatch**\
Przewinięcie do najwyższej wersji poprawki. Spowoduje to wyłączenie wycofywania wersji pomocniczej.
- **Średni**\
Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej. Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady **LatestPatch** .
- **Znaczny**\
Zaczekaj na najmniejszą wyższą wersję główną i najniższą wersję pomocniczą, jeśli brakuje żądanej wersji głównej. Jeśli jest obecna żądana wersja główna, są używane  zasady pomocnicze.
- **LatestMinor**\
Przewinięcie do przodu do najwyższej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza. Przeznaczone do scenariuszy hostingu składników.
- **LatestMajor**\
Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli jest obecny żądany główny. Przeznaczone do scenariuszy hostingu składników.
- **Wyłącza**\
Nie przetaczaj dalej. Powiąż tylko z określoną wersją. Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek. Ta wartość jest zalecana tylko do celów testowych.

Oprócz ustawienia **Wyłącz** wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.

## <a name="windows-desktop"></a>Pulpit systemu Windows

Program .NET Core 3,0 obsługuje aplikacje klasyczne systemu Windows przy użyciu Windows Presentation Foundation (WPF) i Windows Forms. Te struktury obsługują również korzystanie z nowoczesnych kontrolek i stylów Fluent z poziomu biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Składnik pulpitu systemu Windows jest częścią zestawu SDK systemu Windows .NET Core 3,0.

Nową aplikację WPF lub Windows Forms można utworzyć przy użyciu następujących `dotnet` poleceń:

```console
dotnet new wpf
dotnet new winforms
```

Program Visual Studio 2019 dodaje **nowe szablony projektów** dla platformy .net Core 3,0 Windows Forms i WPF.

Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [port WPF projekty](../porting/wpf.md) i [projekty Windows Forms portów](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>Składniki wywoływane przez COM — Windows Desktop

W systemie Windows można teraz tworzyć zarządzane składniki COM. Ta funkcja ma kluczowe znaczenie dla korzystania z platformy .NET Core z modelami dodatków COM, a także do zapewnienia parzystości .NET Framework.

W przeciwieństwie do .NET Framework, w którym *Biblioteka mscoree. dll* była używana jako serwer com, podczas kompilowania składnika com program .NET Core doda natywną bibliotekę DLL uruchamiania do katalogu *bin* .

Przykład sposobu tworzenia składnika modelu COM i korzystania z niego można znaleźć w [demonstracji modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>Wdrażanie MSIX — Windows Desktop

[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows. Można go użyć do wdrożenia aplikacji klasycznych platformy .NET Core 3,0 w systemie Windows 10.

[Projekt pakietu aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX przy użyciu [](../deploying/index.md#self-contained-deployments-scd) samodzielnych aplikacji .NET Core.

Plik projektu .NET Core musi określać obsługiwane środowiska uruchomieniowe we `<RuntimeIdentifiers>` właściwości:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

Aplikacje .NET Core Windows Forms mogą ustawiać tryb wysokiej rozdzielczości DPI <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>przy użyciu. Metoda ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że ustawienie zostało ustawione za pomocą innych metod, `App.Manifest` takich jak lub P/ `Application.Run`Invokeprzed. `SetHighDpiMode`

Możliwe `highDpiMode` wartości wyrażone <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> przez wyliczenie są następujące:

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy <xref:System.Index?displayProperty=nameWithType> typ może służyć do indeksowania. Można utworzyć jedną z nich na `int` podstawie liczby od początku lub z operatorem prefiksu `^` (C#), który liczy się od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa się z dwóch `Index` wartości, jeden dla początku i jeden dla końca, i `x..y` może być zapisany z wyrażeniem zakresu (C#). Następnie można indeksować za pomocą `Range`, co spowoduje utworzenie wycinka:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Strumienie asynchroniczne

Typ jest nową wersją asynchroniczną programu <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Collections.Generic.IAsyncEnumerable%601> Język pozwala `await foreach` `IAsyncEnumerable<T>` na korzystanie z ich elementów i używanie `yield return` ich do tworzenia elementów.

Poniższy przykład ilustruje produkcję i zużycie strumieni asynchronicznych. Instrukcja jest asynchroniczna i sama używa `yield return` do tworzenia strumienia asynchronicznego dla obiektów wywołujących. `foreach` Ten wzorzec (using `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznych.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

Oprócz możliwości `await foreach`można także tworzyć Iteratory asynchroniczne, na przykład iterator, który `IAsyncEnumerable/IAsyncEnumerator` zwraca, że można zarówno `await` , jak i `yield` w. W przypadku obiektów, które muszą zostać usunięte, można użyć `IAsyncDisposable`różnych typów BCL, takich jak `Stream` i `Timer`.

Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>Udoskonalenia zmiennoprzecinkowe IEEE

Interfejsy API zmiennoprzecinkowe są aktualizowane w celu zapewnienia zgodności z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Celem tych zmian jest uwidocznienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [udoskonalenia analizy i formatowania zmiennoprzecinkowe w wpisie na blogu programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

Poprawki dotyczące analizowania i formatowania obejmują:

* Poprawnie Analizuj i Zaokrąglij dane wejściowe o dowolnej długości.
* Prawidłowo Przeanalizuj i sformatuj ujemną wartość zero.
* Poprawne analizowanie `Infinity` i `NaN` wykonywanie kontroli bez uwzględniania wielkości liter i Zezwalanie na opcjonalne poprzednie `+` , jeśli ma to zastosowanie.

Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:

* <xref:System.Math.BitIncrement(System.Double)>lub<xref:System.Math.BitDecrement(System.Double)>\
Odnosi się do `nextUp` operacji `nextDown` i IEEE. Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio). Na przykład `Math.BitIncrement(0.0)` zwrócimy `double.Epsilon`.

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)>lub<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odnosi się do `maxNumMag` operacji `minNumMag` i IEEE, zwracają wartość, która jest większa lub mniejsza o wielkości dwóch danych wejściowych (odpowiednio). Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwrócimy `-3.0`.

* <xref:System.Math.ILogB(System.Double)>\
Odnosi się do `logB` operacji IEEE, która zwraca wartość całkowitą, zwraca integralny dziennik Base-2 parametru wejściowego. Ta metoda jest efektywnie taka sama jak `floor(log2(x))`, ale została wykonana z minimalnym błędem zaokrąglania.

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odnosi się do `scaleB` operacji IEEE, która przyjmuje wartość całkowitą, która zwraca efektywność `x * pow(2, n)`, ale jest wykonywana z minimalnym błędem zaokrąglania.

* <xref:System.Math.Log2(System.Double)>\
Odpowiada operacji `log2` IEEE, Zwraca logarytm o podstawie 2. Minimalizuje błąd zaokrąglania.

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odnosi się do `fma` operacji IEEE, dlatego wykonuje odrzucane mnożenie dodawania. Oznacza to, `(x * y) + z` że jest to jedyna operacja, czyli przez zminimalizowanie błędu zaokrąglania. Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` zwracana wartość `1e308`. Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity`.

* <xref:System.Math.CopySign(System.Double,System.Double)>\
Odpowiada operacji `x`IEEE, zwraca wartość, `y`ale ze znakiem. `copySign`

## <a name="fast-built-in-json-support"></a>Szybka Wbudowana obsługa JSON

Użytkownicy platformy .NET mogą w dużym stopniu korzystać z [**JSON.NET**](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal są dobrym wybórem. **JSON.NET** używa ciągów .NET jako podstawowego elementu DataType, który jest UTF-16 pod okapem.

Nowa Wbudowana obsługa JSON to wysoka wydajność, niska alokacja i oparta na `Span<byte>`. Do programu .NET Core 3,0 <xref:System.Text.Json?displayProperty=nameWithType> przestrzeń nazw dodano trzy nowe główne typy powiązane z JSON. Te typy nie obsługują *jeszcze* zwykłych serializacji i deserializacji obiektu CLR (POCO).

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, `ReadOnlySpan<byte>`Odczytaj od. `Utf8JsonReader` Jest to podstawowy typ niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji. Odczytywanie za pośrednictwem ładunku JSON przy `Utf8JsonReader` użyciu nowego jest szybsze niż używanie czytnika z **JSON.NET**. Nie jest przydzielany do momentu, gdy wymagane jest actualize tokenów JSON jako ciągów (UTF-16).

Oto przykład odczytywania za pomocą pliku [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) utworzonego przez Visual Studio Code:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>zapewnia wysoką wydajność, niebuforowaną, tylko do przodu sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów, takich `String`jak `Int32`,, `DateTime`i. Podobnie jak w przypadku czytnika, moduł zapisujący jest podstawą typu, który może służyć do tworzenia serializatorów niestandardowych. Zapis ładunku JSON przy użyciu nowego `Utf8JsonWriter` programu to 30-80% szybciej niż przy użyciu składnika zapisywania z **JSON.NET** i nie jest przydzielany.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>jest zbudowany z góry `Utf8JsonReader`. `JsonDocument` Zapewnia możliwość analizowania danych JSON i tworzenia Document Object Model tylko do odczytu (dom), do których można wykonywać zapytania, aby obsługiwać losowy dostęp i Wyliczenie. Do elementów JSON, które tworzą dane, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu, który jest udostępniany `JsonDocument` przez właściwość o `RootElement`nazwie. `JsonElement` Zawiera tablicę JSON i moduł wyliczający obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET. Analizowanie typowego ładunku JSON i uzyskiwanie dostępu do wszystkich jego `JsonDocument` elementów członkowskich przy użyciu programu ma wartość 2-3 — szybszy niż **JSON.NET** z małym alokacją dla danych o rozsądnym rozmiarze (czyli < 1 MB).

Oto przykładowe użycie `JsonDocument` i `JsonElement` , które może służyć jako punkt początkowy:

Poniżej znajduje się C# przykład 8,0 do odczytu za pomocą pliku [Launch. json](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) utworzonego przez Visual Studio Code:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType>jest zbudowany w oparciu o <xref:System.Text.Json.Utf8JsonReader> i <xref:System.Text.Json.Utf8JsonWriter> , aby zapewnić szybką opcję serializacji o niskiej pamięci podczas pracy z dokumentami i fragmentami JSON.

Badanie: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md aby zapoznać się z przykładem dotyczącym portu do tego artykułu

Oto przykład serializacji obiektu do formatu JSON:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Oto przykład deserializacji ciągu JSON do obiektu. Można użyć ciągu JSON utworzonego w poprzednim przykładzie:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Udoskonalenia międzyoperacyjności

Program .NET Core 3,0 zwiększa natywną międzyoperacyjność interfejsu API.

### <a name="type-nativelibrary"></a>Wpisz: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>zapewnia hermetyzację do ładowania biblioteki natywnej (przy użyciu tej samej logiki obciążenia co .NET Core P/Invoke) i udostępniającej odpowiednie funkcje pomocnika, `getSymbol`takie jak. Aby zapoznać się z przykładowym kodem, zobacz [Demonstracja DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).

### <a name="windows-native-interop"></a>Windows Native Interop

System Windows oferuje bogaty natywny interfejs API w postaci prostych interfejsów API języka C, COM i WinRT. Podczas gdy platforma .NET Core obsługuje funkcję **P/Invoke**, program .net Core 3,0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywowania interfejsów API WinRT**. Aby zapoznać się z przykładem kodu, zobacz [Demonstracja programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>Obsługa protokołu HTTP/2

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typ obsługuje protokół HTTP/2. Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/CLIENTHELLO ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się go użyć.

Domyślnym protokołem jest protokół HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby. Najpierw można ustawić komunikat żądania HTTP na potrzeby używania protokołu HTTP/2:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Po drugie, można domyślnie <xref:System.Net.Http.HttpClient> zmienić użycie protokołu HTTP/2:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

W wielu przypadkach podczas tworzenia aplikacji chcesz użyć nieszyfrowanego połączenia. Jeśli wiesz, że docelowy punkt końcowy będzie używać protokołu HTTP/2, możesz włączyć nieszyfrowane połączenia dla protokołu HTTP/2. Można ją włączyć przez ustawienie `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` zmiennej środowiskowej na `1` lub przez włączenie jej w kontekście aplikacji:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1,3 & OpenSSL 1.1.1 w systemie Linux

Platforma .NET Core wykorzystuje teraz zalety [protokołu TLS 1,3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest on dostępny w danym środowisku. Z protokołem TLS 1,3:

* Czas połączenia jest ulepszony ze zredukowanymi przedziałami rundy między klientem i serwerem.
* Ulepszone zabezpieczenia spowodowane usuwaniem różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.

Jeśli jest dostępny, program .NET Core 3,0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux. Gdy **OpenSSL 1.1.1** jest dostępny, oba <xref:System.Net.Security.SslStream?displayProperty=nameWithType> typy <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i używają **protokołu TLS 1,3** (przy założeniu, że zarówno klient, jak i serwer obsługują **protokół TLS 1,3**).

>[!IMPORTANT]
>Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1,3**. Platforma .NET Core 3,0 będzie obsługiwać **protokół TLS 1,3** w tych systemach operacyjnych, gdy będzie dostępna pomoc techniczna.

Poniższy C# przykład 8,0 ilustruje platformę .net Core 3,0 na Ubuntu 18,10 <https://www.cloudflare.com>z:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Szyfrowanie kryptografii

Program .NET 3,0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM** , implementowanych <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> za <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> pomocą i odpowiednio. Te algorytmy są [uwierzytelnianiem uwierzytelnianym przy użyciu algorytmów danych skojarzenia (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Poniższy kod ilustruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania danych losowych.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Import/Eksport klucza kryptograficznego

Program .NET Core 3,0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych z formatów standardowych. Nie musisz używać certyfikatu X. 509.

Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDSA*i *ECDiffieHellman*, obsługują następujące formaty:

* **Klucz publiczny**
  * SubjectPublicKeyInfo X. 509

* **Klucz prywatny**
  * PrivateKeyInfo PKCS # 8
  * EncryptedPrivateKeyInfo PKCS # 8

Klucze RSA obsługują również:

* **Klucz publiczny**
  * RSAPublicKey PKCS # 1

* **Klucz prywatny**
  * RSAPrivateKey PKCS # 1

Metody eksportowania generują dane binarne kodowane algorytmem DER, a metody importowe oczekują na to samo. Jeśli klucz jest przechowywany w formacie PEM przyjaznym dla tekstu, wywołujący będzie musiał odkodować zawartość przed wywołaniem metody Import.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

Można sprawdzać <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> pliki **PKCS # 8** i <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>pliki **PFX/PKCS # 12** . Pliki **PFX/PKCS # 12** można manipulować przy użyciu programu <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>Klasy SerialPort dla systemu Linux

Platforma .NET Core 3,0 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> obsługuje system Linux.

Wcześniej platforma .NET Core jest obsługiwana `SerialPort` tylko w systemie Windows.

## <a name="docker-and-cgroup-memory-limits"></a>Limity pamięci Docker i cgroup

Począwszy od wersji zapoznawczej 3, uruchomienie programu .NET Core 3,0 w systemie Linux z rozwiązaniem Docker działa lepiej z limitami pamięci cgroup. Uruchamianie kontenera Docker z limitami pamięci, na przykład z `docker run -m`, zmienia sposób działania programu .NET Core.

* Domyślny rozmiar sterty modułu wyrzucania elementów bezużytecznych (GC): maksymalnie 20 MB lub 75% limitu pamięci w kontenerze.
* Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu cgroup.
* Minimalny zarezerwowany rozmiar segmentu na stos GC to 16 MB. Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.

## <a name="smaller-garbage-collection-heap-sizes"></a>Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych

Rozmiar sterty domyślnej modułu wyrzucania elementów bezużytecznych został zmniejszony z powodu mniejszej ilości pamięci w programie .NET Core. Ta zmiana jest lepsza w porównaniu z budżetem alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej.

## <a name="garbage-collection-large-page-support"></a>Obsługa dużej strony odzyskiwania pamięci

Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny może ustalić obszary pamięci większe niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.

Moduł wyrzucania elementów bezużytecznych można teraz skonfigurować przy użyciu ustawienia **GCLargePages** jako funkcji wyboru do przydzielania dużych stron w systemie Windows.

## <a name="gpio-support-for-raspberry-pi"></a>Obsługa interfejsu GPIO dla Raspberry Pi

Do programu NuGet zostały wydane dwa pakiety, których można użyć do programowania interfejsu GPIO:

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
* [IoT. Device. bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Pakiety GPIO obejmują interfejsy API dla urządzeń z interfejsem *GPIO*, *SPI*, *I2C*i *PWM* . Pakiet powiązań IoT obejmuje powiązania urządzeń. Aby uzyskać więcej informacji, zobacz [repozytorium GitHub](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>Obsługa systemu Linux ARM64

Program .NET Core 3,0 dodaje obsługę ARM64 dla systemu Linux. Podstawowy przypadek użycia dla ARM64 jest obecnie z scenariuszami IoT. Aby uzyskać więcej informacji, zobacz temat [stan arm64 programu .NET Core](https://github.com/dotnet/announcements/issues/82).

[Obrazy Docker dla platformy .NET Core w systemie arm64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.

> [!NOTE]
> **Arm64** Obsługa systemu Windows nie jest jeszcze dostępna.
