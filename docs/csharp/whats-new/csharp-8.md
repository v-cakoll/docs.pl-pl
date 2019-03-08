---
title: Co nowego C# 8.0 - C# przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8.0. W tym artykule jest aktualny i 2 w wersji zapoznawczej.
ms.date: 02/12/2019
ms.openlocfilehash: 3a19cc7ffae706769cf1b1a19fdaff7c7cdc07fc
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674448"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="ae705-104">Co nowego C# 8.0</span><span class="sxs-lookup"><span data-stu-id="ae705-104">What's new in C# 8.0</span></span>

<span data-ttu-id="ae705-105">Istnieje wiele ulepszeń C# języka, które możesz wypróbować już w wersji zapoznawczej 2.</span><span class="sxs-lookup"><span data-stu-id="ae705-105">There are many enhancements to the C# language that you can try out already with preview 2.</span></span> <span data-ttu-id="ae705-106">Dostępne są następujące nowe funkcje dodane w wersji zapoznawczej 2:</span><span class="sxs-lookup"><span data-stu-id="ae705-106">The new features added in preview 2 are:</span></span>

- <span data-ttu-id="ae705-107">[Rozszerzenia dopasowywania wzorca](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="ae705-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="ae705-108">Wyrażenia Switch</span><span class="sxs-lookup"><span data-stu-id="ae705-108">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="ae705-109">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="ae705-109">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="ae705-110">Wzorce krotki</span><span class="sxs-lookup"><span data-stu-id="ae705-110">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="ae705-111">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="ae705-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="ae705-112">Za pomocą deklaracji</span><span class="sxs-lookup"><span data-stu-id="ae705-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="ae705-113">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="ae705-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="ae705-114">Struktury ref możliwe do rozporządzania</span><span class="sxs-lookup"><span data-stu-id="ae705-114">Disposable ref structs</span></span>](#disposable-ref-structs)

<span data-ttu-id="ae705-115">Następujące funkcje języka najpierw pojawiła się C# 8.0 w wersji zapoznawczej 1:</span><span class="sxs-lookup"><span data-stu-id="ae705-115">The following language features first appeared in C# 8.0 preview 1:</span></span>

- [<span data-ttu-id="ae705-116">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="ae705-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="ae705-117">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="ae705-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="ae705-118">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="ae705-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="ae705-119">W tym artykule został ostatnio zaktualizowany na potrzeby C# 8.0 w wersji preview 2.</span><span class="sxs-lookup"><span data-stu-id="ae705-119">This article was last updated for C# 8.0 preview 2.</span></span>

<span data-ttu-id="ae705-120">Te funkcje można krótko opisano w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="ae705-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="ae705-121">Jeżeli dostępne są szczegółowe artykuły, znajdują się linki do omówienia i samouczki.</span><span class="sxs-lookup"><span data-stu-id="ae705-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="ae705-122">Więcej wzorców w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="ae705-122">More patterns in more places</span></span>

<span data-ttu-id="ae705-123">**Dopasowanie wzorca** udostępnia narzędzia do zapewnienia funkcji zależnych od kształtu powiązane, ale różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="ae705-123">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="ae705-124">C#Składnia dla typów deseni i wzory stałych 7.0 wprowadza się przy użyciu [ `is` ](../language-reference/keywords/is.md) wyrażenia i [ `switch` ](../language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae705-124">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="ae705-125">Te funkcje reprezentowane pierwszych kroków niepewnego kierunku obsługi paradygmatów programowania, w których funkcji i danych na żywo od siebie.</span><span class="sxs-lookup"><span data-stu-id="ae705-125">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="ae705-126">Przemieszcza się w branży więcej mikrousług i innymi architektury oparte na chmurze, potrzebne są inne narzędzia języka.</span><span class="sxs-lookup"><span data-stu-id="ae705-126">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="ae705-127">C#8.0 rozwija tego słownika, aby można było używać więcej wzorzec wyrażenia w wielu miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ae705-127">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="ae705-128">Gdy Twoje dane i funkcje są oddzielone, należy wziąć pod uwagę te funkcje.</span><span class="sxs-lookup"><span data-stu-id="ae705-128">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="ae705-129">Należy wziąć pod uwagę w przypadku algorytmów zależą od faktów, innej niż typ środowiska uruchomieniowego obiektu dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="ae705-129">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="ae705-130">Metody te zawierają express projekty w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="ae705-130">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="ae705-131">Oprócz nowych wzorców w nowych miejscach C# dodaje 8.0 **wzorców cyklicznego**.</span><span class="sxs-lookup"><span data-stu-id="ae705-131">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="ae705-132">Wynik dowolne wyrażenie wzorca jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="ae705-132">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="ae705-133">Wzorzec cyklicznego jest po prostu wyrażenie wzorzec, które są stosowane do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="ae705-133">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="ae705-134">Wyrażenia Switch</span><span class="sxs-lookup"><span data-stu-id="ae705-134">switch expressions</span></span>

<span data-ttu-id="ae705-135">Często [ `switch` ](../language-reference/keywords/switch.md) instrukcja generuje wartości w każdym z jego `case` bloków.</span><span class="sxs-lookup"><span data-stu-id="ae705-135">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="ae705-136">**Przełącz wyrażenia** umożliwiają korzystanie z bardziej zwięzłym składni wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="ae705-136">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="ae705-137">Istnieją mniej powtarzalne `case` i `break` słów kluczowych i mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="ae705-137">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="ae705-138">Na przykład należy wziąć pod uwagę następujące wyliczenia, który wyświetla kolory tęczowego:</span><span class="sxs-lookup"><span data-stu-id="ae705-138">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="ae705-139">Można przekonwertować `Rainbow` wartość do jego wartości RGB, przy użyciu następującej metody zawierającą wyrażenie switch:</span><span class="sxs-lookup"><span data-stu-id="ae705-139">You could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="ae705-140">Istnieje kilka ulepszeń składni tutaj:</span><span class="sxs-lookup"><span data-stu-id="ae705-140">There are several syntax improvements here:</span></span>

- <span data-ttu-id="ae705-141">Zmienna znajduje się przed `switch` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ae705-141">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="ae705-142">Inną kolejność ułatwia wizualnie do odróżnienia wyrażenia switch z instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="ae705-142">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="ae705-143">`case` i `:` elementy są zastępowane `=>`.</span><span class="sxs-lookup"><span data-stu-id="ae705-143">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="ae705-144">Jest bardziej zwięzłe i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="ae705-144">It's more concise and intuitive.</span></span>
- <span data-ttu-id="ae705-145">`default` Przypadek jest zastępowany `_` odrzucić.</span><span class="sxs-lookup"><span data-stu-id="ae705-145">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="ae705-146">Jednostki są wyrażeniami, nie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae705-146">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="ae705-147">Natomiast, za pomocą klasycznego kodu równoważne `switch` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="ae705-147">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor fromRainbowClassic(Rainbow colorBand)
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

### <a name="property-patterns"></a><span data-ttu-id="ae705-148">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="ae705-148">Property patterns</span></span>

<span data-ttu-id="ae705-149">**Wzorzec właściwość** pozwala do dopasowania właściwości obiektu badania.</span><span class="sxs-lookup"><span data-stu-id="ae705-149">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="ae705-150">Należy wziąć pod uwagę witryny handlu elektronicznego, który należy obliczyć podatku od sprzedaży, w oparciu o adres kupującego.</span><span class="sxs-lookup"><span data-stu-id="ae705-150">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="ae705-151">Obliczenie jest nie odpowiedzialność za rdzeń `Address` klasy.</span><span class="sxs-lookup"><span data-stu-id="ae705-151">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="ae705-152">Zostanie on zmieniony wraz z upływem czasu, prawdopodobnie częściej niż zmiany formatu adresu.</span><span class="sxs-lookup"><span data-stu-id="ae705-152">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="ae705-153">Kwota podatku od sprzedaży, który jest zależny od `State` właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="ae705-153">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="ae705-154">Poniższa metoda używa wzorca właściwości można obliczyć podatku od sprzedaży, adres i ceny:</span><span class="sxs-lookup"><span data-stu-id="ae705-154">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="ae705-155">Dopasowanie wzorca tworzy zwarta składnia dla wyrażania ten algorytm.</span><span class="sxs-lookup"><span data-stu-id="ae705-155">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="ae705-156">Wzorce krotki</span><span class="sxs-lookup"><span data-stu-id="ae705-156">Tuple patterns</span></span>

<span data-ttu-id="ae705-157">Niektóre algorytmy są zależne od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ae705-157">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="ae705-158">**Wzorce krotki** zezwala na przełączanie na podstawie wielu wartości wyrażonej w postaci [krotki](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ae705-158">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="ae705-159">Poniższy kod pokazuje wyrażenie switch dla gry *rock, dokument, nożyczek*:</span><span class="sxs-lookup"><span data-stu-id="ae705-159">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="ae705-160">Komunikaty wskazują zwycięzca.</span><span class="sxs-lookup"><span data-stu-id="ae705-160">The messages indicate the winner.</span></span> <span data-ttu-id="ae705-161">W przypadku odrzucenia reprezentuje trzy kombinacje w celach węzłów lub inne dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="ae705-161">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="ae705-162">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="ae705-162">Positional patterns</span></span>

<span data-ttu-id="ae705-163">Niektóre typy obejmują `Deconstruct` metodę, która deconstructs jego właściwości w zmiennych dyskretnego.</span><span class="sxs-lookup"><span data-stu-id="ae705-163">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="ae705-164">Gdy `Deconstruct` metody jest dostępny, można użyć **pozycyjne wzorców** sprawdzić właściwości obiektu i korzystać z tych właściwości dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="ae705-164">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="ae705-165">Należy wziąć pod uwagę następujące `Point` klasy, która obejmuje `Deconstruct` metodę, aby utworzyć zmienne dyskretnego `X` i `Y`:</span><span class="sxs-lookup"><span data-stu-id="ae705-165">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="ae705-166">Używa następującej metody **pozycyjne wzorzec** do wyodrębnienia wartości `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="ae705-166">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="ae705-167">Następnie używa `when` klauzuli, aby określić quadrant punktu:</span><span class="sxs-lookup"><span data-stu-id="ae705-167">Then, it uses a `when` clause to determine the quadrant of the point:</span></span>

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

<span data-ttu-id="ae705-168">Wzorca odrzucania w poprzednim przełącznika pasuje, podczas albo `x` lub `y`, ale nie obu wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="ae705-168">The discard pattern in the preceding switch matches when either `x` or `y`, but not both, is 0.</span></span> <span data-ttu-id="ae705-169">Wyrażenie switch musi mieć wartość albo zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ae705-169">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="ae705-170">Wyrażenie switch zgłasza wyjątek, jeśli żaden z przypadków są zgodne.</span><span class="sxs-lookup"><span data-stu-id="ae705-170">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="ae705-171">Kompilator generuje ostrzeżenia dla Ciebie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ae705-171">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

## <a name="using-declarations"></a><span data-ttu-id="ae705-172">Za pomocą deklaracji</span><span class="sxs-lookup"><span data-stu-id="ae705-172">using declarations</span></span>

<span data-ttu-id="ae705-173">A **użycie — deklaracja** jest deklaracja zmiennej jest poprzedzony `using` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ae705-173">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="ae705-174">Go informuje kompilator, że na końcu zasięgu powinny zostać zlikwidowane deklarowanej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ae705-174">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="ae705-175">Na przykład rozważmy następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="ae705-175">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="ae705-176">W powyższym przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="ae705-176">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="ae705-177">To już koniec zakresu, w którym `file` jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="ae705-177">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="ae705-178">Powyższy kod jest równoważny z następującym kodem przy użyciu klasycznej [za pomocą instrukcji](../language-reference/keywords/using-statement.md) instrukcji:</span><span class="sxs-lookup"><span data-stu-id="ae705-178">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>


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

<span data-ttu-id="ae705-179">W powyższym przykładzie plik zostanie usunięty skojarzony zamykającego nawiasu klamrowego `using` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="ae705-179">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="ae705-180">W obu przypadkach, kompilator generuje wywołanie `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="ae705-180">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="ae705-181">Kompilator generuje błąd, jeśli wyrażenie za pomocą instrukcji nie jest możliwe do likwidacji.</span><span class="sxs-lookup"><span data-stu-id="ae705-181">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="ae705-182">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="ae705-182">Static local functions</span></span>

<span data-ttu-id="ae705-183">Teraz możesz dodać `static` modyfikatora funkcje lokalne, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołanie w) wszystkie zmienne z otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ae705-183">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="ae705-184">Ten sposób generuje `CS8421`, "statycznych funkcji lokalnej nie może zawierać odwołanie do <variable>."</span><span class="sxs-lookup"><span data-stu-id="ae705-184">Doing so generates `CS8421`, "A static local function can't contain a reference to <variable>."</span></span> 

<span data-ttu-id="ae705-185">Rozważmy poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="ae705-185">Consider the following code.</span></span> <span data-ttu-id="ae705-186">Funkcja lokalna `LocalFunction` uzyskuje dostęp do zmiennej `y`, zadeklarowana w otaczającym zakresie (metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="ae705-186">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="ae705-187">W związku z tym `LocalFunction` nie może być zadeklarowana z `static` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="ae705-187">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="ae705-188">Poniższy kod zawiera funkcję statyczną lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ae705-188">The following code contains a static local function.</span></span> <span data-ttu-id="ae705-189">Może być statyczne, ponieważ system nie ma dostępu do żadnych zmiennych w obejmującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="ae705-189">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="ae705-190">Struktury ref możliwe do rozporządzania</span><span class="sxs-lookup"><span data-stu-id="ae705-190">Disposable ref structs</span></span>

<span data-ttu-id="ae705-191">A `struct` zadeklarowane za pomocą `ref` modyfikator nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="ae705-191">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="ae705-192">W związku z tym aby umożliwić `ref struct` usuwana, musi mieć dostępne `void Dispose()` metody.</span><span class="sxs-lookup"><span data-stu-id="ae705-192">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="ae705-193">Dotyczy to również `readonly ref struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ae705-193">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="ae705-194">Typy dopuszczające wartości null odwołań</span><span class="sxs-lookup"><span data-stu-id="ae705-194">Nullable reference types</span></span>

<span data-ttu-id="ae705-195">W kontekście annotation dopuszczający wartość null, dowolnej zmiennej typu odwołania jest uważany za **Typ referencyjny niedopuszczające wartości null**.</span><span class="sxs-lookup"><span data-stu-id="ae705-195">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="ae705-196">Jeśli chcesz wskazać, że zmienna może mieć wartości null, należy dołączyć nazwę typu z `?` Aby zadeklarować zmienną jako **typu dopuszczającego wartość null odwołania**.</span><span class="sxs-lookup"><span data-stu-id="ae705-196">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="ae705-197">Dla typów odwołań kolumną kompilator używa analizę przepływu, aby upewnić się, że zmienne lokalne są inicjowane na wartość inną niż null, gdy zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="ae705-197">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="ae705-198">Pola muszą być zainicjowane w trakcie konstruowania.</span><span class="sxs-lookup"><span data-stu-id="ae705-198">Fields must be initialized during construction.</span></span> <span data-ttu-id="ae705-199">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiony przez wywołanie do dowolnych dostępnych konstruktorów lub inicjatora.</span><span class="sxs-lookup"><span data-stu-id="ae705-199">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="ae705-200">Ponadto typy odwołań kolumną nie można przypisać wartość, która może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="ae705-200">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="ae705-201">Typy dopuszczające wartości null odwołań nie są sprawdzany w celu zapewnienia ich nie są przypisywany lub zainicjowany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="ae705-201">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="ae705-202">Jednak kompilator używa analizę przepływu, aby upewnić się, że jakakolwiek zmienna typu odwołania dopuszczającego wartość null jest sprawdzana względem o wartości null, przed jego dostępny lub przypisane do typu odwołania niedopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="ae705-202">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="ae705-203">Dowiedz się więcej na temat funkcji w przeglądzie [typy dopuszczające wartości null odwołań](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="ae705-203">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="ae705-204">Samodzielnie wypróbować tę funkcję w nowej aplikacji, w tym [samouczek typy dopuszczające wartości null odwołanie](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae705-204">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="ae705-205">Dowiedz się więcej o kroki, aby migrować dane istniejącej bazy kodu w zapewnienie użytkowania typy dopuszczające wartości null odwołań w [migrowania aplikacji do użycia odwołania nullable typy samouczek](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="ae705-205">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="ae705-206">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="ae705-206">Asynchronous streams</span></span>

<span data-ttu-id="ae705-207">Począwszy od C# 8.0, możesz utworzyć i wykorzystują strumienie asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="ae705-207">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="ae705-208">Metody, która zwraca strumień asynchroniczny ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="ae705-208">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="ae705-209">Jest zadeklarowana za pomocą `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="ae705-209">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="ae705-210">Zwraca <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ae705-210">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="ae705-211">Metoda zawiera `yield return` instrukcji, aby zwrócić kolejne elementy w strumieniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="ae705-211">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="ae705-212">Korzystanie z strumień asynchroniczny wymaga dodania `await` — słowo kluczowe przed `foreach` — słowo kluczowe podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="ae705-212">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="ae705-213">Dodawanie `await` — słowo kluczowe wymaga metody, która wylicza strumień asynchroniczny, które mają zostać zadeklarowane za pomocą `async` modyfikator i zwracać typ, jest dozwolony dla `async` metody.</span><span class="sxs-lookup"><span data-stu-id="ae705-213">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="ae705-214">Zwykle oznacza to, zwracając <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ae705-214">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ae705-215">Może to być także <xref:System.Threading.Tasks.ValueTask> lub <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="ae705-215">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="ae705-216">Metoda może wykorzystywać i generuje strumień asynchroniczny, oznacza to, co spowoduje przywrócenie <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ae705-216">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="ae705-217">Poniższy kod generuje sekwencji z zakresu od 0 do 19 oczekiwania 100 ms między generowania poszczególnych liczb:</span><span class="sxs-lookup"><span data-stu-id="ae705-217">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="ae705-218">Należy wyliczyć, przy użyciu sekwencji `await foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="ae705-218">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="ae705-219">Możesz spróbować asynchronicznymi strumieniami samodzielnie w naszym samouczku [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="ae705-219">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="ae705-220">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="ae705-220">Indices and ranges</span></span>

<span data-ttu-id="ae705-221">Zakresy i indeksów, które zapewniają zwięzłą składnię do określania podzakresów w tablicy, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="ae705-221">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="ae705-222">Można określić indeksu **od końca**.</span><span class="sxs-lookup"><span data-stu-id="ae705-222">You can specify an index **from the end**.</span></span> <span data-ttu-id="ae705-223">Należy określić **od końca** przy użyciu `^` operatora.</span><span class="sxs-lookup"><span data-stu-id="ae705-223">You specify **from the end** using the `^` operator.</span></span> <span data-ttu-id="ae705-224">Znasz `array[2]` oznacza element "2 od samego początku".</span><span class="sxs-lookup"><span data-stu-id="ae705-224">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="ae705-225">Teraz `array[^2]` oznacza, że element "2 od końca".</span><span class="sxs-lookup"><span data-stu-id="ae705-225">Now, `array[^2]` means the element "2 from the end".</span></span> <span data-ttu-id="ae705-226">Indeks `^0` oznacza "koniec" lub indeks, który następuje po ostatnim elemencie.</span><span class="sxs-lookup"><span data-stu-id="ae705-226">The index `^0` means "the end", or the index that follows the last element.</span></span>

<span data-ttu-id="ae705-227">Można określić **zakres** z **operatora zakresu**: `..`.</span><span class="sxs-lookup"><span data-stu-id="ae705-227">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="ae705-228">Na przykład `0..^0` określa cały zakres tablicy: 0 od początku do, z wyłączeniem 0 od końca.</span><span class="sxs-lookup"><span data-stu-id="ae705-228">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="ae705-229">Jeden z operandów może używać "start" lub "end".</span><span class="sxs-lookup"><span data-stu-id="ae705-229">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="ae705-230">Ponadto można pominąć oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ae705-230">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="ae705-231">Wartości domyślne to `0` dla indeksu początkowego i `^0` dla indeksu zakończenia.</span><span class="sxs-lookup"><span data-stu-id="ae705-231">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

<span data-ttu-id="ae705-232">Spójrzmy na kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="ae705-232">Let's look at a few examples.</span></span> <span data-ttu-id="ae705-233">Rozważmy następującą tablicę, oznaczony za pomocą jej indeks, od samego początku i na końcu:</span><span class="sxs-lookup"><span data-stu-id="ae705-233">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="ae705-234">Indeks każdego elementu wspiera koncepcję "od rozpoczęcia" i "od końca", a zakresy są nie do końca zakresu.</span><span class="sxs-lookup"><span data-stu-id="ae705-234">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="ae705-235">"Start" całej tablicy jest pierwszym elementem.</span><span class="sxs-lookup"><span data-stu-id="ae705-235">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="ae705-236">"Koniec" całej tablicy jest *przeszłości* po ostatnim elemencie.</span><span class="sxs-lookup"><span data-stu-id="ae705-236">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="ae705-237">Możesz pobrać ostatni wyraz z `^1` indeksu:</span><span class="sxs-lookup"><span data-stu-id="ae705-237">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="ae705-238">Poniższy kod tworzy Podzakres przy użyciu słowa "szybkie", "brown" i "fox".</span><span class="sxs-lookup"><span data-stu-id="ae705-238">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="ae705-239">Zawiera on `words[1]` za pośrednictwem `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="ae705-239">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="ae705-240">Element `words[4]` nie znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="ae705-240">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="ae705-241">Poniższy kod tworzy Podzakres "z opóźnieniem" i "dog".</span><span class="sxs-lookup"><span data-stu-id="ae705-241">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="ae705-242">Zawiera on `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="ae705-242">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="ae705-243">Indeks końcowy `words[^0]` nie jest dołączony:</span><span class="sxs-lookup"><span data-stu-id="ae705-243">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="ae705-244">Poniższe przykłady tworzą zakresy, które są otwarte zakończył się dla początkowego i końcowego:</span><span class="sxs-lookup"><span data-stu-id="ae705-244">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

<span data-ttu-id="ae705-245">Zakresy można również zadeklarować jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="ae705-245">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="ae705-246">Zakres następnie można używać wewnątrz `[` i `]` znaków:</span><span class="sxs-lookup"><span data-stu-id="ae705-246">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```
