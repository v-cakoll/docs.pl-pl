---
title: What's new in .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: e31f4391a057d0863f9dcdca00c90f9e591bc5e8
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739140"
---
# <a name="whats-new-in-net-core-30-preview-2"></a>What's new in .NET Core 3.0 (wersja zapoznawcza 2)

W tym artykule opisano nowości w programie .NET Core 3.0 (wersja zapoznawcza 2). Jedną z największych ulepszenia to obsługa aplikacji klasycznych Windows (tylko Windows). Przy użyciu zestawu SDK programu .NET Core 3.0 składnika o nazwie Windows Desktop, można portu usługi Windows Forms i aplikacji Windows Presentation Foundation (WPF). Było jasne, składnik Windows Desktop jest tylko obsługiwana i uwzględniane na Windows. Aby uzyskać więcej informacji, zobacz sekcję [pulpitu Windows](#windows-desktop) poniżej.

.NET core 3.0 dodaje obsługę C# 8.0.

[Pobierz i rozpoczynanie pracy z usługą .NET Core 3 w wersji zapoznawczej 2](https://aka.ms/netcore3download) teraz na Windows, Mac i Linux. Można wyświetlić szczegółowe informacje o wersji w [informacje o wersji platformy .NET Core 3 w wersji zapoznawczej 2](https://aka.ms/netcore3releasenotes).

Aby uzyskać więcej informacji na temat co została wydana w wersji zapoznawczej 1, zobacz [ogłoszenie .NET Core 3.0 w wersji zapoznawczej 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).

Aby uzyskać więcej informacji na temat co została wydana w wersji 2 zobacz [ogłoszenie .NET Core 3.0 w wersji zapoznawczej 1]().

## <a name="c-8"></a>C# 8

Obsługuje platformy .NET core 3.0 C# 8, a począwszy od platformy .NET Core 3.0 w wersji zapoznawczej 2 obsługuje te nowe funkcje. Aby uzyskać więcej informacji na temat C# funkcje 8.0, zobacz następujące wpisy na blogu:

- [Osiągnij więcej ze wzorców w C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/)
- [Wykonaj C# 8.0 dla pokrętła](https://blogs.msdn.microsoft.com/dotnet/2018/12/05/take-c-8-0-for-a-spin/)
- [Building C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/)


### <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy `Index` typ może być używany do indeksowania. Można utworzyć jeden z `int` , jest liczona od początku lub z prefiksem `^` — operator (C#), jest liczona od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również `Range` typ, który składa się z dwóch `Index` wartości, jeden dla początkowego i jeden dla elementu end i mogą być zapisywane z `x..y` zakres wyrażenia (C#). Następnie można zaindeksować z `Range` w celu tworzenia wycinka:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a>Asynchroniczne strumienie

`IAsyncEnumerable<T>` Typu jest nowa wersja asynchroniczne `IEnumerable<T>`. Język umożliwia `await foreach` za pośrednictwem `IAsyncEnumerable<T>` używanie ich elementy i używać `yield return` do ich do produkcji elementów.

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

>[!NOTE]
>Potrzebujesz .NET Core 3.0 w wersji zapoznawczej 2, aby użyć strumieni asynchronicznych, jeśli chcesz tworzyć aplikacje za pomocą programu Visual Studio 2019 r w wersji zapoznawczej 2 lub jego najnowszej wersji zapoznawczej [ C# rozszerzenia programu Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5). Jeśli używasz platformy .NET Core 3.0 w wersji zapoznawczej 2 w wierszu polecenia, następnie wszystko, co będzie działać zgodnie z oczekiwaniami.

### <a name="using-declarations"></a>Za pomocą deklaracji

*Za pomocą deklaracji* to nowy sposób, aby upewnić się, obiekt jest prawidłowo usunięte. A *użycie — deklaracja* utrzymuje aktywność obiekt jest nadal w zakresie. Gdy obiekt staje się poza zakresem, jest automatycznie usuwany. Spowoduje to zmniejszenie zagnieżdżonych *za pomocą instrukcji* i sprawić, że kod jest bardziej przejrzysty.

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a>Wyrażenia Switch

*Przełącz wyrażenia* są bardziej przejrzysty sposób zapobiegania zrobić *switch, instrukcja* , ale ponieważ jest to wyrażenie zwraca wartość. *Przełącz wyrażenia* także w pełni zintegrowane z dopasowywania do wzorca, a następnie użyj wzorca odrzucania `_`, do reprezentowania `default` wartość.

Można wyświetlić składnię *Przełącz wyrażenia* w następującym przykładzie:

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

Istnieją dwa wzorce podstawą w tym przykładzie. `o` najpierw jest zgodna z `Point` *wpisz wzór* i następnie *wzorzec właściwość* wewnątrz *{nawiasów klamrowych}*. `_` Opisuje `discard pattern`, która jest taka sama jak `default` dla *instrukcje switch*.

Wzorce umożliwiają pisanie kod deklaratywny, która przechwytuje zgodne z zamiarami użytkownika zamiast procedurach kod, który implementuje testy dla niego. Kompilator staje się odpowiedzialnych za wykonanie zadań żmudnych kod proceduralny i gwarantuje zawsze wykonuj poprawnie.

Nadal będą przypadki gdzie *instrukcje switch* będzie lepszym rozwiązaniem niż *Przełącz wyrażenia* i wzorce mogą być używane z obu stylów składni.

Aby uzyskać więcej informacji, zobacz [więcej możliwości dzięki wzorce w C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/).

## <a name="ieee-floating-point-improvements"></a>Ulepszenia zmiennoprzecinkowej IEEE

Liczb zmiennoprzecinkowych punktu interfejsy API są w trakcie aktualizacji do wykonania [poprawki 754-2008 IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Celem tych zmian jest obsługa wszystkich operacji "required" i upewnij się, że ich behaviorally zgodne ze specyfikacji IEEE.

Formatowanie poprawki i analizowanie:

* Poprawnie przeanalizować i zaokrąglanie danych wejściowych o dowolnej długości.
* Poprawnie przeanalizować i sformatować ujemna zero.
* Poprawnie przeanalizować nieskończoności i NaN poprzez sprawdzanie bez uwzględniania wielkości liter, dzięki czemu, opcjonalny poprzedzających `+` jeśli ma to zastosowanie.

Matematyczne nowe interfejsy API są:

* `BitIncrement/BitDecrement`\
Odnosi się do `nextUp` i `nextDown` IEEE operacji. Zwracają najmniejsza liczba zmiennoprzecinkowa porównuje w mniejszym lub większym niż dane wejściowe (odpowiednio). Na przykład `Math.BitIncrement(0.0)` zwróci `double.Epsilon`.

* `MaxMagnitude/MinMagnitude`\
Odnosi się do `maxNumMag` i `minNumMag` operacje IEEE zwracają wartość, która jest większy lub mniejszy w wielkości dwóch danych wejściowych (odpowiednio). Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwróci `-3.0`.

* `ILogB`\
Odnosi się do `logB` IEEE operacji, która zwraca wartość całkowitą, zwraca całkowitą dziennik base 2 parametr wejściowy. Efektywnie jest taka sama jak `floor(log2(x))`, ale pracy z minimalnym błąd zaokrąglania.

* `ScaleB`\
Odnosi się do `scaleB` IEEE operacji, która przyjmuje wartość całkowitą, funkcja zwraca skutecznie `x * pow(2, n)`, ale odbywa się przy użyciu minimalnego błąd zaokrąglania.

* `Log2`\
Odnosi się do `log2` operacji IEEE Zwraca logarytm o podstawie 2 dla podanego. Minimalizuje błędów zaokrąglania.

* `FusedMultiplyAdd`\
Odnosi się do `fma` wykonuje operację IEEE kolei wielokrotnie dodać. Oznacza to robi `(x * y) + z` jako pojedyncza operacja,-, minimalizując błąd zaokrąglania. Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` co powoduje zwrócenie `1e308`. Regularne `(1e308 * 2.0) - 1e308` zwraca `double.PositiveInfinity`.

* `CopySign`\
Odnosi się do `copySign` IEEE operację, zwraca wartość `x`, ale przy użyciu konta z `y`.

## <a name="net-platform-dependent-intrinsics"></a>Wewnętrzne zależne platformy .NET

Dodano interfejsy API, takich jak zezwalające na dostęp do niektórych instrukcji zorientowane na wydajności procesora CPU **SIMD** lub **instrukcji manipulowania Bit** ustawia. Te instrukcje może pomóc w osiągnięciu ulepszenia wydajności big Data w niektórych scenariuszach, takich jak przetwarzanie danych, efektywnie równolegle. Oprócz udostępnianie interfejsów API do programów do użycia, do bibliotek .NET rozpoczęły się przy użyciu tych instrukcji, aby zwiększyć wydajność.

Następujące żądania ściągnięcia CoreCLR pokazują niektóre funkcje wewnętrzne, za pośrednictwem implementacji lub użyj:

* [Implementowanie prostego funkcje wewnętrzne sprzętu SSE2](https://github.com/dotnet/coreclr/pull/15585)
* [Implementuje funkcje wewnętrzne sprzętu SSE](https://github.com/dotnet/coreclr/pull/15538)
* [Funkcje wewnętrzne Arm64 podstawowego sprzętu](https://github.com/dotnet/coreclr/pull/16822)
* [Użyj TZCNT i LZCNT dla lokalizacji {pierwszy | Znaleziono ostatnie} {bajt | Char}](https://github.com/dotnet/coreclr/pull/21073)

Aby uzyskać więcej informacji, zobacz [wewnętrzne zależne platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), który definiuje podejście do definiowania tej infrastruktury sprzętowej, dzięki czemu Microsoft, dostawców mikroukładu lub wszelkie inne firmy lub osoby do definiowania scalonym / W przypadku interfejsów API, które powinny być udostępniana dla kodu platformy .NET.

## <a name="default-executables"></a>Domyślne pliki wykonywalne

.NET core będzie teraz tworzyć [zależny od struktury plików wykonywalnych](../deploying/index.md#framework-dependent-executables-fde) domyślnie. Jest to nowość w aplikacji, które używają globalnie zainstalowaną wersję platformy .NET Core. Do tej pory tylko [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) dałby w efekcie plik wykonywalny.

Podczas `dotnet build` lub `dotnet publish`, plik wykonywalny jest tworzony, pod warunkiem, które odpowiadają środowisko i platforma używasz zestawu SDK. Mogą spodziewać się tego samego rzeczy, korzystając z tych plików wykonywalnych, tak jak w innych natywnych plików wykonywalnych, takich jak:

* Możesz kliknąć dwukrotnie plik wykonywalny.
* Można uruchomić aplikacji z poziomu wiersza polecenia, takie jak `myapp.exe` na Windows, i `./myapp` w systemie Linux i macOS.

## <a name="build-copies-dependencies"></a>Kopiuje zależności kompilacji

`dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięcią podręczną programu NuGet do folderu wyjściowego kompilacji. Wcześniej zależności zostały skopiowane tylko jako część `dotnet publish`. 

Istnieją pewne operacje takie jak łączenie i razor strony publikowania, który nadal będzie wymagać publikowania.


## <a name="local-dotnet-tools"></a>Narzędzia do lokalnego dotnet

>[!WARNING]
>Nastąpiła zmiana w lokalnym narzędzia .NET Core między .NET Core 3.0 w wersji zapoznawczej 1 i .NET Core 3.0 w wersji zapoznawczej 2.  Jeśli wypróbowane lokalne narzędzia w wersji zapoznawczej 1, uruchamiając polecenie, takie jak `dotnet tool restore` lub `dotnet tool install`, należy usunąć folder pamięci podręcznej narzędzia lokalnym przed narzędzia lokalnych będą działać poprawnie w wersji zapoznawczej 2. Ten folder znajduje się w:
>
>Na komputerze mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
>Na Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`
>
>Jeśli ten folder nie zostaną usunięte, zostanie wyświetlony błąd.

.NET Core 2.1 obsługiwana globalnego narzędzia, .NET Core 3.0 to ma teraz lokalne narzędzia. Lokalne narzędzia są podobne do narzędzia globalnych, ale są skojarzone z określonej lokalizacji na dysku. Dzięki temu projektów i narzędzi na repozytorium. Wszystkie zainstalowane lokalnie narzędzie nie jest globalnie dostępna. Narzędzia są dystrybuowane jako pakiety NuGet.

Lokalne narzędzia opierają się na nazwę pliku manifestu `dotnet-tools.json` w bieżącym katalogu. Ten plik manifestu definiuje narzędzia była dostępna, w tym folderze, jak i poniżej. Ten plik manifestu są tworzone w katalogu głównym repozytorium, możesz upewnij się, każdy klonowania kodu można przywrócić i korzystania z narzędzi, które są niezbędne do pomyślnie pracę z kodem.

Aby utworzyć `dotnet-tools.json` plik manifestu, użyj:

```console
dotnet new tool-manifest
```

Dodaj nowe narzędzie do lokalnego manifestu za pomocą:

```console
dotnet tool install <packageId>
```

Może również wyświetlać listę narzędzi dostępnych w lokalnym manifest za pomocą:

```console
dotnet tool list
```

Aby zobaczyć, jakie narzędzia są zainstalowane globalnie, należy użyć:

```console
dotnet tool list -g
```

Narzędzia do lokalnego manifestu plik jest dostępny, ale narzędzia zdefiniowany w manifeście nie został zainstalowany, użyj następującego polecenia, aby automatyczne pobranie i zainstalowanie tych narzędzi:

```console
dotnet tool restore
```

Uruchom narzędzie lokalnych za pomocą następującego polecenia:

```console
dotnet tool run <tool-command-name>
```

Po uruchomieniu lokalne narzędzie dotnet wyszukuje manifest zapasową bieżącej struktury katalogów. W przypadku odnalezienia pliku manifestu narzędzie przeszukiwany jest dla żądanego narzędzia. Jeśli narzędzie zostanie znaleziony w manifeście, ale nie pamięci podręcznej, użytkownik otrzyma błąd i musi zostać uruchomiony `dotnet tool restore`.

Aby usunąć narzędzie z pliku manifestu lokalne narzędzie, uruchom następujące polecenie:

```console
dotnet tool uninstall <packageId>
```

Plik manifestu narzędzia zaprojektowano w celu Zezwól na edytowanie strony — co może zrobić, aby zaktualizować wersję wymagane do pracy z repozytorium. Oto przykład `dotnet-tools.json` pliku:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Globalne i lokalne narzędzi zgodna wersja środowiska uruchomieniowego jest wymagana. Wiele narzędzi, obecnie w witrynie NuGet.org docelowej platformy .NET Core środowiska uruchomieniowego 2.1. Aby zainstalować te globalnie lub lokalnie, czy nadal należy zainstalować [środowisko uruchomieniowe programu NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="windows-desktop"></a>Pulpit systemu Windows

Począwszy od programu .NET Core 3.0 w wersji zapoznawczej 1, możesz tworzyć aplikacje pulpitu Windows przy użyciu WPF i Windows Forms. Następujące struktury obsługi, za pomocą nowoczesnych kontrolek i Fluent stylów z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [Wyspy XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Składnik Windows Desktop jest częścią Windows zestaw SDK programu .NET Core 3.0.

Można utworzyć nowej aplikacji WPF i Windows Forms z następującymi `dotnet` poleceń:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 Preview 2 dodaje **nowy projekt** szablonów dla platformy .NET Core 3.0 Windows Forms i WPF. Projektanci nadal jeszcze nie są obsługiwane. I można otwierać, uruchamianie i debugowanie tych projektów w programie Visual Studio 2019 r.

Visual Studio 2017 15.9 dodaje możliwość [Włącz podglądy platformy .NET Core](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/), ale konieczne jest włączenie tej funkcji i nie jest obsługiwanym scenariuszem.

Nowe projekty są takie same jak istniejących projektów .NET Core z dodatkami kilka. Oto porównanie podstawowy projekt konsoli .NET Core i podstawowy projekt Windows Forms i WPF.

W projekcie konsoli .NET Core, projekt korzysta z `Microsoft.NET.Sdk` zestawu SDK ale deklaruje zależności na .NET Core 3.0 to za pośrednictwem `netcoreapp3.0` platformy docelowej. Aby utworzyć aplikację pulpitu Windows, należy użyć `Microsoft.NET.Sdk.WindowsDesktop` zestawu SDK i wybierz polecenie struktury interfejsu użytkownika, których można użyć:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Aby wybrać Windows Forms w WPF, należy ustawić `UseWindowsForms` zamiast `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Zarówno `UseWPF` i `UseWindowsForms` można ustawić `true` Jeśli aplikacja korzysta z obu platform, na przykład gdy okno dialogowe Windows Forms jest hosting kontrolki WPF.

Podziel się swoją opinię na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) i [dotnet/core](https://github.com/dotnet/core/issues) repozytoriów.

## <a name="msix-deployment-for-windows-desktop"></a>Wdrożenie MSIX for Windows Desktop

[MSIX](https://docs.microsoft.com/windows/msix/) jest nowy format pakietu aplikacji Windows. Może służyć do wdrażania aplikacji klasycznych .NET Core 3.0 dla systemu Windows 10.

[Projekt pakietu aplikacji Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępne w wersji 2 (wersja zapoznawcza) 2019 r w usłudze Visual Studio, umożliwia tworzenie pakietów MSIX [niezależna](../deploying/index.md#self-contained-deployments-scd) aplikacji .NET Core.

>Uwaga: Plik projektu .NET Core, musisz określić obsługiwane środowiska uruchomieniowe w `<RuntimeIdentifiers>` właściwości:
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a>Szybkie wbudowanej obsługi formatu JSON

Ekosystemu .NET opierało się na [ **Json.NET** ](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal dobrych wyborów. **Program Json.NET** używa ciągów .NET jako jego podstawowy datatype kulisy używanej na UTF-16.

Nowa funkcja wbudowanej obsługi JSON to alokacji o wysokiej wydajności, niski i oparte na `Span<byte>`. Trzy nowe główne powiązane JSON typy zostały dodane do platformy .NET Core 3.0 `System.Text.Json` przestrzeni nazw.

### <a name="utf8jsonreader"></a>Utf8JsonReader

`System.Text.Json.Utf8JsonReader` jest o wysokiej wydajności, niski alokacji, tylko do przodu czytnik UTF-8 kodowany w formacie JSON tekst odczytywane `ReadOnlySpan<byte>`. `Utf8JsonReader` Jest typem podstawowe, niskiego poziomu, który można wykorzystać do tworzenia niestandardowych analizatory i deserializers. Odczytywanie za pośrednictwem ładunek w formacie JSON za pomocą nowego `Utf8JsonReader` wynosi 2 x szybciej niż przy użyciu czytnika, z **Json.NET**. Nie przydziela do czasu konieczne actualize tokenów JSON jako ciągi (UTF-16).

Ten nowy interfejs API obejmuje następujące składniki:

* W wersji zapoznawczej 1: Czytnik JSON (dostępu sekwencyjnego)
* Dodana w następnej kolejności: Moduł zapisujący JSON, modelu DOM (dostępu swobodnego) obiektów poco elementu serializującego obiektów poco Deserializator

Oto pętli czytnika podstawowego `Utf8JsonReader` mogą służyć jako punkt początkowy:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

`System.Text.Json.Utf8JsonWriter` zapewnia wysoce wydajnych niebuforowanym, tylko do zapisu kodowany w formacie UTF-8 do przodu tekstu JSON z popularnych typów .NET, takich jak `String`, `Int32`, i `DateTime`. Podobnie jak czytelnik moduł zapisujący jest typu podstawowe, niskiego poziomu, który można wykorzystać do tworzenia niestandardowych serializatory. Zapis ładunku JSON za pomocą nowego `Utf8JsonWriter` wynosi 30-80% szybciej niż przy użyciu składnika zapisywania z **Json.NET** i nie przydziela.

Poniżej przedstawiono przykładowe zastosowanie `Utf8JsonWriter` mogą służyć jako punkt początkowy:

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

`Utf8JsonWriter` Akceptuje `IBufferWriter<byte>` jako lokalizacja danych wyjściowych synchronicznie zapisać dane json, a jako obiekt wywołujący należy podać konkretną implementację. Platforma nie zawiera implementację tego interfejsu. Na przykład `IBufferWriter<byte>`, zobacz [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)

### <a name="jsondocument"></a>JsonDocument

`System.Text.Json.JsonDocument` jest wbudowana w górnej części `Utf8JsonReader`. `JsonDocument` Zapewnia możliwość analizowania danych JSON i dokonać jego kompilacji tylko do odczytu modelu DOM (Document Object) można wykonywać zapytania do obsługi dostępu losowego i wyliczenia. Elementy JSON, które tworzą dane można uzyskać dostęp za pośrednictwem `JsonElement` typu, który jest uwidaczniany przez `JsonDocument` jako właściwość o nazwie `RootElement`. `JsonElement` Zawiera wyliczenia tablicy i obiektów JSON, wraz z interfejsów API do konwertowania tekstu JSON do popularnych typów .NET. Analizowanie typowe ładunek w formacie JSON i uzyskiwania dostępu do wszystkich jej członków przy użyciu `JsonDocument` jest szybsza niż x 2 – 3 **Json.NET** z niewielkim alokacji dla danych, które są racjonalnie o rozmiarze (czyli < 1 MB).

Poniżej przedstawiono przykładowe zastosowanie `JsonDocument` i `JsonElement` mogą służyć jako punkt początkowy:

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a>Unloadability zestawu

Unloadability zestawu jest nową funkcją `AssemblyLoadContext`. Ta nowa funkcja jest w dużej mierze przejrzyste z perspektywy API udostępnianych za pomocą zaledwie kilku nowych interfejsów API. Dzięki temu można zwolnić zwalnianie pamięci wszystkich wystąpień typów, pola statyczne i samego montażu kontekst modułu ładującego. Aplikacja powinna mieć możliwość ładowanie i zwalnianie zestawów za pomocą tego mechanizmu w nieskończoność, bez występuje przeciek pamięci.

Ta nowa funkcja może służyć do scenariuszy, podobnie do:

* Wtyczka scenariuszy, w której dodatek dynamicznej, ładowanie i zwalnianie jest wymagana. 
* Dynamiczne kompilowanie, uruchamianie i następnie opróżnianie kodu. Przydatne w przypadku witryn sieci web, skryptów aparatów itp.
* Ładowanie zestawów do introspekcji (na przykład ReflectionOnlyLoad), mimo że [MetadataLoadContext](#type-metadataloadcontext) (wydane w wersji zapoznawczej 1) będzie lepszym rozwiązaniem w wielu przypadkach.

Aby uzyskać więcej informacji, zobacz [przy użyciu Unloadability](https://github.com/dotnet/coreclr/pull/22221) dokumentu.

Zwalnianie zestawów wymaga znaczących opieki, aby upewnić się, że wszystkie odwołania do obiektów zarządzanych z poza kontekstem modułu ładującego są zrozumiałe i zarządzane. Kontekst modułu ładującego zleconą można zwolnić zewnętrznego odwołania musi zostać nieużywanej tak, aby kontekst modułu ładującego jest spójny tylko do samego siebie.

W .NET Framework podano unloadability zestawu domen aplikacji (domen aplikacji), które nie są obsługiwane za pomocą programu .NET Core. Domen aplikacji ma zalety i ograniczenia w porównaniu do tego nowego modelu. Należy wziąć pod uwagę ten nowy model modułu ładującego do bardziej elastyczne i wyższej wydajności w porównaniu do domen aplikacji.

## <a name="windows-native-interop"></a>Współdziałanie natywne Windows

Windows oferuje zaawansowane natywne interfejsy API, w postaci prostych interfejsów API języka C, COM i WinRT. Od platformy .NET Core 1.0 **P/Invoke** obsługiwana. Za pomocą platformy .NET Core 3.0 to obsługują teraz możliwość **CoCreate interfejsów API modelu COM** i **aktywować interfejsów API WinRT** został dodany.

Możesz zobaczyć przykład korzystając z modelu COM za pomocą [kodu źródłowego w wersji demonstracyjnej programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).


## <a name="type-sequencereader"></a>Wpisz: SequenceReader

W programie .NET Core 3.0 `System.Buffers.SequenceReader` dodano, który może służyć jako czytnik `ReadOnlySequence<T>`. Umożliwia to łatwe w użyciu o wysokiej wydajności, niski alokacji analizowanie `System.IO.Pipelines` dane, które mogą przechodzić przez kilka buforów zapasowy. 

Poniższy przykład dzieli dane wejściowe `Sequence` na prawidłowe `CR/LF` rozdzielonych wiersze:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Wpisz: MetadataLoadContext

`MetadataLoadContext` Typ został dodany, który umożliwia odczytywanie zestawu metadanych, bez wywierania wpływu na domeny aplikacji obiektu wywołującego. Zestawy są odczytywane jako dane, w tym zestawy stworzona z myślą o różnych architektur oraz platformach niż bieżącego środowiska. `MetadataLoadContext` nakłada się na <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, która jest dostępna tylko w programie .NET Framework.

`MetdataLoadContext` jest dostępna w [pakietu System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). To pakiet .NET Standard 2.0.

`MetadataLoadContext` Udostępnia interfejsy API, podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale nie zależy od tego typu. Podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` umożliwia ładowanie zestawów w zestawie izolowane ładowania wszechświat. `MetdataLoadContext` Interfejsy API zwracają <xref:System.Reflection.Assembly> obiektów, umożliwiające użycie odbicia dobrze znanych interfejsów API. Wykonanie zorientowane na interfejsy API, takich jak [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nie są dozwolone i będzie zgłaszać wyjątek InvalidOperationException.

W poniższym przykładzie pokazano, jak znaleźć konkretne typy w zestawie, który implementuje danego interfejsu:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Scenariusze dotyczące `MetadataLoadContext` obejmują funkcje czasu projektowania, narzędzi, czas kompilacji i środowiska uruchomieniowego światła w górę funkcje wymagające sprawdzanie zbiór zestawów danych i ma blokady wszystkich plików i pamięć zwolniona po kontroli jest wykonywane.

`MetadataLoadContext` Przeszła klasy programu rozpoznawania nazw dla jego konstruktora. Zadanie programu rozpoznawania nazw ma ładować `Assembly` biorąc pod uwagę jej `AssemblyName`. Klasa rozpoznawania pochodzi z abstrakcyjnej `MetadataAssemblyResolver` klasy. Implementacja programu rozpoznawania nazw dla scenariuszy opartych na ścieżkach jest dostarczana z `PathAssemblyResolver`.

[Testy MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) pokazują wielu przypadków użycia. [Zestawu testów](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) są dobrym miejscem do rozpoczęcia.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 w systemie Linux

.NET core będą teraz korzystać z [Obsługa protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy będzie ona dostępna w danym środowisku. Istnieją różne korzyści 1.3 protokołu TLS na [zespołu OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Czas połączenia ulepszona z powodu ograniczenia liczby rund między klientem a serwerem.

* Ulepszone zabezpieczenia z powodu usunięcia rozmaite algorytmy kryptograficzne przestarzały i niezabezpieczone i szyfrowania większej uzgadniania połączenia.

.NET core 3.0 w wersji zapoznawczej 1 jest w stanie wykorzystujących **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, lub **OpenSSL 1.0.2** (niezależnie od znaleziono wersji najlepiej jest, w systemie Linux).  Podczas **OpenSSL 1.1.1** jest dostępna będzie używać typów SslStream i HttpClient **TLS 1.3** korzystając z `SslProtocols.None` (protokołów domyślne systemu), zakładając, że klient i serwer obsługi **TLS 1.3**.

W poniższym przykładzie pokazano .NET Core 3.0 w wersji zapoznawczej 1 na 18.10 Ubuntu nawiązywania połączenia z <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows i macOS nie jest jeszcze obsługiwany **TLS 1.3**. .NET core 3.0 to będzie obsługiwać **TLS 1.3** w tych systemach operacyjnych po udostępnieniu Pomocy technicznej.

## <a name="cryptography"></a>Kryptografia

Dodano obsługę dla **AES-GCM** i **AES-CCM** szyfrów, wdrożone za pośrednictwem `System.Security.Cryptography.AesGcm` i `System.Security.Cryptography.AesCcm`. Te algorytmy są [uwierzytelnione szyfrowanie za pomocą algorytmów skojarzenia danych (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)i pierwszy algorytmów szyfrowania uwierzytelniony (AE) dodane do platformy .NET Core.

Poniższy kod demonstruje użycie **AesGcm** szyfrowania do szyfrowania i odszyfrowywania danych losowych.

Kod **AesCcm** będzie wyglądała niemal identyczne (tylko nazwy zmiennych klasy może się różnić).

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Kryptograficznych kluczy importu/eksportu

.NET core 3.0 w wersji zapoznawczej 1 obsługuje importowanie i eksportowanie kluczy asymetrycznych publicznych i prywatnych z standardowych formatów, bez konieczności korzystania z certyfikatu X.509.

Wszystkie klucza Obsługa typów (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** format kluczy publicznych i **PKCS #8 PrivateKeyInfo** i **PKCS #8 EncryptedPrivateKeyInfo**  formatów dla kluczy prywatnych. Dodatkowo obsługuje RSA **PKCS #1 RSAPublicKey** i **PKCS #1 RSAPrivateKey**. Wszystkie metody eksportowania generuje dane binarne zakodowane w formacie DER i metod import oczekiwać takie same. Jeśli klucz jest przechowywany w formacie PEM przyjaznego tekstu, obiekt wywołujący, będą musieli base64 — dekodowanie zawartości przed wywołaniem metody importu.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

Pliki PKCS #8 mogą być kontrolowane za pomocą `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` klasy.

Pliki PFX/PKCS #12, które mogą być kontrolowane i modyfikować za pomocą `System.Security.Cryptography.Pkcs.Pkcs12Info` i `System.Security.Cryptography.Pkcs.Pkcs12Builder`, odpowiednio.

## <a name="serialport-for-linux"></a>Portu SerialPort dla systemu Linux

.NET core 3.0 obsługuje teraz <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.

Wcześniej, .NET Core obsługiwana tylko przy użyciu `SerialPort` typu na Windows.

## <a name="more-bcl-improvements"></a>Więcej udoskonaleń BCL

`Span<T>`, `Memory<T>`, I w środowisku .NET Core 3.0 zostały zoptymalizowane powiązanych typów, które zostały wprowadzone w programie .NET Core 2.1. Typowe operacje takie jak span konstrukcji, dzielenie, analizowania i formatowanie teraz działać lepiej. 

Ponadto takie jak typy `String` przejrzane czyni je bardziej efektywnymi, gdy jest używana jako klucze o ulepszenia w obszarze cover `Dictionary<TKey, TValue>` i innych kolekcji. Bez zmian w kodzie są wymagane do korzystania z tych ulepszeń.

Następujące ulepszenia również są nowe w .NET Core 3 (wersja zapoznawcza) 1:

* Obsługa Brotli wbudowanej w HttpClient
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Złożone operatory arytmetyczne
* Podtrzymywania API gniazda TCP
* StringBuilder.GetChunks
* IPEndPoint analizy
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Warstwowe kompilacji

[Warstwowe kompilacji](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) jest domyślnie przy użyciu platformy .NET Core 3.0. Jest funkcją, która umożliwia bardziej adaptacyjnie Użyj kompilator just in Time (JIT), aby uzyskać lepszą wydajność, zarówno podczas uruchamiania i w celu zmaksymalizowania wydajności.

Ta funkcja została dodana jako funkcja opcjonalna w [platformy .NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) i następnie została włączona domyślnie w [.NET Core 2.2 w wersji zapoznawczej 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/). Następnie został on przywrócony do zoptymalizowany pod kątem się przy użyciu wersji platformy .NET Core 2.2.

## <a name="arm64-linux-support"></a>Obsługa systemu Linux ARM64

Dodano obsługę dla architektury ARM64 dla systemu Linux. Głównym zastosowaniem dla architektury ARM64 jest obecnie używany w scenariuszach IoT.

Firma Alpine, Debian i Ubuntu [obrazów platformy Docker są dostępne dla platformy .NET Core dla architektury ARM64](https://hub.docker.com/r/microsoft/dotnet/).

Sprawdź, czy [stanu programu .NET Core ARM64](https://github.com/dotnet/announcements/issues/82) Aby uzyskać więcej informacji.

>[!NOTE]
> **ARM64** pomocy technicznej Windows nie jest jeszcze dostępna.

## <a name="install-net-core-30-previews-on-linux-with-snap"></a>Instalowanie wersji zapoznawczych programu .NET Core 3.0 w systemie Linux za pomocą przystawki

Przystawki jest preferowanym sposobem zainstalować i spróbować wersji zapoznawczych platformy .NET Core [systemu Linux obsługujących przystawki](https://docs.snapcraft.io/installing-snapd/6735).

Po skonfigurowaniu przyciągania w systemie, uruchom następujące polecenie, aby zainstalować [zestawu SDK platformy .NET Core SDK 3.0 w wersji zapoznawczej](https://snapcraft.io/dotnet-sdk).

```console
sudo snap install dotnet-sdk --beta --classic
```
 
.NET Core w zainstalowanych przy użyciu pakietu przystawki domyślnego polecenia .NET Core po `dotnet-sdk.dotnet`, a nie po prostu `dotnet`. Polecenie namespaced ma, nie będzie ona konflikt z globalnie zainstalowanej wersji platformy .NET Core, które mogą wiązać Ciebie. To polecenie może być aliasem do `dotnet` za pomocą:

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

Niektóre dystrybucje wymagają dodatkowych czynności, aby umożliwić dostęp do certyfikatu SSL. Zobacz nasze [Konfiguracja w systemie Linux](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) Aby uzyskać szczegółowe informacje.

## <a name="gpio-support-for-raspberry-pi"></a>Interfejs GPIO obsługa urządzenia Raspberry Pi

Dwa nowe pakiety zostały zwolnione do narzędzia NuGet używanego do programowania GPIO.

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

Pakiety GPIO obejmuje funkcje interfejsu API dla urządzeń z GPIO, SPI, I2C i PWM. Pakiet IoT powiązania obejmuje [powiązania urządzenia](https://github.com/dotnet/iot/blob/master/src/devices/README.md) różne kawałki i czujników, taki sam, te, które są dostępne pod adresem [dotnet/iot-src/urządzeń](https://github.com/dotnet/iot/tree/master/src/devices).

Zaktualizowano portu szeregowego nie należą do tych pakietów interfejsów API, które zostały ogłoszone w ramach platformy .NET Core 3.0 w wersji zapoznawczej 1, ale są dostępne w ramach platformy .NET Core.


## <a name="platform-support"></a>Obsługa platformy

.NET core 3 będą obsługiwane w następujących systemach operacyjnych:

* Klient Windows: 7, 8.1, 10 (1607+)
* Windows Server: 20012 R2 SP1+
* macOS: 10.12+
* RHEL: 6+
* Fedora: 26+
* Ubuntu: 16.04+
* Debian: 9+
* SLES: 12+
* openSUSE: 42.3+
* Firma Alpine: 3.8+

Obsługa mikroukładu następująco:

* x64 w Windows, macOS i Linux
* x86 na Windows
* ARM32 w systemach Windows i Linux
* ARM64 w systemie Linux

W przypadku systemu Linux ARM32 jest obsługiwana na Debian 9 + i systemem Ubuntu 16.04 +. Dla architektury ARM64 jest taka sama jak ARM32 dodając Alpine 3.8. Są to te same wersje tych dystrybucje, ponieważ jest obsługiwana X64.

Obrazy platformy docker dla platformy .NET Core 3.0 są dostępne pod adresem [microsoft/dotnet w usłudze Docker Hub](https://hub.docker.com/r/microsoft/dotnet/). Firma Microsoft jest obecnie w trakcie przyjmowania [rejestru kontenerów firmy Microsoft (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) i oczekuje się, że końcowy obrazów platformy .NET Core 3.0 tylko zostaną opublikowane na MCR.
