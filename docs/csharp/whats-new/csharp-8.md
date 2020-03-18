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
# <a name="whats-new-in-c-80"></a><span data-ttu-id="5d306-103">Co nowego w języku C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5d306-103">What's new in C# 8.0</span></span>

<span data-ttu-id="5d306-104">C# 8.0 dodaje następujące funkcje i ulepszenia do języka Języka C#:</span><span class="sxs-lookup"><span data-stu-id="5d306-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="5d306-105">Członkowie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d306-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="5d306-106">Domyślne metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="5d306-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="5d306-107">[Ulepszenia dopasowywania wzorców:](#more-patterns-in-more-places)</span><span class="sxs-lookup"><span data-stu-id="5d306-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="5d306-108">Przełączanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5d306-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="5d306-109">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="5d306-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="5d306-110">Wzory krotki</span><span class="sxs-lookup"><span data-stu-id="5d306-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="5d306-111">Wzory pozycyjne</span><span class="sxs-lookup"><span data-stu-id="5d306-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="5d306-112">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="5d306-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="5d306-113">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="5d306-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="5d306-114">Jednorazowe struktury ref</span><span class="sxs-lookup"><span data-stu-id="5d306-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="5d306-115">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="5d306-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="5d306-116">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="5d306-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="5d306-117">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="5d306-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="5d306-118">Przypisanie łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="5d306-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="5d306-119">Typy skonstruowane niezarządzane</span><span class="sxs-lookup"><span data-stu-id="5d306-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="5d306-120">Stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="5d306-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="5d306-121">Wzmocnienie interpolowanych ciągów dosłownych</span><span class="sxs-lookup"><span data-stu-id="5d306-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="5d306-122">C# 8.0 jest obsługiwany w **.NET Core 3.x** i **.NET Standard 2.1**.</span><span class="sxs-lookup"><span data-stu-id="5d306-122">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="5d306-123">Aby uzyskać więcej informacji, zobacz [C# language versioning](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-123">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="5d306-124">W dalszej części tego artykułu opisano pokrótce te funkcje.</span><span class="sxs-lookup"><span data-stu-id="5d306-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="5d306-125">Tam, gdzie dostępne są szczegółowe artykuły, dostępne są łącza do tych samouczków i przeglądów.</span><span class="sxs-lookup"><span data-stu-id="5d306-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="5d306-126">Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`</span><span class="sxs-lookup"><span data-stu-id="5d306-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="5d306-127">Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="5d306-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="5d306-128">Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="5d306-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="5d306-129">Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *próbek.*</span><span class="sxs-lookup"><span data-stu-id="5d306-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="5d306-130">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="5d306-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="5d306-131">Członkowie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d306-131">Readonly members</span></span>

<span data-ttu-id="5d306-132">`readonly` Modyfikator można zastosować do elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="5d306-132">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="5d306-133">Oznacza to, że element członkowski nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="5d306-133">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="5d306-134">Jest bardziej szczegółowy niż stosowanie `readonly` modyfikatora `struct` do deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5d306-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="5d306-135">Należy wziąć pod uwagę następujące struktury zmienne:</span><span class="sxs-lookup"><span data-stu-id="5d306-135">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="5d306-136">Podobnie jak większość struktur, `ToString()` metoda nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="5d306-136">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="5d306-137">Można wskazać, że `readonly` dodając modyfikator `ToString()`do deklaracji:</span><span class="sxs-lookup"><span data-stu-id="5d306-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="5d306-138">Powyższa zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp do `Distance` właściwości, która nie jest oznaczona: `readonly`</span><span class="sxs-lookup"><span data-stu-id="5d306-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="5d306-139">Kompilator ostrzega, gdy musi utworzyć kopię obronną.</span><span class="sxs-lookup"><span data-stu-id="5d306-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="5d306-140">Właściwość `Distance` nie zmienia stanu, więc można naprawić to `readonly` ostrzeżenie, dodając modyfikator do deklaracji:</span><span class="sxs-lookup"><span data-stu-id="5d306-140">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="5d306-141">Należy zauważyć, że `readonly` modyfikator jest konieczne na właściwość tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5d306-141">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="5d306-142">Kompilator nie `get` zakłada, że akcesory nie modyfikują stanu; należy zadeklarować `readonly` jawnie.</span><span class="sxs-lookup"><span data-stu-id="5d306-142">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="5d306-143">Właściwości implementowane automatycznie są wyjątkiem; kompilator będzie traktować wszystkie automatycznie implementowane getters jako tylko do `readonly` odczytu, `X` więc `Y` tutaj nie ma potrzeby, aby dodać modyfikator do i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d306-143">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="5d306-144">Kompilator wymusza regułę, że `readonly` członkowie nie modyfikują stanu.</span><span class="sxs-lookup"><span data-stu-id="5d306-144">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="5d306-145">Następująca metoda nie zostanie skompilowana, `readonly` dopóki nie usuniesz modyfikatora:</span><span class="sxs-lookup"><span data-stu-id="5d306-145">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="5d306-146">Ta funkcja umożliwia określenie intencji projektu, dzięki czemu kompilator może go wymusić i dokonać optymalizacji na podstawie tego zamiaru.</span><span class="sxs-lookup"><span data-stu-id="5d306-146">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="5d306-147">Możesz dowiedzieć się więcej o członków tylko [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)do odczytu w artykule odniesienia języka na .</span><span class="sxs-lookup"><span data-stu-id="5d306-147">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="5d306-148">Domyślne metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="5d306-148">Default interface methods</span></span>

