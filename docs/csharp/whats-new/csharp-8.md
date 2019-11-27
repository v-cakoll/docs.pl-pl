---
title: Co nowego w C# 8,0 — C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8,0.
ms.date: 09/20/2019
ms.openlocfilehash: 540b95beaf00c17812a3b602602504278be69b0e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429392"
---
# <a name="whats-new-in-c-80"></a>Co nowego w C# 8,0

C#8,0 dodaje do C# języka następujące funkcje i ulepszenia:

- [Elementy członkowskie tylko do odczytu](#readonly-members)
- [Domyślne metody interfejsu](#default-interface-methods)
- [Ulepszenia dopasowania wzorców](#more-patterns-in-more-places):
  - [Przełącz wyrażenia](#switch-expressions)
  - [Wzorce właściwości](#property-patterns)
  - [Wzorce krotek](#tuple-patterns)
  - [Wzorce pozycyjne](#positional-patterns)
- [Korzystanie z deklaracji](#using-declarations)
- [Statyczne funkcje lokalne](#static-local-functions)
- [Nierozporządzalne struktury ref](#disposable-ref-structs)
- [Typy referencyjne dopuszczające wartość null](#nullable-reference-types)
- [Strumienie asynchroniczne](#asynchronous-streams)
- [Indeksy i zakresy](#indices-and-ranges)
- [Przypisanie do łączenia o wartości null](#null-coalescing-assignment)
- [Niezarządzane typy skonstruowane](#unmanaged-constructed-types)
- [Stackalloc w wyrażeniach zagnieżdżonych](#stackalloc-in-nested-expressions)
- [Ulepszenie interpolowanych ciągów Verbatim](#enhancement-of-interpolated-verbatim-strings)

C#8,0 jest obsługiwane w **programie .NET Core 3. x** i **.NET Standard 2,1**. Aby uzyskać więcej informacji, zobacz [ C# przechowywanie wersji języka](../language-reference/configure-language-version.md).

W pozostałej części tego artykułu krótko opisano te funkcje. Tam, gdzie są dostępne szczegółowe artykuły, znajdują się linki do samouczków i przeglądów. Te funkcje można eksplorować w środowisku za pomocą narzędzia globalnego `dotnet try`:

1. Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-Samples* .
1. Uruchom `dotnet try`.

## <a name="readonly-members"></a>Elementy członkowskie tylko do odczytu

Do elementów członkowskich struktury można zastosować modyfikator `readonly`. Wskazuje, że element członkowski nie modyfikuje stanu. Jest to bardziej szczegółowe niż zastosowanie modyfikatora `readonly` do deklaracji `struct`.  Weź pod uwagę następującą niemodyfikowalną strukturę:

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

Podobnie jak większość struktur, Metoda `ToString()` nie modyfikuje stanu. Można wskazać, że dodając modyfikator `readonly` do deklaracji `ToString()`:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Poprzednia zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp do właściwości `Distance`, która nie jest oznaczona `readonly`:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilator ostrzega o tym, gdy musi utworzyć kopię obronną.  Właściwość `Distance` nie zmienia stanu, więc możesz naprawić to ostrzeżenie, dodając modyfikator `readonly` do deklaracji:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Należy zauważyć, że modyfikator `readonly` jest konieczny dla właściwości tylko do odczytu. Kompilator nie zakłada, `get` metody dostępu nie modyfikują stanu; należy zadeklarować `readonly` jawnie. Zaimplementowane właściwości są wyjątkiem; kompilator będzie traktować wszystkie zaimplementowane metody pobierające jako tylko do odczytu, więc nie ma potrzeby dodawania modyfikatora `readonly` do właściwości `X` i `Y`.

Kompilator wymusza zasadę, która `readonly` członkowie nie modyfikują stanu. Następująca metoda nie zostanie skompilowana, chyba że usuniesz modyfikator `readonly`:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Ta funkcja umożliwia określenie zamierzonego projektu, aby kompilator mógł go wymusić i dokonać optymalizacji na podstawie tego zamiaru. Więcej informacji o elementach członkowskich w trybie tylko do odczytu znajduje się w artykule Skorowidz języka na [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).

## <a name="default-interface-methods"></a>Domyślne metody interfejsu

Teraz można dodawać członków do interfejsów i dostarczać implementację dla tych członków. Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach, bez podzielenia zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu. Istniejące implementacje *dziedziczą* implementację domyślną. Ta funkcja umożliwia C# również współdziałanie z interfejsami API przeznaczonymi dla systemu Android lub SWIFT, które obsługują podobne funkcje. Domyślne metody interfejsu zapewniają również scenariusze podobne do funkcji języka "cechy".

Domyślne metody interfejsu mają wpływ na wiele scenariuszy i elementów języka. W pierwszym samouczku omówiono [aktualizowanie interfejsu przy użyciu domyślnych implementacji](../tutorials/default-interface-methods-versions.md). Inne samouczki i aktualizacje referencyjne są dostępne w czasie do wydania ogólnego.

## <a name="more-patterns-in-more-places"></a>Więcej wzorców w większej liczbie miejsc

**Dopasowanie wzorców** oferuje narzędzia do zapewniania funkcji zależnych od kształtu między powiązanymi, ale różnymi rodzajami danych. C#7,0 wprowadzono składnię dla wzorców typu i wzorców stałych przy użyciu wyrażenia [`is`](../language-reference/keywords/is.md) i instrukcji [`switch`](../language-reference/keywords/switch.md) . Te funkcje przedstawiają pierwsze wstępnie wymagane kroki w kierunku obsługi odmian programistycznych, w których dane i funkcje są aktywne. Gdy branża jest przenoszona do większej liczby mikrousług i architektur opartych na chmurze, inne narzędzia języka są zbędne.

C#8,0 rozwija ten słownik, aby można było używać więcej wyrażeń wzorca w większej liczbie miejsc w kodzie. Te funkcje należy wziąć pod uwagę, gdy dane i funkcje są osobne. Rozważ dopasowanie wzorców, gdy algorytmy zależą od faktu innego niż typ środowiska uruchomieniowego obiektu. Techniki te zapewniają inny sposób tworzenia projektów.

Oprócz nowych wzorców w nowych miejscach, C# 8,0 dodaje **cykliczne wzorce**. Wynikiem dowolnego wyrażenia wzorca jest wyrażenie. Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.

### <a name="switch-expressions"></a>Przełącz wyrażenia

Często instrukcja [`switch`](../language-reference/keywords/switch.md) generuje wartość w każdym z bloków `case`. **Wyrażenia Switch** umożliwiają użycie bardziej zwięzłej składni wyrażeń. Istnieje mniej powtarzających się `case` i `break` słów kluczowych i mniej nawiasów klamrowych.  Na przykład rozważmy następujące Wyliczenie, które zawiera listę kolorów tęczu:

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

Jeśli aplikacja definiuje typ `RGBColor`, który jest zbudowany ze składników `R`, `G` i `B`, można skonwertować wartość `Rainbow` na wartości RGB przy użyciu następującej metody zawierającej wyrażenie Switch:

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

Poniżej przedstawiono kilka ulepszeń składni:

- Zmienna jest wcześniejsza niż słowo kluczowe `switch`. Inna kolejność ułatwia odróżnienie wyrażenia Switch od instrukcji switch.
- Elementy `case` i `:` są zastępowane `=>`. Jest to bardziej zwięzłe i intuicyjne.
- Przypadek `default` jest zastępowany `_` odrzucania.
- Treść to wyrażenia, a nie instrukcje.

Kontrast, który ma odpowiedni kod przy użyciu klasycznej instrukcji `switch`:

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

**Wzorzec właściwości** pozwala dopasować się do właściwości badanego obiektu. Rozważmy witrynę handlu elektronicznego, która musi obliczać podatek od sprzedaży na podstawie adresu kupującego. To obliczenie nie jest podstawowym zakresem odpowiedzialności klasy `Address`. Zostanie ona zmieniona z upływem czasu, co prawdopodobnie częściej niż zmienia format adresu. Kwota podatku od sprzedaży zależy od właściwości `State` adresu. Poniższa metoda używa wzorca właściwości do obliczania podatku od adresu i ceny:

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

### <a name="tuple-patterns"></a>Wzorce krotek

Niektóre algorytmy zależą od wielu danych wejściowych. **Wzorce krotek** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako [krotka](../tuples.md).  Poniższy kod przedstawia wyrażenie Switch dla *skały, papieru, nożyczków*:

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

Komunikaty wskazują zwycięzcę. Przypadek odrzucania reprezentuje trzy kombinacje powiązań lub inne dane wejściowe tekstu.

### <a name="positional-patterns"></a>Wzorce pozycyjne

Niektóre typy obejmują metodę `Deconstruct`, która dekonstruuje jego właściwości w zmiennych dyskretnych. Gdy `Deconstruct` Metoda jest dostępna, można użyć **wzorców pozycyjnych** do inspekcji właściwości obiektu i używania tych właściwości dla wzorca.  Rozważmy następujące klasy `Point`, które obejmują metodę `Deconstruct` do tworzenia zmiennych dyskretnych dla `X` i `Y`:

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

Dodatkowo Rozważmy następujące Wyliczenie, które reprezentuje różne położenia ćwiartki:

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

Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i `y`. Następnie używa klauzuli `when` do określenia `Quadrant` punktu:

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

Wzorzec Discard w poprzednim przełączniku pasuje, gdy `x` lub `y` ma wartość 0, ale nie oba. Wyrażenie Switch musi utworzyć wartość lub zgłosić wyjątek. Jeśli żaden z przypadków nie jest zgodny, wyrażenie Switch zgłasza wyjątek. Kompilator generuje ostrzeżenie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu Switch.

Techniki dopasowania wzorców można eksplorować w tym [zaawansowanym samouczku dotyczącym dopasowania wzorców](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Korzystanie z deklaracji

**Deklaracja using** jest deklaracją zmiennej poprzedzoną słowem kluczowym `using`. Informuje kompilator, że zadeklarowana zmienna powinna zostać usunięta na końcu otaczającego zakresu. Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:

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

W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody. Jest to koniec zakresu, w którym zadeklarowano `file`. Poprzedni kod jest odpowiednikiem poniższego kodu, który używa klasycznej [instrukcji using](../language-reference/keywords/using-statement.md):

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

W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego skojarzonego z instrukcją `using`.

W obu przypadkach kompilator generuje wywołanie do `Dispose()`. Kompilator generuje błąd, jeśli wyrażenie w instrukcji `using` nie jest jednorazowe.

## <a name="static-local-functions"></a>Statyczne funkcje lokalne

Teraz można dodać modyfikator `static` do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (nie dotyczy) żadnych zmiennych z otaczającego zakresu. Spowoduje to wygenerowanie `CS8421`"statyczna funkcja lokalna nie może zawierać odwołania do \<zmiennej >". 

Rozważmy następujący kod. Funkcja lokalna `LocalFunction` uzyskuje dostęp do zmiennej `y`, zadeklarowanej w otaczającym zakresie (Metoda `M`). W związku z tym `LocalFunction` nie można zadeklarować za pomocą modyfikatora `static`:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Poniższy kod zawiera statyczną funkcję lokalną. Może być statyczny, ponieważ nie uzyskuje dostępu do żadnych zmiennych w otaczającym zakresie:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Nierozporządzalne struktury ref

`struct` zadeklarowana z modyfikatorem `ref` nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>. W związku z tym, aby umożliwić pozbycie `ref struct`, musi on mieć dostępną metodę `void Dispose()`. Ta funkcja dotyczy również deklaracji `readonly ref struct`.

## <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

Wewnątrz bezwartościowego kontekstu adnotacji Każda zmienna typu referencyjnego jest uważana za **typ referencyjny, który nie ma wartości null**. Aby wskazać, że zmienna może mieć wartość null, należy dołączyć nazwę typu z `?`, aby zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null**.

W przypadku typów referencyjnych, które nie mają wartości null, kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null, gdy zostanie zadeklarowana. Pola muszą być inicjowane podczas konstruowania. Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiana przez wywołanie do któregokolwiek z dostępnych konstruktorów lub inicjatora. Ponadto nie można przypisać wartości, która może mieć wartość null.

Typy odwołań dopuszczających wartość null nie są sprawdzane w celu zapewnienia, że nie są przypisane ani zainicjowane do wartości null. Jednak kompilator używa analizy przepływu, aby upewnić się, że jakakolwiek zmienna typu referencyjnego null jest sprawdzana pod kątem wartości null przed uzyskaniem dostępu lub przypisaniem do niezerowego typu odwołania.

Więcej informacji na temat funkcji można znaleźć w omówieniu [typów referencyjnych dopuszczających wartość null](../nullable-references.md). Wypróbuj go samodzielnie w nowej aplikacji w tym [samouczku typów odwołań dopuszczających wartość null](../tutorials/nullable-reference-types.md). Zapoznaj się z instrukcjami dotyczącymi migracji istniejącej bazy kodu w celu użycia w [samouczku Migrowanie aplikacji do korzystania](../tutorials/upgrade-to-nullable-references.md)z typów odwołań dopuszczających wartość null.

## <a name="asynchronous-streams"></a>Strumienie asynchroniczne

Począwszy od C# 8,0, można tworzyć strumienie i korzystać z nich asynchronicznie. Metoda zwracająca strumień asynchroniczny ma trzy właściwości:

1. Jest on zadeklarowany za pomocą modyfikatora `async`.
1. Zwraca <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Metoda zawiera instrukcje `yield return`, które zwracają kolejne elementy w strumieniu asynchronicznym.

Zużywanie strumienia asynchronicznego wymaga dodania słowa kluczowego `await` przed słowem kluczowym `foreach` podczas wyliczania elementów strumienia. Dodanie słowa kluczowego `await` wymaga metody, która wylicza strumień asynchroniczny, który ma zostać zadeklarowany za pomocą modyfikatora `async` i zwraca typ dozwolony dla metody `async`. Zwykle oznacza to zwrócenie <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Może to być również <xref:System.Threading.Tasks.ValueTask> lub <xref:System.Threading.Tasks.ValueTask%601>. Metoda może jednocześnie zużywać i generować strumień asynchroniczny, co oznacza, że zwróci <xref:System.Collections.Generic.IAsyncEnumerable%601>. Poniższy kod generuje sekwencję z przedziału od 0 do 19, oczekującą 100 ms między generowaniem każdej liczby:

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

Sekwencję można wyliczyć przy użyciu instrukcji `await foreach`:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Możesz samodzielnie wypróbować strumienie asynchroniczne w naszym samouczku dotyczącym [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Indeksy i zakresy

Indeksy i zakresy zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w sekwencji.

Ten język obsługuje dwa nowe typy i dwa nowe operatory:

- <xref:System.Index?displayProperty=nameWithType> reprezentuje indeks w sekwencji.
- Indeks z operatora końcowego `^`, który określa, że indeks jest względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType> reprezentuje Podzakres sekwencji.
- Operator zakresu `..`, który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od reguł dotyczących indeksów. Rozważ użycie tablicy `sequence`. Indeks `0` jest taki sam jak `sequence[0]`. Indeks `^0` jest taki sam jak `sequence[sequence.Length]`. Należy zauważyć, że `sequence[^0]` generuje wyjątek, tak jak `sequence[sequence.Length]`. Dla dowolnej liczby `n`indeks `^n` jest taka sama jak `sequence.Length - n`.

Zakres określa *początek* i *koniec* zakresu. Początek zakresu jest włączony, ale koniec zakresu jest na wyłączność, co oznacza, że *początek* znajduje się w zakresie, ale *końcowy* nie należy do zakresu. Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres.

Przyjrzyjmy się kilku przykładom. Rozważmy następującą tablicę zawierającą adnotację z jej indeksem od początku i od końca:

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

Możesz pobrać ostatni wyraz z indeksem `^1`:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox". Zawiera `words[1]` do `words[3]`. Element `words[4]` nie należy do zakresu.

```csharp
var quickBrownFox = words[1..4];
```

Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog". Zawiera `words[^2]` i `words[^1]`. `words[^0]` indeksu końcowego nie jest uwzględniony:

```csharp
var lazyDog = words[^2..^0];
```

W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Można również zadeklarować zakresy jako zmienne:

```csharp
Range phrase = 1..4;
```

Zakres może być następnie używany wewnątrz `[` i `]` znaków:

```csharp
var text = words[phrase];
```

Nie tylko tablice obsługują indeksy i zakresy. Można również użyć indeksów i zakresów z [ciągiem](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>lub <xref:System.ReadOnlySpan%601>. Aby uzyskać więcej informacji, zobacz [Obsługa typów indeksów i zakresów](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Więcej informacji o indeksach i zakresach można dowiedzieć się w samouczku dotyczącym [indeksów i zakresów](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Przypisanie do łączenia o wartości null

C#8,0 wprowadza `??=`operatora przypisania łączącego wartości null. Możesz użyć operatora `??=`, aby przypisać wartość jego operandu po lewej stronie tylko wtedy, gdy operand z lewej strony szacuje się `null`.

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Aby uzyskać więcej informacji, zobacz [? =](../language-reference/operators/null-coalescing-operator.md) — artykuł.

## <a name="unmanaged-constructed-types"></a>Niezarządzane typy skonstruowane

W C# 7,3 i starszych, typ skonstruowany (typ, który zawiera co najmniej jeden argument typu) nie może być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md). Począwszy od C# 8,0, skonstruowany typ wartości jest niezarządzany, jeśli zawiera pola tylko typów niezarządzanych.

Na przykład uwzględniając następujące definicje ogólnego typu `Coords<T>`:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

Typ `Coords<int>` jest typem niezarządzanym w C# 8,0 i nowszych. Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Aby uzyskać więcej informacji, zobacz [typy niezarządzane](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>Stackalloc w wyrażeniach zagnieżdżonych

Rozpoczynając od C# 8,0, jeśli wynik wyrażenia [stackalloc](../language-reference/operators/stackalloc.md) ma typ <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, można użyć wyrażenia `stackalloc` w innych wyrażeniach:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Ulepszenie interpolowanych ciągów Verbatim

Kolejność `$` i tokenów `@` w [interpolowanych](../language-reference/tokens/interpolated.md) ciągach Verbatim może być dowolna: zarówno `$@"..."`, jak i `@$"..."` są prawidłowymi interpolowanymi ciągami Verbatim. We wcześniejszych C# wersjach token `$` musi znajdować się przed tokenem `@`.
