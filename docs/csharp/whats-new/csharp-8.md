---
title: Co nowego w C# 8.0 - C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w języku C# 8.0.
ms.date: 04/07/2020
ms.openlocfilehash: fcba0526fbcbe46a02cef167822c219f9db2eb63
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738165"
---
# <a name="whats-new-in-c-80"></a>Co nowego w języku C# 8.0

C# 8.0 dodaje następujące funkcje i ulepszenia do języka C#:

- [Czytaj tylko członków](#readonly-members)
- [Domyślne metody interfejsu](#default-interface-methods)
- [Ulepszenia dopasowywania wzorców:](#more-patterns-in-more-places)
  - [Przełączanie wyrażeń](#switch-expressions)
  - [Wzorce właściwości](#property-patterns)
  - [Wzory krotki](#tuple-patterns)
  - [Wzory pozycyjne](#positional-patterns)
- [Używanie deklaracji](#using-declarations)
- [Statyczne funkcje lokalne](#static-local-functions)
- [Jednorazowe struktury ref](#disposable-ref-structs)
- [Typy referencyjne dopuszczające wartość null](#nullable-reference-types)
- [Strumienie asynchroniczne](#asynchronous-streams)
- [Asynchroniczne jednorazowe](#asynchronous-disposable)
- [Indeksy i zakresy](#indices-and-ranges)
- [Przypisanie scalania wartości null](#null-coalescing-assignment)
- [Niezarządzane typy skonstruowane](#unmanaged-constructed-types)
- [Stackalloc w wyrażeniach zagnieżdżonych](#stackalloc-in-nested-expressions)
- [Wzmocnienie interpolowanych ciągów dosłownie](#enhancement-of-interpolated-verbatim-strings)

C# 8.0 jest obsługiwany w **.NET Core 3.x** i **.NET Standard 2.1**. Aby uzyskać więcej informacji, zobacz [wersja językowa języka C #](../language-reference/configure-language-version.md).

Poniżej dalsza część artykułu Pokrótce opisano te funkcje. Tam, gdzie dostępne są szczegółowe artykuły, znajdują się łącza do tych samouczków i przeglądów. Za pomocą narzędzia globalnego można `dotnet try` eksplorować te funkcje w swoim środowisku:

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Sklonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-samples.*
1. Uruchom polecenie `dotnet try`.

## <a name="readonly-members"></a>Czytaj tylko członków

`readonly` Modyfikator można zastosować do elementów członkowskich struktury. Wskazuje, że element członkowski nie modyfikuje stanu. Jest bardziej szczegółowe niż stosowanie `readonly` modyfikatora `struct` do deklaracji.  Należy wziąć pod uwagę następujące modyfikowalne struktury:

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

Poprzednia zmiana generuje ostrzeżenie kompilatora, `ToString` `Distance` ponieważ uzyskuje dostęp do `readonly`właściwości, która nie jest oznaczona:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilator ostrzega, gdy trzeba utworzyć kopię obronną.  Właściwość `Distance` nie zmienia stanu, więc można naprawić to `readonly` ostrzeżenie, dodając modyfikator do deklaracji:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Należy zauważyć, że `readonly` modyfikator jest konieczne we właściwości tylko do odczytu. Kompilator nie zakłada, że `get` akcesory nie modyfikują stanu; należy zadeklarować `readonly` jawnie. Automatycznie implementowane właściwości są wyjątkiem; kompilator będzie traktować wszystkie automatycznie implementowane `readonly`getters jako , więc `readonly` tutaj nie `X` ma `Y` potrzeby, aby dodać modyfikator do i właściwości.

Kompilator wymusza `readonly` regułę, że członkowie nie modyfikują stanu. Następująca metoda nie zostanie skompilowana, chyba że usuniesz `readonly` modyfikator:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Ta funkcja umożliwia określenie intencji projektu, dzięki czemu kompilator może wymusić go i dokonać optymalizacji na podstawie tej intencji.

Aby uzyskać więcej [ `readonly` ](../language-reference/builtin-types/struct.md#readonly-instance-members) informacji, zobacz sekcję członków wystąpienia w artykule [Typy struktury.](../language-reference/builtin-types/struct.md)

## <a name="default-interface-methods"></a>Domyślne metody interfejsu

Teraz można dodać członków do interfejsów i zapewnić implementację dla tych elementów członkowskich. Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach bez przerywania zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu. Istniejące implementacje *dziedziczą* domyślną implementację. Ta funkcja umożliwia również C# do współpracy z interfejsami API, które są przeznaczone dla systemu Android lub Swift, które obsługują podobne funkcje. Domyślne metody interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".

Domyślne metody interfejsu wpływa na wiele scenariuszy i elementów języka. Nasz pierwszy samouczek obejmuje [aktualizowanie interfejsu z domyślnymi implementacjami](../tutorials/default-interface-methods-versions.md). Inne samouczki i aktualizacje odwołań nadchodzą w czasie do wydania ogólnego.

## <a name="more-patterns-in-more-places"></a>Więcej wzorów w większej liczbie miejsc

**Dopasowywanie wzorców** daje narzędzia, aby zapewnić funkcje zależne od kształtu w pokrewnych, ale różnych rodzajów danych. C# 7.0 wprowadzono składni dla wzorców typów i [`is`](../language-reference/keywords/is.md) wzorców stałych [`switch`](../language-reference/keywords/switch.md) przy użyciu wyrażenia i instrukcji. Te funkcje stanowiły pierwsze wstępne kroki w kierunku obsługi paradygmatów programowania, w których dane i funkcje żyją osobno. W miarę jak branża przechodzi w kierunku większej liczby mikrousług i innych architektur opartych na chmurze, potrzebne są inne narzędzia językowe.

C# 8.0 rozszerza to słownictwo, dzięki czemu można użyć więcej wyrażeń wzorca w większej liczbie miejsc w kodzie. Należy wziąć pod uwagę te funkcje, gdy dane i funkcje są oddzielne. Należy wziąć pod uwagę dopasowanie wzorca, gdy algorytmy zależą od faktu innego niż typ środowiska wykonawczego obiektu. Techniki te zapewniają inny sposób wyrażania projektów.

Oprócz nowych wzorców w nowych miejscach, C# 8.0 dodaje **wzorce cykliczne**. Wynikiem dowolnego wyrażenia wzorca jest wyrażenie. Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.

### <a name="switch-expressions"></a>Przełączanie wyrażeń

Często instrukcja [`switch`](../language-reference/keywords/switch.md) tworzy wartość w każdym `case` z jego bloków. **Wyrażenia przełączania** umożliwiają użycie bardziej zwięzłej składni wyrażeń. Jest mniej powtarzających `case` się `break` i słów kluczowych, a mniej nawiasów klamrowych.  Na przykład należy wziąć pod uwagę następujące wyliczenia, które zawiera listę kolorów tęczy:

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

Jeśli aplikacja zdefiniowała `RGBColor` typ, który `R`jest `G` `B` skonstruowany z programu `Rainbow` , i składników, można przekonwertować wartość na jego wartości RGB przy użyciu następującej metody zawierającej wyrażenie przełącznika:

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

Istnieje kilka ulepszeń składni w tym miejscu:

- Zmienna jest `switch` przed słowem kluczowym. Różne kolejność sprawia, że wizualnie łatwo odróżnić wyrażenie przełącznika od instrukcji switch.
- Elementy `case` `:` i elementy `=>`są zastępowane . Jest bardziej zwięzły i intuicyjny.
- Obudowa `default` jest `_` zastępowana odrzutem.
- Obiekty są wyrażeniami, a nie instrukcjami.

Kontrast, że z równoważnym `switch` kodem przy użyciu instrukcji klasycznej:

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

**Wzorzec właściwości** umożliwia dopasowanie właściwości badanego obiektu. Rozważmy witrynę eCommerce, która musi obliczyć podatek na podstawie adresu kupującego. To obliczenie nie jest podstawową `Address` odpowiedzialnością klasy. Będzie się zmieniać w czasie, prawdopodobnie częściej niż zmiany formatu adresu. Kwota podatku zależy od `State` właściwości adresu. Następująca metoda używa wzorca właściwości do obliczenia podatku na podstawie adresu i ceny:

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

Dopasowywanie wzorców tworzy zwięzłą składnię do wyrażania tego algorytmu.

### <a name="tuple-patterns"></a>Wzory krotki

Niektóre algorytmy zależą od wielu danych wejściowych. **Wzory krotki** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako [krotka.](../tuples.md)  Poniższy kod pokazuje wyrażenie przełączania dla *gry rock, papier, nożyczki:*

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

Wiadomości wskazują zwycięzcę. Przypadek odrzucenia reprezentuje trzy kombinacje dla powiązań lub innych danych wejściowych tekstu.

### <a name="positional-patterns"></a>Wzory pozycyjne

Niektóre typy `Deconstruct` zawierają metodę, która dekonstruuje swoje właściwości na zmienne dyskretne. Gdy `Deconstruct` metoda jest dostępna, można użyć **wzorców pozycyjnych** do sprawdzania właściwości obiektu i używać tych właściwości dla wzorca.  Należy wziąć `Point` pod uwagę `Deconstruct` następującą klasę, która `X` zawiera `Y`metodę tworzenia zmiennych dyskretnych dla i:

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

Ponadto należy wziąć pod uwagę następujące wyliczenia, który reprezentuje różne pozycje kwadrantu:

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

Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i `y`. Następnie używa `when` klauzuli do określenia `Quadrant` punktu:

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

Wzorzec odrzucenia w poprzednim przełączniku pasuje, gdy albo `x` jest 0, `y` ale nie oba. Wyrażenie switch musi albo utworzyć wartość lub zgłosić wyjątek. Jeśli żaden z przypadków nie jest zgodny, wyrażenie switch zgłasza wyjątek. Kompilator generuje ostrzeżenie dla Ciebie, jeśli nie obejmuje wszystkich możliwych przypadków w wyrażeniu przełącznika.

Można zbadać techniki dopasowywania wzorców w tym [zaawansowanym samouczku na temat dopasowywania wzorców](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Używanie deklaracji

**Using declaration** jest deklaracją zmiennej `using` poprzedzoną słowem kluczowym. Informuje kompilator, że zmienna jest zadeklarowana powinny być usuwane na końcu otaczającego zakresu. Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:

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

W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu klamrowego dla metody. To koniec zakresu, w którym `file` jest zadeklarowany. Powyższy kod jest odpowiednikiem następującego kodu, który używa klasycznego [using instrukcji:](../language-reference/keywords/using-statement.md)

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

W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu `using` klamrowego zamknięcia skojarzonego z instrukcją.

W obu przypadkach kompilator generuje `Dispose()`wywołanie . Kompilator generuje błąd, jeśli wyrażenie `using` w instrukcji nie jest jednorazowe.

## <a name="static-local-functions"></a>Statyczne funkcje lokalne

Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołuje się) żadnych zmiennych z zakresu otaczającego. W ten `CS8421`sposób generuje , "Statyczna funkcja lokalna \<nie może zawierać odwołania do zmiennej>."

Należy wziąć pod uwagę następujący kod. Funkcja `LocalFunction` lokalna uzyskuje `y`dostęp do zmiennej, zadeklarowanej `M`w otaczającym zakresie (metoda). W związku `LocalFunction` z tym nie `static` można zadeklarować za pomocą modyfikatora:

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

Zadeklarowany `struct` z `ref` modyfikatorem może nie implementować żadnych <xref:System.IDisposable>interfejsów i dlatego nie można zaimplementować . W związku z `ref struct` tym, aby umożliwić a do `void Dispose()` usunięcia, musi mieć metodę dostępną. Ta funkcja dotyczy `readonly ref struct` również deklaracji.

## <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

Wewnątrz kontekstu adnotacji możliwej do unieważnienia każda zmienna typu odwołania jest uważana za **niesytrzalną typ odwołania.** Jeśli chcesz wskazać, że zmienna może mieć wartość null, `?` należy dołączyć nazwę typu z nazwą, aby zadeklarować zmienną jako **typ odwołania z dopuszczalną wartością null.**

W przypadku typów odwołań nieobjawialnych kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null po zadeklarowaniu. Pola muszą być inicjowane podczas budowy. Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie dowolnego z dostępnych konstruktorów lub przez inicjatora. Ponadto nie można przypisać typów odwołań nieskłocyjnych.

Typy odwołań nullable nie są sprawdzane, aby upewnić się, że nie są przypisane lub zainicjowane do wartości null. Jednak kompilator używa analizy przepływu, aby upewnić się, że każda zmienna typu odwołania nullable jest sprawdzana względem null przed uzyskaniam dostępu lub przypisaniem do nieskrójnego typu odwołania.

Więcej informacji na temat tej funkcji można znaleźć w przeglądzie [typów odwołań podlegającym wartości null.](../nullable-references.md) Spróbuj sam w nowej aplikacji w tym [nullable typy odwołań samouczek](../tutorials/nullable-reference-types.md). Dowiedz się więcej o krokach migracji istniejącej bazy kodu w celu wykorzystania typów odwołań do nullable w [migracji aplikacji do korzystania z samouczka typów odwołań nullable](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Strumienie asynchroniczne

Począwszy od języka C# 8.0, można tworzyć i zużywać strumienie asynchronicznie. Metoda zwraca strumień asynchroniczne ma trzy właściwości:

1. Jest zadeklarowany za `async` pomocą modyfikatora.
1. Zwraca wartość <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Metoda zawiera `yield return` instrukcje do zwracania kolejnych elementów w strumieniu asynchroniczne.

Korzystanie ze strumienia asynchroniiowego `await` wymaga dodania słowa kluczowego przed `foreach` słowem kluczowym podczas wyliczania elementów strumienia. Dodawanie `await` słowa kluczowego wymaga metody, która wylicza strumień asynchroniczne, które mają być zadeklarowane za pomocą `async` modyfikatora i zwrócić typ dozwolony `async` dla metody. Zazwyczaj oznacza to powrót <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>lub . Może to być <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601>również lub . Metoda może zarówno zużywać, jak i wytwarzać strumień asynchroniczne, co oznacza, że zwróci . <xref:System.Collections.Generic.IAsyncEnumerable%601> Poniższy kod generuje sekwencję od 0 do 19, oczekiwanie 100 ms między generowania każdej liczby:

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

Sekwencja należy wyliczyć `await foreach` za pomocą instrukcji:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Możesz spróbować strumieni asynchronicznych samodzielnie w naszym tutorialu na [temat tworzenia i spożywania strumieni asynchnc](../tutorials/generate-consume-asynchronous-stream.md). Domyślnie elementy strumienia są przetwarzane w kontekście przechwycone. Jeśli chcesz wyłączyć przechwytywanie kontekstu, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> użyj metody rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [korzystania z wzorca asynchronicznego opartego](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniach .

## <a name="asynchronous-disposable"></a>Asynchroniczne jednorazowe

Począwszy od języka C# 8.0, język obsługuje asynchroniczne jednorazowe typy, które implementują <xref:System.IAsyncDisposable?displayProperty=nameWithType> interfejs. Operand `using` wyrażenia można zaimplementować albo <xref:System.IDisposable> lub <xref:System.IAsyncDisposable>. W przypadku `IAsyncDisposable`kompilator generuje kod `await` do <xref:System.Threading.Tasks.Task> zwracanego z <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [ `using` instrukcję](../language-reference/keywords/using-statement.md).

## <a name="indices-and-ranges"></a>Indeksy i zakresy

Indeksy i zakresy zapewniają zwięzłą składnię dostępu do pojedynczych elementów lub zakresów w sekwencji.

Ta obsługa języka opiera się na dwóch nowych typach i dwóch nowych operatorach:

- <xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.
- Indeks z operatora `^`końcowego , który określa, że indeks jest względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType>reprezentuje podzakres sekwencji.
- Operator `..`zakresu , który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od reguł dla indeksów. Należy wziąć `sequence`pod uwagę tablicę . Indeks `0` jest taki `sequence[0]`sam jak . Indeks `^0` jest taki `sequence[sequence.Length]`sam jak . Należy `sequence[^0]` zauważyć, że zgłasza `sequence[sequence.Length]` wyjątek, podobnie jak robi. Dla dowolnej `n`liczby `^n` indeks jest `sequence.Length - n`taki sam jak .

Zakres określa *początek* i *koniec* zakresu. Początek zakresu jest włącznie, ale koniec zakresu jest wyłączny, co oznacza, że *początek* jest uwzględniony w zakresie, ale *koniec* nie jest uwzględniony w zakresie. Zakres `[0..^0]` reprezentuje cały zakres, `[0..sequence.Length]` podobnie jak reprezentuje cały zakres.

Oto kilka przykładów. Należy wziąć pod uwagę następującą tablicę, z adnotacjami z indeksem od początku i od końca:

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

Ostatnie słowo można pobrać za `^1` pomocą indeksu:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Poniższy kod tworzy podzakład z napisami "quick", "brown" i "fox". Obejmuje `words[1]` ona `words[3]`poprzez . Element `words[4]` nie jest w zakresie.

```csharp
var quickBrownFox = words[1..4];
```

Poniższy kod tworzy podzakład z "leniwy" i "pies". Obejmuje `words[^2]` ona `words[^1]`i . Indeks `words[^0]` końcowy nie jest uwzględniony:

```csharp
var lazyDog = words[^2..^0];
```

Poniższe przykłady tworzą zakresy, które są otwarte dla początku, końca lub obu:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Zakresy można również deklarować jako zmienne:

```csharp
Range phrase = 1..4;
```

Zakres może być następnie `[` używany `]` wewnątrz znaków i:

```csharp
var text = words[phrase];
```

Nie tylko macierze obsługują indeksy i zakresy. Można również użyć indeksów i zakresów <xref:System.Span%601>z <xref:System.ReadOnlySpan%601> [ciągiem](../language-reference/builtin-types/reference-types.md#the-string-type), lub . Aby uzyskać więcej informacji, zobacz [Obsługa typów indeksów i zakresów](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Możesz dowiedzieć się więcej o indeksach i zakresach w samouczku na temat [indeksów i zakresów](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Przypisanie scalania wartości null

C# 8.0 wprowadza operatora `??=`przypisania scalania wartości null . `??=` Za pomocą operatora można przypisać wartość jego prawej opery do jego lewej operndu tylko wtedy, `null`gdy leworęczny operand ocenia .

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

## <a name="unmanaged-constructed-types"></a>Niezarządzane typy skonstruowane

W języku C# 7.3 i wcześniejszych typu konstruowanego (typu zawierającego co najmniej jeden argument typu) nie może być [typem niezarządzanym.](../language-reference/builtin-types/unmanaged-types.md) Począwszy od języka C# 8.0, skonstruowany typ wartości jest niezarządzane, jeśli zawiera pola typu niezarządzanego tylko.

Na przykład, biorąc pod uwagę `Coords<T>` następującą definicję typu ogólnego:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>` typ jest typem niezarządzanym w języku C# 8.0 i nowszym. Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:

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

Począwszy od języka C# 8.0, jeśli wynik wyrażenia <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> [stackalloc](../language-reference/operators/stackalloc.md) jest `stackalloc` typu lub, można użyć wyrażenia w innych wyrażeniach:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Wzmocnienie interpolowanych ciągów dosłownie

Kolejność `$` i `@` tokeny w [interpolowanych](../language-reference/tokens/interpolated.md) ciągów dosłownie może `$@"..."` być `@$"..."` dowolny: oba i są prawidłowe interpolowane dosłownie ciągi. We wcześniejszych wersjach `$` języka C# `@` token musi pojawić się przed tokenem.