<span data-ttu-id="5d306-149">Teraz można dodać członków do interfejsów i zapewnić implementację dla tych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5d306-149">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="5d306-150">Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach bez przerywania zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d306-150">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="5d306-151">Istniejące implementacje *dziedziczą* domyślną implementację.</span><span class="sxs-lookup"><span data-stu-id="5d306-151">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="5d306-152">Ta funkcja umożliwia również C# do współdziałania z interfejsami API, które są przeznaczone dla systemu Android lub Swift, które obsługują podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="5d306-152">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="5d306-153">Domyślne metody interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".</span><span class="sxs-lookup"><span data-stu-id="5d306-153">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="5d306-154">Domyślne metody interfejsu wpływa na wiele scenariuszy i elementów języka.</span><span class="sxs-lookup"><span data-stu-id="5d306-154">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="5d306-155">Nasz pierwszy samouczek obejmuje [aktualizację interfejsu z domyślnymi implementacjami](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-155">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="5d306-156">Inne samouczki i aktualizacje referencyjne nadchodzą w czasie do wydania ogólnego.</span><span class="sxs-lookup"><span data-stu-id="5d306-156">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="5d306-157">Więcej wzorów w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="5d306-157">More patterns in more places</span></span>

<span data-ttu-id="5d306-158">**Dopasowywanie wzorców** zapewnia narzędzia zapewniające funkcje zależne od kształtu w powiązanych, ale różnych rodzajach danych.</span><span class="sxs-lookup"><span data-stu-id="5d306-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="5d306-159">C# 7.0 wprowadzono składnię wzorców typów [`is`](../language-reference/keywords/is.md) i [`switch`](../language-reference/keywords/switch.md) wzorców stałych przy użyciu wyrażenia i instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5d306-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="5d306-160">Funkcje te stanowiły pierwsze wstępne kroki w kierunku obsługi paradygmatów programowania, w których dane i funkcje są dostępne oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="5d306-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="5d306-161">W miarę jak branża przechodzi w kierunku większej liczby mikrousług i innych architektur opartych na chmurze, potrzebne są inne narzędzia językowe.</span><span class="sxs-lookup"><span data-stu-id="5d306-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="5d306-162">C# 8.0 rozszerza to słownictwo, dzięki czemu można użyć więcej wyrażeń wzorca w większej liczbie miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d306-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="5d306-163">Należy wziąć pod uwagę te funkcje, gdy dane i funkcje są oddzielne.</span><span class="sxs-lookup"><span data-stu-id="5d306-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="5d306-164">Należy wziąć pod uwagę dopasowywanie wzorca, gdy algorytmy zależą od faktu innego niż typ czasu wykonywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d306-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="5d306-165">Techniki te zapewniają inny sposób wyrażania wzorów.</span><span class="sxs-lookup"><span data-stu-id="5d306-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="5d306-166">Oprócz nowych wzorców w nowych miejscach C# 8.0 dodaje **wzorce cykliczne**.</span><span class="sxs-lookup"><span data-stu-id="5d306-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="5d306-167">Wynikiem dowolnego wyrażenia wzorca jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5d306-167">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="5d306-168">Wzorzec cykliczny jest po prostu wyrażenie wzorca stosowane do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="5d306-168">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="5d306-169">Przełączanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5d306-169">Switch expressions</span></span>

