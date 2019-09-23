---
title: Co nowego w C# 8,0 — C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w C# 8,0. Ten artykuł jest aktualny w wersji zapoznawczej 5.
ms.date: 09/20/2019
ms.openlocfilehash: a434d1f7598bc3f6787f7466e48fb161db192761
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182409"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="c0445-104">Co nowego w C# 8,0</span><span class="sxs-lookup"><span data-stu-id="c0445-104">What's new in C# 8.0</span></span>

<span data-ttu-id="c0445-105">Istnieje wiele ulepszeń C# języka, który można wypróbować już.</span><span class="sxs-lookup"><span data-stu-id="c0445-105">There are many enhancements to the C# language that you can try out already.</span></span>

- [<span data-ttu-id="c0445-106">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c0445-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="c0445-107">Domyślne elementy członkowskie interfejsu</span><span class="sxs-lookup"><span data-stu-id="c0445-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="c0445-108">[Ulepszenia dopasowania wzorców](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="c0445-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="c0445-109">Przełącz wyrażenia</span><span class="sxs-lookup"><span data-stu-id="c0445-109">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="c0445-110">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="c0445-110">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="c0445-111">Wzorce krotek</span><span class="sxs-lookup"><span data-stu-id="c0445-111">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="c0445-112">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="c0445-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="c0445-113">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="c0445-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="c0445-114">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="c0445-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="c0445-115">Nierozporządzalne struktury ref</span><span class="sxs-lookup"><span data-stu-id="c0445-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="c0445-116">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="c0445-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="c0445-117">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="c0445-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="c0445-118">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="c0445-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="c0445-119">Przypisanie do łączenia o wartości null</span><span class="sxs-lookup"><span data-stu-id="c0445-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="c0445-120">Niezarządzane typy skonstruowane</span><span class="sxs-lookup"><span data-stu-id="c0445-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="c0445-121">stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="c0445-121">stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="c0445-122">Ulepszenie interpolowanych ciągów Verbatim</span><span class="sxs-lookup"><span data-stu-id="c0445-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> <span data-ttu-id="c0445-123">Ten artykuł został ostatnio zaktualizowany do C# wersji 8,0 Preview 5.</span><span class="sxs-lookup"><span data-stu-id="c0445-123">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="c0445-124">W pozostałej części tego artykułu krótko opisano te funkcje.</span><span class="sxs-lookup"><span data-stu-id="c0445-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="c0445-125">Tam, gdzie są dostępne szczegółowe artykuły, znajdują się linki do samouczków i przeglądów.</span><span class="sxs-lookup"><span data-stu-id="c0445-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="c0445-126">Te funkcje można eksplorować w środowisku za pomocą `dotnet try` narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="c0445-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="c0445-127">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="c0445-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="c0445-128">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="c0445-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="c0445-129">Ustaw bieżący katalog na podkatalog *csharp8* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="c0445-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="c0445-130">Uruchom `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="c0445-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="c0445-131">Elementy członkowskie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c0445-131">Readonly members</span></span>

<span data-ttu-id="c0445-132">Można zastosować `readonly` modyfikator do dowolnego elementu członkowskiego struktury.</span><span class="sxs-lookup"><span data-stu-id="c0445-132">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="c0445-133">Wskazuje, że element członkowski nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="c0445-133">It indicates that the member does not modify state.</span></span> <span data-ttu-id="c0445-134">Jest to bardziej szczegółowe niż stosowanie `readonly` modyfikatora `struct` do deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c0445-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="c0445-135">Weź pod uwagę następującą niemodyfikowalną strukturę:</span><span class="sxs-lookup"><span data-stu-id="c0445-135">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="c0445-136">Podobnie jak większość struktur, `ToString()` Metoda nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="c0445-136">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="c0445-137">Można wskazać, że dodając `readonly` modyfikator do `ToString()`deklaracji:</span><span class="sxs-lookup"><span data-stu-id="c0445-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="c0445-138">Poprzednia zmiana generuje ostrzeżenie kompilatora, ponieważ `ToString` uzyskuje dostęp `Distance` do właściwości, która nie jest `readonly`oznaczona:</span><span class="sxs-lookup"><span data-stu-id="c0445-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="c0445-139">Kompilator ostrzega o tym, gdy musi utworzyć kopię obronną.</span><span class="sxs-lookup"><span data-stu-id="c0445-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="c0445-140">Właściwość nie zmienia stanu, więc możesz naprawić to ostrzeżenie, `readonly` dodając modyfikator do deklaracji: `Distance`</span><span class="sxs-lookup"><span data-stu-id="c0445-140">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="c0445-141">Należy zauważyć, `readonly` że modyfikator jest konieczny dla właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c0445-141">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="c0445-142">Kompilator nie zakłada `get` , że metody dostępu nie modyfikują stanu; należy zadeklarować `readonly` jawnie.</span><span class="sxs-lookup"><span data-stu-id="c0445-142">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="c0445-143">Kompilator wymusza zasadę, której `readonly` elementy członkowskie nie modyfikują stanu.</span><span class="sxs-lookup"><span data-stu-id="c0445-143">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="c0445-144">Następująca metoda nie zostanie skompilowana, chyba że zostanie usunięty `readonly` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="c0445-144">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="c0445-145">Ta funkcja umożliwia określenie zamierzonego projektu, aby kompilator mógł go wymusić i dokonać optymalizacji na podstawie tego zamiaru.</span><span class="sxs-lookup"><span data-stu-id="c0445-145">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="c0445-146">Domyślne elementy członkowskie interfejsu</span><span class="sxs-lookup"><span data-stu-id="c0445-146">Default interface members</span></span>

<span data-ttu-id="c0445-147">Teraz można dodawać członków do interfejsów i dostarczać implementację dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="c0445-147">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="c0445-148">Ta funkcja języka umożliwia autorom interfejsu API dodawanie metod do interfejsu w nowszych wersjach, bez podzielenia zgodności źródłowej lub binarnej z istniejącymi implementacjami tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c0445-148">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="c0445-149">Istniejące implementacje *dziedziczą* implementację domyślną.</span><span class="sxs-lookup"><span data-stu-id="c0445-149">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="c0445-150">Ta funkcja umożliwia C# również współdziałanie z interfejsami API przeznaczonymi dla systemu Android lub SWIFT, które obsługują podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="c0445-150">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="c0445-151">Domyślne elementy członkowskie interfejsu umożliwiają również scenariusze podobne do funkcji języka "cechy".</span><span class="sxs-lookup"><span data-stu-id="c0445-151">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="c0445-152">Domyślne elementy członkowskie interfejsu mają wpływ na wiele scenariuszy i elementów języka.</span><span class="sxs-lookup"><span data-stu-id="c0445-152">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="c0445-153">W pierwszym samouczku omówiono [aktualizowanie interfejsu przy użyciu domyślnych implementacji](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-153">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="c0445-154">Inne samouczki i aktualizacje referencyjne są dostępne w czasie do wydania ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c0445-154">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="c0445-155">Więcej wzorców w większej liczbie miejsc</span><span class="sxs-lookup"><span data-stu-id="c0445-155">More patterns in more places</span></span>

<span data-ttu-id="c0445-156">**Dopasowanie wzorców** oferuje narzędzia do zapewniania funkcji zależnych od kształtu między powiązanymi, ale różnymi rodzajami danych.</span><span class="sxs-lookup"><span data-stu-id="c0445-156">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="c0445-157">C#7,0 wprowadzono składnię dla wzorców typu i wzorców stałych przy użyciu [`is`](../language-reference/keywords/is.md) wyrażenia [`switch`](../language-reference/keywords/switch.md) i instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c0445-157">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="c0445-158">Te funkcje przedstawiają pierwsze wstępnie wymagane kroki w kierunku obsługi odmian programistycznych, w których dane i funkcje są aktywne.</span><span class="sxs-lookup"><span data-stu-id="c0445-158">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="c0445-159">Gdy branża jest przenoszona do większej liczby mikrousług i architektur opartych na chmurze, inne narzędzia języka są zbędne.</span><span class="sxs-lookup"><span data-stu-id="c0445-159">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="c0445-160">C#8,0 rozwija ten słownik, aby można było używać więcej wyrażeń wzorca w większej liczbie miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c0445-160">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="c0445-161">Te funkcje należy wziąć pod uwagę, gdy dane i funkcje są osobne.</span><span class="sxs-lookup"><span data-stu-id="c0445-161">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="c0445-162">Rozważ dopasowanie wzorców, gdy algorytmy zależą od faktu innego niż typ środowiska uruchomieniowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c0445-162">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="c0445-163">Techniki te zapewniają inny sposób tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="c0445-163">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="c0445-164">Oprócz nowych wzorców w nowych miejscach, C# 8,0 dodaje cykliczne **wzorce**.</span><span class="sxs-lookup"><span data-stu-id="c0445-164">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="c0445-165">Wynikiem dowolnego wyrażenia wzorca jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="c0445-165">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="c0445-166">Wzorzec cykliczny jest po prostu wyrażeniem wzorca zastosowanym do danych wyjściowych innego wyrażenia wzorca.</span><span class="sxs-lookup"><span data-stu-id="c0445-166">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="c0445-167">Przełącz wyrażenia</span><span class="sxs-lookup"><span data-stu-id="c0445-167">switch expressions</span></span>

<span data-ttu-id="c0445-168">Często instrukcja generuje wartość w każdym z jego `case` bloków. [`switch`](../language-reference/keywords/switch.md)</span><span class="sxs-lookup"><span data-stu-id="c0445-168">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="c0445-169">**Wyrażenia Switch** umożliwiają użycie bardziej zwięzłej składni wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="c0445-169">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="c0445-170">Jest mniej powtarzające `case` się `break` i słowa kluczowe i mniej nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="c0445-170">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="c0445-171">Na przykład rozważmy następujące Wyliczenie, które zawiera listę kolorów tęczu:</span><span class="sxs-lookup"><span data-stu-id="c0445-171">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="c0445-172">Jeśli aplikacja `RGBColor` definiuje typ, który jest zbudowany `G` `R`ze składników, i `B` , można skonwertować `Rainbow` wartość na wartości RGB przy użyciu następującej metody zawierającej wyrażenie Switch:</span><span class="sxs-lookup"><span data-stu-id="c0445-172">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="c0445-173">Poniżej przedstawiono kilka ulepszeń składni:</span><span class="sxs-lookup"><span data-stu-id="c0445-173">There are several syntax improvements here:</span></span>

- <span data-ttu-id="c0445-174">Zmienna jest wcześniejsza niż `switch` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c0445-174">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="c0445-175">Inna kolejność ułatwia odróżnienie wyrażenia Switch od instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="c0445-175">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="c0445-176">Elementy `case` `=>`i `:` są zamieniane na.</span><span class="sxs-lookup"><span data-stu-id="c0445-176">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="c0445-177">Jest to bardziej zwięzłe i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="c0445-177">It's more concise and intuitive.</span></span>
- <span data-ttu-id="c0445-178">Przypadek jest zastępowany `_`odrzuceniem. `default`</span><span class="sxs-lookup"><span data-stu-id="c0445-178">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="c0445-179">Treść to wyrażenia, a nie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="c0445-179">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="c0445-180">Kontrast, który ma odpowiedni kod przy użyciu instrukcji `switch` klasycznej:</span><span class="sxs-lookup"><span data-stu-id="c0445-180">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="c0445-181">Wzorce właściwości</span><span class="sxs-lookup"><span data-stu-id="c0445-181">Property patterns</span></span>

<span data-ttu-id="c0445-182">**Wzorzec właściwości** pozwala dopasować się do właściwości badanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c0445-182">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="c0445-183">Rozważmy witrynę handlu elektronicznego, która musi obliczać podatek od sprzedaży na podstawie adresu kupującego.</span><span class="sxs-lookup"><span data-stu-id="c0445-183">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="c0445-184">To obliczenie nie jest podstawową odpowiedzialnością `Address` klasy.</span><span class="sxs-lookup"><span data-stu-id="c0445-184">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="c0445-185">Zostanie ona zmieniona z upływem czasu, co prawdopodobnie częściej niż zmienia format adresu.</span><span class="sxs-lookup"><span data-stu-id="c0445-185">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="c0445-186">Podatek od sprzedaży zależy `State` od właściwości adresu.</span><span class="sxs-lookup"><span data-stu-id="c0445-186">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="c0445-187">Poniższa metoda używa wzorca właściwości do obliczania podatku od adresu i ceny:</span><span class="sxs-lookup"><span data-stu-id="c0445-187">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="c0445-188">Dopasowanie wzorca tworzy zwięzłą składnię do wyrażania tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="c0445-188">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="c0445-189">Wzorce krotek</span><span class="sxs-lookup"><span data-stu-id="c0445-189">Tuple patterns</span></span>

<span data-ttu-id="c0445-190">Niektóre algorytmy zależą od wielu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="c0445-190">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="c0445-191">**Wzorce krotek** umożliwiają przełączanie na podstawie wielu wartości wyrażonych jako krotka [](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-191">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="c0445-192">Poniższy kod przedstawia wyrażenie Switch dla *skały, papieru, nożyczków*:</span><span class="sxs-lookup"><span data-stu-id="c0445-192">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="c0445-193">Komunikaty wskazują zwycięzcę.</span><span class="sxs-lookup"><span data-stu-id="c0445-193">The messages indicate the winner.</span></span> <span data-ttu-id="c0445-194">Przypadek odrzucania reprezentuje trzy kombinacje powiązań lub inne dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="c0445-194">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="c0445-195">Wzorce pozycyjne</span><span class="sxs-lookup"><span data-stu-id="c0445-195">Positional patterns</span></span>

<span data-ttu-id="c0445-196">Niektóre typy obejmują `Deconstruct` metodę, która dekonstrukcjauje swoje właściwości do zmiennych dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="c0445-196">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="c0445-197">Gdy metoda jest dostępna, można użyć wzorców pozycyjnych do inspekcji właściwości obiektu i używania tych właściwości dla wzorca. `Deconstruct`</span><span class="sxs-lookup"><span data-stu-id="c0445-197">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="c0445-198">Rozważmy następujące `Point` klasy, które `Deconstruct` obejmują metodę tworzenia zmiennych dyskretnych dla `X` i `Y`:</span><span class="sxs-lookup"><span data-stu-id="c0445-198">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="c0445-199">Dodatkowo Rozważmy następujące Wyliczenie, które reprezentuje różne położenia ćwiartki:</span><span class="sxs-lookup"><span data-stu-id="c0445-199">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="c0445-200">Poniższa metoda używa **wzorca pozycyjnego** do wyodrębnienia wartości `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="c0445-200">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="c0445-201">Następnie używa `when` klauzuli do `Quadrant` określenia punktu:</span><span class="sxs-lookup"><span data-stu-id="c0445-201">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="c0445-202">Odrzuć wzorzec w poprzednim przełączniku dopasowuje się `x` , `y` gdy lub ma wartość 0, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="c0445-202">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="c0445-203">Wyrażenie Switch musi utworzyć wartość lub zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c0445-203">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="c0445-204">Jeśli żaden z przypadków nie jest zgodny, wyrażenie Switch zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c0445-204">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="c0445-205">Kompilator generuje ostrzeżenie, jeśli nie obejmują wszystkich możliwych przypadków w wyrażeniu Switch.</span><span class="sxs-lookup"><span data-stu-id="c0445-205">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="c0445-206">Techniki dopasowania wzorców można eksplorować w tym [zaawansowanym samouczku dotyczącym dopasowania wzorców](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-206">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="c0445-207">Korzystanie z deklaracji</span><span class="sxs-lookup"><span data-stu-id="c0445-207">using declarations</span></span>

<span data-ttu-id="c0445-208">**Deklaracja using** jest deklaracją zmiennej poprzedzoną `using` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="c0445-208">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="c0445-209">Informuje kompilator, że zadeklarowana zmienna powinna zostać usunięta na końcu otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c0445-209">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="c0445-210">Rozważmy na przykład następujący kod, który zapisuje plik tekstowy:</span><span class="sxs-lookup"><span data-stu-id="c0445-210">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="c0445-211">W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="c0445-211">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="c0445-212">To koniec zakresu, w którym `file` jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="c0445-212">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="c0445-213">Poprzedni kod jest odpowiednikiem poniższego kodu, który używa klasycznej [instrukcji using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="c0445-213">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="c0445-214">W poprzednim przykładzie plik jest usuwany po osiągnięciu zamykającego nawiasu klamrowego skojarzonego `using` z instrukcją.</span><span class="sxs-lookup"><span data-stu-id="c0445-214">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="c0445-215">W obu przypadkach kompilator generuje wywołanie `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="c0445-215">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="c0445-216">Kompilator generuje błąd, jeśli wyrażenie w `using` instrukcji nie jest jednorazowe.</span><span class="sxs-lookup"><span data-stu-id="c0445-216">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="c0445-217">Statyczne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="c0445-217">Static local functions</span></span>

<span data-ttu-id="c0445-218">Teraz można dodać `static` modyfikator do funkcji lokalnych, aby upewnić się, że funkcja lokalna nie przechwytuje (nie dotyczy) żadnych zmiennych z zakresu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="c0445-218">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="c0445-219">Spowoduje to wygenerowanie `CS8421`, "statyczna funkcja lokalna nie może zawierać odwołania \<do zmiennej >".</span><span class="sxs-lookup"><span data-stu-id="c0445-219">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="c0445-220">Rozważmy następujący kod.</span><span class="sxs-lookup"><span data-stu-id="c0445-220">Consider the following code.</span></span> <span data-ttu-id="c0445-221">Funkcja `LocalFunction` lokalna uzyskuje dostęp do zmiennej `y`zadeklarowanej w zakresie otaczającym (Metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="c0445-221">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="c0445-222">W związku`static` z tym niemożnazadeklarować`LocalFunction` z modyfikatorem:</span><span class="sxs-lookup"><span data-stu-id="c0445-222">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="c0445-223">Poniższy kod zawiera statyczną funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="c0445-223">The following code contains a static local function.</span></span> <span data-ttu-id="c0445-224">Może być statyczny, ponieważ nie uzyskuje dostępu do żadnych zmiennych w otaczającym zakresie:</span><span class="sxs-lookup"><span data-stu-id="c0445-224">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="c0445-225">Nierozporządzalne struktury ref</span><span class="sxs-lookup"><span data-stu-id="c0445-225">Disposable ref structs</span></span>

<span data-ttu-id="c0445-226">Deklaracja z modyfikatorem nie może implementować żadnych interfejsów i dlatego nie może implementować <xref:System.IDisposable>. `struct` `ref`</span><span class="sxs-lookup"><span data-stu-id="c0445-226">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="c0445-227">W związku z tym, `ref struct` aby można było usunąć element, musi on mieć `void Dispose()` dostępną metodę.</span><span class="sxs-lookup"><span data-stu-id="c0445-227">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="c0445-228">Dotyczy to również `readonly ref struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c0445-228">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="c0445-229">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="c0445-229">Nullable reference types</span></span>

<span data-ttu-id="c0445-230">Wewnątrz bezwartościowego kontekstu adnotacji Każda zmienna typu referencyjnego jest uważana za typ referencyjny, który nie **ma wartości null**.</span><span class="sxs-lookup"><span data-stu-id="c0445-230">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="c0445-231">Aby wskazać, że zmienna może mieć wartość null, należy dołączyć nazwę typu z, `?` aby zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null**.</span><span class="sxs-lookup"><span data-stu-id="c0445-231">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="c0445-232">W przypadku typów referencyjnych, które nie mają wartości null, kompilator używa analizy przepływu, aby upewnić się, że zmienne lokalne są inicjowane do wartości innej niż null, gdy zostanie zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="c0445-232">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="c0445-233">Pola muszą być inicjowane podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="c0445-233">Fields must be initialized during construction.</span></span> <span data-ttu-id="c0445-234">Kompilator generuje ostrzeżenie, jeśli zmienna nie jest ustawiona przez wywołanie do któregokolwiek z dostępnych konstruktorów lub inicjatora.</span><span class="sxs-lookup"><span data-stu-id="c0445-234">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="c0445-235">Ponadto nie można przypisać wartości, która może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="c0445-235">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="c0445-236">Typy odwołań dopuszczających wartość null nie są sprawdzane w celu zapewnienia, że nie są przypisane ani zainicjowane do wartości null.</span><span class="sxs-lookup"><span data-stu-id="c0445-236">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="c0445-237">Jednak kompilator używa analizy przepływu, aby upewnić się, że jakakolwiek zmienna typu referencyjnego null jest sprawdzana pod kątem wartości null przed uzyskaniem dostępu lub przypisaniem do niezerowego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="c0445-237">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="c0445-238">Więcej informacji na temat funkcji można znaleźć w omówieniu [typów referencyjnych dopuszczających wartość null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-238">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="c0445-239">Wypróbuj go samodzielnie w nowej aplikacji w tym [samouczku typów odwołań dopuszczających wartość null](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-239">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="c0445-240">Zapoznaj się z instrukcjami dotyczącymi migracji istniejącej bazy kodu w celu użycia w [samouczku Migrowanie aplikacji do korzystania](../tutorials/upgrade-to-nullable-references.md)z typów odwołań dopuszczających wartość null.</span><span class="sxs-lookup"><span data-stu-id="c0445-240">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="c0445-241">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="c0445-241">Asynchronous streams</span></span>

<span data-ttu-id="c0445-242">Począwszy od C# 8,0, można tworzyć strumienie i korzystać z nich asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="c0445-242">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="c0445-243">Metoda zwracająca strumień asynchroniczny ma trzy właściwości:</span><span class="sxs-lookup"><span data-stu-id="c0445-243">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="c0445-244">Jest on zadeklarowany z `async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="c0445-244">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="c0445-245">Zwraca wartość <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c0445-245">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="c0445-246">Metoda zawiera `yield return` instrukcje do zwrócenia kolejnych elementów w strumieniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="c0445-246">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="c0445-247">Użycie strumienia asynchronicznego wymaga dodania `await` słowa kluczowego `foreach` przed słowem kluczowym podczas wyliczania elementów strumienia.</span><span class="sxs-lookup"><span data-stu-id="c0445-247">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="c0445-248">Dodanie słowa kluczowego wymaga metody, która wylicza strumień asynchroniczny, który ma zostać zadeklarowany `async` z modyfikatorem i zwraca typ dozwolony dla `async` metody. `await`</span><span class="sxs-lookup"><span data-stu-id="c0445-248">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="c0445-249">Zwykle oznacza to zwrócenie <xref:System.Threading.Tasks.Task> lub. <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="c0445-249">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c0445-250">Może być <xref:System.Threading.Tasks.ValueTask> również lub <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="c0445-250">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="c0445-251">Metoda może jednocześnie zużywać i generować strumień asynchroniczny, co oznacza, że zwróci <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c0445-251">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="c0445-252">Poniższy kod generuje sekwencję z przedziału od 0 do 19, oczekującą 100 ms między generowaniem każdej liczby:</span><span class="sxs-lookup"><span data-stu-id="c0445-252">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="c0445-253">Sekwencję można wyliczyć przy użyciu `await foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c0445-253">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="c0445-254">Możesz samodzielnie wypróbować strumienie asynchroniczne w naszym samouczku dotyczącym [tworzenia i używania strumieni asynchronicznych](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-254">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="c0445-255">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="c0445-255">Indices and ranges</span></span>

<span data-ttu-id="c0445-256">Zakresy i indeksy zapewniają zwięzłą składnię do określania podzakresów w tablicy, [ciągu znaków](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="c0445-256">Ranges and indices provide a succinct syntax for specifying subranges in an array, [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="c0445-257">Ten język obsługuje dwa nowe typy i dwa nowe operatory:</span><span class="sxs-lookup"><span data-stu-id="c0445-257">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="c0445-258"><xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c0445-258"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="c0445-259">`^` Operator, który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c0445-259">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="c0445-260"><xref:System.Range?displayProperty=nameWithType>reprezentuje Podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c0445-260"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="c0445-261">Operator zakresu (`..`), który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="c0445-261">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="c0445-262">Zacznijmy od reguł dotyczących indeksów.</span><span class="sxs-lookup"><span data-stu-id="c0445-262">Let's start with the rules for indexes.</span></span> <span data-ttu-id="c0445-263">Weź pod uwagę `sequence`tablicę.</span><span class="sxs-lookup"><span data-stu-id="c0445-263">Consider an array `sequence`.</span></span> <span data-ttu-id="c0445-264">Indeks jest taki sam jak `sequence[0]`. `0`</span><span class="sxs-lookup"><span data-stu-id="c0445-264">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="c0445-265">Indeks jest taki sam jak `sequence[sequence.Length]`. `^0`</span><span class="sxs-lookup"><span data-stu-id="c0445-265">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="c0445-266">Należy pamiętać `sequence[^0]` , że generuje wyjątek, podobnie jak `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="c0445-266">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="c0445-267">Dla dowolnej liczby `n`indeks `^n` jest taki sam jak `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="c0445-267">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="c0445-268">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="c0445-268">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="c0445-269">Początek zakresu jest włączony, ale koniec zakresu jest na wyłączność, co oznacza, że *początek* znajduje się w zakresie, ale *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="c0445-269">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="c0445-270">Zakres `[0..^0]` reprezentuje cały zakres, tak jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="c0445-270">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="c0445-271">Przyjrzyjmy się kilku przykładom.</span><span class="sxs-lookup"><span data-stu-id="c0445-271">Let's look at a few examples.</span></span> <span data-ttu-id="c0445-272">Rozważmy następującą tablicę zawierającą adnotację z jej indeksem od początku i od końca:</span><span class="sxs-lookup"><span data-stu-id="c0445-272">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="c0445-273">Możesz pobrać ostatni wyraz z `^1` indeksem:</span><span class="sxs-lookup"><span data-stu-id="c0445-273">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="c0445-274">Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox".</span><span class="sxs-lookup"><span data-stu-id="c0445-274">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="c0445-275">Zawiera `words[1]` .`words[3]`</span><span class="sxs-lookup"><span data-stu-id="c0445-275">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="c0445-276">Element `words[4]` nie należy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="c0445-276">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="c0445-277">Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog".</span><span class="sxs-lookup"><span data-stu-id="c0445-277">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="c0445-278">Obejmuje `words[^2]` i .`words[^1]`</span><span class="sxs-lookup"><span data-stu-id="c0445-278">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="c0445-279">Indeks `words[^0]` końcowy nie jest uwzględniony:</span><span class="sxs-lookup"><span data-stu-id="c0445-279">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="c0445-280">W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="c0445-280">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="c0445-281">Można również zadeklarować zakresy jako zmienne:</span><span class="sxs-lookup"><span data-stu-id="c0445-281">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="c0445-282">Zakres może być następnie używany wewnątrz `[` znaków i: `]`</span><span class="sxs-lookup"><span data-stu-id="c0445-282">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="c0445-283">Więcej informacji o indeksach i zakresach można dowiedzieć się w samouczku dotyczącym [indeksów i zakresów](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-283">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="c0445-284">Przypisanie do łączenia o wartości null</span><span class="sxs-lookup"><span data-stu-id="c0445-284">Null-coalescing assignment</span></span>

<span data-ttu-id="c0445-285">C#8,0 wprowadza operator `??=`przypisania łączenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="c0445-285">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="c0445-286">`??=` Operatora można używać do przypisywania wartości operandu po prawej stronie do jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie jest obliczany `null`.</span><span class="sxs-lookup"><span data-stu-id="c0445-286">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(' ', numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="c0445-287">Aby uzyskać więcej informacji, zobacz [? =](../language-reference/operators/null-coalescing-operator.md) — artykuł.</span><span class="sxs-lookup"><span data-stu-id="c0445-287">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="c0445-288">Niezarządzane typy skonstruowane</span><span class="sxs-lookup"><span data-stu-id="c0445-288">Unmanaged constructed types</span></span>

<span data-ttu-id="c0445-289">W C# 7,3 i starszych, typ skonstruowany (typ, który zawiera co najmniej jeden argument typu) nie może być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-289">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) cannot be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="c0445-290">Począwszy od C# 8,0, skonstruowany typ wartości jest niezarządzany, jeśli zawiera pola tylko typów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="c0445-290">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="c0445-291">Na przykład, uwzględniając następującą definicję typu ogólnego `Coords<T>` :</span><span class="sxs-lookup"><span data-stu-id="c0445-291">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="c0445-292">Typ jest typem niezarządzanym w C# 8,0 i nowszych. `Coords<int>`</span><span class="sxs-lookup"><span data-stu-id="c0445-292">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="c0445-293">Podobnie jak w przypadku dowolnego typu niezarządzanego, można utworzyć wskaźnik do zmiennej tego typu lub [przydzielić blok pamięci na stosie](../language-reference/operators/stackalloc.md) dla wystąpień tego typu:</span><span class="sxs-lookup"><span data-stu-id="c0445-293">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="c0445-294">Aby uzyskać więcej informacji, zobacz [typy niezarządzane](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="c0445-294">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="c0445-295">stackalloc w wyrażeniach zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="c0445-295">stackalloc in nested expressions</span></span>

<span data-ttu-id="c0445-296">Rozpoczynając od C# 8,0, jeśli wynik wyrażenia [stackalloc](../language-reference/operators/stackalloc.md) <xref:System.Span%601?displayProperty=nameWithType> jest typu lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , można użyć `stackalloc` wyrażenia w innych wyrażeniach:</span><span class="sxs-lookup"><span data-stu-id="c0445-296">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="c0445-297">Ulepszenie interpolowanych ciągów Verbatim</span><span class="sxs-lookup"><span data-stu-id="c0445-297">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="c0445-298">`@$"..."` `$@"..."` [](../language-reference/tokens/interpolated.md) Kolejność tokenów `@`iw interpolowanych ciągach Verbatim może być dowolna: oba i są prawidłowymi interpolowanymi ciągami Verbatim. `$`</span><span class="sxs-lookup"><span data-stu-id="c0445-298">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="c0445-299">We wcześniejszych C# wersjach `$` token `@` musi znajdować się przed tokenem.</span><span class="sxs-lookup"><span data-stu-id="c0445-299">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
