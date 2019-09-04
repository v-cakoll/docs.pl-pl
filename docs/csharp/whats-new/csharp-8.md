---
title: Co nowego w C# 8,0 — C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8,0. Ten artykuł jest aktualny w wersji zapoznawczej 5.
ms.date: 09/02/2019
ms.openlocfilehash: 7210f2e978f307b3ecef2eff272fea0d19025de6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252900"
---
# <a name="whats-new-in-c-80"></a>Co nowego w C# 8,0

Istnieje wiele ulepszeń C# języka, który można wypróbować już.

- [Elementy członkowskie tylko do odczytu](#readonly-members)
- [Domyślne elementy członkowskie interfejsu](#default-interface-members)
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
- [Ulepszenie interpolowanych ciągów Verbatim](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> Ten artykuł został ostatnio zaktualizowany do C# wersji 8,0 Preview 5.

W pozostałej części tego artykułu krótko opisano te funkcje. Tam, gdzie są dostępne szczegółowe artykuły, znajdują się linki do samouczków i przeglądów. Te funkcje można eksplorować w środowisku za pomocą `dotnet try` narzędzia globalnego:

1. Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-Samples* .
1. Uruchom `dotnet try`.

## <a name="readonly-members"></a>Elementy członkowskie tylko do odczytu

Można zastosować `readonly` modyfikator do dowolnego elementu członkowskiego struktury. Wskazuje, że element członkowski nie modyfikuje stanu. Jest to bardziej szczegółowe niż stosowanie `readonly` modyfikatora `struct` do deklaracji.  Weź pod uwagę następującą niemodyfikowalną strukturę:

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

Podobnie jak większość struktur, `ToString()` Metoda nie modyfikuje stanu. Można wskazać, że dodając `readonly` modyfikator do `ToString()`deklaracji:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Poprzednia zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp `Distance` do właściwości, która nie jest `readonly`oznaczona:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilator ostrzega o tym, gdy musi utworzyć kopię obronną.  Właściwość nie zmienia stanu, więc możesz naprawić to ostrzeżenie, `readonly` dodając modyfikator do deklaracji: `Distance`

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Należy zauważyć, `readonly` że modyfikator jest konieczny dla właściwości tylko do odczytu. Kompilator nie zakłada `get` , że metody dostępu nie modyfikują stanu; należy zadeklarować `readonly` jawnie. Kompilator wymusza zasadę, której `readonly` elementy członkowskie nie modyfikują stanu. Następująca metoda nie zostanie skompilowana, chyba że zostanie usunięty `readonly` modyfikator:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Ta funkcja umożliwia określenie zamierzonego projektu, aby kompilator mógł go wymusić i dokonać optymalizacji na podstawie tego zamiaru.

## <a name="default-interface-members"></a>Domyślne elementy członkowskie interfejsu

Teraz można dodawać członków do interfejsów i dostarczać implementację dla tych członków. Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach, bez podzielenia zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu. Istniejące implementacje *dziedziczą* implementację domyślną. Ta funkcja umożliwia C# również współdziałanie z interfejsami API przeznaczonymi dla systemu Android lub SWIFT, które obsługują podobne funkcje. Domyślne elementy członkowskie interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".

Domyślne elementy członkowskie interfejsu mają wpływ na wiele scenariuszy i elementów języka. W pierwszym samouczku omówiono [aktualizowanie interfejsu przy użyciu domyślnych implementacji](../tutorials/default-interface-members-versions.md). Inne samouczki i aktualizacje referencyjne są dostępne w czasie do wydania ogólnego.

## <a name="more-patterns-in-more-places"></a>Więcej wzorców w większej liczbie miejsc

**Dopasowanie wzorców** oferuje narzędzia do zapewniania funkcji zależnych od kształtu między powiązanymi, ale różnymi rodzajami danych. C#7,0 wprowadzono składnię dla wzorców typu i wzorców stałych przy użyciu [`is`](../language-reference/keywords/is.md) wyrażenia [`switch`](../language-reference/keywords/switch.md) i instrukcji. Te funkcje przedstawiają pierwsze wstępnie wymagane kroki w kierunku obsługi odmian programistycznych, w których dane i funkcje są aktywne. Gdy branża jest przenoszona do większej liczby mikrousług i architektur opartych na chmurze, inne narzędzia języka są zbędne.

C#8,0 rozwija ten słownik, aby można było używać więcej wyrażeń wzorca w większej liczbie miejsc w kodzie. Te funkcje należy wziąć pod uwagę, gdy dane i funkcje są osobne. Rozważ dopasowanie wzorców, gdy algorytmy zależą od faktu innego niż typ środowiska uruchomieniowego obiektu. Techniki te zapewniają inny sposób tworzenia projektów.

Oprócz nowych wzorców w nowych miejscach, C# 8,0 dodaje **cykliczne wzorce**. Wynikiem dowolnego wyrażenia wzorca jest wyrażenie. Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.

### <a name="switch-expressions"></a>Przełącz wyrażenia

Często instrukcja generuje wartość w każdym z jego `case` bloków. [`switch`](../language-reference/keywords/switch.md) **Wyrażenia Switch** umożliwiają użycie bardziej zwięzłej składni wyrażeń. Jest mniej powtarzające `case` się `break` i słowa kluczowe i mniej nawiasów klamrowych.  Na przykład rozważmy następujące Wyliczenie, które zawiera listę kolorów tęczu:

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

Jeśli aplikacja `RGBColor` definiuje typ, który jest zbudowany `G` `R`ze składników, i `B` , można skonwertować `Rainbow` wartość na wartości RGB przy użyciu następującej metody zawierającej wyrażenie Switch:

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

- Zmienna jest wcześniejsza niż `switch` słowo kluczowe. Inna kolejność ułatwia odróżnienie wyrażenia Switch od instrukcji switch.
- Elementy `case` `=>`i `:` są zamieniane na. Jest to bardziej zwięzłe i intuicyjne.
- Przypadek jest zastępowany `_`odrzuceniem. `default`
- Treść to wyrażenia, a nie instrukcje.

Kontrast, który ma odpowiedni kod przy użyciu instrukcji `switch` klasycznej:

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

**Wzorzec właściwości** pozwala dopasować się do właściwości badanego obiektu. Rozważmy witrynę handlu elektronicznego, która musi obliczać podatek od sprzedaży na podstawie adresu kupującego. To obliczenie nie jest podstawową odpowiedzialnością `Address` klasy. Zostanie ona zmieniona z upływem czasu, co prawdopodobnie częściej niż zmienia format adresu. Podatek od sprzedaży zależy `State` od właściwości adresu. Poniższa metoda używa wzorca właściwości do obliczania podatku od adresu i ceny:

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

Niektóre typy obejmują `Deconstruct` metodę, która dekonstrukcjauje swoje właściwości do zmiennych dyskretnych. Gdy metoda jest dostępna, można użyć **wzorców pozycyjnych** do inspekcji właściwości obiektu i używania tych właściwości dla wzorca. `Deconstruct`  Rozważmy następujące `Point` klasy, które `Deconstruct` obejmują metodę tworzenia zmiennych dyskretnych dla `X` i `Y`:

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

Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i. `y` Następnie używa `when` klauzuli do `Quadrant` określenia punktu:

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

Odrzuć wzorzec w poprzednim przełączniku dopasowuje się `x` , `y` gdy lub ma wartość 0, ale nie oba. Wyrażenie Switch musi utworzyć wartość lub zgłosić wyjątek. Jeśli żaden z przypadków nie jest zgodny, wyrażenie Switch zgłasza wyjątek. Kompilator generuje ostrzeżenie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu Switch.

Techniki dopasowania wzorców można eksplorować w tym [zaawansowanym samouczku dotyczącym dopasowania wzorców](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Korzystanie z deklaracji

**Deklaracja using** jest deklaracją zmiennej poprzedzoną `using` słowem kluczowym. Informuje kompilator, że zadeklarowana zmienna powinna zostać usunięta na końcu otaczającego zakresu. Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody. To koniec zakresu, w którym `file` jest zadeklarowany. Poprzedni kod jest odpowiednikiem poniższego kodu, który używa klasycznej [instrukcji using](../language-reference/keywords/using-statement.md):

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego skojarzonego `using` z instrukcją.

W obu przypadkach kompilator generuje wywołanie `Dispose()`. Kompilator generuje błąd, jeśli wyrażenie w `using` instrukcji nie jest jednorazowe.

## <a name="static-local-functions"></a>Statyczne funkcje lokalne

Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (nie dotyczy) żadnych zmiennych z zakresu otaczającego. Spowoduje to wygenerowanie `CS8421`, "statyczna funkcja lokalna nie może zawierać odwołania \<do zmiennej >". 

Rozważmy następujący kod. Funkcja `LocalFunction` lokalna uzyskuje dostęp do zmiennej `y`zadeklarowanej w zakresie otaczającym (Metoda `M`). W związku`static` z tym niemożnazadeklarować`LocalFunction` z modyfikatorem:

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

Deklaracja z modyfikatorem nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>. `struct` `ref` W związku z tym, `ref struct` aby można było usunąć element, musi on mieć `void Dispose()` dostępną metodę. Dotyczy to również `readonly ref struct` deklaracji.

## <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

Wewnątrz bezwartościowego kontekstu adnotacji Każda zmienna typu referencyjnego jest uważana za **typ referencyjny, który nie ma wartości null**. Aby wskazać, że zmienna może mieć wartość null, należy dołączyć nazwę typu z, `?` aby zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null**.

W przypadku typów referencyjnych, które nie mają wartości null, kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null, gdy zostanie zadeklarowana. Pola muszą być inicjowane podczas konstruowania. Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie do któregokolwiek z dostępnych konstruktorów lub inicjatora. Ponadto nie można przypisać wartości, która może mieć wartość null.

Typy odwołań dopuszczających wartość null nie są sprawdzane w celu zapewnienia, że nie są przypisane ani zainicjowane do wartości null. Jednak kompilator używa analizy przepływu, aby upewnić się, że jakakolwiek zmienna typu referencyjnego null jest sprawdzana pod kątem wartości null przed uzyskaniem dostępu lub przypisaniem do niezerowego typu odwołania.

Więcej informacji na temat funkcji można znaleźć w omówieniu [typów referencyjnych dopuszczających wartość null](../nullable-references.md). Wypróbuj go samodzielnie w nowej aplikacji w tym [samouczku typów odwołań dopuszczających wartość null](../tutorials/nullable-reference-types.md). Zapoznaj się z instrukcjami dotyczącymi migracji istniejącej bazy kodu w celu użycia w [samouczku Migrowanie aplikacji do korzystania](../tutorials/upgrade-to-nullable-references.md)z typów odwołań dopuszczających wartość null.

## <a name="asynchronous-streams"></a>Strumienie asynchroniczne

Począwszy od C# 8,0, można tworzyć strumienie i korzystać z nich asynchronicznie. Metoda zwracająca strumień asynchroniczny ma trzy właściwości:

1. Jest on zadeklarowany z `async` modyfikatorem.
1. Zwraca wartość <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Metoda zawiera `yield return` instrukcje do zwrócenia kolejnych elementów w strumieniu asynchronicznym.

Użycie strumienia asynchronicznego wymaga dodania `await` słowa kluczowego `foreach` przed słowem kluczowym podczas wyliczania elementów strumienia. Dodanie słowa kluczowego wymaga metody, która wylicza strumień asynchroniczny, który ma zostać zadeklarowany `async` z modyfikatorem i zwraca typ dozwolony dla `async` metody. `await` Zwykle oznacza to zwrócenie <xref:System.Threading.Tasks.Task> lub. <xref:System.Threading.Tasks.Task%601> Może być <xref:System.Threading.Tasks.ValueTask> również lub <xref:System.Threading.Tasks.ValueTask%601>. Metoda może jednocześnie zużywać i generować strumień asynchroniczny, co oznacza, że zwróci <xref:System.Collections.Generic.IAsyncEnumerable%601>. Poniższy kod generuje sekwencję z przedziału od 0 do 19, oczekującą 100 ms między generowaniem każdej liczby:

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

Sekwencję można wyliczyć przy użyciu `await foreach` instrukcji:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Możesz samodzielnie wypróbować strumienie asynchroniczne w naszym samouczku dotyczącym [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Indeksy i zakresy

Zakresy i indeksy zapewniają zwięzłą składnię do określania podzakresów w tablicy, <xref:System.Span%601>lub. <xref:System.ReadOnlySpan%601>

Ten język obsługuje dwa nowe typy i dwa nowe operatory:

- <xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.
- `^` Operator, który określa, że indeks jest względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType>reprezentuje Podzakres sekwencji.
- Operator zakresu (`..`), który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od reguł dotyczących indeksów. Weź pod uwagę `sequence`tablicę. Indeks jest taki sam jak `sequence[0]`. `0` Indeks jest taki sam jak `sequence[sequence.Length]`. `^0` Należy pamiętać `sequence[^0]` , że generuje wyjątek, podobnie jak `sequence[sequence.Length]` . Dla dowolnej liczby `n`indeks `^n` jest taki sam jak `sequence.Length - n`.

Zakres określa *początek* i *koniec* zakresu. Początek zakresu jest włączony, ale koniec zakresu jest na wyłączność, co oznacza, że *początek* znajduje się w zakresie, ale *koniec* nie jest uwzględniony w zakresie. Zakres `[0..^0]` reprezentuje cały zakres, tak jak `[0..sequence.Length]` reprezentuje cały zakres. 

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

Możesz pobrać ostatni wyraz z `^1` indeksem:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox". Zawiera `words[1]` .`words[3]` Element `words[4]` nie należy do zakresu.

```csharp
var quickBrownFox = words[1..4];
```

Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog". Obejmuje `words[^2]` i .`words[^1]` Indeks `words[^0]` końcowy nie jest uwzględniony:

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

Zakres może być następnie używany wewnątrz `[` znaków i: `]`

```csharp
var text = words[phrase];
```

Więcej informacji o indeksach i zakresach można dowiedzieć się w samouczku dotyczącym [indeksów i zakresów](../tutorials/ranges-indexes.md).

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Ulepszenie interpolowanych ciągów Verbatim

`@$"..."` `$@"..."` [](../language-reference/tokens/interpolated.md) Kolejność tokenów `@`iw interpolowanych ciągach Verbatim może być dowolna: oba i są prawidłowymi interpolowanymi ciągami Verbatim. `$` We wcześniejszych C# wersjach `$` token `@` musi znajdować się przed tokenem.