<span data-ttu-id="5d306-170">Często instrukcja [`switch`](../language-reference/keywords/switch.md) tworzy wartość w każdym `case` z jego bloków.</span><span class="sxs-lookup"><span data-stu-id="5d306-170">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="5d306-171">**Wyrażenia przełącznika** umożliwiają użycie bardziej zwięzłej składni wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5d306-171">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="5d306-172">Jest mniej powtarzających `case` się `break` i słów kluczowych i mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="5d306-172">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="5d306-173">Na przykład należy wziąć pod uwagę następujące wyliczenie, które zawiera listę kolorów tęczy:</span><span class="sxs-lookup"><span data-stu-id="5d306-173">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="5d306-174">Jeśli aplikacja `RGBColor` zdefiniowała typ `R`skonstruowany z programu , `G` a `B` składniki, można przekonwertować `Rainbow` wartość na jej wartości RGB przy użyciu następującej metody zawierającej wyrażenie przełącznika:</span><span class="sxs-lookup"><span data-stu-id="5d306-174">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="5d306-175">Istnieje kilka ulepszeń składni tutaj:</span><span class="sxs-lookup"><span data-stu-id="5d306-175">There are several syntax improvements here:</span></span>

- <span data-ttu-id="5d306-176">Zmienna jest `switch` przed słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="5d306-176">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="5d306-177">Różna kolejność ułatwia wizualnie odróżnienie wyrażenia przełącznika od instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="5d306-177">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="5d306-178">Elementy `case` `:` i są `=>`zastępowane .</span><span class="sxs-lookup"><span data-stu-id="5d306-178">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="5d306-179">Jest bardziej zwięzły i intuicyjny.</span><span class="sxs-lookup"><span data-stu-id="5d306-179">It's more concise and intuitive.</span></span>
- <span data-ttu-id="5d306-180">Obudowę `default` zastępuje się `_` odrzuceniem.</span><span class="sxs-lookup"><span data-stu-id="5d306-180">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="5d306-181">Obiekty są wyrażeniami, a nie instrukcjami.</span><span class="sxs-lookup"><span data-stu-id="5d306-181">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="5d306-182">Kontrast, że z równoważny `switch` kod przy użyciu instrukcji classic:</span><span class="sxs-lookup"><span data-stu-id="5d306-182">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="5d306-183">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="5d306-183">Property patterns</span></span>

<span data-ttu-id="5d306-184">**Wzorzec właściwości** umożliwia dopasowanie właściwości badanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d306-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="5d306-185">Rozważmy witrynę handlu elektronicznego, która musi obliczyć podatek na podstawie adresu kupującego.</span><span class="sxs-lookup"><span data-stu-id="5d306-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="5d306-186">To obliczenia nie jest podstawową odpowiedzialnością `Address` klasy.</span><span class="sxs-lookup"><span data-stu-id="5d306-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="5d306-187">Z czasem będzie się zmieniać, prawdopodobnie częściej niż zmiany formatu adresu.</span><span class="sxs-lookup"><span data-stu-id="5d306-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="5d306-188">Wysokość podatku zależy od `State` właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="5d306-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="5d306-189">Poniższa metoda używa wzorca właściwości do obliczenia podatku od sprzedaży z adresu i ceny:</span><span class="sxs-lookup"><span data-stu-id="5d306-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="5d306-190">Dopasowanie wzorca tworzy zwięzłą składnię do wyrażania tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="5d306-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="5d306-191">Wzory krotki</span><span class="sxs-lookup"><span data-stu-id="5d306-191">Tuple patterns</span></span>

<span data-ttu-id="5d306-192">Niektóre algorytmy zależą od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5d306-192">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="5d306-193">**Wzorce krotki** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako [krotka](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-193">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="5d306-194">Poniższy kod pokazuje wyrażenie przełącznika dla *rock gry, papieru, nożyczek:*</span><span class="sxs-lookup"><span data-stu-id="5d306-194">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="5d306-195">Komunikaty wskazują zwycięzcę.</span><span class="sxs-lookup"><span data-stu-id="5d306-195">The messages indicate the winner.</span></span> <span data-ttu-id="5d306-196">Przypadek odrzucenia reprezentuje trzy kombinacje dla powiązań lub inne dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="5d306-196">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="5d306-197">Wzory pozycyjne</span><span class="sxs-lookup"><span data-stu-id="5d306-197">Positional patterns</span></span>

