---
title: Co nowego w C# 8,0 — C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8,0. Ten artykuł jest aktualny w wersji zapoznawczej 5.
ms.date: 02/12/2019
ms.openlocfilehash: bf67baba926effd012ae01d3d802ba921e41ad5a
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363897"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="1321f-104">Co nowego w C# 8,0</span><span class="sxs-lookup"><span data-stu-id="1321f-104">What's new in C# 8.0</span></span>

<span data-ttu-id="1321f-105">Istnieje wiele ulepszeń C# języka, który można wypróbować już.</span><span class="sxs-lookup"><span data-stu-id="1321f-105">There are many enhancements to the C# language that you can try out already.</span></span> 

- [<span data-ttu-id="1321f-106">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1321f-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="1321f-107">Domyślne elementy członkowskie interfejsu</span><span class="sxs-lookup"><span data-stu-id="1321f-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="1321f-108">[Ulepszenia dopasowania wzorców](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="1321f-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="1321f-109">Przełącz wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1321f-109">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="1321f-110">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="1321f-110">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="1321f-111">Wzorce krotek</span><span class="sxs-lookup"><span data-stu-id="1321f-111">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="1321f-112">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="1321f-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="1321f-113">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="1321f-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="1321f-114">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="1321f-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="1321f-115">Nierozporządzalne struktury ref</span><span class="sxs-lookup"><span data-stu-id="1321f-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="1321f-116">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="1321f-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="1321f-117">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1321f-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="1321f-118">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="1321f-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="1321f-119">Ten artykuł został ostatnio zaktualizowany do C# wersji 8,0 Preview 5.</span><span class="sxs-lookup"><span data-stu-id="1321f-119">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="1321f-120">W pozostałej części tego artykułu krótko opisano te funkcje.</span><span class="sxs-lookup"><span data-stu-id="1321f-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="1321f-121">Tam, gdzie są dostępne szczegółowe artykuły, znajdują się linki do samouczków i przeglądów.</span><span class="sxs-lookup"><span data-stu-id="1321f-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="1321f-122">Te funkcje można eksplorować w środowisku za pomocą `dotnet try` narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="1321f-122">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="1321f-123">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="1321f-123">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="1321f-124">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="1321f-124">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="1321f-125">Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="1321f-125">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="1321f-126">Uruchom `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="1321f-126">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="1321f-127">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1321f-127">Readonly members</span></span>

<span data-ttu-id="1321f-128">Można zastosować `readonly` modyfikator do dowolnego elementu członkowskiego struktury.</span><span class="sxs-lookup"><span data-stu-id="1321f-128">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="1321f-129">Wskazuje, że element członkowski nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="1321f-129">It indicates that the member does not modify state.</span></span> <span data-ttu-id="1321f-130">Jest to bardziej szczegółowe niż stosowanie `readonly` modyfikatora `struct` do deklaracji.</span><span class="sxs-lookup"><span data-stu-id="1321f-130">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="1321f-131">Weź pod uwagę następującą niemodyfikowalną strukturę:</span><span class="sxs-lookup"><span data-stu-id="1321f-131">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="1321f-132">Podobnie jak większość struktur, `ToString()` Metoda nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="1321f-132">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="1321f-133">Można wskazać, że dodając `readonly` modyfikator do `ToString()`deklaracji:</span><span class="sxs-lookup"><span data-stu-id="1321f-133">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="1321f-134">Poprzednia zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp `Distance` do właściwości, która nie jest `readonly`oznaczona:</span><span class="sxs-lookup"><span data-stu-id="1321f-134">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="1321f-135">Kompilator ostrzega o tym, gdy musi utworzyć kopię obronną.</span><span class="sxs-lookup"><span data-stu-id="1321f-135">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="1321f-136">Właściwość nie zmienia stanu, więc możesz naprawić to ostrzeżenie, `readonly` dodając modyfikator do deklaracji: `Distance`</span><span class="sxs-lookup"><span data-stu-id="1321f-136">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="1321f-137">Należy zauważyć, `readonly` że modyfikator jest konieczny dla właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1321f-137">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="1321f-138">Kompilator nie zakłada `get` , że metody dostępu nie modyfikują stanu; należy zadeklarować `readonly` jawnie.</span><span class="sxs-lookup"><span data-stu-id="1321f-138">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="1321f-139">Kompilator wymusza zasadę, której `readonly` elementy członkowskie nie modyfikują stanu.</span><span class="sxs-lookup"><span data-stu-id="1321f-139">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="1321f-140">Następująca metoda nie zostanie skompilowana, chyba że zostanie usunięty `readonly` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="1321f-140">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="1321f-141">Ta funkcja umożliwia określenie zamierzonego projektu, aby kompilator mógł go wymusić i dokonać optymalizacji na podstawie tego zamiaru.</span><span class="sxs-lookup"><span data-stu-id="1321f-141">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="1321f-142">Domyślne elementy członkowskie interfejsu</span><span class="sxs-lookup"><span data-stu-id="1321f-142">Default interface members</span></span>

<span data-ttu-id="1321f-143">Teraz można dodawać członków do interfejsów i dostarczać implementację dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="1321f-143">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="1321f-144">Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach, bez podzielenia zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1321f-144">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="1321f-145">Istniejące implementacje *dziedziczą* implementację domyślną.</span><span class="sxs-lookup"><span data-stu-id="1321f-145">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="1321f-146">Ta funkcja umożliwia C# również współdziałanie z interfejsami API przeznaczonymi dla systemu Android lub SWIFT, które obsługują podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="1321f-146">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="1321f-147">Domyślne elementy członkowskie interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".</span><span class="sxs-lookup"><span data-stu-id="1321f-147">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="1321f-148">Domyślne elementy członkowskie interfejsu mają wpływ na wiele scenariuszy i elementów języka.</span><span class="sxs-lookup"><span data-stu-id="1321f-148">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="1321f-149">W pierwszym samouczku omówiono [aktualizowanie interfejsu przy użyciu domyślnych implementacji](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-149">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="1321f-150">Inne samouczki i aktualizacje referencyjne są dostępne w czasie do wydania ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1321f-150">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="1321f-151">Więcej wzorców w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="1321f-151">More patterns in more places</span></span>

<span data-ttu-id="1321f-152">**Dopasowanie wzorców** oferuje narzędzia do zapewniania funkcji zależnych od kształtu między powiązanymi, ale różnymi rodzajami danych.</span><span class="sxs-lookup"><span data-stu-id="1321f-152">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="1321f-153">C#7,0 wprowadzono składnię dla wzorców typu i wzorców stałych przy użyciu [`is`](../language-reference/keywords/is.md) wyrażenia [`switch`](../language-reference/keywords/switch.md) i instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1321f-153">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="1321f-154">Te funkcje przedstawiają pierwsze wstępnie wymagane kroki w kierunku obsługi odmian programistycznych, w których dane i funkcje są aktywne.</span><span class="sxs-lookup"><span data-stu-id="1321f-154">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="1321f-155">Gdy branża jest przenoszona do większej liczby mikrousług i architektur opartych na chmurze, inne narzędzia języka są zbędne.</span><span class="sxs-lookup"><span data-stu-id="1321f-155">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="1321f-156">C#8,0 rozwija ten słownik, aby można było używać więcej wyrażeń wzorca w większej liczbie miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1321f-156">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="1321f-157">Te funkcje należy wziąć pod uwagę, gdy dane i funkcje są osobne.</span><span class="sxs-lookup"><span data-stu-id="1321f-157">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="1321f-158">Rozważ dopasowanie wzorców, gdy algorytmy zależą od faktu innego niż typ środowiska uruchomieniowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1321f-158">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="1321f-159">Techniki te zapewniają inny sposób tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="1321f-159">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="1321f-160">Oprócz nowych wzorców w nowych miejscach, C# 8,0 dodaje cykliczne **wzorce**.</span><span class="sxs-lookup"><span data-stu-id="1321f-160">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="1321f-161">Wynikiem dowolnego wyrażenia wzorca jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1321f-161">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="1321f-162">Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="1321f-162">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="1321f-163">Przełącz wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1321f-163">switch expressions</span></span>

<span data-ttu-id="1321f-164">Często instrukcja generuje wartość w każdym z jego `case` bloków. [`switch`](../language-reference/keywords/switch.md)</span><span class="sxs-lookup"><span data-stu-id="1321f-164">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="1321f-165">**Wyrażenia Switch** umożliwiają użycie bardziej zwięzłej składni wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1321f-165">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="1321f-166">Jest mniej powtarzające `case` się `break` i słowa kluczowe i mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="1321f-166">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="1321f-167">Na przykład rozważmy następujące Wyliczenie, które zawiera listę kolorów tęczu:</span><span class="sxs-lookup"><span data-stu-id="1321f-167">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="1321f-168">Jeśli aplikacja `RGBColor` definiuje typ, który jest zbudowany `G` `R`ze składników, i `B` , można skonwertować `Rainbow` wartość na wartości RGB przy użyciu następującej metody zawierającej wyrażenie Switch:</span><span class="sxs-lookup"><span data-stu-id="1321f-168">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="1321f-169">Poniżej przedstawiono kilka ulepszeń składni:</span><span class="sxs-lookup"><span data-stu-id="1321f-169">There are several syntax improvements here:</span></span>

- <span data-ttu-id="1321f-170">Zmienna jest wcześniejsza niż `switch` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1321f-170">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="1321f-171">Inna kolejność ułatwia odróżnienie wyrażenia Switch od instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="1321f-171">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="1321f-172">Elementy `case` `=>`i `:` są zamieniane na.</span><span class="sxs-lookup"><span data-stu-id="1321f-172">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="1321f-173">Jest to bardziej zwięzłe i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="1321f-173">It's more concise and intuitive.</span></span>
- <span data-ttu-id="1321f-174">Przypadek jest zastępowany `_`odrzuceniem. `default`</span><span class="sxs-lookup"><span data-stu-id="1321f-174">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="1321f-175">Treść to wyrażenia, a nie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="1321f-175">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="1321f-176">Kontrast, który ma odpowiedni kod przy użyciu instrukcji `switch` klasycznej:</span><span class="sxs-lookup"><span data-stu-id="1321f-176">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="1321f-177">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="1321f-177">Property patterns</span></span>

<span data-ttu-id="1321f-178">**Wzorzec właściwości** pozwala dopasować się do właściwości badanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1321f-178">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="1321f-179">Rozważmy witrynę handlu elektronicznego, która musi obliczać podatek od sprzedaży na podstawie adresu kupującego.</span><span class="sxs-lookup"><span data-stu-id="1321f-179">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="1321f-180">To obliczenie nie jest podstawową odpowiedzialnością `Address` klasy.</span><span class="sxs-lookup"><span data-stu-id="1321f-180">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="1321f-181">Zostanie ona zmieniona z upływem czasu, co prawdopodobnie częściej niż zmienia format adresu.</span><span class="sxs-lookup"><span data-stu-id="1321f-181">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="1321f-182">Podatek od sprzedaży zależy `State` od właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="1321f-182">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="1321f-183">Poniższa metoda używa wzorca właściwości do obliczania podatku od adresu i ceny:</span><span class="sxs-lookup"><span data-stu-id="1321f-183">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="1321f-184">Dopasowanie wzorca tworzy zwięzłą składnię do wyrażania tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="1321f-184">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="1321f-185">Wzorce krotek</span><span class="sxs-lookup"><span data-stu-id="1321f-185">Tuple patterns</span></span>

<span data-ttu-id="1321f-186">Niektóre algorytmy zależą od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1321f-186">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="1321f-187">**Wzorce krotek** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako krotka [](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-187">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="1321f-188">Poniższy kod przedstawia wyrażenie Switch dla *skały, papieru, nożyczków*:</span><span class="sxs-lookup"><span data-stu-id="1321f-188">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="1321f-189">Komunikaty wskazują zwycięzcę.</span><span class="sxs-lookup"><span data-stu-id="1321f-189">The messages indicate the winner.</span></span> <span data-ttu-id="1321f-190">Przypadek odrzucania reprezentuje trzy kombinacje powiązań lub inne dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="1321f-190">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="1321f-191">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="1321f-191">Positional patterns</span></span>

<span data-ttu-id="1321f-192">Niektóre typy obejmują `Deconstruct` metodę, która dekonstrukcjauje swoje właściwości do zmiennych dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="1321f-192">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="1321f-193">Gdy metoda jest dostępna, można użyć wzorców pozycyjnych do inspekcji właściwości obiektu i używania tych właściwości dla wzorca.  `Deconstruct`</span><span class="sxs-lookup"><span data-stu-id="1321f-193">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="1321f-194">Rozważmy następujące `Point` klasy, które `Deconstruct` obejmują metodę tworzenia zmiennych dyskretnych dla `X` i `Y`:</span><span class="sxs-lookup"><span data-stu-id="1321f-194">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="1321f-195">Dodatkowo Rozważmy następujące Wyliczenie, które reprezentuje różne położenia ćwiartki:</span><span class="sxs-lookup"><span data-stu-id="1321f-195">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="1321f-196">Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="1321f-196">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="1321f-197">Następnie używa `when` klauzuli do `Quadrant` określenia punktu:</span><span class="sxs-lookup"><span data-stu-id="1321f-197">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="1321f-198">Odrzuć wzorzec w poprzednim przełączniku dopasowuje się `x` , `y` gdy lub ma wartość 0, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="1321f-198">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="1321f-199">Wyrażenie Switch musi utworzyć wartość lub zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1321f-199">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="1321f-200">Jeśli żaden z przypadków nie jest zgodny, wyrażenie Switch zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1321f-200">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="1321f-201">Kompilator generuje ostrzeżenie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu Switch.</span><span class="sxs-lookup"><span data-stu-id="1321f-201">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="1321f-202">Techniki dopasowania wzorców można eksplorować w tym [zaawansowanym samouczku dotyczącym dopasowania wzorców](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-202">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="1321f-203">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="1321f-203">using declarations</span></span>

<span data-ttu-id="1321f-204">**Deklaracja using** jest deklaracją zmiennej poprzedzoną `using` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="1321f-204">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="1321f-205">Informuje kompilator, że zadeklarowana zmienna powinna zostać usunięta na końcu otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="1321f-205">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="1321f-206">Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="1321f-206">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="1321f-207">W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="1321f-207">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="1321f-208">To koniec zakresu, w którym `file` jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="1321f-208">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="1321f-209">Poprzedni kod jest odpowiednikiem poniższego kodu, który używa klasycznej [instrukcji using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="1321f-209">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="1321f-210">W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego skojarzonego `using` z instrukcją.</span><span class="sxs-lookup"><span data-stu-id="1321f-210">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="1321f-211">W obu przypadkach kompilator generuje wywołanie `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="1321f-211">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="1321f-212">Kompilator generuje błąd, jeśli wyrażenie w `using` instrukcji nie jest jednorazowe.</span><span class="sxs-lookup"><span data-stu-id="1321f-212">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="1321f-213">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="1321f-213">Static local functions</span></span>

<span data-ttu-id="1321f-214">Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (nie dotyczy) żadnych zmiennych z zakresu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="1321f-214">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="1321f-215">Spowoduje to wygenerowanie `CS8421`, "statyczna funkcja lokalna nie może zawierać odwołania \<do zmiennej >".</span><span class="sxs-lookup"><span data-stu-id="1321f-215">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="1321f-216">Rozważmy następujący kod.</span><span class="sxs-lookup"><span data-stu-id="1321f-216">Consider the following code.</span></span> <span data-ttu-id="1321f-217">Funkcja `LocalFunction` lokalna uzyskuje dostęp do zmiennej `y`zadeklarowanej w zakresie otaczającym (Metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="1321f-217">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="1321f-218">W związku`static` z tym niemożnazadeklarować`LocalFunction` z modyfikatorem:</span><span class="sxs-lookup"><span data-stu-id="1321f-218">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="1321f-219">Poniższy kod zawiera statyczną funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="1321f-219">The following code contains a static local function.</span></span> <span data-ttu-id="1321f-220">Może być statyczny, ponieważ nie uzyskuje dostępu do żadnych zmiennych w otaczającym zakresie:</span><span class="sxs-lookup"><span data-stu-id="1321f-220">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="1321f-221">Nierozporządzalne struktury ref</span><span class="sxs-lookup"><span data-stu-id="1321f-221">Disposable ref structs</span></span>

<span data-ttu-id="1321f-222">Deklaracja z modyfikatorem nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>. `struct` `ref`</span><span class="sxs-lookup"><span data-stu-id="1321f-222">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="1321f-223">W związku z tym, `ref struct` aby można było usunąć element, musi on mieć `void Dispose()` dostępną metodę.</span><span class="sxs-lookup"><span data-stu-id="1321f-223">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="1321f-224">Dotyczy to również `readonly ref struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="1321f-224">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="1321f-225">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="1321f-225">Nullable reference types</span></span>

<span data-ttu-id="1321f-226">Wewnątrz bezwartościowego kontekstu adnotacji Każda zmienna typu referencyjnego jest uważana za typ referencyjny, który nie **ma wartości null**.</span><span class="sxs-lookup"><span data-stu-id="1321f-226">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="1321f-227">Aby wskazać, że zmienna może mieć wartość null, należy dołączyć nazwę typu z, `?` aby zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null**.</span><span class="sxs-lookup"><span data-stu-id="1321f-227">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="1321f-228">W przypadku typów referencyjnych, które nie mają wartości null, kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null, gdy zostanie zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="1321f-228">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="1321f-229">Pola muszą być inicjowane podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="1321f-229">Fields must be initialized during construction.</span></span> <span data-ttu-id="1321f-230">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie do któregokolwiek z dostępnych konstruktorów lub inicjatora.</span><span class="sxs-lookup"><span data-stu-id="1321f-230">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="1321f-231">Ponadto nie można przypisać wartości, która może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="1321f-231">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="1321f-232">Typy odwołań dopuszczających wartość null nie są sprawdzane w celu zapewnienia, że nie są przypisane ani zainicjowane do wartości null.</span><span class="sxs-lookup"><span data-stu-id="1321f-232">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="1321f-233">Jednak kompilator używa analizy przepływu, aby upewnić się, że jakakolwiek zmienna typu referencyjnego null jest sprawdzana pod kątem wartości null przed uzyskaniem dostępu lub przypisaniem do niezerowego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="1321f-233">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="1321f-234">Więcej informacji na temat funkcji można znaleźć w omówieniu [typów referencyjnych dopuszczających wartość null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-234">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="1321f-235">Wypróbuj go samodzielnie w nowej aplikacji w tym [samouczku typów odwołań dopuszczających wartość null](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-235">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="1321f-236">Zapoznaj się z instrukcjami dotyczącymi migracji istniejącej bazy kodu w celu użycia w [samouczku Migrowanie aplikacji do korzystania](../tutorials/upgrade-to-nullable-references.md)z typów odwołań dopuszczających wartość null.</span><span class="sxs-lookup"><span data-stu-id="1321f-236">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="1321f-237">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1321f-237">Asynchronous streams</span></span>

<span data-ttu-id="1321f-238">Począwszy od C# 8,0, można tworzyć strumienie i korzystać z nich asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1321f-238">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="1321f-239">Metoda zwracająca strumień asynchroniczny ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="1321f-239">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="1321f-240">Jest on zadeklarowany z `async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="1321f-240">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="1321f-241">Zwraca wartość <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1321f-241">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="1321f-242">Metoda zawiera `yield return` instrukcje do zwrócenia kolejnych elementów w strumieniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="1321f-242">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="1321f-243">Użycie strumienia asynchronicznego wymaga dodania `await` słowa kluczowego `foreach` przed słowem kluczowym podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="1321f-243">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="1321f-244">Dodanie słowa kluczowego wymaga metody, która wylicza strumień asynchroniczny, który ma zostać zadeklarowany `async` z modyfikatorem i zwraca typ dozwolony dla `async` metody. `await`</span><span class="sxs-lookup"><span data-stu-id="1321f-244">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="1321f-245">Zwykle oznacza to zwrócenie <xref:System.Threading.Tasks.Task> lub. <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="1321f-245">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1321f-246">Może być <xref:System.Threading.Tasks.ValueTask> również lub <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="1321f-246">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="1321f-247">Metoda może jednocześnie zużywać i generować strumień asynchroniczny, co oznacza, że zwróci <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1321f-247">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="1321f-248">Poniższy kod generuje sekwencję z przedziału od 0 do 19, oczekującą 100 ms między generowaniem każdej liczby:</span><span class="sxs-lookup"><span data-stu-id="1321f-248">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="1321f-249">Sekwencję można wyliczyć przy użyciu `await foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1321f-249">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="1321f-250">Możesz samodzielnie wypróbować strumienie asynchroniczne w naszym samouczku dotyczącym [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-250">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="1321f-251">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="1321f-251">Indices and ranges</span></span>

<span data-ttu-id="1321f-252">Zakresy i indeksy zapewniają zwięzłą składnię do określania podzakresów w tablicy, <xref:System.Span%601>lub. <xref:System.ReadOnlySpan%601></span><span class="sxs-lookup"><span data-stu-id="1321f-252">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="1321f-253">Ten język obsługuje dwa nowe typy i dwa nowe operatory.</span><span class="sxs-lookup"><span data-stu-id="1321f-253">This language support relies on two new types, and two new operators.</span></span>
- <span data-ttu-id="1321f-254"><xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1321f-254"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="1321f-255">`^` Operator, który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1321f-255">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="1321f-256"><xref:System.Range?displayProperty=nameWithType>reprezentuje Podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1321f-256"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="1321f-257">Operator zakresu (`..`), który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="1321f-257">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="1321f-258">Zacznijmy od reguł dotyczących indeksów.</span><span class="sxs-lookup"><span data-stu-id="1321f-258">Let's start with the rules for indexes.</span></span> <span data-ttu-id="1321f-259">Weź pod uwagę `sequence`tablicę.</span><span class="sxs-lookup"><span data-stu-id="1321f-259">Consider an array `sequence`.</span></span> <span data-ttu-id="1321f-260">Indeks jest taki sam jak `sequence[0]`. `0`</span><span class="sxs-lookup"><span data-stu-id="1321f-260">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="1321f-261">Indeks jest taki sam jak `sequence[sequence.Length]`. `^0`</span><span class="sxs-lookup"><span data-stu-id="1321f-261">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="1321f-262">Należy pamiętać `sequence[^0]` , że generuje wyjątek, podobnie jak `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="1321f-262">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="1321f-263">Dla dowolnej liczby `n`indeks `^n` jest taki sam jak `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="1321f-263">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="1321f-264">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="1321f-264">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="1321f-265">Początek zakresu jest włączony, ale koniec zakresu jest na wyłączność, co oznacza, że *początek* znajduje się w zakresie, ale *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1321f-265">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="1321f-266">Zakres `[0..^0]` reprezentuje cały zakres, tak jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="1321f-266">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="1321f-267">Przyjrzyjmy się kilku przykładom.</span><span class="sxs-lookup"><span data-stu-id="1321f-267">Let's look at a few examples.</span></span> <span data-ttu-id="1321f-268">Rozważmy następującą tablicę zawierającą adnotację z jej indeksem od początku i od końca:</span><span class="sxs-lookup"><span data-stu-id="1321f-268">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="1321f-269">Możesz pobrać ostatni wyraz z `^1` indeksem:</span><span class="sxs-lookup"><span data-stu-id="1321f-269">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="1321f-270">Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox".</span><span class="sxs-lookup"><span data-stu-id="1321f-270">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="1321f-271">Zawiera `words[1]` .`words[3]`</span><span class="sxs-lookup"><span data-stu-id="1321f-271">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="1321f-272">Element `words[4]` nie należy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="1321f-272">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="1321f-273">Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog".</span><span class="sxs-lookup"><span data-stu-id="1321f-273">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="1321f-274">Obejmuje `words[^2]` i .`words[^1]`</span><span class="sxs-lookup"><span data-stu-id="1321f-274">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="1321f-275">Indeks `words[^0]` końcowy nie jest uwzględniony:</span><span class="sxs-lookup"><span data-stu-id="1321f-275">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="1321f-276">W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="1321f-276">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="1321f-277">Można również zadeklarować zakresy jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="1321f-277">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="1321f-278">Zakres może być następnie używany wewnątrz `[` znaków i: `]`</span><span class="sxs-lookup"><span data-stu-id="1321f-278">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="1321f-279">Więcej informacji o indeksach i zakresach można dowiedzieć się w samouczku dotyczącym [indeksów i zakresów](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="1321f-279">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>
