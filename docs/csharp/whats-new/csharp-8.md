---
title: Co nowego w C# 8.0 - C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w języku C# 8.0.
ms.date: 04/07/2020
ms.openlocfilehash: 1a005750751129969f2d1e9caf156330dbe61cb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989210"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="1d367-103">Co nowego w języku C# 8.0</span><span class="sxs-lookup"><span data-stu-id="1d367-103">What's new in C# 8.0</span></span>

<span data-ttu-id="1d367-104">C# 8.0 dodaje następujące funkcje i ulepszenia do języka C#:</span><span class="sxs-lookup"><span data-stu-id="1d367-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="1d367-105">Czytaj tylko członków</span><span class="sxs-lookup"><span data-stu-id="1d367-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="1d367-106">Domyślne metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="1d367-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="1d367-107">[Ulepszenia dopasowywania wzorców:](#more-patterns-in-more-places)</span><span class="sxs-lookup"><span data-stu-id="1d367-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="1d367-108">Przełączanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1d367-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="1d367-109">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="1d367-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="1d367-110">Wzory krotki</span><span class="sxs-lookup"><span data-stu-id="1d367-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="1d367-111">Wzory pozycyjne</span><span class="sxs-lookup"><span data-stu-id="1d367-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="1d367-112">Używanie deklaracji</span><span class="sxs-lookup"><span data-stu-id="1d367-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="1d367-113">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="1d367-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="1d367-114">Jednorazowe struktury ref</span><span class="sxs-lookup"><span data-stu-id="1d367-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="1d367-115">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="1d367-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="1d367-116">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1d367-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="1d367-117">Asynchroniczne jednorazowe</span><span class="sxs-lookup"><span data-stu-id="1d367-117">Asynchronous disposable</span></span>](#asynchronous-disposable)
- [<span data-ttu-id="1d367-118">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="1d367-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="1d367-119">Przypisanie scalania wartości null</span><span class="sxs-lookup"><span data-stu-id="1d367-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="1d367-120">Niezarządzane typy skonstruowane</span><span class="sxs-lookup"><span data-stu-id="1d367-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="1d367-121">Stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="1d367-121">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="1d367-122">Wzmocnienie interpolowanych ciągów dosłownie</span><span class="sxs-lookup"><span data-stu-id="1d367-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="1d367-123">C# 8.0 jest obsługiwany w **.NET Core 3.x** i **.NET Standard 2.1**.</span><span class="sxs-lookup"><span data-stu-id="1d367-123">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="1d367-124">Aby uzyskać więcej informacji, zobacz [wersja językowa języka C #](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-124">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="1d367-125">Poniżej dalsza część artykułu Pokrótce opisano te funkcje.</span><span class="sxs-lookup"><span data-stu-id="1d367-125">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="1d367-126">Tam, gdzie dostępne są szczegółowe artykuły, znajdują się łącza do tych samouczków i przeglądów.</span><span class="sxs-lookup"><span data-stu-id="1d367-126">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="1d367-127">Za pomocą narzędzia globalnego można `dotnet try` eksplorować te funkcje w swoim środowisku:</span><span class="sxs-lookup"><span data-stu-id="1d367-127">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="1d367-128">Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="1d367-128">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="1d367-129">Sklonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="1d367-129">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="1d367-130">Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-samples.*</span><span class="sxs-lookup"><span data-stu-id="1d367-130">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="1d367-131">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="1d367-131">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="1d367-132">Czytaj tylko członków</span><span class="sxs-lookup"><span data-stu-id="1d367-132">Readonly members</span></span>

<span data-ttu-id="1d367-133">`readonly` Modyfikator można zastosować do elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="1d367-133">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="1d367-134">Wskazuje, że element członkowski nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="1d367-134">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="1d367-135">Jest bardziej szczegółowe niż stosowanie `readonly` modyfikatora `struct` do deklaracji.</span><span class="sxs-lookup"><span data-stu-id="1d367-135">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="1d367-136">Należy wziąć pod uwagę następujące modyfikowalne struktury:</span><span class="sxs-lookup"><span data-stu-id="1d367-136">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="1d367-137">Podobnie jak większość struktur, `ToString()` metoda nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="1d367-137">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="1d367-138">Można wskazać, że `readonly` dodając modyfikator `ToString()`do deklaracji:</span><span class="sxs-lookup"><span data-stu-id="1d367-138">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="1d367-139">Poprzednia zmiana generuje ostrzeżenie kompilatora, `ToString` `Distance` ponieważ uzyskuje dostęp do `readonly`właściwości, która nie jest oznaczona:</span><span class="sxs-lookup"><span data-stu-id="1d367-139">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="1d367-140">Kompilator ostrzega, gdy trzeba utworzyć kopię obronną.</span><span class="sxs-lookup"><span data-stu-id="1d367-140">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="1d367-141">Właściwość `Distance` nie zmienia stanu, więc można naprawić to `readonly` ostrzeżenie, dodając modyfikator do deklaracji:</span><span class="sxs-lookup"><span data-stu-id="1d367-141">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="1d367-142">Należy zauważyć, że `readonly` modyfikator jest konieczne we właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1d367-142">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="1d367-143">Kompilator nie zakłada, że `get` akcesory nie modyfikują stanu; należy zadeklarować `readonly` jawnie.</span><span class="sxs-lookup"><span data-stu-id="1d367-143">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="1d367-144">Automatycznie implementowane właściwości są wyjątkiem; kompilator będzie traktować wszystkie automatycznie implementowane getters jako readonly, więc `readonly` w tym `X` miejscu `Y` nie ma potrzeby, aby dodać modyfikator do i właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d367-144">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="1d367-145">Kompilator wymusza `readonly` regułę, że członkowie nie modyfikują stanu.</span><span class="sxs-lookup"><span data-stu-id="1d367-145">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="1d367-146">Następująca metoda nie zostanie skompilowana, chyba że usuniesz `readonly` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="1d367-146">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="1d367-147">Ta funkcja umożliwia określenie intencji projektu, dzięki czemu kompilator może wymusić go i dokonać optymalizacji na podstawie tej intencji.</span><span class="sxs-lookup"><span data-stu-id="1d367-147">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="1d367-148">Możesz dowiedzieć się więcej o readonly [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)członków w artykule referencyjnym języka na .</span><span class="sxs-lookup"><span data-stu-id="1d367-148">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="1d367-149">Domyślne metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="1d367-149">Default interface methods</span></span>

<span data-ttu-id="1d367-150">Teraz można dodać członków do interfejsów i zapewnić implementację dla tych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1d367-150">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="1d367-151">Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach bez przerywania zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1d367-151">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="1d367-152">Istniejące implementacje *dziedziczą* domyślną implementację.</span><span class="sxs-lookup"><span data-stu-id="1d367-152">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="1d367-153">Ta funkcja umożliwia również C# do współpracy z interfejsami API, które są przeznaczone dla systemu Android lub Swift, które obsługują podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="1d367-153">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="1d367-154">Domyślne metody interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".</span><span class="sxs-lookup"><span data-stu-id="1d367-154">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="1d367-155">Domyślne metody interfejsu wpływa na wiele scenariuszy i elementów języka.</span><span class="sxs-lookup"><span data-stu-id="1d367-155">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="1d367-156">Nasz pierwszy samouczek obejmuje [aktualizowanie interfejsu z domyślnymi implementacjami](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-156">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="1d367-157">Inne samouczki i aktualizacje odwołań nadchodzą w czasie do wydania ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1d367-157">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="1d367-158">Więcej wzorów w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="1d367-158">More patterns in more places</span></span>

<span data-ttu-id="1d367-159">**Dopasowywanie wzorców** daje narzędzia, aby zapewnić funkcje zależne od kształtu w pokrewnych, ale różnych rodzajów danych.</span><span class="sxs-lookup"><span data-stu-id="1d367-159">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="1d367-160">C# 7.0 wprowadzono składni dla wzorców typów i [`is`](../language-reference/keywords/is.md) wzorców stałych [`switch`](../language-reference/keywords/switch.md) przy użyciu wyrażenia i instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1d367-160">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="1d367-161">Te funkcje stanowiły pierwsze wstępne kroki w kierunku obsługi paradygmatów programowania, w których dane i funkcje żyją osobno.</span><span class="sxs-lookup"><span data-stu-id="1d367-161">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="1d367-162">W miarę jak branża przechodzi w kierunku większej liczby mikrousług i innych architektur opartych na chmurze, potrzebne są inne narzędzia językowe.</span><span class="sxs-lookup"><span data-stu-id="1d367-162">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="1d367-163">C# 8.0 rozszerza to słownictwo, dzięki czemu można użyć więcej wyrażeń wzorca w większej liczbie miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1d367-163">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="1d367-164">Należy wziąć pod uwagę te funkcje, gdy dane i funkcje są oddzielne.</span><span class="sxs-lookup"><span data-stu-id="1d367-164">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="1d367-165">Należy wziąć pod uwagę dopasowanie wzorca, gdy algorytmy zależą od faktu innego niż typ środowiska wykonawczego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d367-165">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="1d367-166">Techniki te zapewniają inny sposób wyrażania projektów.</span><span class="sxs-lookup"><span data-stu-id="1d367-166">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="1d367-167">Oprócz nowych wzorców w nowych miejscach, C# 8.0 dodaje **wzorce cykliczne**.</span><span class="sxs-lookup"><span data-stu-id="1d367-167">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="1d367-168">Wynikiem dowolnego wyrażenia wzorca jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1d367-168">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="1d367-169">Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="1d367-169">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="1d367-170">Przełączanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1d367-170">Switch expressions</span></span>

<span data-ttu-id="1d367-171">Często instrukcja [`switch`](../language-reference/keywords/switch.md) tworzy wartość w każdym `case` z jego bloków.</span><span class="sxs-lookup"><span data-stu-id="1d367-171">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="1d367-172">**Wyrażenia przełączania** umożliwiają użycie bardziej zwięzłej składni wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d367-172">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="1d367-173">Jest mniej powtarzających `case` się `break` i słów kluczowych, a mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="1d367-173">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="1d367-174">Na przykład należy wziąć pod uwagę następujące wyliczenia, które zawiera listę kolorów tęczy:</span><span class="sxs-lookup"><span data-stu-id="1d367-174">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="1d367-175">Jeśli aplikacja zdefiniowała `RGBColor` typ, który `R`jest `G` `B` skonstruowany z programu `Rainbow` , i składników, można przekonwertować wartość na jego wartości RGB przy użyciu następującej metody zawierającej wyrażenie przełącznika:</span><span class="sxs-lookup"><span data-stu-id="1d367-175">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="1d367-176">Istnieje kilka ulepszeń składni w tym miejscu:</span><span class="sxs-lookup"><span data-stu-id="1d367-176">There are several syntax improvements here:</span></span>

- <span data-ttu-id="1d367-177">Zmienna jest `switch` przed słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="1d367-177">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="1d367-178">Różne kolejność sprawia, że wizualnie łatwo odróżnić wyrażenie przełącznika od instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="1d367-178">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="1d367-179">Elementy `case` `:` i elementy `=>`są zastępowane .</span><span class="sxs-lookup"><span data-stu-id="1d367-179">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="1d367-180">Jest bardziej zwięzły i intuicyjny.</span><span class="sxs-lookup"><span data-stu-id="1d367-180">It's more concise and intuitive.</span></span>
- <span data-ttu-id="1d367-181">Obudowa `default` jest `_` zastępowana odrzutem.</span><span class="sxs-lookup"><span data-stu-id="1d367-181">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="1d367-182">Obiekty są wyrażeniami, a nie instrukcjami.</span><span class="sxs-lookup"><span data-stu-id="1d367-182">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="1d367-183">Kontrast, że z równoważnym `switch` kodem przy użyciu instrukcji klasycznej:</span><span class="sxs-lookup"><span data-stu-id="1d367-183">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="1d367-184">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="1d367-184">Property patterns</span></span>

<span data-ttu-id="1d367-185">**Wzorzec właściwości** umożliwia dopasowanie właściwości badanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d367-185">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="1d367-186">Rozważmy witrynę eCommerce, która musi obliczyć podatek na podstawie adresu kupującego.</span><span class="sxs-lookup"><span data-stu-id="1d367-186">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="1d367-187">To obliczenie nie jest podstawową `Address` odpowiedzialnością klasy.</span><span class="sxs-lookup"><span data-stu-id="1d367-187">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="1d367-188">Będzie się zmieniać w czasie, prawdopodobnie częściej niż zmiany formatu adresu.</span><span class="sxs-lookup"><span data-stu-id="1d367-188">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="1d367-189">Kwota podatku zależy od `State` właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="1d367-189">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="1d367-190">Następująca metoda używa wzorca właściwości do obliczenia podatku na podstawie adresu i ceny:</span><span class="sxs-lookup"><span data-stu-id="1d367-190">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="1d367-191">Dopasowywanie wzorców tworzy zwięzłą składnię do wyrażania tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="1d367-191">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="1d367-192">Wzory krotki</span><span class="sxs-lookup"><span data-stu-id="1d367-192">Tuple patterns</span></span>

<span data-ttu-id="1d367-193">Niektóre algorytmy zależą od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1d367-193">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="1d367-194">**Wzory krotki** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako [krotka.](../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="1d367-194">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="1d367-195">Poniższy kod pokazuje wyrażenie przełączania dla *gry rock, papier, nożyczki:*</span><span class="sxs-lookup"><span data-stu-id="1d367-195">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="1d367-196">Wiadomości wskazują zwycięzcę.</span><span class="sxs-lookup"><span data-stu-id="1d367-196">The messages indicate the winner.</span></span> <span data-ttu-id="1d367-197">Przypadek odrzucenia reprezentuje trzy kombinacje dla powiązań lub innych danych wejściowych tekstu.</span><span class="sxs-lookup"><span data-stu-id="1d367-197">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="1d367-198">Wzory pozycyjne</span><span class="sxs-lookup"><span data-stu-id="1d367-198">Positional patterns</span></span>

<span data-ttu-id="1d367-199">Niektóre typy `Deconstruct` zawierają metodę, która dekonstruuje swoje właściwości na zmienne dyskretne.</span><span class="sxs-lookup"><span data-stu-id="1d367-199">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="1d367-200">Gdy `Deconstruct` metoda jest dostępna, można użyć **wzorców pozycyjnych** do sprawdzania właściwości obiektu i używać tych właściwości dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="1d367-200">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="1d367-201">Należy wziąć `Point` pod uwagę `Deconstruct` następującą klasę, która `X` zawiera `Y`metodę tworzenia zmiennych dyskretnych dla i:</span><span class="sxs-lookup"><span data-stu-id="1d367-201">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="1d367-202">Ponadto należy wziąć pod uwagę następujące wyliczenia, który reprezentuje różne pozycje kwadrantu:</span><span class="sxs-lookup"><span data-stu-id="1d367-202">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="1d367-203">Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="1d367-203">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="1d367-204">Następnie używa `when` klauzuli do określenia `Quadrant` punktu:</span><span class="sxs-lookup"><span data-stu-id="1d367-204">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="1d367-205">Wzorzec odrzucenia w poprzednim przełączniku pasuje, gdy albo `x` jest 0, `y` ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="1d367-205">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="1d367-206">Wyrażenie switch musi albo utworzyć wartość lub zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1d367-206">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="1d367-207">Jeśli żaden z przypadków nie jest zgodny, wyrażenie switch zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1d367-207">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="1d367-208">Kompilator generuje ostrzeżenie dla Ciebie, jeśli nie obejmuje wszystkich możliwych przypadków w wyrażeniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="1d367-208">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="1d367-209">Można zbadać techniki dopasowywania wzorców w tym [zaawansowanym samouczku na temat dopasowywania wzorców](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-209">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="1d367-210">Używanie deklaracji</span><span class="sxs-lookup"><span data-stu-id="1d367-210">Using declarations</span></span>

<span data-ttu-id="1d367-211">**Using declaration** jest deklaracją zmiennej `using` poprzedzoną słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="1d367-211">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="1d367-212">Informuje kompilator, że zmienna jest zadeklarowana powinny być usuwane na końcu otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="1d367-212">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="1d367-213">Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="1d367-213">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="1d367-214">W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu klamrowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="1d367-214">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="1d367-215">To koniec zakresu, w którym `file` jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="1d367-215">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="1d367-216">Powyższy kod jest odpowiednikiem następującego kodu, który używa klasycznego [using instrukcji:](../language-reference/keywords/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="1d367-216">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="1d367-217">W poprzednim przykładzie plik jest usuwany po osiągnięciu nawiasu `using` klamrowego zamknięcia skojarzonego z instrukcją.</span><span class="sxs-lookup"><span data-stu-id="1d367-217">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="1d367-218">W obu przypadkach kompilator generuje `Dispose()`wywołanie .</span><span class="sxs-lookup"><span data-stu-id="1d367-218">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="1d367-219">Kompilator generuje błąd, jeśli wyrażenie `using` w instrukcji nie jest jednorazowe.</span><span class="sxs-lookup"><span data-stu-id="1d367-219">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="1d367-220">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="1d367-220">Static local functions</span></span>

<span data-ttu-id="1d367-221">Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (odwołuje się) żadnych zmiennych z zakresu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="1d367-221">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="1d367-222">W ten `CS8421`sposób generuje , "Statyczna funkcja lokalna \<nie może zawierać odwołania do zmiennej>."</span><span class="sxs-lookup"><span data-stu-id="1d367-222">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="1d367-223">Należy wziąć pod uwagę następujący kod.</span><span class="sxs-lookup"><span data-stu-id="1d367-223">Consider the following code.</span></span> <span data-ttu-id="1d367-224">Funkcja `LocalFunction` lokalna uzyskuje `y`dostęp do zmiennej, zadeklarowanej `M`w otaczającym zakresie (metoda).</span><span class="sxs-lookup"><span data-stu-id="1d367-224">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="1d367-225">W związku `LocalFunction` z tym nie `static` można zadeklarować za pomocą modyfikatora:</span><span class="sxs-lookup"><span data-stu-id="1d367-225">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="1d367-226">Poniższy kod zawiera statyczną funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="1d367-226">The following code contains a static local function.</span></span> <span data-ttu-id="1d367-227">Może być statyczny, ponieważ nie ma dostępu do żadnych zmiennych w otaczającym zakresie:</span><span class="sxs-lookup"><span data-stu-id="1d367-227">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="1d367-228">Jednorazowe struktury ref</span><span class="sxs-lookup"><span data-stu-id="1d367-228">Disposable ref structs</span></span>

<span data-ttu-id="1d367-229">Zadeklarowany `struct` z `ref` modyfikatorem może nie implementować żadnych <xref:System.IDisposable>interfejsów i dlatego nie można zaimplementować .</span><span class="sxs-lookup"><span data-stu-id="1d367-229">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="1d367-230">W związku z `ref struct` tym, aby umożliwić a do `void Dispose()` usunięcia, musi mieć metodę dostępną.</span><span class="sxs-lookup"><span data-stu-id="1d367-230">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="1d367-231">Ta funkcja dotyczy `readonly ref struct` również deklaracji.</span><span class="sxs-lookup"><span data-stu-id="1d367-231">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="1d367-232">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="1d367-232">Nullable reference types</span></span>

<span data-ttu-id="1d367-233">Wewnątrz kontekstu adnotacji możliwej do unieważnienia każda zmienna typu odwołania jest uważana za **niesytrzalną typ odwołania.**</span><span class="sxs-lookup"><span data-stu-id="1d367-233">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="1d367-234">Jeśli chcesz wskazać, że zmienna może mieć wartość null, `?` należy dołączyć nazwę typu z nazwą, aby zadeklarować zmienną jako **typ odwołania z dopuszczalną wartością null.**</span><span class="sxs-lookup"><span data-stu-id="1d367-234">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="1d367-235">W przypadku typów odwołań nieobjawialnych kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null po zadeklarowaniu.</span><span class="sxs-lookup"><span data-stu-id="1d367-235">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="1d367-236">Pola muszą być inicjowane podczas budowy.</span><span class="sxs-lookup"><span data-stu-id="1d367-236">Fields must be initialized during construction.</span></span> <span data-ttu-id="1d367-237">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie dowolnego z dostępnych konstruktorów lub przez inicjatora.</span><span class="sxs-lookup"><span data-stu-id="1d367-237">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="1d367-238">Ponadto nie można przypisać typów odwołań nieskłocyjnych.</span><span class="sxs-lookup"><span data-stu-id="1d367-238">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="1d367-239">Typy odwołań nullable nie są sprawdzane, aby upewnić się, że nie są przypisane lub zainicjowane do wartości null.</span><span class="sxs-lookup"><span data-stu-id="1d367-239">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="1d367-240">Jednak kompilator używa analizy przepływu, aby upewnić się, że każda zmienna typu odwołania nullable jest sprawdzana względem null przed uzyskaniam dostępu lub przypisaniem do nieskrójnego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="1d367-240">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="1d367-241">Więcej informacji na temat tej funkcji można znaleźć w przeglądzie [typów odwołań podlegającym wartości null.](../nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="1d367-241">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="1d367-242">Spróbuj sam w nowej aplikacji w tym [nullable typy odwołań samouczek](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-242">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="1d367-243">Dowiedz się więcej o krokach migracji istniejącej bazy kodu w celu wykorzystania typów odwołań do nullable w [migracji aplikacji do korzystania z samouczka typów odwołań nullable](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-243">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="1d367-244">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1d367-244">Asynchronous streams</span></span>

<span data-ttu-id="1d367-245">Począwszy od języka C# 8.0, można tworzyć i zużywać strumienie asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1d367-245">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="1d367-246">Metoda zwraca strumień asynchroniczne ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="1d367-246">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="1d367-247">Jest zadeklarowany za `async` pomocą modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="1d367-247">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="1d367-248">Zwraca wartość <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1d367-248">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="1d367-249">Metoda zawiera `yield return` instrukcje do zwracania kolejnych elementów w strumieniu asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1d367-249">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="1d367-250">Korzystanie ze strumienia asynchroniiowego `await` wymaga dodania słowa kluczowego przed `foreach` słowem kluczowym podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="1d367-250">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="1d367-251">Dodawanie `await` słowa kluczowego wymaga metody, która wylicza strumień asynchroniczne, które mają być zadeklarowane za pomocą `async` modyfikatora i zwrócić typ dozwolony `async` dla metody.</span><span class="sxs-lookup"><span data-stu-id="1d367-251">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="1d367-252">Zazwyczaj oznacza to powrót <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>lub .</span><span class="sxs-lookup"><span data-stu-id="1d367-252">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1d367-253">Może to być <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601>również lub .</span><span class="sxs-lookup"><span data-stu-id="1d367-253">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="1d367-254">Metoda może zarówno zużywać, jak i wytwarzać strumień asynchroniczne, co oznacza, że zwróci . <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="1d367-254">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="1d367-255">Poniższy kod generuje sekwencję od 0 do 19, oczekiwanie 100 ms między generowania każdej liczby:</span><span class="sxs-lookup"><span data-stu-id="1d367-255">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="1d367-256">Sekwencja należy wyliczyć `await foreach` za pomocą instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1d367-256">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="1d367-257">Możesz spróbować strumieni asynchronicznych samodzielnie w naszym tutorialu na [temat tworzenia i spożywania strumieni asynchnc](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-257">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="1d367-258">Domyślnie elementy strumienia są przetwarzane w kontekście przechwycone.</span><span class="sxs-lookup"><span data-stu-id="1d367-258">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="1d367-259">Jeśli chcesz wyłączyć przechwytywanie kontekstu, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> użyj metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1d367-259">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="1d367-260">Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [korzystania z wzorca asynchronicznego opartego](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniach .</span><span class="sxs-lookup"><span data-stu-id="1d367-260">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="asynchronous-disposable"></a><span data-ttu-id="1d367-261">Asynchroniczne jednorazowe</span><span class="sxs-lookup"><span data-stu-id="1d367-261">Asynchronous disposable</span></span>

<span data-ttu-id="1d367-262">Począwszy od języka C# 8.0, język obsługuje asynchroniczne jednorazowe typy, które implementują <xref:System.IAsyncDisposable?displayProperty=nameWithType> interfejs.</span><span class="sxs-lookup"><span data-stu-id="1d367-262">Starting with C# 8.0, the language supports asynchronous disposable types that implement the <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="1d367-263">Operand `using` wyrażenia można zaimplementować albo <xref:System.IDisposable> lub <xref:System.IAsyncDisposable>.</span><span class="sxs-lookup"><span data-stu-id="1d367-263">The operand of a `using` expression can implement either <xref:System.IDisposable> or <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="1d367-264">W przypadku `IAsyncDisposable`kompilator generuje kod `await` do <xref:System.Threading.Tasks.Task> zwracanego z <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1d367-264">In the case of `IAsyncDisposable`, the compiler generates code to `await` the <xref:System.Threading.Tasks.Task> returned from <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d367-265">Aby uzyskać więcej informacji, zobacz [ `using` instrukcję](../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-265">For more information, see the [`using` statement](../language-reference/keywords/using-statement.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="1d367-266">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="1d367-266">Indices and ranges</span></span>

<span data-ttu-id="1d367-267">Indeksy i zakresy zapewniają zwięzłą składnię dostępu do pojedynczych elementów lub zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1d367-267">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="1d367-268">Ta obsługa języka opiera się na dwóch nowych typach i dwóch nowych operatorach:</span><span class="sxs-lookup"><span data-stu-id="1d367-268">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="1d367-269"><xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1d367-269"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="1d367-270">Indeks z operatora `^`końcowego , który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1d367-270">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="1d367-271"><xref:System.Range?displayProperty=nameWithType>reprezentuje podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1d367-271"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="1d367-272">Operator `..`zakresu , który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="1d367-272">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="1d367-273">Zacznijmy od reguł dla indeksów.</span><span class="sxs-lookup"><span data-stu-id="1d367-273">Let's start with the rules for indexes.</span></span> <span data-ttu-id="1d367-274">Należy wziąć `sequence`pod uwagę tablicę .</span><span class="sxs-lookup"><span data-stu-id="1d367-274">Consider an array `sequence`.</span></span> <span data-ttu-id="1d367-275">Indeks `0` jest taki `sequence[0]`sam jak .</span><span class="sxs-lookup"><span data-stu-id="1d367-275">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="1d367-276">Indeks `^0` jest taki `sequence[sequence.Length]`sam jak .</span><span class="sxs-lookup"><span data-stu-id="1d367-276">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="1d367-277">Należy `sequence[^0]` zauważyć, że zgłasza `sequence[sequence.Length]` wyjątek, podobnie jak robi.</span><span class="sxs-lookup"><span data-stu-id="1d367-277">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="1d367-278">Dla dowolnej `n`liczby `^n` indeks jest `sequence.Length - n`taki sam jak .</span><span class="sxs-lookup"><span data-stu-id="1d367-278">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="1d367-279">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="1d367-279">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="1d367-280">Początek zakresu jest włącznie, ale koniec zakresu jest wyłączny, co oznacza, że *początek* jest uwzględniony w zakresie, ale *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1d367-280">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="1d367-281">Zakres `[0..^0]` reprezentuje cały zakres, `[0..sequence.Length]` podobnie jak reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="1d367-281">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="1d367-282">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="1d367-282">Let's look at a few examples.</span></span> <span data-ttu-id="1d367-283">Należy wziąć pod uwagę następującą tablicę, z adnotacjami z indeksem od początku i od końca:</span><span class="sxs-lookup"><span data-stu-id="1d367-283">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="1d367-284">Ostatnie słowo można pobrać za `^1` pomocą indeksu:</span><span class="sxs-lookup"><span data-stu-id="1d367-284">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="1d367-285">Poniższy kod tworzy podzakład z napisami "quick", "brown" i "fox".</span><span class="sxs-lookup"><span data-stu-id="1d367-285">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="1d367-286">Obejmuje `words[1]` ona `words[3]`poprzez .</span><span class="sxs-lookup"><span data-stu-id="1d367-286">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="1d367-287">Element `words[4]` nie jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1d367-287">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="1d367-288">Poniższy kod tworzy podzakład z "leniwy" i "pies".</span><span class="sxs-lookup"><span data-stu-id="1d367-288">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="1d367-289">Obejmuje `words[^2]` ona `words[^1]`i .</span><span class="sxs-lookup"><span data-stu-id="1d367-289">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="1d367-290">Indeks `words[^0]` końcowy nie jest uwzględniony:</span><span class="sxs-lookup"><span data-stu-id="1d367-290">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="1d367-291">Poniższe przykłady tworzą zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="1d367-291">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="1d367-292">Zakresy można również deklarować jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="1d367-292">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="1d367-293">Zakres może być następnie `[` używany `]` wewnątrz znaków i:</span><span class="sxs-lookup"><span data-stu-id="1d367-293">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="1d367-294">Nie tylko macierze obsługują indeksy i zakresy.</span><span class="sxs-lookup"><span data-stu-id="1d367-294">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="1d367-295">Można również używać indeksów i zakresów <xref:System.Span%601>z <xref:System.ReadOnlySpan%601> [ciągiem](../language-reference/builtin-types/reference-types.md#the-string-type), lub .</span><span class="sxs-lookup"><span data-stu-id="1d367-295">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="1d367-296">Aby uzyskać więcej informacji, zobacz [Obsługa typów indeksów i zakresów](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="1d367-296">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="1d367-297">Możesz dowiedzieć się więcej o indeksach i zakresach w samouczku na temat [indeksów i zakresów](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-297">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="1d367-298">Przypisanie scalania wartości null</span><span class="sxs-lookup"><span data-stu-id="1d367-298">Null-coalescing assignment</span></span>

<span data-ttu-id="1d367-299">C# 8.0 wprowadza operatora `??=`przypisania scalania wartości null .</span><span class="sxs-lookup"><span data-stu-id="1d367-299">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="1d367-300">`??=` Za pomocą operatora można przypisać wartość jego prawej opery do jego lewej operndu tylko wtedy, `null`gdy leworęczny operand ocenia .</span><span class="sxs-lookup"><span data-stu-id="1d367-300">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="1d367-301">Aby uzyskać więcej informacji, zobacz [?? i ?? = artykuł operatorów.](../language-reference/operators/null-coalescing-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1d367-301">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="1d367-302">Niezarządzane typy skonstruowane</span><span class="sxs-lookup"><span data-stu-id="1d367-302">Unmanaged constructed types</span></span>

<span data-ttu-id="1d367-303">W języku C# 7.3 i wcześniejszych typu konstruowanego (typu zawierającego co najmniej jeden argument typu) nie może być [typem niezarządzanym.](../language-reference/builtin-types/unmanaged-types.md)</span><span class="sxs-lookup"><span data-stu-id="1d367-303">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="1d367-304">Począwszy od języka C# 8.0, skonstruowany typ wartości jest niezarządzane, jeśli zawiera pola typu niezarządzanego tylko.</span><span class="sxs-lookup"><span data-stu-id="1d367-304">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="1d367-305">Na przykład, biorąc pod uwagę `Coords<T>` następującą definicję typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="1d367-305">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="1d367-306">`Coords<int>` typ jest typem niezarządzanym w języku C# 8.0 i nowszym.</span><span class="sxs-lookup"><span data-stu-id="1d367-306">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="1d367-307">Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:</span><span class="sxs-lookup"><span data-stu-id="1d367-307">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="1d367-308">Aby uzyskać więcej informacji, zobacz [Typy niezarządzane](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="1d367-308">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="1d367-309">Stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="1d367-309">Stackalloc in nested expressions</span></span>

<span data-ttu-id="1d367-310">Począwszy od języka C# 8.0, jeśli wynik wyrażenia <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> [stackalloc](../language-reference/operators/stackalloc.md) jest `stackalloc` typu lub, można użyć wyrażenia w innych wyrażeniach:</span><span class="sxs-lookup"><span data-stu-id="1d367-310">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="1d367-311">Wzmocnienie interpolowanych ciągów dosłownie</span><span class="sxs-lookup"><span data-stu-id="1d367-311">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="1d367-312">Kolejność `$` i `@` tokeny w [interpolowanych](../language-reference/tokens/interpolated.md) ciągów dosłownie może `$@"..."` być `@$"..."` dowolny: oba i są prawidłowe interpolowane dosłownie ciągi.</span><span class="sxs-lookup"><span data-stu-id="1d367-312">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="1d367-313">We wcześniejszych wersjach `$` języka C# `@` token musi pojawić się przed tokenem.</span><span class="sxs-lookup"><span data-stu-id="1d367-313">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