<span data-ttu-id="5d306-198">Niektóre typy `Deconstruct` zawierają metodę, która dekonstruuje jego właściwości na zmienne dyskretne.</span><span class="sxs-lookup"><span data-stu-id="5d306-198">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="5d306-199">Gdy `Deconstruct` metoda jest dostępna, można użyć **wzorców pozycyjnych** do sprawdzania właściwości obiektu i używać tych właściwości dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="5d306-199">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="5d306-200">Należy wziąć `Point` pod uwagę `Deconstruct` następującą klasę, która `X` `Y`zawiera metodę tworzenia zmiennych dyskretnych dla i:</span><span class="sxs-lookup"><span data-stu-id="5d306-200">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="5d306-201">Ponadto należy wziąć pod uwagę następujące wyliczenie, które reprezentuje różne pozycje kwadrantu:</span><span class="sxs-lookup"><span data-stu-id="5d306-201">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="5d306-202">Poniższa metoda używa **wzorca pozycyjnego** `x` do `y`wyodrębniania wartości i .</span><span class="sxs-lookup"><span data-stu-id="5d306-202">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="5d306-203">Następnie używa klauzuli `when` do `Quadrant` określenia punktu:</span><span class="sxs-lookup"><span data-stu-id="5d306-203">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="5d306-204">Wzorzec odrzutów w `x` poprzednim `y` przełączniku pasuje, gdy jeden lub jest 0, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="5d306-204">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="5d306-205">Wyrażenie przełącznika musi generować wartość lub zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5d306-205">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="5d306-206">Jeśli żaden z przypadków są zgodne, wyrażenie przełącznika zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5d306-206">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="5d306-207">Kompilator generuje ostrzeżenie dla Ciebie, jeśli nie obejmuje wszystkich możliwych przypadków w wyrażeniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="5d306-207">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="5d306-208">Możesz eksplorować techniki dopasowywania wzorców w tym [zaawansowanym samouczku na temat dopasowywania wzorców](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-208">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="5d306-209">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="5d306-209">Using declarations</span></span>

<span data-ttu-id="5d306-210">Using **deklaracji** jest deklaracja zmiennej `using` poprzedzone słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="5d306-210">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="5d306-211">Informuje kompilator, że zmienna deklarowana powinna być usuwana na końcu otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="5d306-211">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="5d306-212">Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="5d306-212">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="5d306-213">W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu zamykającego dla metody.</span><span class="sxs-lookup"><span data-stu-id="5d306-213">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="5d306-214">To koniec zakresu, w którym `file` jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="5d306-214">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="5d306-215">Poprzedni kod jest odpowiednikiem następującego kodu, który używa instrukcji klasycznej [using:](../language-reference/keywords/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5d306-215">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="5d306-216">W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu zamykającego skojarzonego z instrukcją. `using`</span><span class="sxs-lookup"><span data-stu-id="5d306-216">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="5d306-217">W obu przypadkach kompilator generuje `Dispose()`wywołanie .</span><span class="sxs-lookup"><span data-stu-id="5d306-217">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="5d306-218">Kompilator generuje błąd, jeśli `using` wyrażenie w instrukcji nie jest jednorazowe.</span><span class="sxs-lookup"><span data-stu-id="5d306-218">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="5d306-219">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="5d306-219">Static local functions</span></span>

<span data-ttu-id="5d306-220">Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołuje się) żadnych zmiennych z otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="5d306-220">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="5d306-221">W ten `CS8421`sposób generuje , "Statyczny funkcja \<lokalna nie może zawierać odwołanie do zmiennej>."</span><span class="sxs-lookup"><span data-stu-id="5d306-221">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="5d306-222">Należy wziąć pod uwagę następujący kod.</span><span class="sxs-lookup"><span data-stu-id="5d306-222">Consider the following code.</span></span> <span data-ttu-id="5d306-223">Funkcja `LocalFunction` lokalna uzyskuje `y`dostęp do zmiennej zadeklarowanej `M`w otaczającym zakresie (metoda).</span><span class="sxs-lookup"><span data-stu-id="5d306-223">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="5d306-224">W `LocalFunction` związku z tym nie `static` można zadeklarować za pomocą modyfikatora:</span><span class="sxs-lookup"><span data-stu-id="5d306-224">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="5d306-225">Poniższy kod zawiera statyczną funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="5d306-225">The following code contains a static local function.</span></span> <span data-ttu-id="5d306-226">Może być statyczny, ponieważ nie ma dostępu do żadnych zmiennych w otaczającym zakresie:</span><span class="sxs-lookup"><span data-stu-id="5d306-226">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="5d306-227">Jednorazowe struktury ref</span><span class="sxs-lookup"><span data-stu-id="5d306-227">Disposable ref structs</span></span>

<span data-ttu-id="5d306-228">Zadeklarowane `struct` za `ref` pomocą modyfikatora może nie implementować żadnych interfejsów, a więc nie można zaimplementować <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="5d306-228">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="5d306-229">W związku z `ref struct` tym, aby umożliwić unieszkodliwiania, musi mieć metodę dostępną. `void Dispose()`</span><span class="sxs-lookup"><span data-stu-id="5d306-229">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="5d306-230">Ta funkcja ma `readonly ref struct` również zastosowanie do deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5d306-230">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="5d306-231">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="5d306-231">Nullable reference types</span></span>

<span data-ttu-id="5d306-232">Wewnątrz kontekstu adnotacji nullable każda zmienna typu odwołania jest uważana za **typ odwołania niepodlegającego unieważnieniu**.</span><span class="sxs-lookup"><span data-stu-id="5d306-232">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="5d306-233">Aby wskazać, że zmienna może mieć wartość null, należy `?` doniąc nazwę typu do zadeklarowania zmiennej jako **typu odwołania unieważnianego**.</span><span class="sxs-lookup"><span data-stu-id="5d306-233">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="5d306-234">W przypadku typów odwołań niepodlegających unieważnieniu kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości niezerowej po zadeklarowaniu.</span><span class="sxs-lookup"><span data-stu-id="5d306-234">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="5d306-235">Pola muszą być zainicjowane podczas budowy.</span><span class="sxs-lookup"><span data-stu-id="5d306-235">Fields must be initialized during construction.</span></span> <span data-ttu-id="5d306-236">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie dowolnego z dostępnych konstruktorów lub przez inicjatora.</span><span class="sxs-lookup"><span data-stu-id="5d306-236">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="5d306-237">Ponadto niemożna przypisać typów odwołań niepodlegających unieważnieniu wartości, która może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="5d306-237">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="5d306-238">Typy odwołań z możliwością null nie są sprawdzane, aby upewnić się, że nie są przypisane lub zainicjowane do wartości null.</span><span class="sxs-lookup"><span data-stu-id="5d306-238">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="5d306-239">Jednak kompilator używa analizy przepływu, aby upewnić się, że każda zmienna typu odwołania nullable jest sprawdzana na podstawie wartości null, zanim zostanie uzyskana lub przypisana do nieunieważnionego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="5d306-239">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="5d306-240">Więcej informacji na temat tej funkcji można znaleźć w przeglądzie [typów odwołań z możliwością unieważnienia.](../nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="5d306-240">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="5d306-241">Spróbuj sam w nowej aplikacji w tym [nullable typy odwołań samouczek](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-241">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="5d306-242">Dowiedz się więcej o krokach migracji istniejącej bazy kodu w celu użycia typów odwołań z możliwością null w [samouczku migracji aplikacji w celu użycia samouczka typu odwołań nullable](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-242">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="5d306-243">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="5d306-243">Asynchronous streams</span></span>

<span data-ttu-id="5d306-244">Począwszy od języka C# 8.0, można tworzyć i używać strumieni asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="5d306-244">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="5d306-245">Metoda zwracająca strumień asynchroniczny ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="5d306-245">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="5d306-246">Jest zadeklarowany za `async` pomocą modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5d306-246">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="5d306-247">Zwraca plik <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5d306-247">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="5d306-248">Metoda zawiera `yield return` instrukcje do zwracania kolejnych elementów w strumieniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="5d306-248">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="5d306-249">Korzystanie ze strumienia asynchronicznego `await` wymaga dodania słowa kluczowego przed `foreach` słowem kluczowym podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="5d306-249">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="5d306-250">Dodanie `await` słowa kluczowego wymaga metody, która wylicza strumień asynchroniczny być zadeklarowane za pomocą `async` modyfikatora i zwrócić typ dozwolony dla `async` metody.</span><span class="sxs-lookup"><span data-stu-id="5d306-250">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="5d306-251">Zazwyczaj oznacza to <xref:System.Threading.Tasks.Task> zwrócenie <xref:System.Threading.Tasks.Task%601>lub .</span><span class="sxs-lookup"><span data-stu-id="5d306-251">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="5d306-252">Może to być <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601>również lub .</span><span class="sxs-lookup"><span data-stu-id="5d306-252">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="5d306-253">Metoda może zarówno zużywać i wytwarzać strumień asynchroniczny, co oznacza, że zwróci . <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5d306-253">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="5d306-254">Poniższy kod generuje sekwencję od 0 do 19, czekając 100 ms między generowaniem każdego numeru:</span><span class="sxs-lookup"><span data-stu-id="5d306-254">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="5d306-255">Sekwencja zostanie wyliczona `await foreach` przy użyciu instrukcji:</span><span class="sxs-lookup"><span data-stu-id="5d306-255">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="5d306-256">Możesz spróbować strumieni asynchronicznych samodzielnie w naszym samouczku na [temat tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-256">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="5d306-257">Domyślnie elementy strumienia są przetwarzane w kontekście przechwyconego.</span><span class="sxs-lookup"><span data-stu-id="5d306-257">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="5d306-258">Jeśli chcesz wyłączyć przechwytywanie kontekstu, należy użyć metody <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="5d306-258">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="5d306-259">Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł na [temat korzystania z wzorca asynchronicznego opartego](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniu .</span><span class="sxs-lookup"><span data-stu-id="5d306-259">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="5d306-260">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="5d306-260">Indices and ranges</span></span>

<span data-ttu-id="5d306-261">Indeksy i zakresy zapewniają zwięzłą składnię dostępu do pojedynczych elementów lub zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5d306-261">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="5d306-262">Ta obsługa języka opiera się na dwóch nowych typach i dwóch nowych operatorach:</span><span class="sxs-lookup"><span data-stu-id="5d306-262">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="5d306-263"><xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5d306-263"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="5d306-264">Indeks od operatora `^`końcowego , który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5d306-264">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="5d306-265"><xref:System.Range?displayProperty=nameWithType>reprezentuje podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5d306-265"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="5d306-266">Operator `..`zakresu , który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="5d306-266">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="5d306-267">Zacznijmy od reguł indeksów.</span><span class="sxs-lookup"><span data-stu-id="5d306-267">Let's start with the rules for indexes.</span></span> <span data-ttu-id="5d306-268">Należy wziąć `sequence`pod uwagę tablicę .</span><span class="sxs-lookup"><span data-stu-id="5d306-268">Consider an array `sequence`.</span></span> <span data-ttu-id="5d306-269">Indeks `0` jest taki `sequence[0]`sam jak .</span><span class="sxs-lookup"><span data-stu-id="5d306-269">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="5d306-270">Indeks `^0` jest taki `sequence[sequence.Length]`sam jak .</span><span class="sxs-lookup"><span data-stu-id="5d306-270">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="5d306-271">Należy `sequence[^0]` zauważyć, że zgłasza `sequence[sequence.Length]` wyjątek, tak jak to robi.</span><span class="sxs-lookup"><span data-stu-id="5d306-271">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="5d306-272">Dla dowolnej `n`liczby `^n` indeks jest `sequence.Length - n`taki sam jak .</span><span class="sxs-lookup"><span data-stu-id="5d306-272">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="5d306-273">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="5d306-273">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="5d306-274">Początek zakresu jest włącznie, ale koniec zakresu jest ekskluzywny, co oznacza, że *początek* jest uwzględniony w zakresie, ale *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="5d306-274">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="5d306-275">Zakres `[0..^0]` reprezentuje cały zakres, podobnie `[0..sequence.Length]` jak cały zakres.</span><span class="sxs-lookup"><span data-stu-id="5d306-275">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="5d306-276">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="5d306-276">Let's look at a few examples.</span></span> <span data-ttu-id="5d306-277">Należy wziąć pod uwagę następującą tablicę, z adnotatorem z indeksem od początku i od końca:</span><span class="sxs-lookup"><span data-stu-id="5d306-277">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="5d306-278">Możesz pobrać ostatnie słowo `^1` z indeksem:</span><span class="sxs-lookup"><span data-stu-id="5d306-278">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="5d306-279">Poniższy kod tworzy podzakres z napisem "szybkie", "brązowy" i "lis".</span><span class="sxs-lookup"><span data-stu-id="5d306-279">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="5d306-280">Obejmuje `words[1]` ona poprzez `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="5d306-280">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="5d306-281">Element `words[4]` nie jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="5d306-281">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="5d306-282">Poniższy kod tworzy podzakres z "leniwy" i "pies".</span><span class="sxs-lookup"><span data-stu-id="5d306-282">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="5d306-283">Obejmuje `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="5d306-283">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="5d306-284">Indeks `words[^0]` końcowy nie jest uwzględniony:</span><span class="sxs-lookup"><span data-stu-id="5d306-284">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="5d306-285">Poniższe przykłady tworzą zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="5d306-285">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="5d306-286">Można również zadeklarować zakresy jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="5d306-286">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="5d306-287">Zakres może być następnie `[` używany `]` wewnątrz znaków i znaków:</span><span class="sxs-lookup"><span data-stu-id="5d306-287">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="5d306-288">Nie tylko tablice obsługują indeksy i zakresy.</span><span class="sxs-lookup"><span data-stu-id="5d306-288">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="5d306-289">Można również użyć indeksów i zakresów <xref:System.Span%601>z <xref:System.ReadOnlySpan%601> [ciągiem](../language-reference/builtin-types/reference-types.md#the-string-type), lub .</span><span class="sxs-lookup"><span data-stu-id="5d306-289">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="5d306-290">Aby uzyskać więcej informacji, zobacz [Obsługa typów indeksów i zakresów](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="5d306-290">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="5d306-291">Możesz dowiedzieć się więcej o indeksach i zakresach w samouczku na [temat indeksów i zakresów](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-291">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="5d306-292">Przypisanie łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="5d306-292">Null-coalescing assignment</span></span>

<span data-ttu-id="5d306-293">C# 8.0 wprowadza operator `??=`przypisania null-łączenie .</span><span class="sxs-lookup"><span data-stu-id="5d306-293">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="5d306-294">Operator służy `??=` do przypisywania wartości jego poprawej operand do jego operand po lewej stronie tylko wtedy, gdy po lewej stronie operand ocenia . `null`</span><span class="sxs-lookup"><span data-stu-id="5d306-294">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="5d306-295">Aby uzyskać więcej informacji, zobacz [?? i ?? = artykuł operatorów.](../language-reference/operators/null-coalescing-operator.md)</span><span class="sxs-lookup"><span data-stu-id="5d306-295">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="5d306-296">Typy skonstruowane niezarządzane</span><span class="sxs-lookup"><span data-stu-id="5d306-296">Unmanaged constructed types</span></span>

<span data-ttu-id="5d306-297">W języku C# 7.3 i wcześniejszych typu skonstruowanego (typ, który zawiera co najmniej jeden typ argumentu) nie może być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-297">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="5d306-298">Począwszy od języka C# 8.0, typ wartości konstruowanej jest niezarządzany, jeśli zawiera tylko pola typów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5d306-298">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="5d306-299">Na przykład, biorąc pod uwagę `Coords<T>` następującą definicję typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="5d306-299">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="5d306-300">`Coords<int>` typ jest typem niezarządzanym w języku C# 8.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="5d306-300">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="5d306-301">Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:</span><span class="sxs-lookup"><span data-stu-id="5d306-301">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="5d306-302">Aby uzyskać więcej informacji, zobacz [Typy niezarządzane](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="5d306-302">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="5d306-303">Stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="5d306-303">Stackalloc in nested expressions</span></span>

<span data-ttu-id="5d306-304">Począwszy od Języka C# 8.0, jeśli wynik wyrażenia <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> [stackalloc](../language-reference/operators/stackalloc.md) jest `stackalloc` typu lub typu, można użyć wyrażenia w innych wyrażeniach:</span><span class="sxs-lookup"><span data-stu-id="5d306-304">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="5d306-305">Wzmocnienie interpolowanych ciągów dosłownych</span><span class="sxs-lookup"><span data-stu-id="5d306-305">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="5d306-306">Kolejność `$` i `@` tokeny w [interpolowanych](../language-reference/tokens/interpolated.md) ciągów dosłownych `$@"..."` może `@$"..."` być dowolny: oba i są prawidłowe interpolowane ciągi dosłowne.</span><span class="sxs-lookup"><span data-stu-id="5d306-306">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="5d306-307">We wcześniejszych wersjach `$` języka C# `@` token musi pojawić się przed tokenem.</span><span class="sxs-lookup"><span data-stu-id="5d306-307">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
