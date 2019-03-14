---
title: Co nowego C# 8.0 - C# przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8.0. W tym artykule jest aktualny i 2 w wersji zapoznawczej.
ms.date: 02/12/2019
ms.openlocfilehash: d723bdf55104fa0a8d4a8e20c60a9debb26c7886
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788599"
---
# <a name="whats-new-in-c-80"></a>Co nowego C# 8.0

Istnieje wiele ulepszeń C# języka, które możesz wypróbować już w wersji zapoznawczej 2. Dostępne są następujące nowe funkcje dodane w wersji zapoznawczej 2:

- [Rozszerzenia dopasowywania wzorca](#more-patterns-in-more-places):
  * [Wyrażenia Switch](#switch-expressions)
  * [Wzorce właściwości](#property-patterns)
  * [Wzorce krotki](#tuple-patterns)
  * [Wzorce pozycyjne](#positional-patterns)
- [Za pomocą deklaracji](#using-declarations)
- [Statyczne funkcje lokalne](#static-local-functions)
- [Struktury ref możliwe do rozporządzania](#disposable-ref-structs)

Następujące funkcje języka najpierw pojawiła się C# 8.0 w wersji zapoznawczej 1:

- [Typy referencyjne dopuszczające wartość null](#nullable-reference-types)
- [Asynchroniczne strumienie](#asynchronous-streams)
- [Indeksy i zakresy](#indices-and-ranges)

> [!NOTE]
> W tym artykule został ostatnio zaktualizowany na potrzeby C# 8.0 w wersji preview 2.

Te funkcje można krótko opisano w dalszej części tego artykułu. Jeżeli dostępne są szczegółowe artykuły, znajdują się linki do omówienia i samouczki.

## <a name="more-patterns-in-more-places"></a>Więcej wzorców w większej liczbie miejsc

**Dopasowanie wzorca** udostępnia narzędzia do zapewnienia funkcji zależnych od kształtu powiązane, ale różnych typów danych. C#Składnia dla typów deseni i wzory stałych 7.0 wprowadza się przy użyciu [ `is` ](../language-reference/keywords/is.md) wyrażenia i [ `switch` ](../language-reference/keywords/switch.md) instrukcji. Te funkcje reprezentowane pierwszych kroków niepewnego kierunku obsługi paradygmatów programowania, w których funkcji i danych na żywo od siebie. Przemieszcza się w branży więcej mikrousług i innymi architektury oparte na chmurze, potrzebne są inne narzędzia języka.

C#8.0 rozwija tego słownika, aby można było używać więcej wzorzec wyrażenia w wielu miejscach w kodzie. Gdy Twoje dane i funkcje są oddzielone, należy wziąć pod uwagę te funkcje. Należy wziąć pod uwagę w przypadku algorytmów zależą od faktów, innej niż typ środowiska uruchomieniowego obiektu dopasowywania do wzorca. Metody te zawierają express projekty w inny sposób.

Oprócz nowych wzorców w nowych miejscach C# dodaje 8.0 **wzorców cyklicznego**. Wynik dowolne wyrażenie wzorca jest wyrażeniem. Wzorzec cyklicznego jest po prostu wyrażenie wzorzec, które są stosowane do danych wyjściowych innego wyrażenia wzorca.

### <a name="switch-expressions"></a>Wyrażenia Switch

Często [ `switch` ](../language-reference/keywords/switch.md) instrukcja generuje wartości w każdym z jego `case` bloków. **Przełącz wyrażenia** umożliwiają korzystanie z bardziej zwięzłym składni wyrażeń. Istnieją mniej powtarzalne `case` i `break` słów kluczowych i mniej nawiasów klamrowych.  Na przykład należy wziąć pod uwagę następujące wyliczenia, który wyświetla kolory tęczowego:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Blue,
    Indigo,
    Violet
}
```

Można przekonwertować `Rainbow` wartość do jego wartości RGB, przy użyciu następującej metody zawierającą wyrażenie switch:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Istnieje kilka ulepszeń składni tutaj:

- Zmienna znajduje się przed `switch` — słowo kluczowe. Inną kolejność ułatwia wizualnie do odróżnienia wyrażenia switch z instrukcji switch.
- `case` i `:` elementy są zastępowane `=>`. Jest bardziej zwięzłe i intuicyjne.
- `default` Przypadek jest zastępowany `_` odrzucić.
- Jednostki są wyrażeniami, nie instrukcji.

Natomiast, za pomocą klasycznego kodu równoważne `switch` instrukcji:

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

**Wzorzec właściwość** pozwala do dopasowania właściwości obiektu badania. Należy wziąć pod uwagę witryny handlu elektronicznego, który należy obliczyć podatku od sprzedaży, w oparciu o adres kupującego. Obliczenie jest nie odpowiedzialność za rdzeń `Address` klasy. Zostanie on zmieniony wraz z upływem czasu, prawdopodobnie częściej niż zmiany formatu adresu. Kwota podatku od sprzedaży, który jest zależny od `State` właściwości adresu. Poniższa metoda używa wzorca właściwości można obliczyć podatku od sprzedaży, adres i ceny:

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

Dopasowanie wzorca tworzy zwarta składnia dla wyrażania ten algorytm.

### <a name="tuple-patterns"></a>Wzorce krotki

Niektóre algorytmy są zależne od wielu danych wejściowych. **Wzorce krotki** zezwala na przełączanie na podstawie wielu wartości wyrażonej w postaci [krotki](../tuples.md).  Poniższy kod pokazuje wyrażenie switch dla gry *rock, dokument, nożyczek*:

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

Komunikaty wskazują zwycięzca. W przypadku odrzucenia reprezentuje trzy kombinacje w celach węzłów lub inne dane wejściowe tekstu.

### <a name="positional-patterns"></a>Wzorce pozycyjne

Niektóre typy obejmują `Deconstruct` metodę, która deconstructs jego właściwości w zmiennych dyskretnego. Gdy `Deconstruct` metody jest dostępny, można użyć **pozycyjne wzorców** sprawdzić właściwości obiektu i korzystać z tych właściwości dla wzorca.  Należy wziąć pod uwagę następujące `Point` klasy, która obejmuje `Deconstruct` metodę, aby utworzyć zmienne dyskretnego `X` i `Y`:

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

Używa następującej metody **pozycyjne wzorzec** do wyodrębnienia wartości `x` i `y`. Następnie używa `when` klauzuli, aby określić quadrant punktu:

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

Wzorca odrzucania w poprzednim przełącznika pasuje, podczas albo `x` lub `y`, ale nie obu wynosi 0. Wyrażenie switch musi mieć wartość albo zgłosić wyjątek. Wyrażenie switch zgłasza wyjątek, jeśli żaden z przypadków są zgodne. Kompilator generuje ostrzeżenia dla Ciebie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu przełącznika.

## <a name="using-declarations"></a>Za pomocą deklaracji

A **użycie — deklaracja** jest deklaracja zmiennej jest poprzedzony `using` — słowo kluczowe. Go informuje kompilator, że na końcu zasięgu powinny zostać zlikwidowane deklarowanej zmiennej. Na przykład rozważmy następujący kod, który zapisuje plik tekstowy:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

W powyższym przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody. To już koniec zakresu, w którym `file` jest zadeklarowana. Powyższy kod jest równoważny z następującym kodem przy użyciu klasycznej [za pomocą instrukcji](../language-reference/keywords/using-statement.md) instrukcji:


```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

W powyższym przykładzie plik zostanie usunięty skojarzony zamykającego nawiasu klamrowego `using` osiągnięta zostanie instrukcja.

W obu przypadkach, kompilator generuje wywołanie `Dispose()`. Kompilator generuje błąd, jeśli wyrażenie za pomocą instrukcji nie jest możliwe do likwidacji.

## <a name="static-local-functions"></a>Statyczne funkcje lokalne

Teraz możesz dodać `static` modyfikatora funkcje lokalne, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołanie w) wszystkie zmienne z otaczającego zakresu. Ten sposób generuje `CS8421`, "statycznych funkcji lokalnej nie może zawierać odwołanie do <variable>." 

Rozważmy poniższy kod. Funkcja lokalna `LocalFunction` uzyskuje dostęp do zmiennej `y`, zadeklarowana w otaczającym zakresie (metoda `M`). W związku z tym `LocalFunction` nie może być zadeklarowana z `static` modyfikator:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Poniższy kod zawiera funkcję statyczną lokalnego. Może być statyczne, ponieważ system nie ma dostępu do żadnych zmiennych w obejmującym zakresie:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Struktury ref możliwe do rozporządzania

A `struct` zadeklarowane za pomocą `ref` modyfikator nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>. W związku z tym aby umożliwić `ref struct` usuwana, musi mieć dostępne `void Dispose()` metody. Dotyczy to również `readonly ref struct` deklaracji.

## <a name="nullable-reference-types"></a>Typy dopuszczające wartości null odwołań

W kontekście annotation dopuszczający wartość null, dowolnej zmiennej typu odwołania jest uważany za **Typ referencyjny niedopuszczające wartości null**. Jeśli chcesz wskazać, że zmienna może mieć wartości null, należy dołączyć nazwę typu z `?` Aby zadeklarować zmienną jako **typu dopuszczającego wartość null odwołania**.

Dla typów odwołań kolumną kompilator używa analizę przepływu, aby upewnić się, że zmienne lokalne są inicjowane na wartość inną niż null, gdy zadeklarowana. Pola muszą być zainicjowane w trakcie konstruowania. Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiony przez wywołanie do dowolnych dostępnych konstruktorów lub inicjatora. Ponadto typy odwołań kolumną nie można przypisać wartość, która może mieć wartości null.

Typy dopuszczające wartości null odwołań nie są sprawdzany w celu zapewnienia ich nie są przypisywany lub zainicjowany do wartości null. Jednak kompilator używa analizę przepływu, aby upewnić się, że jakakolwiek zmienna typu odwołania dopuszczającego wartość null jest sprawdzana względem o wartości null, przed jego dostępny lub przypisane do typu odwołania niedopuszczające wartości null.

Dowiedz się więcej na temat funkcji w przeglądzie [typy dopuszczające wartości null odwołań](../nullable-references.md). Samodzielnie wypróbować tę funkcję w nowej aplikacji, w tym [samouczek typy dopuszczające wartości null odwołanie](../tutorials/nullable-reference-types.md). Dowiedz się więcej o kroki, aby migrować dane istniejącej bazy kodu w zapewnienie użytkowania typy dopuszczające wartości null odwołań w [migrowania aplikacji do użycia odwołania nullable typy samouczek](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Asynchroniczne strumienie

Począwszy od C# 8.0, możesz utworzyć i wykorzystują strumienie asynchronicznie. Metody, która zwraca strumień asynchroniczny ma trzy właściwości:

1. Jest zadeklarowana za pomocą `async` modyfikator.
1. Zwraca <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Metoda zawiera `yield return` instrukcji, aby zwrócić kolejne elementy w strumieniu asynchronicznym.

Korzystanie z strumień asynchroniczny wymaga dodania `await` — słowo kluczowe przed `foreach` — słowo kluczowe podczas wyliczania elementów strumienia. Dodawanie `await` — słowo kluczowe wymaga metody, która wylicza strumień asynchroniczny, które mają zostać zadeklarowane za pomocą `async` modyfikator i zwracać typ, jest dozwolony dla `async` metody. Zwykle oznacza to, zwracając <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Może to być także <xref:System.Threading.Tasks.ValueTask> lub <xref:System.Threading.Tasks.ValueTask%601>. Metoda może wykorzystywać i generuje strumień asynchroniczny, oznacza to, co spowoduje przywrócenie <xref:System.Collections.Generic.IAsyncEnumerable%601>. Poniższy kod generuje sekwencji z zakresu od 0 do 19 oczekiwania 100 ms między generowania poszczególnych liczb:

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

Należy wyliczyć, przy użyciu sekwencji `await foreach` instrukcji:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Możesz spróbować asynchronicznymi strumieniami samodzielnie w naszym samouczku [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Indeksy i zakresy

Zakresy i indeksów, które zapewniają zwięzłą składnię do określania podzakresów w tablicy, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>.

Można określić indeksu **od końca**. Należy określić **od końca** przy użyciu `^` operatora. Znasz `array[2]` oznacza element "2 od samego początku". Teraz `array[^2]` oznacza, że element "2 od końca". Indeks `^0` oznacza "koniec" lub indeks, który następuje po ostatnim elemencie.

Można określić **zakres** z **operatora zakresu**: `..`. Na przykład `0..^0` określa cały zakres tablicy: 0 od początku do, z wyłączeniem 0 od końca. Jeden z operandów może używać "start" lub "end". Ponadto można pominąć oba operandy. Wartości domyślne to `0` dla indeksu początkowego i `^0` dla indeksu zakończenia.

Spójrzmy na kilka przykładów. Rozważmy następującą tablicę, oznaczony za pomocą jej indeks, od samego początku i na końcu:

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
};
```

Indeks każdego elementu wspiera koncepcję "od rozpoczęcia" i "od końca", a zakresy są nie do końca zakresu. "Start" całej tablicy jest pierwszym elementem. "Koniec" całej tablicy jest *przeszłości* po ostatnim elemencie.

Możesz pobrać ostatni wyraz z `^1` indeksu:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Poniższy kod tworzy Podzakres przy użyciu słowa "szybkie", "brown" i "fox". Zawiera on `words[1]` za pośrednictwem `words[3]`. Element `words[4]` nie znajduje się w zakresie.

```csharp
var quickBrownFox = words[1..4];
```

Poniższy kod tworzy Podzakres "z opóźnieniem" i "dog". Zawiera on `words[^2]` i `words[^1]`. Indeks końcowy `words[^0]` nie jest dołączony:

```csharp
var lazyDog = words[^2..^0];
```

Poniższe przykłady tworzą zakresy, które są otwarte zakończył się dla początkowego i końcowego:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

Zakresy można również zadeklarować jako zmienne:

```csharp
Range phrase = 1..4;
```

Zakres następnie można używać wewnątrz `[` i `]` znaków:

```csharp
var text = words[phrase];
```
