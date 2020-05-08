---
title: Co nowego w języku C# 8,0 — przewodnik w języku C#
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w języku C# 8,0.
ms.date: 04/07/2020
ms.openlocfilehash: 27c2d7e2d6f0e665e7abe4fdcfb94c140224cc89
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895433"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="cf7a6-103">Co nowego w języku C# 8,0</span><span class="sxs-lookup"><span data-stu-id="cf7a6-103">What's new in C# 8.0</span></span>

<span data-ttu-id="cf7a6-104">W języku c# 8,0 dodano następujące funkcje i ulepszenia języka C#:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="cf7a6-105">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf7a6-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="cf7a6-106">Domyślne metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="cf7a6-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="cf7a6-107">[Ulepszenia dopasowania wzorców](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="cf7a6-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="cf7a6-108">Przełącz wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cf7a6-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="cf7a6-109">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="cf7a6-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="cf7a6-110">Wzorce krotek</span><span class="sxs-lookup"><span data-stu-id="cf7a6-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="cf7a6-111">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="cf7a6-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="cf7a6-112">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="cf7a6-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="cf7a6-113">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="cf7a6-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="cf7a6-114">Nierozporządzalne struktury ref</span><span class="sxs-lookup"><span data-stu-id="cf7a6-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="cf7a6-115">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="cf7a6-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="cf7a6-116">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="cf7a6-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="cf7a6-117">Asynchroniczne jednorazowe</span><span class="sxs-lookup"><span data-stu-id="cf7a6-117">Asynchronous disposable</span></span>](#asynchronous-disposable)
- [<span data-ttu-id="cf7a6-118">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="cf7a6-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="cf7a6-119">Przypisanie do łączenia o wartości null</span><span class="sxs-lookup"><span data-stu-id="cf7a6-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="cf7a6-120">Niezarządzane typy skonstruowane</span><span class="sxs-lookup"><span data-stu-id="cf7a6-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="cf7a6-121">Stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="cf7a6-121">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="cf7a6-122">Ulepszenie interpolowanych ciągów Verbatim</span><span class="sxs-lookup"><span data-stu-id="cf7a6-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="cf7a6-123">Język C# 8,0 jest obsługiwany w **programie .NET Core 3. x** i **.NET Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-123">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="cf7a6-124">Aby uzyskać więcej informacji, zobacz [wersja języka C#](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-124">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="cf7a6-125">W pozostałej części tego artykułu krótko opisano te funkcje.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-125">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="cf7a6-126">Tam, gdzie są dostępne szczegółowe artykuły, znajdują się linki do samouczków i przeglądów.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-126">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="cf7a6-127">Te funkcje można eksplorować w środowisku za pomocą narzędzia `dotnet try` globalnego:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-127">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="cf7a6-128">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-128">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="cf7a6-129">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="cf7a6-129">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="cf7a6-130">Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="cf7a6-130">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="cf7a6-131">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-131">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="cf7a6-132">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf7a6-132">Readonly members</span></span>

<span data-ttu-id="cf7a6-133">Można zastosować `readonly` modyfikator do elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-133">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="cf7a6-134">Wskazuje, że element członkowski nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-134">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="cf7a6-135">Jest to bardziej szczegółowe niż stosowanie `readonly` modyfikatora do `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-135">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="cf7a6-136">Weź pod uwagę następującą niemodyfikowalną strukturę:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-136">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="cf7a6-137">Podobnie jak większość struktur, `ToString()` Metoda nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-137">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="cf7a6-138">Można wskazać, że dodając `readonly` modyfikator do deklaracji: `ToString()`</span><span class="sxs-lookup"><span data-stu-id="cf7a6-138">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="cf7a6-139">Poprzednia zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp `Distance` do właściwości, która nie `readonly`jest oznaczona:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-139">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="cf7a6-140">Kompilator ostrzega o tym, gdy musi utworzyć kopię obronną.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-140">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="cf7a6-141">`Distance` Właściwość nie zmienia stanu, więc możesz naprawić to ostrzeżenie, dodając `readonly` modyfikator do deklaracji:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-141">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="cf7a6-142">Należy zauważyć, `readonly` że modyfikator jest konieczny dla właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-142">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="cf7a6-143">Kompilator nie zakłada, `get` że metody dostępu nie modyfikują stanu; należy zadeklarować `readonly` jawnie.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-143">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="cf7a6-144">Zaimplementowane właściwości są wyjątkiem; kompilator będzie `readonly`traktować wszystkie zaimplementowane metody pobierające jako, dlatego nie trzeba dodawać `readonly` modyfikatora do właściwości `X` i. `Y`</span><span class="sxs-lookup"><span data-stu-id="cf7a6-144">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as `readonly`, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="cf7a6-145">Kompilator wymusza zasadę, której `readonly` elementy członkowskie nie modyfikują stanu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-145">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="cf7a6-146">Następująca metoda nie zostanie skompilowana, chyba że usuniesz `readonly` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-146">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="cf7a6-147">Ta funkcja umożliwia określenie zamierzonego projektu, aby kompilator mógł go wymusić i dokonać optymalizacji na podstawie tego zamiaru.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-147">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

<span data-ttu-id="cf7a6-148">Aby uzyskać więcej informacji, zobacz sekcję [ `readonly` elementy członkowskie wystąpienia](../language-reference/builtin-types/struct.md#readonly-instance-members) w artykule [typy struktury](../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="cf7a6-148">For more information, see the [`readonly` instance members](../language-reference/builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../language-reference/builtin-types/struct.md) article.</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="cf7a6-149">Domyślne metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="cf7a6-149">Default interface methods</span></span>

<span data-ttu-id="cf7a6-150">Teraz można dodawać członków do interfejsów i dostarczać implementację dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-150">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="cf7a6-151">Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach, bez podzielenia zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-151">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="cf7a6-152">Istniejące implementacje *dziedziczą* implementację domyślną.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-152">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="cf7a6-153">Ta funkcja umożliwia również współdziałanie języka C# z interfejsami API przeznaczonymi dla systemu Android lub SWIFT, które obsługują podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-153">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="cf7a6-154">Domyślne metody interfejsu zapewniają również scenariusze podobne do funkcji języka "cechy".</span><span class="sxs-lookup"><span data-stu-id="cf7a6-154">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="cf7a6-155">Domyślne metody interfejsu mają wpływ na wiele scenariuszy i elementów języka.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-155">Default interface methods affect many scenarios and language elements.</span></span> <span data-ttu-id="cf7a6-156">W pierwszym samouczku omówiono [aktualizowanie interfejsu przy użyciu domyślnych implementacji](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-156">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="cf7a6-157">Inne samouczki i aktualizacje referencyjne są dostępne w czasie do wydania ogólnego.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-157">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="cf7a6-158">Więcej wzorców w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="cf7a6-158">More patterns in more places</span></span>

<span data-ttu-id="cf7a6-159">**Dopasowanie wzorców** oferuje narzędzia do zapewniania funkcji zależnych od kształtu między powiązanymi, ale różnymi rodzajami danych.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-159">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="cf7a6-160">W języku C# 7,0 wprowadzono składnię wzorców typów i wzorców stałych przy [`is`](../language-reference/keywords/is.md) użyciu wyrażenia i [`switch`](../language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-160">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="cf7a6-161">Te funkcje przedstawiają pierwsze wstępnie wymagane kroki w kierunku obsługi odmian programistycznych, w których dane i funkcje są aktywne.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-161">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="cf7a6-162">Gdy branża jest przenoszona do większej liczby mikrousług i architektur opartych na chmurze, inne narzędzia języka są zbędne.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-162">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="cf7a6-163">Język C# 8,0 rozszerza ten słownik, aby można było używać więcej wyrażeń wzorca w większej liczbie miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-163">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="cf7a6-164">Te funkcje należy wziąć pod uwagę, gdy dane i funkcje są osobne.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-164">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="cf7a6-165">Rozważ dopasowanie wzorców, gdy algorytmy zależą od faktu innego niż typ środowiska uruchomieniowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-165">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="cf7a6-166">Techniki te zapewniają inny sposób tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-166">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="cf7a6-167">Oprócz nowych wzorców w nowych miejscach, C# 8,0 dodaje **cykliczne wzorce**.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-167">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="cf7a6-168">Wynikiem dowolnego wyrażenia wzorca jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-168">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="cf7a6-169">Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-169">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="cf7a6-170">Przełącz wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cf7a6-170">Switch expressions</span></span>

<span data-ttu-id="cf7a6-171">Często [`switch`](../language-reference/keywords/switch.md) instrukcja generuje wartość w każdym z jego `case` bloków.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-171">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="cf7a6-172">**Wyrażenia Switch** umożliwiają użycie bardziej zwięzłej składni wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-172">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="cf7a6-173">Jest mniej powtarzające `case` się `break` i słowa kluczowe i mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-173">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="cf7a6-174">Na przykład rozważmy następujące Wyliczenie, które zawiera listę kolorów tęczu:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-174">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="cf7a6-175">Jeśli aplikacja definiuje `RGBColor` typ, który jest zbudowany ze składników `R`, `G` i `B` , można skonwertować `Rainbow` wartość na wartości RGB przy użyciu następującej metody zawierającej wyrażenie Switch:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-175">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="cf7a6-176">Poniżej przedstawiono kilka ulepszeń składni:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-176">There are several syntax improvements here:</span></span>

- <span data-ttu-id="cf7a6-177">Zmienna jest wcześniejsza niż `switch` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-177">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="cf7a6-178">Inna kolejność ułatwia odróżnienie wyrażenia Switch od instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-178">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="cf7a6-179">Elementy `case` i `:` są zamieniane na `=>`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-179">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="cf7a6-180">Jest to bardziej zwięzłe i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-180">It's more concise and intuitive.</span></span>
- <span data-ttu-id="cf7a6-181">`default` Przypadek jest zastępowany `_` odrzuceniem.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-181">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="cf7a6-182">Treść to wyrażenia, a nie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-182">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="cf7a6-183">Kontrast, który ma odpowiedni kod przy użyciu instrukcji `switch` klasycznej:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-183">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="cf7a6-184">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="cf7a6-184">Property patterns</span></span>

<span data-ttu-id="cf7a6-185">**Wzorzec właściwości** pozwala dopasować się do właściwości badanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-185">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="cf7a6-186">Rozważmy witrynę handlu elektronicznego, która musi obliczać podatek od sprzedaży na podstawie adresu kupującego.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-186">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="cf7a6-187">To obliczenie nie jest zasadniczą odpowiedzialnością `Address` klasy.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-187">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="cf7a6-188">Zostanie ona zmieniona z upływem czasu, co prawdopodobnie częściej niż zmienia format adresu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-188">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="cf7a6-189">Podatek od sprzedaży zależy od `State` właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-189">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="cf7a6-190">Poniższa metoda używa wzorca właściwości do obliczania podatku od adresu i ceny:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-190">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.075M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="cf7a6-191">Dopasowanie wzorca tworzy zwięzłą składnię do wyrażania tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-191">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="cf7a6-192">Wzorce krotek</span><span class="sxs-lookup"><span data-stu-id="cf7a6-192">Tuple patterns</span></span>

<span data-ttu-id="cf7a6-193">Niektóre algorytmy zależą od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-193">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="cf7a6-194">**Wzorce krotek** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako [krotka](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-194">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="cf7a6-195">Poniższy kod przedstawia wyrażenie Switch dla *skały, papieru, nożyczków*:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-195">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="cf7a6-196">Komunikaty wskazują zwycięzcę.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-196">The messages indicate the winner.</span></span> <span data-ttu-id="cf7a6-197">Przypadek odrzucania reprezentuje trzy kombinacje powiązań lub inne dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-197">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="cf7a6-198">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="cf7a6-198">Positional patterns</span></span>

<span data-ttu-id="cf7a6-199">Niektóre typy obejmują `Deconstruct` metodę, która dekonstrukcjauje swoje właściwości do zmiennych dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-199">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="cf7a6-200">Gdy `Deconstruct` Metoda jest dostępna, można użyć **wzorców pozycyjnych** do inspekcji właściwości obiektu i używania tych właściwości dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-200">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="cf7a6-201">Rozważmy następujące `Point` klasy, które obejmują `Deconstruct` metodę tworzenia zmiennych dyskretnych dla `X` i `Y`:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-201">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="cf7a6-202">Dodatkowo Rozważmy następujące Wyliczenie, które reprezentuje różne położenia ćwiartki:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-202">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="cf7a6-203">Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i. `y`</span><span class="sxs-lookup"><span data-stu-id="cf7a6-203">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="cf7a6-204">Następnie używa `when` klauzuli do określenia `Quadrant` punktu:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-204">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="cf7a6-205">Odrzuć wzorzec w poprzednim przełączniku dopasowuje się `x` , `y` gdy lub ma wartość 0, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-205">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="cf7a6-206">Wyrażenie Switch musi utworzyć wartość lub zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-206">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="cf7a6-207">Jeśli żaden z przypadków nie jest zgodny, wyrażenie Switch zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-207">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="cf7a6-208">Kompilator generuje ostrzeżenie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu Switch.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-208">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="cf7a6-209">Techniki dopasowania wzorców można eksplorować w tym [zaawansowanym samouczku dotyczącym dopasowania wzorców](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-209">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="cf7a6-210">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="cf7a6-210">Using declarations</span></span>

<span data-ttu-id="cf7a6-211">**Deklaracja using** jest deklaracją zmiennej poprzedzoną `using` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-211">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="cf7a6-212">Informuje kompilator, że zadeklarowana zmienna powinna zostać usunięta na końcu otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-212">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="cf7a6-213">Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-213">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="cf7a6-214">W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-214">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="cf7a6-215">To koniec zakresu, w którym `file` jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-215">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="cf7a6-216">Poprzedni kod jest odpowiednikiem poniższego kodu, który używa klasycznej [instrukcji using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="cf7a6-216">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="cf7a6-217">W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego skojarzonego `using` z instrukcją.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-217">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="cf7a6-218">W obu przypadkach kompilator generuje wywołanie `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-218">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="cf7a6-219">Kompilator generuje błąd, jeśli wyrażenie w `using` instrukcji nie jest jednorazowe.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-219">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="cf7a6-220">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="cf7a6-220">Static local functions</span></span>

<span data-ttu-id="cf7a6-221">Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (nie dotyczy) żadnych zmiennych z zakresu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-221">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="cf7a6-222">Spowoduje to wygenerowanie `CS8421`, "statyczna funkcja lokalna nie może zawierać odwołania \<do zmiennej>".</span><span class="sxs-lookup"><span data-stu-id="cf7a6-222">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="cf7a6-223">Rozważmy następujący kod.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-223">Consider the following code.</span></span> <span data-ttu-id="cf7a6-224">Funkcja `LocalFunction` lokalna uzyskuje dostęp do zmiennej `y`zadeklarowanej w zakresie otaczającym (Metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-224">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="cf7a6-225">W związku `LocalFunction` z tym nie można zadeklarować z `static` modyfikatorem:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-225">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="cf7a6-226">Poniższy kod zawiera statyczną funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-226">The following code contains a static local function.</span></span> <span data-ttu-id="cf7a6-227">Może być statyczny, ponieważ nie uzyskuje dostępu do żadnych zmiennych w otaczającym zakresie:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-227">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="cf7a6-228">Nierozporządzalne struktury ref</span><span class="sxs-lookup"><span data-stu-id="cf7a6-228">Disposable ref structs</span></span>

<span data-ttu-id="cf7a6-229">`struct` Deklaracja z `ref` modyfikatorem nie może implementować żadnych interfejsów i dlatego nie może <xref:System.IDisposable>implementować.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-229">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="cf7a6-230">W związku z tym, `ref struct` aby można było usunąć element, musi on mieć `void Dispose()` dostępną metodę.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-230">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="cf7a6-231">Ta funkcja dotyczy również `readonly ref struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-231">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="cf7a6-232">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="cf7a6-232">Nullable reference types</span></span>

<span data-ttu-id="cf7a6-233">Wewnątrz bezwartościowego kontekstu adnotacji Każda zmienna typu referencyjnego jest uważana za **typ referencyjny, który nie ma wartości null**.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-233">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="cf7a6-234">Aby wskazać, że zmienna może mieć wartość null, należy dołączyć nazwę typu z, `?` aby zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null**.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-234">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="cf7a6-235">W przypadku typów referencyjnych, które nie mają wartości null, kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null, gdy zostanie zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-235">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="cf7a6-236">Pola muszą być inicjowane podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-236">Fields must be initialized during construction.</span></span> <span data-ttu-id="cf7a6-237">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiana przez wywołanie do któregokolwiek z dostępnych konstruktorów lub inicjatora.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-237">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="cf7a6-238">Ponadto nie można przypisać wartości, która może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-238">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="cf7a6-239">Typy odwołań dopuszczających wartość null nie są sprawdzane w celu zapewnienia, że nie są przypisane ani zainicjowane do wartości null.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-239">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="cf7a6-240">Jednak kompilator używa analizy przepływu, aby upewnić się, że jakakolwiek zmienna typu referencyjnego null jest sprawdzana pod kątem wartości null przed uzyskaniem dostępu lub przypisaniem do niezerowego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-240">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="cf7a6-241">Więcej informacji na temat funkcji można znaleźć w omówieniu [typów referencyjnych dopuszczających wartość null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-241">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="cf7a6-242">Wypróbuj go samodzielnie w nowej aplikacji w tym [samouczku typów odwołań dopuszczających wartość null](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-242">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="cf7a6-243">Zapoznaj się z instrukcjami dotyczącymi migracji istniejącej bazy kodu w celu użycia w [samouczku Migrowanie aplikacji do korzystania](../tutorials/upgrade-to-nullable-references.md)z typów odwołań dopuszczających wartość null.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-243">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="cf7a6-244">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="cf7a6-244">Asynchronous streams</span></span>

<span data-ttu-id="cf7a6-245">Począwszy od języka C# 8,0, można tworzyć strumienie i korzystać z nich asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-245">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="cf7a6-246">Metoda zwracająca strumień asynchroniczny ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-246">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="cf7a6-247">Jest on zadeklarowany z `async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-247">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="cf7a6-248">Zwraca wartość <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-248">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="cf7a6-249">Metoda zawiera `yield return` instrukcje do zwrócenia kolejnych elementów w strumieniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-249">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="cf7a6-250">Użycie strumienia asynchronicznego wymaga dodania `await` słowa kluczowego przed `foreach` słowem kluczowym podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-250">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="cf7a6-251">Dodanie `await` słowa kluczowego wymaga metody, która wylicza strumień asynchroniczny, który ma zostać zadeklarowany z `async` modyfikatorem i zwraca typ dozwolony dla `async` metody.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-251">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="cf7a6-252">Zwykle oznacza to zwrócenie <xref:System.Threading.Tasks.Task> lub. <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="cf7a6-252">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="cf7a6-253">Może być również <xref:System.Threading.Tasks.ValueTask> lub <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-253">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="cf7a6-254">Metoda może jednocześnie zużywać i generować strumień asynchroniczny, co oznacza, że zwróci <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-254">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="cf7a6-255">Poniższy kod generuje sekwencję z przedziału od 0 do 19, oczekującą 100 ms między generowaniem każdej liczby:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-255">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="cf7a6-256">Sekwencję można wyliczyć przy użyciu `await foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-256">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="cf7a6-257">Możesz samodzielnie wypróbować strumienie asynchroniczne w naszym samouczku dotyczącym [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-257">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="cf7a6-258">Domyślnie elementy strumienia są przetwarzane w przechwyconym kontekście.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-258">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="cf7a6-259">Jeśli chcesz wyłączyć przechwytywanie kontekstu, użyj metody <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-259">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="cf7a6-260">Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [konsumowania wzorca asynchronicznego opartego na zadaniach](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-260">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="asynchronous-disposable"></a><span data-ttu-id="cf7a6-261">Asynchroniczne jednorazowe</span><span class="sxs-lookup"><span data-stu-id="cf7a6-261">Asynchronous disposable</span></span>

<span data-ttu-id="cf7a6-262">Począwszy od języka C# 8,0, język obsługuje asynchroniczne typy jednorazowe, które <xref:System.IAsyncDisposable?displayProperty=nameWithType> implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-262">Starting with C# 8.0, the language supports asynchronous disposable types that implement the <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="cf7a6-263">Operand `using` wyrażenia może implementować jedną <xref:System.IDisposable> lub. <xref:System.IAsyncDisposable></span><span class="sxs-lookup"><span data-stu-id="cf7a6-263">The operand of a `using` expression can implement either <xref:System.IDisposable> or <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="cf7a6-264">W przypadku `IAsyncDisposable`, kompilator generuje kod do `await` <xref:System.Threading.Tasks.Task> zwróconych z. <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cf7a6-264">In the case of `IAsyncDisposable`, the compiler generates code to `await` the <xref:System.Threading.Tasks.Task> returned from <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cf7a6-265">Aby uzyskać więcej informacji, zobacz [ `using` instrukcję](../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-265">For more information, see the [`using` statement](../language-reference/keywords/using-statement.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="cf7a6-266">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="cf7a6-266">Indices and ranges</span></span>

<span data-ttu-id="cf7a6-267">Indeksy i zakresy zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-267">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="cf7a6-268">Ten język obsługuje dwa nowe typy i dwa nowe operatory:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-268">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="cf7a6-269"><xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-269"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="cf7a6-270">Indeks od operatora `^`końcowego, który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-270">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="cf7a6-271"><xref:System.Range?displayProperty=nameWithType>reprezentuje Podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-271"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="cf7a6-272">Operator `..`zakresu, który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-272">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="cf7a6-273">Zacznijmy od reguł dotyczących indeksów.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-273">Let's start with the rules for indexes.</span></span> <span data-ttu-id="cf7a6-274">Weź pod uwagę `sequence`tablicę.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-274">Consider an array `sequence`.</span></span> <span data-ttu-id="cf7a6-275">`0` Indeks jest taki sam jak `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-275">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="cf7a6-276">`^0` Indeks jest taki sam jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-276">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="cf7a6-277">Należy pamiętać `sequence[^0]` , że generuje wyjątek, podobnie jak `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="cf7a6-277">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="cf7a6-278">Dla dowolnej liczby `n`indeks `^n` jest taki sam jak `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-278">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="cf7a6-279">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-279">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="cf7a6-280">Początek zakresu jest włączony, ale koniec zakresu jest na wyłączność, co oznacza, że *początek* znajduje się w zakresie, ale *końcowy* nie należy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-280">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="cf7a6-281">Zakres `[0..^0]` reprezentuje cały zakres, tak jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-281">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="cf7a6-282">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-282">Let's look at a few examples.</span></span> <span data-ttu-id="cf7a6-283">Rozważmy następującą tablicę zawierającą adnotację z jej indeksem od początku i od końca:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-283">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="cf7a6-284">Możesz pobrać ostatni wyraz z `^1` indeksem:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-284">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="cf7a6-285">Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox".</span><span class="sxs-lookup"><span data-stu-id="cf7a6-285">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="cf7a6-286">Zawiera `words[1]` `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-286">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="cf7a6-287">Element `words[4]` nie należy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-287">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="cf7a6-288">Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog".</span><span class="sxs-lookup"><span data-stu-id="cf7a6-288">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="cf7a6-289">Obejmuje `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-289">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="cf7a6-290">Indeks `words[^0]` końcowy nie jest uwzględniony:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-290">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="cf7a6-291">W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-291">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="cf7a6-292">Można również zadeklarować zakresy jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-292">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="cf7a6-293">Zakres może być następnie używany wewnątrz znaków `[` i: `]`</span><span class="sxs-lookup"><span data-stu-id="cf7a6-293">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="cf7a6-294">Nie tylko tablice obsługują indeksy i zakresy.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-294">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="cf7a6-295">Można również użyć indeksów i zakresów z [ciągiem](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-295">You can also use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="cf7a6-296">Aby uzyskać więcej informacji, zobacz [Obsługa typów indeksów i zakresów](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-296">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="cf7a6-297">Więcej informacji o indeksach i zakresach można dowiedzieć się w samouczku dotyczącym [indeksów i zakresów](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-297">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="cf7a6-298">Przypisanie do łączenia o wartości null</span><span class="sxs-lookup"><span data-stu-id="cf7a6-298">Null-coalescing assignment</span></span>

<span data-ttu-id="cf7a6-299">W języku C# 8,0 wprowadzono operator `??=`przypisania łączenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-299">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="cf7a6-300">`??=` Operatora można używać do przypisywania wartości operandu po prawej stronie do jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie jest obliczany `null`.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-300">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="cf7a6-301">Aby uzyskać więcej informacji, zobacz [? =](../language-reference/operators/null-coalescing-operator.md) — artykuł.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-301">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="cf7a6-302">Niezarządzane typy skonstruowane</span><span class="sxs-lookup"><span data-stu-id="cf7a6-302">Unmanaged constructed types</span></span>

<span data-ttu-id="cf7a6-303">W języku C# 7,3 i starszych, typ skonstruowany (typ, który zawiera co najmniej jeden argument typu) nie może być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-303">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="cf7a6-304">Począwszy od języka C# 8,0, skonstruowany typ wartości jest niezarządzany, jeśli zawiera pola tylko typów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-304">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="cf7a6-305">Na przykład, uwzględniając następującą definicję typu ogólnego `Coords<T>` :</span><span class="sxs-lookup"><span data-stu-id="cf7a6-305">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="cf7a6-306">`Coords<int>` typ jest typem niezarządzanym w języku C# 8,0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-306">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="cf7a6-307">Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-307">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="cf7a6-308">Aby uzyskać więcej informacji, zobacz [typy niezarządzane](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a6-308">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="cf7a6-309">Stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="cf7a6-309">Stackalloc in nested expressions</span></span>

<span data-ttu-id="cf7a6-310">Począwszy od języka C# 8,0, jeśli wynik wyrażenia [stackalloc](../language-reference/operators/stackalloc.md) jest typu <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , można użyć `stackalloc` wyrażenia w innych wyrażeniach:</span><span class="sxs-lookup"><span data-stu-id="cf7a6-310">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="cf7a6-311">Ulepszenie interpolowanych ciągów Verbatim</span><span class="sxs-lookup"><span data-stu-id="cf7a6-311">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="cf7a6-312">Kolejność tokenów `$` i `@` w [interpolowanych](../language-reference/tokens/interpolated.md) ciągach Verbatim może być dowolna: `$@"..."` oba `@$"..."` i są prawidłowymi interpolowanymi ciągami Verbatim.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-312">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="cf7a6-313">We wcześniejszych wersjach języka C# `$` token musi znajdować się przed `@` tokenem.</span><span class="sxs-lookup"><span data-stu-id="cf7a6-313">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
