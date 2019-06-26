---
title: Co nowego C# 8.0 - C# przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8.0. W tym artykule jest aktualny w wersji zapoznawczej 5.
ms.date: 02/12/2019
ms.openlocfilehash: 962829b68c5d02c3a7e563a00d391c4698024d47
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397770"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="dba43-104">Co nowego C# 8.0</span><span class="sxs-lookup"><span data-stu-id="dba43-104">What's new in C# 8.0</span></span>

<span data-ttu-id="dba43-105">Istnieje wiele ulepszeń C# języka, które możesz wypróbować już.</span><span class="sxs-lookup"><span data-stu-id="dba43-105">There are many enhancements to the C# language that you can try out already.</span></span> 

- [<span data-ttu-id="dba43-106">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dba43-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="dba43-107">Domyślni członkowie interfejsu</span><span class="sxs-lookup"><span data-stu-id="dba43-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="dba43-108">[Rozszerzenia dopasowywania wzorca](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="dba43-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="dba43-109">Wyrażenia Switch</span><span class="sxs-lookup"><span data-stu-id="dba43-109">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="dba43-110">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="dba43-110">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="dba43-111">Wzorce krotki</span><span class="sxs-lookup"><span data-stu-id="dba43-111">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="dba43-112">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="dba43-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="dba43-113">Za pomocą deklaracji</span><span class="sxs-lookup"><span data-stu-id="dba43-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="dba43-114">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="dba43-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="dba43-115">Struktury ref możliwe do rozporządzania</span><span class="sxs-lookup"><span data-stu-id="dba43-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="dba43-116">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="dba43-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="dba43-117">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="dba43-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="dba43-118">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="dba43-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="dba43-119">W tym artykule został ostatnio zaktualizowany na potrzeby C# 8.0 w wersji zapoznawczej 5.</span><span class="sxs-lookup"><span data-stu-id="dba43-119">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="dba43-120">Te funkcje można krótko opisano w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="dba43-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="dba43-121">Jeżeli dostępne są szczegółowe artykuły, znajdują się linki do omówienia i samouczki.</span><span class="sxs-lookup"><span data-stu-id="dba43-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="dba43-122">Możesz zapoznać się z tych funkcji w środowisku przy użyciu `dotnet try` narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="dba43-122">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="dba43-123">Zainstaluj [spróbuj dotnet](https://github.com/dotnet/try/blob/master/README.md#setup) narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="dba43-123">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="dba43-124">Klonuj [dotnet/try-samples](https://github.com/dotnet/try-samples) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="dba43-124">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="dba43-125">Ustaw bieżący katalog *csharp8* podkatalog *try-samples* repozytorium.</span><span class="sxs-lookup"><span data-stu-id="dba43-125">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="dba43-126">Uruchom `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="dba43-126">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="dba43-127">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dba43-127">Readonly members</span></span>

<span data-ttu-id="dba43-128">Można zastosować `readonly` modyfikator do wszystkich elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="dba43-128">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="dba43-129">Oznacza to element członkowski nie powoduje modyfikacji stanu.</span><span class="sxs-lookup"><span data-stu-id="dba43-129">It indicates that the member does not modify state.</span></span> <span data-ttu-id="dba43-130">Jest bardziej szczegółowe niż stosowanie `readonly` modyfikatora `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="dba43-130">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="dba43-131">Należy rozważyć następujące struktury mutable:</span><span class="sxs-lookup"><span data-stu-id="dba43-131">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="dba43-132">Większość struktur, takich jak `ToString()` metoda nie powoduje modyfikacji stanu.</span><span class="sxs-lookup"><span data-stu-id="dba43-132">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="dba43-133">Może sygnalizować, dodając `readonly` modyfikatora deklaracji `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="dba43-133">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="dba43-134">Zmian poprzednim generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp do `Distance` właściwość, która nie jest oznaczony jako `readonly`:</span><span class="sxs-lookup"><span data-stu-id="dba43-134">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="dba43-135">Kompilator ostrzega o tym, kiedy zachodzi potrzeba utworzenia kopii obrony.</span><span class="sxs-lookup"><span data-stu-id="dba43-135">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="dba43-136">`Distance` Właściwości nie zmienia stanu, dzięki czemu możesz rozwiązać tego ostrzeżenia, dodając `readonly` modyfikatora deklaracji:</span><span class="sxs-lookup"><span data-stu-id="dba43-136">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="dba43-137">Należy zauważyć, że `readonly` modyfikator jest konieczne na właściwością tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="dba43-137">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="dba43-138">Kompilator nie zakłada `get` akcesory nie należy modyfikować stanu; należy zadeklarować `readonly` jawnie.</span><span class="sxs-lookup"><span data-stu-id="dba43-138">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="dba43-139">Kompilator wymusić regułę, która `readonly` elementów członkowskich, nie należy modyfikować stanu.</span><span class="sxs-lookup"><span data-stu-id="dba43-139">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="dba43-140">Poniższa metoda nie zostanie skompilowany, chyba że usuniesz `readonly` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="dba43-140">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="dba43-141">Ta funkcja umożliwia określanie zgodną z planem projektu, dzięki czemu kompilator może go wymusić i wprowadzić optymalizacje oparte na tym przeznaczeniem.</span><span class="sxs-lookup"><span data-stu-id="dba43-141">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="dba43-142">Domyślni członkowie interfejsu</span><span class="sxs-lookup"><span data-stu-id="dba43-142">Default interface members</span></span>

<span data-ttu-id="dba43-143">Można teraz dodawać członków do interfejsów i zapewniać implementację dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="dba43-143">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="dba43-144">Tej funkcji języka umożliwia autorom interfejsu API Dodaj metody do interfejsu w nowszych wersjach bez przerywania źródła lub zgodność binarną przy użyciu istniejących implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dba43-144">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="dba43-145">Istniejących implementacji *dziedziczą* domyślną implementację.</span><span class="sxs-lookup"><span data-stu-id="dba43-145">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="dba43-146">Ta funkcja umożliwia również C# pod kątem współdziałania z interfejsów API przeznaczonych dla systemu Android lub Swift, który obsługuje podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="dba43-146">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="dba43-147">Domyślne elementy członkowskie z interfejsu też włączyć scenariusze podobne do funkcji języka "cech".</span><span class="sxs-lookup"><span data-stu-id="dba43-147">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="dba43-148">Domyślni członkowie interfejsu wpływa na wiele scenariuszy i elementy języka.</span><span class="sxs-lookup"><span data-stu-id="dba43-148">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="dba43-149">Nasz pierwszy samouczek obejmuje [aktualizowanie interfejs za pomocą domyślnej implementacji](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-149">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="dba43-150">Inne samouczki i dokumentacja aktualizacje zostaną wprowadzone w termin głównym wydaniu.</span><span class="sxs-lookup"><span data-stu-id="dba43-150">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="dba43-151">Więcej wzorców w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="dba43-151">More patterns in more places</span></span>

<span data-ttu-id="dba43-152">**Dopasowanie wzorca** udostępnia narzędzia do zapewnienia funkcji zależnych od kształtu powiązane, ale różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="dba43-152">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="dba43-153">C#Składnia dla typów deseni i wzory stałych 7.0 wprowadza się przy użyciu [ `is` ](../language-reference/keywords/is.md) wyrażenia i [ `switch` ](../language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="dba43-153">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="dba43-154">Te funkcje reprezentowane pierwszych kroków niepewnego kierunku obsługi paradygmatów programowania, w których funkcji i danych na żywo od siebie.</span><span class="sxs-lookup"><span data-stu-id="dba43-154">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="dba43-155">Przemieszcza się w branży więcej mikrousług i innymi architektury oparte na chmurze, potrzebne są inne narzędzia języka.</span><span class="sxs-lookup"><span data-stu-id="dba43-155">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="dba43-156">C#8.0 rozwija tego słownika, aby można było używać więcej wzorzec wyrażenia w wielu miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="dba43-156">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="dba43-157">Gdy Twoje dane i funkcje są oddzielone, należy wziąć pod uwagę te funkcje.</span><span class="sxs-lookup"><span data-stu-id="dba43-157">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="dba43-158">Należy wziąć pod uwagę w przypadku algorytmów zależą od faktów, innej niż typ środowiska uruchomieniowego obiektu dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="dba43-158">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="dba43-159">Metody te zawierają express projekty w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="dba43-159">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="dba43-160">Oprócz nowych wzorców w nowych miejscach C# dodaje 8.0 **wzorców cyklicznego**.</span><span class="sxs-lookup"><span data-stu-id="dba43-160">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="dba43-161">Wynik dowolne wyrażenie wzorca jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="dba43-161">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="dba43-162">Wzorzec cyklicznego jest po prostu wyrażenie wzorzec, które są stosowane do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="dba43-162">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="dba43-163">Wyrażenia Switch</span><span class="sxs-lookup"><span data-stu-id="dba43-163">switch expressions</span></span>

<span data-ttu-id="dba43-164">Często [ `switch` ](../language-reference/keywords/switch.md) instrukcja generuje wartości w każdym z jego `case` bloków.</span><span class="sxs-lookup"><span data-stu-id="dba43-164">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="dba43-165">**Przełącz wyrażenia** umożliwiają korzystanie z bardziej zwięzłym składni wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="dba43-165">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="dba43-166">Istnieją mniej powtarzalne `case` i `break` słów kluczowych i mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="dba43-166">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="dba43-167">Na przykład należy wziąć pod uwagę następujące wyliczenia, który wyświetla kolory tęczowego:</span><span class="sxs-lookup"><span data-stu-id="dba43-167">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="dba43-168">Jeśli definicja aplikacji `RGBColor` typu, który jest konstruowany z `R`, `G` i `B` składników, można przekonwertować `Rainbow` wartość do jego wartości RGB, przy użyciu następującej metody zawierającą wyrażenie switch:</span><span class="sxs-lookup"><span data-stu-id="dba43-168">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="dba43-169">Istnieje kilka ulepszeń składni tutaj:</span><span class="sxs-lookup"><span data-stu-id="dba43-169">There are several syntax improvements here:</span></span>

- <span data-ttu-id="dba43-170">Zmienna znajduje się przed `switch` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="dba43-170">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="dba43-171">Inną kolejność ułatwia wizualnie do odróżnienia wyrażenia switch z instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="dba43-171">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="dba43-172">`case` i `:` elementy są zastępowane `=>`.</span><span class="sxs-lookup"><span data-stu-id="dba43-172">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="dba43-173">Jest bardziej zwięzłe i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="dba43-173">It's more concise and intuitive.</span></span>
- <span data-ttu-id="dba43-174">`default` Przypadek jest zastępowany `_` odrzucić.</span><span class="sxs-lookup"><span data-stu-id="dba43-174">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="dba43-175">Jednostki są wyrażeniami, nie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="dba43-175">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="dba43-176">Natomiast, za pomocą klasycznego kodu równoważne `switch` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="dba43-176">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="dba43-177">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="dba43-177">Property patterns</span></span>

<span data-ttu-id="dba43-178">**Wzorzec właściwość** pozwala do dopasowania właściwości obiektu badania.</span><span class="sxs-lookup"><span data-stu-id="dba43-178">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="dba43-179">Należy wziąć pod uwagę witryny handlu elektronicznego, który należy obliczyć podatku od sprzedaży, w oparciu o adres kupującego.</span><span class="sxs-lookup"><span data-stu-id="dba43-179">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="dba43-180">Obliczenie jest nie odpowiedzialność za rdzeń `Address` klasy.</span><span class="sxs-lookup"><span data-stu-id="dba43-180">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="dba43-181">Zostanie on zmieniony wraz z upływem czasu, prawdopodobnie częściej niż zmiany formatu adresu.</span><span class="sxs-lookup"><span data-stu-id="dba43-181">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="dba43-182">Kwota podatku od sprzedaży, który jest zależny od `State` właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="dba43-182">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="dba43-183">Poniższa metoda używa wzorca właściwości można obliczyć podatku od sprzedaży, adres i ceny:</span><span class="sxs-lookup"><span data-stu-id="dba43-183">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="dba43-184">Dopasowanie wzorca tworzy zwarta składnia dla wyrażania ten algorytm.</span><span class="sxs-lookup"><span data-stu-id="dba43-184">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="dba43-185">Wzorce krotki</span><span class="sxs-lookup"><span data-stu-id="dba43-185">Tuple patterns</span></span>

<span data-ttu-id="dba43-186">Niektóre algorytmy są zależne od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="dba43-186">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="dba43-187">**Wzorce krotki** zezwala na przełączanie na podstawie wielu wartości wyrażonej w postaci [krotki](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-187">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="dba43-188">Poniższy kod pokazuje wyrażenie switch dla gry *rock, dokument, nożyczek*:</span><span class="sxs-lookup"><span data-stu-id="dba43-188">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="dba43-189">Komunikaty wskazują zwycięzca.</span><span class="sxs-lookup"><span data-stu-id="dba43-189">The messages indicate the winner.</span></span> <span data-ttu-id="dba43-190">W przypadku odrzucenia reprezentuje trzy kombinacje w celach węzłów lub inne dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="dba43-190">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="dba43-191">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="dba43-191">Positional patterns</span></span>

<span data-ttu-id="dba43-192">Niektóre typy obejmują `Deconstruct` metodę, która deconstructs jego właściwości w zmiennych dyskretnego.</span><span class="sxs-lookup"><span data-stu-id="dba43-192">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="dba43-193">Gdy `Deconstruct` metody jest dostępny, można użyć **pozycyjne wzorców** sprawdzić właściwości obiektu i korzystać z tych właściwości dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="dba43-193">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="dba43-194">Należy wziąć pod uwagę następujące `Point` klasy, która obejmuje `Deconstruct` metodę, aby utworzyć zmienne dyskretnego `X` i `Y`:</span><span class="sxs-lookup"><span data-stu-id="dba43-194">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="dba43-195">Ponadto należy wziąć pod uwagę następujące wyliczenia, który reprezentuje różne stanowiska quadrant:</span><span class="sxs-lookup"><span data-stu-id="dba43-195">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="dba43-196">Używa następującej metody **pozycyjne wzorzec** do wyodrębnienia wartości `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="dba43-196">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="dba43-197">Następnie używa `when` klauzuli, aby określić `Quadrant` punktu:</span><span class="sxs-lookup"><span data-stu-id="dba43-197">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="dba43-198">Podczas pasuje do wzorca odrzucania w poprzednim przełącznika albo `x` lub `y` jest 0, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="dba43-198">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="dba43-199">Wyrażenie switch musi mieć wartość albo zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dba43-199">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="dba43-200">Wyrażenie switch zgłasza wyjątek, jeśli żaden z przypadków są zgodne.</span><span class="sxs-lookup"><span data-stu-id="dba43-200">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="dba43-201">Kompilator generuje ostrzeżenia dla Ciebie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="dba43-201">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="dba43-202">Możesz zapoznać się z technik, w tym dopasowania do wzorca [zaawansowane samouczek na temat dopasowywania do wzorca](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-202">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="dba43-203">Za pomocą deklaracji</span><span class="sxs-lookup"><span data-stu-id="dba43-203">using declarations</span></span>

<span data-ttu-id="dba43-204">A **użycie — deklaracja** jest deklaracja zmiennej jest poprzedzony `using` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="dba43-204">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="dba43-205">Go informuje kompilator, że na końcu zasięgu powinny zostać zlikwidowane deklarowanej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dba43-205">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="dba43-206">Na przykład rozważmy następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="dba43-206">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="dba43-207">W powyższym przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="dba43-207">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="dba43-208">To już koniec zakresu, w którym `file` jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="dba43-208">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="dba43-209">Powyższy kod jest równoważny z następującym kodem przy użyciu klasycznej [za pomocą instrukcji](../language-reference/keywords/using-statement.md) instrukcji:</span><span class="sxs-lookup"><span data-stu-id="dba43-209">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>

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

<span data-ttu-id="dba43-210">W powyższym przykładzie plik zostanie usunięty skojarzony zamykającego nawiasu klamrowego `using` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="dba43-210">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="dba43-211">W obu przypadkach, kompilator generuje wywołanie `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="dba43-211">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="dba43-212">Kompilator generuje błąd, jeśli wyrażenie za pomocą instrukcji nie jest możliwe do likwidacji.</span><span class="sxs-lookup"><span data-stu-id="dba43-212">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="dba43-213">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="dba43-213">Static local functions</span></span>

<span data-ttu-id="dba43-214">Teraz możesz dodać `static` modyfikatora funkcje lokalne, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołanie w) wszystkie zmienne z otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="dba43-214">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="dba43-215">Ten sposób generuje `CS8421`, "statycznych funkcji lokalnej nie może zawierać odwołanie do \<zmienna >."</span><span class="sxs-lookup"><span data-stu-id="dba43-215">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="dba43-216">Rozważmy poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="dba43-216">Consider the following code.</span></span> <span data-ttu-id="dba43-217">Funkcja lokalna `LocalFunction` uzyskuje dostęp do zmiennej `y`, zadeklarowana w otaczającym zakresie (metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="dba43-217">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="dba43-218">W związku z tym `LocalFunction` nie może być zadeklarowana z `static` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="dba43-218">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="dba43-219">Poniższy kod zawiera funkcję statyczną lokalnego.</span><span class="sxs-lookup"><span data-stu-id="dba43-219">The following code contains a static local function.</span></span> <span data-ttu-id="dba43-220">Może być statyczne, ponieważ system nie ma dostępu do żadnych zmiennych w obejmującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="dba43-220">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="dba43-221">Struktury ref możliwe do rozporządzania</span><span class="sxs-lookup"><span data-stu-id="dba43-221">Disposable ref structs</span></span>

<span data-ttu-id="dba43-222">A `struct` zadeklarowane za pomocą `ref` modyfikator nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="dba43-222">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="dba43-223">W związku z tym aby umożliwić `ref struct` usuwana, musi mieć dostępne `void Dispose()` metody.</span><span class="sxs-lookup"><span data-stu-id="dba43-223">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="dba43-224">Dotyczy to również `readonly ref struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="dba43-224">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="dba43-225">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="dba43-225">Nullable reference types</span></span>

<span data-ttu-id="dba43-226">W kontekście annotation dopuszczający wartość null, dowolnej zmiennej typu odwołania jest uważany za **Typ referencyjny niedopuszczające wartości null**.</span><span class="sxs-lookup"><span data-stu-id="dba43-226">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="dba43-227">Jeśli chcesz wskazać, że zmienna może mieć wartości null, należy dołączyć nazwę typu z `?` Aby zadeklarować zmienną jako **typu dopuszczającego wartość null odwołania**.</span><span class="sxs-lookup"><span data-stu-id="dba43-227">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="dba43-228">Dla typów odwołań kolumną kompilator używa analizę przepływu, aby upewnić się, że zmienne lokalne są inicjowane na wartość inną niż null, gdy zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="dba43-228">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="dba43-229">Pola muszą być zainicjowane w trakcie konstruowania.</span><span class="sxs-lookup"><span data-stu-id="dba43-229">Fields must be initialized during construction.</span></span> <span data-ttu-id="dba43-230">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiony przez wywołanie do dowolnych dostępnych konstruktorów lub inicjatora.</span><span class="sxs-lookup"><span data-stu-id="dba43-230">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="dba43-231">Ponadto typy odwołań kolumną nie można przypisać wartość, która może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="dba43-231">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="dba43-232">Typy dopuszczające wartości null odwołań nie są sprawdzany w celu zapewnienia ich nie są przypisywany lub zainicjowany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="dba43-232">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="dba43-233">Jednak kompilator używa analizę przepływu, aby upewnić się, że jakakolwiek zmienna typu odwołania dopuszczającego wartość null jest sprawdzana względem o wartości null, przed jego dostępny lub przypisane do typu odwołania niedopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="dba43-233">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="dba43-234">Dowiedz się więcej na temat funkcji w przeglądzie [typy dopuszczające wartości null odwołań](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-234">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="dba43-235">Samodzielnie wypróbować tę funkcję w nowej aplikacji, w tym [samouczek typy dopuszczające wartości null odwołanie](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-235">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="dba43-236">Dowiedz się więcej o kroki, aby migrować dane istniejącej bazy kodu w zapewnienie użytkowania typy dopuszczające wartości null odwołań w [migrowania aplikacji do użycia odwołania nullable typy samouczek](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-236">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="dba43-237">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="dba43-237">Asynchronous streams</span></span>

<span data-ttu-id="dba43-238">Począwszy od C# 8.0, możesz utworzyć i wykorzystują strumienie asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="dba43-238">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="dba43-239">Metody, która zwraca strumień asynchroniczny ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="dba43-239">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="dba43-240">Jest zadeklarowana za pomocą `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="dba43-240">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="dba43-241">Zwraca <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dba43-241">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="dba43-242">Metoda zawiera `yield return` instrukcji, aby zwrócić kolejne elementy w strumieniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="dba43-242">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="dba43-243">Korzystanie z strumień asynchroniczny wymaga dodania `await` — słowo kluczowe przed `foreach` — słowo kluczowe podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="dba43-243">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="dba43-244">Dodawanie `await` — słowo kluczowe wymaga metody, która wylicza strumień asynchroniczny, które mają zostać zadeklarowane za pomocą `async` modyfikator i zwracać typ, jest dozwolony dla `async` metody.</span><span class="sxs-lookup"><span data-stu-id="dba43-244">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="dba43-245">Zwykle oznacza to, zwracając <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="dba43-245">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="dba43-246">Może to być także <xref:System.Threading.Tasks.ValueTask> lub <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="dba43-246">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="dba43-247">Metoda może wykorzystywać i generuje strumień asynchroniczny, oznacza to, co spowoduje przywrócenie <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dba43-247">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="dba43-248">Poniższy kod generuje sekwencji z zakresu od 0 do 19 oczekiwania 100 ms między generowania poszczególnych liczb:</span><span class="sxs-lookup"><span data-stu-id="dba43-248">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="dba43-249">Należy wyliczyć, przy użyciu sekwencji `await foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="dba43-249">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="dba43-250">Możesz spróbować asynchronicznymi strumieniami samodzielnie w naszym samouczku [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-250">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="dba43-251">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="dba43-251">Indices and ranges</span></span>

<span data-ttu-id="dba43-252">Zakresy i indeksów, które zapewniają zwięzłą składnię do określania podzakresów w tablicy, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="dba43-252">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="dba43-253">Obsługa tego języka opiera się na dwóch nowych typów i dwóch nowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="dba43-253">This language support relies on two new types, and two new operators.</span></span>
- <span data-ttu-id="dba43-254"><xref:System.Index?displayProperty=nameWithType> reprezentuje indeks do sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dba43-254"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="dba43-255">`^` Operatora, który określa, że indeks względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dba43-255">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="dba43-256"><xref:System.Range?displayProperty=nameWithType> reprezentuje zakres sub sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dba43-256"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="dba43-257">Operator zakresu (`..`), który określa początek i koniec zakresu, co jest operandów.</span><span class="sxs-lookup"><span data-stu-id="dba43-257">The Range operator (`..`), which specifies the start and end of a range as is operands.</span></span>

<span data-ttu-id="dba43-258">Zacznijmy od reguł dla indeksów.</span><span class="sxs-lookup"><span data-stu-id="dba43-258">Let's start with the rules for indexes.</span></span> <span data-ttu-id="dba43-259">Należy wziąć pod uwagę tablicy `sequence`.</span><span class="sxs-lookup"><span data-stu-id="dba43-259">Consider an array `sequence`.</span></span> <span data-ttu-id="dba43-260">`0` Indeksu jest taka sama jak `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="dba43-260">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="dba43-261">`^0` Indeksu jest taka sama jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="dba43-261">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="dba43-262">Należy pamiętać, że `sequence[^0]` zgłosić wyjątek, podobnie jak `sequence[sequence.Length]` jest.</span><span class="sxs-lookup"><span data-stu-id="dba43-262">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="dba43-263">Dowolną liczbą `n`, indeks `^n` jest taka sama jak `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="dba43-263">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="dba43-264">Określa zakres *start* i *zakończenia* zakresu.</span><span class="sxs-lookup"><span data-stu-id="dba43-264">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="dba43-265">Początek zakresu (włącznie), ale koniec zakresu jest wzajemnie, co oznacza *start* znajduje się w zakresie, ale *zakończenia* nie wchodzi w zakres.</span><span class="sxs-lookup"><span data-stu-id="dba43-265">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="dba43-266">Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="dba43-266">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="dba43-267">Spójrzmy na kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="dba43-267">Let's look at a few examples.</span></span> <span data-ttu-id="dba43-268">Rozważmy następującą tablicę, oznaczony za pomocą jej indeks, od samego początku i na końcu:</span><span class="sxs-lookup"><span data-stu-id="dba43-268">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="dba43-269">Możesz pobrać ostatni wyraz z `^1` indeksu:</span><span class="sxs-lookup"><span data-stu-id="dba43-269">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="dba43-270">Poniższy kod tworzy Podzakres przy użyciu słowa "szybkie", "brown" i "fox".</span><span class="sxs-lookup"><span data-stu-id="dba43-270">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="dba43-271">Zawiera on `words[1]` za pośrednictwem `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="dba43-271">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="dba43-272">Element `words[4]` nie znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="dba43-272">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="dba43-273">Poniższy kod tworzy Podzakres "z opóźnieniem" i "dog".</span><span class="sxs-lookup"><span data-stu-id="dba43-273">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="dba43-274">Zawiera on `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="dba43-274">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="dba43-275">Indeks końcowy `words[^0]` nie jest dołączony:</span><span class="sxs-lookup"><span data-stu-id="dba43-275">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="dba43-276">Poniższe przykłady tworzą zakresy, które są otwarte zakończył się dla początkowego i końcowego:</span><span class="sxs-lookup"><span data-stu-id="dba43-276">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="dba43-277">Zakresy można również zadeklarować jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="dba43-277">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="dba43-278">Zakres następnie można używać wewnątrz `[` i `]` znaków:</span><span class="sxs-lookup"><span data-stu-id="dba43-278">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="dba43-279">Możesz zapoznać się więcej na temat indeksów i zakresów adresów w tym samouczku na [indeksów i zakresy](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="dba43-279">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>
