---
title: Co nowego w języku C# 8.0 - C# Przewodnik
description: Zapoznaj się z nowymi funkcjami dostępnymi w języku C# 8.0.
ms.date: 09/20/2019
ms.openlocfilehash: 0013f621268e2a4f1b916b226d83d18c68445ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399680"
---
# <a name="whats-new-in-c-80"></a>Co nowego w języku C# 8.0

C# 8.0 dodaje następujące funkcje i ulepszenia do języka Języka C#:

- [Członkowie tylko do odczytu](#readonly-members)
- [Domyślne metody interfejsu](#default-interface-methods)
- [Ulepszenia dopasowywania wzorców:](#more-patterns-in-more-places)
  - [Przełączanie wyrażeń](#switch-expressions)
  - [Wzorce właściwości](#property-patterns)
  - [Wzory krotki](#tuple-patterns)
  - [Wzory pozycyjne](#positional-patterns)
- [Korzystanie z deklaracji](#using-declarations)
- [Statyczne funkcje lokalne](#static-local-functions)
- [Jednorazowe struktury ref](#disposable-ref-structs)
- [Typy referencyjne dopuszczające wartość null](#nullable-reference-types)
- [Strumienie asynchroniczne](#asynchronous-streams)
- [Indeksy i zakresy](#indices-and-ranges)
- [Przypisanie łączenia wartości null](#null-coalescing-assignment)
- [Typy skonstruowane niezarządzane](#unmanaged-constructed-types)
- [Stackalloc w wyrażeniach zagnieżdżonych](#stackalloc-in-nested-expressions)
- [Wzmocnienie interpolowanych ciągów dosłownych](#enhancement-of-interpolated-verbatim-strings)

C# 8.0 jest obsługiwany w **.NET Core 3.x** i **.NET Standard 2.1**. Aby uzyskać więcej informacji, zobacz [C# language versioning](../language-reference/configure-language-version.md).

W dalszej części tego artykułu opisano pokrótce te funkcje. Tam, gdzie dostępne są szczegółowe artykuły, dostępne są łącza do tych samouczków i przeglądów. Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *próbek.*
1. Uruchom polecenie `dotnet try`.

## <a name="readonly-members"></a>Członkowie tylko do odczytu

`readonly` Modyfikator można zastosować do elementów członkowskich struktury. Oznacza to, że element członkowski nie modyfikuje stanu. Jest bardziej szczegółowy niż stosowanie `readonly` modyfikatora `struct` do deklaracji.  Należy wziąć pod uwagę następujące struktury zmienne:

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

Podobnie jak większość struktur, `ToString()` metoda nie modyfikuje stanu. Można wskazać, że `readonly` dodając modyfikator `ToString()`do deklaracji:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Powyższa zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp do `Distance` właściwości, która nie jest oznaczona: `readonly`

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilator ostrzega, gdy musi utworzyć kopię obronną.  Właściwość `Distance` nie zmienia stanu, więc można naprawić to `readonly` ostrzeżenie, dodając modyfikator do deklaracji:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Należy zauważyć, że `readonly` modyfikator jest konieczne na właściwość tylko do odczytu. Kompilator nie `get` zakłada, że akcesory nie modyfikują stanu; należy zadeklarować `readonly` jawnie. Właściwości implementowane automatycznie są wyjątkiem; kompilator będzie traktować wszystkie automatycznie implementowane getters jako tylko do `readonly` odczytu, `X` więc `Y` tutaj nie ma potrzeby, aby dodać modyfikator do i właściwości.

Kompilator wymusza regułę, że `readonly` członkowie nie modyfikują stanu. Następująca metoda nie zostanie skompilowana, `readonly` dopóki nie usuniesz modyfikatora:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Ta funkcja umożliwia określenie intencji projektu, dzięki czemu kompilator może go wymusić i dokonać optymalizacji na podstawie tego zamiaru. Możesz dowiedzieć się więcej o członków tylko [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)do odczytu w artykule odniesienia języka na .

## <a name="default-interface-methods"></a>Domyślne metody interfejsu

Teraz można dodać członków do interfejsów i zapewnić implementację dla tych elementów członkowskich. Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach bez przerywania zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu. Istniejące implementacje *dziedziczą* domyślną implementację. Ta funkcja umożliwia również C# do współdziałania z interfejsami API, które są przeznaczone dla systemu Android lub Swift, które obsługują podobne funkcje. Domyślne metody interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".

Domyślne metody interfejsu wpływa na wiele scenariuszy i elementów języka. Nasz pierwszy samouczek obejmuje [aktualizację interfejsu z domyślnymi implementacjami](../tutorials/default-interface-methods-versions.md). Inne samouczki i aktualizacje referencyjne nadchodzą w czasie do wydania ogólnego.

## <a name="more-patterns-in-more-places"></a>Więcej wzorów w większej liczbie miejsc

**Dopasowywanie wzorców** zapewnia narzędzia zapewniające funkcje zależne od kształtu w powiązanych, ale różnych rodzajach danych. C# 7.0 wprowadzono składnię wzorców typów [`is`](../language-reference/keywords/is.md) i [`switch`](../language-reference/keywords/switch.md) wzorców stałych przy użyciu wyrażenia i instrukcji. Funkcje te stanowiły pierwsze wstępne kroki w kierunku obsługi paradygmatów programowania, w których dane i funkcje są dostępne oddzielnie. W miarę jak branża przechodzi w kierunku większej liczby mikrousług i innych architektur opartych na chmurze, potrzebne są inne narzędzia językowe.

C# 8.0 rozszerza to słownictwo, dzięki czemu można użyć więcej wyrażeń wzorca w większej liczbie miejsc w kodzie. Należy wziąć pod uwagę te funkcje, gdy dane i funkcje są oddzielne. Należy wziąć pod uwagę dopasowywanie wzorca, gdy algorytmy zależą od faktu innego niż typ czasu wykonywania obiektu. Techniki te zapewniają inny sposób wyrażania wzorów.

Oprócz nowych wzorców w nowych miejscach C# 8.0 dodaje **wzorce cykliczne**. Wynikiem dowolnego wyrażenia wzorca jest wyrażenie. Wzorzec cykliczny jest po prostu wyrażenie wzorca stosowane do danych wyjściowych innego wyrażenia wzorca.

### <a name="switch-expressions"></a>Przełączanie wyrażeń

Często instrukcja [`switch`](../language-reference/keywords/switch.md) tworzy wartość w każdym `case` z jego bloków. **Wyrażenia przełącznika** umożliwiają użycie bardziej zwięzłej składni wyrażenia. Jest mniej powtarzających `case` się `break` i słów kluczowych i mniej nawiasów klamrowych.  Na przykład należy wziąć pod uwagę następujące wyliczenie, które zawiera listę kolorów tęczy:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

Jeśli aplikacja `RGBColor` zdefiniowała typ `R`skonstruowany z programu , `G` a `B` składniki, można przekonwertować `Rainbow` wartość na jej wartości RGB przy użyciu następującej metody zawierającej wyrażenie przełącznika:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Istnieje kilka ulepszeń składni tutaj:

- Zmienna jest `switch` przed słowem kluczowym. Różna kolejność ułatwia wizualnie odróżnienie wyrażenia przełącznika od instrukcji switch.
- Elementy `case` `:` i są `=>`zastępowane . Jest bardziej zwięzły i intuicyjny.
- Obudowę `default` zastępuje się `_` odrzuceniem.
- Obiekty są wyrażeniami, a nie instrukcjami.

Kontrast, że z równoważny `switch` kod przy użyciu instrukcji classic:

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>Wzorce właściwości

**Wzorzec właściwości** umożliwia dopasowanie właściwości badanego obiektu. Rozważmy witrynę handlu elektronicznego, która musi obliczyć podatek na podstawie adresu kupującego. To obliczenia nie jest podstawową odpowiedzialnością `Address` klasy. Z czasem będzie się zmieniać, prawdopodobnie częściej niż zmiany formatu adresu. Wysokość podatku zależy od `State` właściwości adresu. Poniższa metoda używa wzorca właściwości do obliczenia podatku od sprzedaży z adresu i ceny:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Dopasowanie wzorca tworzy zwięzłą składnię do wyrażania tego algorytmu.

### <a name="tuple-patterns"></a>Wzory krotki

Niektóre algorytmy zależą od wielu danych wejściowych. **Wzorce krotki** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako [krotka](../tuples.md).  Poniższy kod pokazuje wyrażenie przełącznika dla *rock gry, papieru, nożyczek:*

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

Komunikaty wskazują zwycięzcę. Przypadek odrzucenia reprezentuje trzy kombinacje dla powiązań lub inne dane wejściowe tekstu.

### <a name="positional-patterns"></a>Wzory pozycyjne

Niektóre typy `Deconstruct` zawierają metodę, która dekonstruuje jego właściwości na zmienne dyskretne. Gdy `Deconstruct` metoda jest dostępna, można użyć **wzorców pozycyjnych** do sprawdzania właściwości obiektu i używać tych właściwości dla wzorca.  Należy wziąć `Point` pod uwagę `Deconstruct` następującą klasę, która `X` `Y`zawiera metodę tworzenia zmiennych dyskretnych dla i:

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

Ponadto należy wziąć pod uwagę następujące wyliczenie, które reprezentuje różne pozycje kwadrantu:

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

Poniższa metoda używa **wzorca pozycyjnego** `x` do `y`wyodrębniania wartości i . Następnie używa klauzuli `when` do `Quadrant` określenia punktu:

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

Wzorzec odrzutów w `x` poprzednim `y` przełączniku pasuje, gdy jeden lub jest 0, ale nie oba. Wyrażenie przełącznika musi generować wartość lub zgłosić wyjątek. Jeśli żaden z przypadków są zgodne, wyrażenie przełącznika zgłasza wyjątek. Kompilator generuje ostrzeżenie dla Ciebie, jeśli nie obejmuje wszystkich możliwych przypadków w wyrażeniu przełącznika.

Możesz eksplorować techniki dopasowywania wzorców w tym [zaawansowanym samouczku na temat dopasowywania wzorców](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Korzystanie z deklaracji

Using **deklaracji** jest deklaracja zmiennej `using` poprzedzone słowem kluczowym. Informuje kompilator, że zmienna deklarowana powinna być usuwana na końcu otaczającego zakresu. Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu zamykającego dla metody. To koniec zakresu, w którym `file` jest zadeklarowany. Poprzedni kod jest odpowiednikiem następującego kodu, który używa instrukcji klasycznej [using:](../language-reference/keywords/using-statement.md)

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu zamykającego skojarzonego z instrukcją. `using`

W obu przypadkach kompilator generuje `Dispose()`wywołanie . Kompilator generuje błąd, jeśli `using` wyrażenie w instrukcji nie jest jednorazowe.

## <a name="static-local-functions"></a>Statyczne funkcje lokalne

Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołuje się) żadnych zmiennych z otaczającego zakresu. W ten `CS8421`sposób generuje , "Statyczny funkcja \<lokalna nie może zawierać odwołanie do zmiennej>."

Należy wziąć pod uwagę następujący kod. Funkcja `LocalFunction` lokalna uzyskuje `y`dostęp do zmiennej zadeklarowanej `M`w otaczającym zakresie (metoda). W `LocalFunction` związku z tym nie `static` można zadeklarować za pomocą modyfikatora:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Poniższy kod zawiera statyczną funkcję lokalną. Może być statyczny, ponieważ nie ma dostępu do żadnych zmiennych w otaczającym zakresie:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Jednorazowe struktury ref

Zadeklarowane `struct` za `ref` pomocą modyfikatora może nie implementować żadnych interfejsów, a więc nie można zaimplementować <xref:System.IDisposable>. W związku z `ref struct` tym, aby umożliwić unieszkodliwiania, musi mieć metodę dostępną. `void Dispose()` Ta funkcja ma `readonly ref struct` również zastosowanie do deklaracji.

## <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

Wewnątrz kontekstu adnotacji nullable każda zmienna typu odwołania jest uważana za **typ odwołania niepodlegającego unieważnieniu**. Aby wskazać, że zmienna może mieć wartość null, należy `?` doniąc nazwę typu do zadeklarowania zmiennej jako **typu odwołania unieważnianego**.

W przypadku typów odwołań niepodlegających unieważnieniu kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości niezerowej po zadeklarowaniu. Pola muszą być zainicjowane podczas budowy. Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie dowolnego z dostępnych konstruktorów lub przez inicjatora. Ponadto niemożna przypisać typów odwołań niepodlegających unieważnieniu wartości, która może mieć wartość null.

Typy odwołań z możliwością null nie są sprawdzane, aby upewnić się, że nie są przypisane lub zainicjowane do wartości null. Jednak kompilator używa analizy przepływu, aby upewnić się, że każda zmienna typu odwołania nullable jest sprawdzana na podstawie wartości null, zanim zostanie uzyskana lub przypisana do nieunieważnionego typu odwołania.

Więcej informacji na temat tej funkcji można znaleźć w przeglądzie [typów odwołań z możliwością unieważnienia.](../nullable-references.md) Spróbuj sam w nowej aplikacji w tym [nullable typy odwołań samouczek](../tutorials/nullable-reference-types.md). Dowiedz się więcej o krokach migracji istniejącej bazy kodu w celu użycia typów odwołań z możliwością null w [samouczku migracji aplikacji w celu użycia samouczka typu odwołań nullable](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Strumienie asynchroniczne

Począwszy od języka C# 8.0, można tworzyć i używać strumieni asynchronicznie. Metoda zwracająca strumień asynchroniczny ma trzy właściwości:

1. Jest zadeklarowany za `async` pomocą modyfikatora.
1. Zwraca plik <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Metoda zawiera `yield return` instrukcje do zwracania kolejnych elementów w strumieniu asynchronicznym.

Korzystanie ze strumienia asynchronicznego `await` wymaga dodania słowa kluczowego przed `foreach` słowem kluczowym podczas wyliczania elementów strumienia. Dodanie `await` słowa kluczowego wymaga metody, która wylicza strumień asynchroniczny być zadeklarowane za pomocą `async` modyfikatora i zwrócić typ dozwolony dla `async` metody. Zazwyczaj oznacza to <xref:System.Threading.Tasks.Task> zwrócenie <xref:System.Threading.Tasks.Task%601>lub . Może to być <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601>również lub . Metoda może zarówno zużywać i wytwarzać strumień asynchroniczny, co oznacza, że zwróci . <xref:System.Collections.Generic.IAsyncEnumerable%601> Poniższy kod generuje sekwencję od 0 do 19, czekając 100 ms między generowaniem każdego numeru:

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

Sekwencja zostanie wyliczona `await foreach` przy użyciu instrukcji:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Możesz spróbować strumieni asynchronicznych samodzielnie w naszym samouczku na [temat tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md). Domyślnie elementy strumienia są przetwarzane w kontekście przechwyconego. Jeśli chcesz wyłączyć przechwytywanie kontekstu, należy użyć metody <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł na [temat korzystania z wzorca asynchronicznego opartego](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniu .

## <a name="indices-and-ranges"></a>Indeksy i zakresy

Indeksy i zakresy zapewniają zwięzłą składnię dostępu do pojedynczych elementów lub zakresów w sekwencji.

Ta obsługa języka opiera się na dwóch nowych typach i dwóch nowych operatorach:

- <xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.
- Indeks od operatora `^`końcowego , który określa, że indeks jest względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType>reprezentuje podzakres sekwencji.
- Operator `..`zakresu , który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od reguł indeksów. Należy wziąć `sequence`pod uwagę tablicę . Indeks `0` jest taki `sequence[0]`sam jak . Indeks `^0` jest taki `sequence[sequence.Length]`sam jak . Należy `sequence[^0]` zauważyć, że zgłasza `sequence[sequence.Length]` wyjątek, tak jak to robi. Dla dowolnej `n`liczby `^n` indeks jest `sequence.Length - n`taki sam jak .

Zakres określa *początek* i *koniec* zakresu. Początek zakresu jest włącznie, ale koniec zakresu jest ekskluzywny, co oznacza, że *początek* jest uwzględniony w zakresie, ale *koniec* nie jest uwzględniony w zakresie. Zakres `[0..^0]` reprezentuje cały zakres, podobnie `[0..sequence.Length]` jak cały zakres.

Oto kilka przykładów. Należy wziąć pod uwagę następującą tablicę, z adnotatorem z indeksem od początku i od końca:

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Możesz pobrać ostatnie słowo `^1` z indeksem:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Poniższy kod tworzy podzakres z napisem "szybkie", "brązowy" i "lis". Obejmuje `words[1]` ona poprzez `words[3]`. Element `words[4]` nie jest w zakresie.

```csharp
var quickBrownFox = words[1..4];
```

Poniższy kod tworzy podzakres z "leniwy" i "pies". Obejmuje `words[^2]` i `words[^1]`. Indeks `words[^0]` końcowy nie jest uwzględniony:

```csharp
var lazyDog = words[^2..^0];
```

Poniższe przykłady tworzą zakresy, które są otwarte dla początku, końca lub obu:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Można również zadeklarować zakresy jako zmienne:

```csharp
Range phrase = 1..4;
```

Zakres może być następnie `[` używany `]` wewnątrz znaków i znaków:

```csharp
var text = words[phrase];
```

Nie tylko tablice obsługują indeksy i zakresy. Można również użyć indeksów i zakresów <xref:System.Span%601>z <xref:System.ReadOnlySpan%601> [ciągiem](../language-reference/builtin-types/reference-types.md#the-string-type), lub . Aby uzyskać więcej informacji, zobacz [Obsługa typów indeksów i zakresów](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Możesz dowiedzieć się więcej o indeksach i zakresach w samouczku na [temat indeksów i zakresów](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Przypisanie łączenia wartości null

C# 8.0 wprowadza operator `??=`przypisania null-łączenie . Operator służy `??=` do przypisywania wartości jego poprawej operand do jego operand po lewej stronie tylko wtedy, gdy po lewej stronie operand ocenia . `null`

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Aby uzyskać więcej informacji, zobacz [?? i ?? = artykuł operatorów.](../language-reference/operators/null-coalescing-operator.md)

## <a name="unmanaged-constructed-types"></a>Typy skonstruowane niezarządzane

W języku C# 7.3 i wcześniejszych typu skonstruowanego (typ, który zawiera co najmniej jeden typ argumentu) nie może być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md). Począwszy od języka C# 8.0, typ wartości konstruowanej jest niezarządzany, jeśli zawiera tylko pola typów niezarządzanych.

Na przykład, biorąc pod uwagę `Coords<T>` następującą definicję typu ogólnego:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>` typ jest typem niezarządzanym w języku C# 8.0 i nowszych. Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Aby uzyskać więcej informacji, zobacz [Typy niezarządzane](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>Stackalloc w wyrażeniach zagnieżdżonych

Począwszy od Języka C# 8.0, jeśli wynik wyrażenia <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> [stackalloc](../language-reference/operators/stackalloc.md) jest `stackalloc` typu lub typu, można użyć wyrażenia w innych wyrażeniach:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Wzmocnienie interpolowanych ciągów dosłownych

Kolejność `$` i `@` tokeny w [interpolowanych](../language-reference/tokens/interpolated.md) ciągów dosłownych `$@"..."` może `@$"..."` być dowolny: oba i są prawidłowe interpolowane ciągi dosłowne. We wcześniejszych wersjach `$` języka C# `@` token musi pojawić się przed tokenem.
