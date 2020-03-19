---
title: C# — konwencje kodowania
description: Podczas pisania kodu F# poznaj ogólne wskazówki i idiomy.
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400310"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="149af-103">C# — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="149af-103">F# coding conventions</span></span>

<span data-ttu-id="149af-104">Następujące konwencje są formułowane z doświadczenia pracy z dużych baz kodu F#.</span><span class="sxs-lookup"><span data-stu-id="149af-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="149af-105">[Pięć zasad dobrego kodu F#](index.md#five-principles-of-good-f-code) są podstawą każdego zalecenia.</span><span class="sxs-lookup"><span data-stu-id="149af-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="149af-106">Są one związane z [wytycznymi projektowania składników F#,](component-design-guidelines.md)ale mają zastosowanie do dowolnego kodu F#, a nie tylko składników, takich jak biblioteki.</span><span class="sxs-lookup"><span data-stu-id="149af-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="149af-107">Organizowanie kodu</span><span class="sxs-lookup"><span data-stu-id="149af-107">Organizing code</span></span>

<span data-ttu-id="149af-108">F# oferuje dwa podstawowe sposoby organizowania kodu: moduły i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="149af-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="149af-109">Są one podobne, ale mają następujące różnice:</span><span class="sxs-lookup"><span data-stu-id="149af-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="149af-110">Przestrzenie nazw są kompilowane jako obszary nazw .NET.</span><span class="sxs-lookup"><span data-stu-id="149af-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="149af-111">Moduły są kompilowane jako klasy statyczne.</span><span class="sxs-lookup"><span data-stu-id="149af-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="149af-112">Przestrzenie nazw są zawsze najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="149af-112">Namespaces are always top level.</span></span> <span data-ttu-id="149af-113">Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="149af-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="149af-114">Przestrzenie nazw mogą obejmujeć wiele plików.</span><span class="sxs-lookup"><span data-stu-id="149af-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="149af-115">Moduły nie mogą.</span><span class="sxs-lookup"><span data-stu-id="149af-115">Modules cannot.</span></span>
* <span data-ttu-id="149af-116">Moduły mogą być `[<RequireQualifiedAccess>]` ozdobione i `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="149af-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="149af-117">Poniższe wskazówki pomogą Ci użyć tych do zorganizowania kodu.</span><span class="sxs-lookup"><span data-stu-id="149af-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="149af-118">Preferuj przestrzenie nazw na najwyższym poziomie</span><span class="sxs-lookup"><span data-stu-id="149af-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="149af-119">Dla każdego publicznie zużywalny kod przestrzenie nazw są preferencyjne dla modułów na najwyższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="149af-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="149af-120">Ponieważ są one kompilowane jako przestrzenie nazw .NET, są one zużywalne z języka C# bez problemu.</span><span class="sxs-lookup"><span data-stu-id="149af-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="149af-121">Przy użyciu modułu najwyższego poziomu nie może wyglądać inaczej, gdy wywoływane tylko z F#, ale dla konsumentów języka C#, obiekty wywołujące mogą być zaskoczeni konieczności zakwalifikowania się `MyClass` z modułem. `MyCode`</span><span class="sxs-lookup"><span data-stu-id="149af-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="149af-122">Ostrożnie nałożyć`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="149af-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="149af-123">Konstrukcja `[<AutoOpen>]` może zanieczyścić zakres tego, co jest dostępne dla dzwoniących, a odpowiedź na to, skąd coś pochodzi, to "magia".</span><span class="sxs-lookup"><span data-stu-id="149af-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="149af-124">To nie jest dobra rzecz.</span><span class="sxs-lookup"><span data-stu-id="149af-124">This is not a good thing.</span></span> <span data-ttu-id="149af-125">Wyjątkiem od tej reguły jest sama biblioteka rdzenia F# (choć ten fakt jest również nieco kontrowersyjny).</span><span class="sxs-lookup"><span data-stu-id="149af-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="149af-126">Jednak jest to wygoda, jeśli masz funkcje pomocnika dla publicznego interfejsu API, który chcesz zorganizować oddzielnie od tego publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="149af-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="149af-127">Dzięki temu można czysto oddzielić szczegóły implementacji od publicznego interfejsu API funkcji bez konieczności pełnego zakwalifikowania pomocnika za każdym razem, gdy go wywołać.</span><span class="sxs-lookup"><span data-stu-id="149af-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="149af-128">Ponadto uwidając metody rozszerzenia i konstruktorów wyrażeń na `[<AutoOpen>]`poziomie przestrzeni nazw można starannie wyrazić za pomocą .</span><span class="sxs-lookup"><span data-stu-id="149af-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="149af-129">Używaj, `[<RequireQualifiedAccess>]` gdy nazwy mogą być sprzeczne lub uważasz, że pomaga w czytelności</span><span class="sxs-lookup"><span data-stu-id="149af-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="149af-130">Dodanie `[<RequireQualifiedAccess>]` atrybutu do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu wymagają jawnego kwalifikowanego dostępu.</span><span class="sxs-lookup"><span data-stu-id="149af-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="149af-131">Na przykład `Microsoft.FSharp.Collections.List` moduł ma ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="149af-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="149af-132">Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą kolidować z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="149af-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="149af-133">Wymaganie wykwalifikowanego dostępu może znacznie zwiększyć długoterminową łatwość konserwacji i evolvability biblioteki.</span><span class="sxs-lookup"><span data-stu-id="149af-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="149af-134">Sortowanie `open` instrukcji topologicznych</span><span class="sxs-lookup"><span data-stu-id="149af-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="149af-135">W F#kolejność deklaracji ma znaczenie, `open` w tym z oświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="149af-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="149af-136">Jest to w przeciwieństwie do `using` Języka `using static` C#, gdzie efekt i jest niezależny od kolejności tych instrukcji w pliku.</span><span class="sxs-lookup"><span data-stu-id="149af-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="149af-137">W F#, elementy otwarte w zakresie może cienia innych już obecnych.</span><span class="sxs-lookup"><span data-stu-id="149af-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="149af-138">Oznacza to, że `open` zmiana kolejności instrukcji może zmienić znaczenie kodu.</span><span class="sxs-lookup"><span data-stu-id="149af-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="149af-139">W rezultacie wszelkie dowolne `open` sortowanie wszystkich instrukcji (na przykład alfanumerycznie) nie jest zalecane, aby nie generować różne zachowanie, które można oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="149af-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="149af-140">Zamiast tego zalecamy sortowanie ich [topologicznie;](https://en.wikipedia.org/wiki/Topological_sorting) oznacza to, `open` że zamów instrukcje w kolejności, w jakiej _warstwy_ systemu są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="149af-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="149af-141">Można również wziąć pod uwagę sortowanie alfanumeryczne w różnych warstwach topologicznych.</span><span class="sxs-lookup"><span data-stu-id="149af-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="149af-142">Na przykład w tym miejscu przedstawiono sortowanie topologiczne dla publicznego pliku interfejsu API usługi kompilatora F#:</span><span class="sxs-lookup"><span data-stu-id="149af-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="149af-143">Należy zauważyć, że podział wiersza oddziela warstwy topologiczne, a każda warstwa jest następnie sortowana alfanumerycznie.</span><span class="sxs-lookup"><span data-stu-id="149af-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="149af-144">To czysto organizuje kod bez przypadkowo przesłanianie wartości.</span><span class="sxs-lookup"><span data-stu-id="149af-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="149af-145">Użyj klas, aby zawierać wartości, które mają skutki uboczne</span><span class="sxs-lookup"><span data-stu-id="149af-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="149af-146">Inicjowanie wartości może mieć wiele razy, takie jak tworzenie wystąpienia kontekstu do bazy danych lub innego zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="149af-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="149af-147">Kuszące jest inicjowanie takich rzeczy w module i używanie ich w kolejnych funkcjach:</span><span class="sxs-lookup"><span data-stu-id="149af-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="149af-148">Jest to często zły pomysł z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="149af-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="149af-149">Po pierwsze, konfiguracja aplikacji jest `dep1` `dep2`wypychana do bazy kodu z i .</span><span class="sxs-lookup"><span data-stu-id="149af-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="149af-150">Jest to trudne do utrzymania w większych bazach kodu.</span><span class="sxs-lookup"><span data-stu-id="149af-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="149af-151">Po drugie, statycznie inicjowane dane nie powinny zawierać wartości, które nie są bezpieczne dla wątków, jeśli składnik będzie sam używać wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="149af-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="149af-152">Jest to wyraźnie `dep3`naruszone przez .</span><span class="sxs-lookup"><span data-stu-id="149af-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="149af-153">Na koniec inicjowanie modułu kompiluje się do konstruktora statycznego dla całej jednostki kompilacji.</span><span class="sxs-lookup"><span data-stu-id="149af-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="149af-154">Jeśli wystąpi błąd w inicjowaniu wartości let-bound w tym `TypeInitializationException` module, manifestuje się jako buforowany przez cały okres istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="149af-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="149af-155">Może to być trudne do zdiagnozowania.</span><span class="sxs-lookup"><span data-stu-id="149af-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="149af-156">Zwykle istnieje wewnętrzny wyjątek, który można spróbować rozsądek o, ale jeśli nie jest, to nie ma co jest przyczyną.</span><span class="sxs-lookup"><span data-stu-id="149af-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="149af-157">Zamiast tego wystarczy użyć prostej klasy do przechowywania zależności:</span><span class="sxs-lookup"><span data-stu-id="149af-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="149af-158">Umożliwia to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="149af-158">This enables the following:</span></span>

1. <span data-ttu-id="149af-159">Wypychanie dowolnego stanu zależnego poza samym interfejsem API.</span><span class="sxs-lookup"><span data-stu-id="149af-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="149af-160">Konfiguracja może być teraz wykonywana poza interfejsem API.</span><span class="sxs-lookup"><span data-stu-id="149af-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="149af-161">Błędy w inicjowaniu dla wartości zależnych `TypeInitializationException`prawdopodobnie nie będą manifestować jako .</span><span class="sxs-lookup"><span data-stu-id="149af-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="149af-162">Interfejs API jest teraz łatwiejsze do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="149af-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="149af-163">Zarządzanie błędami</span><span class="sxs-lookup"><span data-stu-id="149af-163">Error management</span></span>

<span data-ttu-id="149af-164">Zarządzanie błędami w dużych systemach jest złożonym i zniuansowanym przedsięwzięciem, a nie ma srebrnych kul w zapewnieniu, że systemy są odporne na uszkodzenia i zachowują się dobrze.</span><span class="sxs-lookup"><span data-stu-id="149af-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="149af-165">Poniższe wskazówki powinny oferować wskazówki dotyczące nawigacji po tej trudnej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="149af-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="149af-166">Reprezentowanie przypadków błędów i niedozwolonych typów wewnętrznych z domeną</span><span class="sxs-lookup"><span data-stu-id="149af-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="149af-167">W [przypadku związków dyskryminowanych](../language-reference/discriminated-unions.md)F# umożliwia reprezentowanie wadliwego stanu programu w systemie typów.</span><span class="sxs-lookup"><span data-stu-id="149af-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="149af-168">Przykład:</span><span class="sxs-lookup"><span data-stu-id="149af-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="149af-169">W tym przypadku istnieją trzy znane sposoby, aby wypłata pieniędzy z konta bankowego może się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="149af-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="149af-170">Każdy przypadek błędu jest reprezentowany w typie i dlatego można je bezpiecznie rozwiązać w całym programie.</span><span class="sxs-lookup"><span data-stu-id="149af-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="149af-171">Ogólnie rzecz biorąc, jeśli można modelować różne sposoby, że coś może **się nie powieść** w domenie, a następnie błąd obsługi kodu nie jest już traktowany jako coś, co musi radzić sobie oprócz regularnego przepływu programu.</span><span class="sxs-lookup"><span data-stu-id="149af-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="149af-172">Jest to po prostu część normalnego przepływu programu, a nie uważane za **wyjątkowe**.</span><span class="sxs-lookup"><span data-stu-id="149af-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="149af-173">Istnieją dwie podstawowe korzyści do tego:</span><span class="sxs-lookup"><span data-stu-id="149af-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="149af-174">Jest to łatwiejsze w utrzymaniu, ponieważ domena zmienia się wraz z uchwadnianiem.</span><span class="sxs-lookup"><span data-stu-id="149af-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="149af-175">Przypadki błędów są łatwiejsze do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="149af-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="149af-176">Użyj wyjątków, gdy błędy nie mogą być reprezentowane z typami</span><span class="sxs-lookup"><span data-stu-id="149af-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="149af-177">Nie wszystkie błędy mogą być reprezentowane w domenie problemu.</span><span class="sxs-lookup"><span data-stu-id="149af-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="149af-178">Tego rodzaju błędy mają *charakter wyjątkowy,* stąd możliwość podnoszenia i wyłapywanie wyjątków w F#.</span><span class="sxs-lookup"><span data-stu-id="149af-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="149af-179">Najpierw zaleca się przeczytanie [wytycznych dotyczących projektowania wyjątków](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="149af-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="149af-180">Mają one również zastosowanie do Języka F#.</span><span class="sxs-lookup"><span data-stu-id="149af-180">These are also applicable to F#.</span></span>

<span data-ttu-id="149af-181">Główne konstrukcje dostępne w języku F# na potrzeby podnoszenia wyjątków powinny być brane pod uwagę w następującej kolejności preferencji:</span><span class="sxs-lookup"><span data-stu-id="149af-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="149af-182">Funkcja</span><span class="sxs-lookup"><span data-stu-id="149af-182">Function</span></span> | <span data-ttu-id="149af-183">Składnia</span><span class="sxs-lookup"><span data-stu-id="149af-183">Syntax</span></span> | <span data-ttu-id="149af-184">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="149af-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="149af-185">Wywołuje `System.ArgumentNullException` nazwę z określonym argumentem.</span><span class="sxs-lookup"><span data-stu-id="149af-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="149af-186">Wywołuje `System.ArgumentException` nazwę określonego argumentu i wiadomość.</span><span class="sxs-lookup"><span data-stu-id="149af-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="149af-187">Wywołuje `System.InvalidOperationException` a z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="149af-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="149af-188">Mechanizm ogólnego przeznaczenia do zgłaszania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="149af-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="149af-189">Wywołuje `System.Exception` a z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="149af-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="149af-190">Wywołuje `System.Exception` z komunikatem określonym przez ciąg formatu i jego dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="149af-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="149af-191">Użyj `nullArg` `invalidArg` , `invalidOp` i jako `ArgumentNullException`mechanizm `ArgumentException` `InvalidOperationException` do rzucania , i kiedy jest to właściwe.</span><span class="sxs-lookup"><span data-stu-id="149af-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="149af-192">I `failwith` `failwithf` funkcje zazwyczaj należy unikać, ponieważ podnieść `Exception` typ podstawowy, a nie określony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="149af-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="149af-193">Zgodnie z [wytycznymi dotyczącymi projektowania wyjątków,](../../standard/design-guidelines/exceptions.md)chcesz podnieść bardziej szczegółowe wyjątki, gdy tylko możesz.</span><span class="sxs-lookup"><span data-stu-id="149af-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="149af-194">Korzystanie ze składni obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="149af-194">Using exception-handling syntax</span></span>

<span data-ttu-id="149af-195">F# obsługuje wzorce `try...with` wyjątków za pośrednictwem składni:</span><span class="sxs-lookup"><span data-stu-id="149af-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="149af-196">Pojednanie funkcji do wykonania w obliczu wyjątku z dopasowywania wzorca może być nieco trudne, jeśli chcesz zachować kod w czystości.</span><span class="sxs-lookup"><span data-stu-id="149af-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="149af-197">Jednym z takich sposobów obsługi jest użycie [aktywnych wzorców](../language-reference/active-patterns.md) jako środka do grupowania funkcji otaczających przypadek błędu z samym wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="149af-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="149af-198">Na przykład może być zużywa interfejsu API, który, gdy zgłasza wyjątek, zawiera cenne informacje w metadanych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="149af-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="149af-199">Rozpakowanie użytecznej wartości w treści przechwyconego wyjątku wewnątrz aktywnego wzorca i zwrócenie tej wartości może być pomocne w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="149af-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="149af-200">Nie używaj obsługi błędów monadyjskich, aby zastąpić wyjątki</span><span class="sxs-lookup"><span data-stu-id="149af-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="149af-201">Wyjątki są postrzegane jako nieco tabu w programowaniu funkcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="149af-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="149af-202">Rzeczywiście, wyjątki naruszają czystość, więc można bezpiecznie uznać je za niecałkiem funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="149af-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="149af-203">Jednak to ignoruje rzeczywistość, gdzie kod musi działać i że mogą wystąpić błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="149af-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="149af-204">Ogólnie rzecz biorąc, napisz kod przy założeniu, że większość rzeczy nie jest ani czysta, ani całkowita, aby zminimalizować nieprzyjemne niespodzianki.</span><span class="sxs-lookup"><span data-stu-id="149af-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="149af-205">Ważne jest, aby wziąć pod uwagę następujące podstawowe mocne/aspekty wyjątków w odniesieniu do ich przydatności i stosowności w ekosystemie wykonywania .NET i międzyjęzykowych jako całości:</span><span class="sxs-lookup"><span data-stu-id="149af-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="149af-206">Zawierają one szczegółowe informacje diagnostyczne, co jest bardzo przydatne podczas debugowania problemu.</span><span class="sxs-lookup"><span data-stu-id="149af-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="149af-207">Są one dobrze rozumiane przez czas wykonywania i innych języków .NET.</span><span class="sxs-lookup"><span data-stu-id="149af-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="149af-208">Mogą one zmniejszyć znaczne standardowe w porównaniu z kodem, który wychodzi z drogi, aby *uniknąć* wyjątków, implementując niektóre podzbiór ich semantyki na zasadzie ad hoc.</span><span class="sxs-lookup"><span data-stu-id="149af-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="149af-209">Ten trzeci punkt ma kluczowe znaczenie.</span><span class="sxs-lookup"><span data-stu-id="149af-209">This third point is critical.</span></span> <span data-ttu-id="149af-210">W przypadku nietrywialnych operacji złożonych nieużycie wyjątków może spowodować radzenie sobie ze strukturami takimi jak ten:</span><span class="sxs-lookup"><span data-stu-id="149af-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="149af-211">Co może łatwo prowadzić do kruchego kodu, takiego jak dopasowywanie wzorców na błędach typu "typu ciągowego":</span><span class="sxs-lookup"><span data-stu-id="149af-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="149af-212">Dodatkowo, może być kuszące, aby połknąć każdy wyjątek w pragnienie "prostej" funkcji, która zwraca typu "ładniejszy":</span><span class="sxs-lookup"><span data-stu-id="149af-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="149af-213">Niestety, `tryReadAllText` może zgłosić wiele wyjątków na podstawie niezliczonych rzeczy, które mogą się zdarzyć w systemie plików, a ten kod odrzuca wszelkie informacje o tym, co może być rzeczywiście dzieje się źle w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="149af-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="149af-214">Jeśli zastąpisz ten kod typem wyniku, powrócisz do analizy komunikatu o błędzie "typu ciągowego":</span><span class="sxs-lookup"><span data-stu-id="149af-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="149af-215">I umieszczenie samego obiektu `Error` wyjątku w konstruktorze po prostu wymusza poprawnie radzić sobie z typem wyjątku w witrynie wywołania, a nie w funkcji.</span><span class="sxs-lookup"><span data-stu-id="149af-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="149af-216">W ten sposób skutecznie tworzy sprawdzone wyjątki, które są notorycznie niezabawne do czynienia jako obiekt wywołujący interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="149af-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="149af-217">Dobrą alternatywą dla powyższych przykładów jest wychwytywanie *określonych* wyjątków i zwracanie znaczącej wartości w kontekście tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="149af-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="149af-218">Jeśli zmodyfikujesz funkcję `tryReadAllText` `None` w następujący sposób, ma większe znaczenie:</span><span class="sxs-lookup"><span data-stu-id="149af-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="149af-219">Zamiast działać jako catch-all, ta funkcja będzie teraz poprawnie obsługiwać sprawę, gdy plik nie został znaleziony i przypisać to znaczenie do zwrotu.</span><span class="sxs-lookup"><span data-stu-id="149af-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="149af-220">Ta wartość zwracana można mapować do tego przypadku błędu, nie odrzucając żadnych informacji kontekstowych lub zmuszając obiekty wywołujące do czynienia ze sprawą, która może nie być istotne w tym momencie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="149af-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="149af-221">Typy, `Result<'Success, 'Error>` takie jak są odpowiednie dla podstawowych operacji, w których nie są zagnieżdżone i F# opcjonalne typy są idealne do reprezentowania, gdy coś może zwrócić *coś* lub *nic*.</span><span class="sxs-lookup"><span data-stu-id="149af-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="149af-222">Nie są one jednak zamiennikiem wyjątków i nie powinny być używane w celu zastąpienia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="149af-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="149af-223">Należy je raczej stosować rozważnie w celu uwzględnienia konkretnych aspektów polityki zarządzania wyjątkami i błędami w sposób ukierunkowany.</span><span class="sxs-lookup"><span data-stu-id="149af-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="149af-224">Częściowe stosowanie i programowanie bezpunktowe</span><span class="sxs-lookup"><span data-stu-id="149af-224">Partial application and point-free programming</span></span>

<span data-ttu-id="149af-225">F# obsługuje częściowej aplikacji, a tym samym różne sposoby programowania w stylu bez punktu.</span><span class="sxs-lookup"><span data-stu-id="149af-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="149af-226">Może to być korzystne dla ponownego użycia kodu w module lub implementacji coś, ale nie jest coś do ujawnienia publicznie.</span><span class="sxs-lookup"><span data-stu-id="149af-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="149af-227">Ogólnie rzecz biorąc, programowanie bez punktów nie jest cnotą samą w sobie i może dodać znaczącą barierę poznawczą dla ludzi, którzy nie są zanurzeni w tym stylu.</span><span class="sxs-lookup"><span data-stu-id="149af-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="149af-228">Nie należy używać częściowej aplikacji i currying w publicznych interfejsów API</span><span class="sxs-lookup"><span data-stu-id="149af-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="149af-229">Z wyjątkiem małych wyjątków, korzystanie z częściowej aplikacji w publicznych interfejsów API może być mylące dla konsumentów.</span><span class="sxs-lookup"><span data-stu-id="149af-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="149af-230">Zazwyczaj `let`wartości powiązane w kodzie F# są **wartościami**, a nie **wartościami funkcji**.</span><span class="sxs-lookup"><span data-stu-id="149af-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="149af-231">Mieszanie wartości i wartości funkcji może spowodować zapisanie niewielkiej liczby wierszy kodu w zamian za sporo `>>` obciążenie poznawcze, zwłaszcza w połączeniu z operatorami, takich jak komponowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="149af-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="149af-232">Należy wziąć pod uwagę implikacje narzędzi dla programowania bezpunktowego</span><span class="sxs-lookup"><span data-stu-id="149af-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="149af-233">Funkcje curried nie oznaczają swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="149af-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="149af-234">Ma to implikacje narzędziowe.</span><span class="sxs-lookup"><span data-stu-id="149af-234">This has tooling implications.</span></span> <span data-ttu-id="149af-235">Należy wziąć pod uwagę następujące dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="149af-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="149af-236">Oba są prawidłowe `funcWithApplication` funkcje, ale jest funkcją curried.</span><span class="sxs-lookup"><span data-stu-id="149af-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="149af-237">Po umieszczeniu wskaźnika myszy na ich typach w edytorze jest widoczne:</span><span class="sxs-lookup"><span data-stu-id="149af-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="149af-238">W witrynie wywołania etykietki narzędzi w narzędziach, takich jak Visual `string` Studio `int` nie daje znaczące informacje, co i typy danych wejściowych faktycznie reprezentują.</span><span class="sxs-lookup"><span data-stu-id="149af-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="149af-239">W przypadku napotkania kodu `funcWithApplication` bezpunktu, takiego jak ten, który jest publicznie zużywalny, zaleca się wykonanie pełnego rozszerzenia η, aby narzędzia mogły odbierać znaczące nazwy argumentów.</span><span class="sxs-lookup"><span data-stu-id="149af-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="149af-240">Ponadto debugowanie kodu bez punktów może być trudne, jeśli nie niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="149af-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="149af-241">Narzędzia debugowania polegać na wartości powiązane `let` z nazwami (na przykład powiązania), dzięki czemu można sprawdzić wartości pośrednie w połowie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="149af-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="149af-242">Gdy kod nie ma żadnych wartości do sprawdzenia, nie ma nic do debugowania.</span><span class="sxs-lookup"><span data-stu-id="149af-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="149af-243">W przyszłości narzędzia debugowania mogą ewoluować, aby syntetyzować te wartości na podstawie wcześniej wykonanych ścieżek, ale nie jest dobrym pomysłem zabezpieczenie zakładów na *potencjalne* funkcje debugowania.</span><span class="sxs-lookup"><span data-stu-id="149af-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="149af-244">Należy rozważyć częściowe zastosowanie jako technikę w celu zmniejszenia wewnętrznych standardowych</span><span class="sxs-lookup"><span data-stu-id="149af-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="149af-245">W przeciwieństwie do poprzedniego punktu, częściowe zastosowanie jest wspaniałym narzędziem do redukcji standardowego wnętrza aplikacji lub głębszych wewnętrznych interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="149af-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="149af-246">Może to być pomocne w testowaniu jednostkowym implementacji bardziej skomplikowanych interfejsów API, gdzie standardowe jest często ból do czynienia z.</span><span class="sxs-lookup"><span data-stu-id="149af-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="149af-247">Na przykład poniższy kod pokazuje, jak można wykonać to, co najbardziej szyderczy chamstwo daje bez podejmowania zależności zewnętrznej od takiej struktury i konieczności uczenia się powiązanych interfejsu API na zamówienie.</span><span class="sxs-lookup"><span data-stu-id="149af-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="149af-248">Rozważmy na przykład następującą topografię rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="149af-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="149af-249">`ImplementationLogic.fsproj`może uwidaczniać kod, takich jak:</span><span class="sxs-lookup"><span data-stu-id="149af-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="149af-250">Testowanie `Transactions.doTransaction` jednostkowe jest `ImplementationLogic.Tests.fsproj` łatwe:</span><span class="sxs-lookup"><span data-stu-id="149af-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="149af-251">Częściowo `doTransaction` stosowane z makiety obiektu kontekstu umożliwia wywołanie funkcji we wszystkich testów jednostkowych bez konieczności konstruowania makiety kontekstu za każdym razem:</span><span class="sxs-lookup"><span data-stu-id="149af-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="149af-252">Ta technika nie powinna być powszechnie stosowana do całej bazy kodu, ale jest to dobry sposób na zmniejszenie standardowego dla skomplikowanych wewnętrznych i testowania jednostek tych wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="149af-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="149af-253">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="149af-253">Access control</span></span>

<span data-ttu-id="149af-254">F# ma wiele opcji [kontroli dostępu,](../language-reference/access-control.md)dziedziczone z tego, co jest dostępne w programie .NET runtime.</span><span class="sxs-lookup"><span data-stu-id="149af-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="149af-255">Nie są one po prostu użyteczne dla typów - można ich używać również do funkcji.</span><span class="sxs-lookup"><span data-stu-id="149af-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="149af-256">Preferuj`public` nie-typy i członków, dopóki nie potrzebujesz ich do publicznego zużywania.</span><span class="sxs-lookup"><span data-stu-id="149af-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="149af-257">To również minimalizuje to, co konsumenci para do.</span><span class="sxs-lookup"><span data-stu-id="149af-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="149af-258">Staraj się zachować wszystkie `private`funkcje pomocnika .</span><span class="sxs-lookup"><span data-stu-id="149af-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="149af-259">Należy wziąć `[<AutoOpen>]` pod uwagę korzystanie z prywatnego modułu funkcji pomocnika, jeśli stają się one liczne.</span><span class="sxs-lookup"><span data-stu-id="149af-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="149af-260">Wnioskowanie o typie i generyk</span><span class="sxs-lookup"><span data-stu-id="149af-260">Type inference and generics</span></span>

<span data-ttu-id="149af-261">Wnioskowanie typu może zaoszczędzić od wpisywania dużo standardowego.</span><span class="sxs-lookup"><span data-stu-id="149af-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="149af-262">Automatyczne uogólnienie w kompilatorze F# może pomóc w zapisie bardziej ogólnego kodu bez prawie żadnego dodatkowego wysiłku ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="149af-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="149af-263">Jednak te cechy nie są powszechnie dobre.</span><span class="sxs-lookup"><span data-stu-id="149af-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="149af-264">Należy wziąć pod uwagę etykietowania nazw argumentów z jawnych typów w publicznych interfejsów API i nie polegać na wnioskowanie o typie dla tego.</span><span class="sxs-lookup"><span data-stu-id="149af-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="149af-265">Powodem tego jest to, że **powinieneś** mieć kontrolę nad kształtem interfejsu API, a nie kompilatorem.</span><span class="sxs-lookup"><span data-stu-id="149af-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="149af-266">Mimo że kompilator może wykonać drobne zadanie przy wnioskowaniu typów dla Ciebie, możliwe jest, aby mieć kształt zmiany interfejsu API, jeśli wewnętrzne, na których opiera się, zmieniły typy.</span><span class="sxs-lookup"><span data-stu-id="149af-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="149af-267">To może być to, co chcesz, ale prawie na pewno spowoduje przełomową zmianę interfejsu API, że downstream konsumentów będzie musiał radzić sobie z.</span><span class="sxs-lookup"><span data-stu-id="149af-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="149af-268">Zamiast tego, jeśli jawnie kontrolować kształt publicznego interfejsu API, a następnie można kontrolować te zmiany.</span><span class="sxs-lookup"><span data-stu-id="149af-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="149af-269">W kategoriach DDD można to traktować jako warstwę antykorupcyjną.</span><span class="sxs-lookup"><span data-stu-id="149af-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="149af-270">Rozważ nadanie znaczącej nazwy argumentom rodzajowym.</span><span class="sxs-lookup"><span data-stu-id="149af-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="149af-271">Jeśli nie piszesz prawdziwie ogólnego kodu, który nie jest specyficzny dla określonej domeny, znacząca nazwa może pomóc innym programistom zrozumieć domenę, w której pracują.</span><span class="sxs-lookup"><span data-stu-id="149af-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="149af-272">Na przykład parametr typu `'Document` o nazwie w kontekście interakcji z bazą danych dokumentów sprawia, że jaśniejsze, że ogólne typy dokumentów mogą być akceptowane przez funkcję lub element członkowski, z którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="149af-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="149af-273">Należy wziąć pod uwagę nazewnictwa parametrów typu ogólnego z PascalCase.</span><span class="sxs-lookup"><span data-stu-id="149af-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="149af-274">Jest to ogólny sposób wykonywania czynności w .NET, dlatego zaleca się użycie PascalCase zamiast snake_case lub camelCase.</span><span class="sxs-lookup"><span data-stu-id="149af-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="149af-275">Na koniec automatyczne uogólnienie nie zawsze jest dobrodziejstwem dla osób, które są nowe f# lub dużej bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="149af-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="149af-276">Istnieje obciążenie poznawcze w użyciu składników, które są ogólne.</span><span class="sxs-lookup"><span data-stu-id="149af-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="149af-277">Ponadto, jeśli automatycznie uogólnione funkcje nie są używane z różnymi typami danych wejściowych (nie mówiąc już o tym, jeśli są przeznaczone do użycia jako takie), to nie ma żadnych rzeczywistych korzyści dla nich jest ogólny w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="149af-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="149af-278">Zawsze należy wziąć pod uwagę, jeśli kod, który piszesz rzeczywiście skorzystają z jest ogólny.</span><span class="sxs-lookup"><span data-stu-id="149af-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="149af-279">Wydajność</span><span class="sxs-lookup"><span data-stu-id="149af-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="149af-280">Preferuj struktury dla małych typów danych</span><span class="sxs-lookup"><span data-stu-id="149af-280">Prefer structs for small data types</span></span>

<span data-ttu-id="149af-281">Przy użyciu struktur (nazywane również typy wartości) często może spowodować wyższą wydajność dla niektórych kodu, ponieważ zazwyczaj pozwala uniknąć przydzielania obiektów.</span><span class="sxs-lookup"><span data-stu-id="149af-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="149af-282">Jednak struktury nie zawsze są przyciskiem "go faster": jeśli rozmiar danych w strukturze przekracza 16 bajtów, kopiowanie danych często może spowodować więcej czasu procesora niż przy użyciu typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="149af-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="149af-283">Aby ustalić, czy należy użyć struktury, należy wziąć pod uwagę następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="149af-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="149af-284">Jeśli rozmiar danych jest 16 bajtów lub mniejsze.</span><span class="sxs-lookup"><span data-stu-id="149af-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="149af-285">Jeśli istnieje prawdopodobieństwo, że wiele z tych typów danych jest dostępnych w pamięci w uruchomionym programie.</span><span class="sxs-lookup"><span data-stu-id="149af-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="149af-286">Jeśli pierwszy warunek ma zastosowanie, należy ogólnie użyć struktury.</span><span class="sxs-lookup"><span data-stu-id="149af-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="149af-287">Jeśli oba stosuje, prawie zawsze należy użyć struktury.</span><span class="sxs-lookup"><span data-stu-id="149af-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="149af-288">Mogą wystąpić przypadki, w których obowiązują poprzednie warunki, ale przy użyciu struktury nie jest lepsze lub gorsze niż przy użyciu typu odniesienia, ale mogą one być rzadkie.</span><span class="sxs-lookup"><span data-stu-id="149af-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="149af-289">Ważne jest, aby zawsze mierzyć przy wprowadzaniu takich zmian, a nie działać na założeniu lub intuicji.</span><span class="sxs-lookup"><span data-stu-id="149af-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="149af-290">Preferuj krotek struct podczas grupowania małych typów wartości</span><span class="sxs-lookup"><span data-stu-id="149af-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="149af-291">Należy wziąć pod uwagę następujące dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="149af-291">Consider the following two functions:</span></span>

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

<span data-ttu-id="149af-292">Podczas porównywania tych funkcji za pomocą statystycznego narzędzia do analizy porównawczej, takiego jak [BenchmarkDotNet,](https://benchmarkdotnet.org/)przekonasz się, że `runWithStructTuple` funkcja, która używa krotek struct działa 40% szybciej i nie przydziela pamięci.</span><span class="sxs-lookup"><span data-stu-id="149af-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="149af-293">Jednak te wyniki nie zawsze będą w przypadku własnego kodu.</span><span class="sxs-lookup"><span data-stu-id="149af-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="149af-294">Jeśli oznaczysz `inline`funkcję jako , kod, który używa krotek referencyjnych może uzyskać dodatkowe optymalizacje lub kod, który przydzieli, może być po prostu zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="149af-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="149af-295">Należy zawsze mierzyć wyniki, gdy chodzi o wydajność, i nigdy nie działać w oparciu o założenia lub intuicji.</span><span class="sxs-lookup"><span data-stu-id="149af-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="149af-296">Preferuj rekordy struktury, gdy typ danych jest mały</span><span class="sxs-lookup"><span data-stu-id="149af-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="149af-297">Reguła opisana wcześniej również przechowuje dla [typów rekordów F#.](../language-reference/records.md)</span><span class="sxs-lookup"><span data-stu-id="149af-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="149af-298">Należy wziąć pod uwagę następujące typy danych i funkcje, które je przetwarzają:</span><span class="sxs-lookup"><span data-stu-id="149af-298">Consider the following data types and functions that process them:</span></span>

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

<span data-ttu-id="149af-299">Jest to podobne do poprzedniego kodu krotki, ale tym razem w przykładzie używa rekordów i wbudowanej funkcji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="149af-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="149af-300">Podczas porównywania tych funkcji za pomocą statystycznego narzędzia do analizy `processStructPoint` porównawczej, takiego jak [BenchmarkDotNet,](https://benchmarkdotnet.org/)przekonasz się, że działa prawie 60% szybciej i nie przydziela niczego na zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="149af-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="149af-301">Preferuj struktury dyskryminowane związki, gdy typ danych jest mały</span><span class="sxs-lookup"><span data-stu-id="149af-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="149af-302">Poprzednie obserwacje dotyczące wydajności z struct krotek i rekordów posiada również dla [F# Dyskryminowane związki](../language-reference/discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="149af-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="149af-303">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="149af-303">Consider the following code:</span></span>

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

<span data-ttu-id="149af-304">Często definiuje się pojedyncze związki dyskryminowane, takie jak ta dla modelowania domen.</span><span class="sxs-lookup"><span data-stu-id="149af-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="149af-305">Podczas porównywania tych funkcji za pomocą statystycznego narzędzia do analizy `structReverseName` porównawczej, takiego jak `reverseName` [BenchmarkDotNet,](https://benchmarkdotnet.org/)przekonasz się, że działa o 25% szybciej niż w przypadku małych ciągów.</span><span class="sxs-lookup"><span data-stu-id="149af-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="149af-306">W przypadku dużych ciągów oba działają mniej więcej tak samo.</span><span class="sxs-lookup"><span data-stu-id="149af-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="149af-307">Tak więc, w tym przypadku, zawsze lepiej jest użyć struktury.</span><span class="sxs-lookup"><span data-stu-id="149af-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="149af-308">Jak wcześniej wspomniano, zawsze mierzyć i nie działać na założeniach lub intuicji.</span><span class="sxs-lookup"><span data-stu-id="149af-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="149af-309">Chociaż poprzedni przykład wykazał, że struktura Unia dyskryminowana przyniosła lepszą wydajność, często podczas modelowania domeny występuje większa liczba dyskryminowanych związków.</span><span class="sxs-lookup"><span data-stu-id="149af-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="149af-310">Większe typy danych, takie jak to może nie działać, jak również, jeśli są one struktury w zależności od operacji na nich, ponieważ więcej kopiowania może być zaangażowany.</span><span class="sxs-lookup"><span data-stu-id="149af-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="149af-311">Programowanie funkcjonalne i mutacja</span><span class="sxs-lookup"><span data-stu-id="149af-311">Functional programming and mutation</span></span>

<span data-ttu-id="149af-312">F# wartości są domyślnie niezmienne, co pozwala uniknąć niektórych klas błędów (zwłaszcza tych obejmujących współbieżność i równoległości).</span><span class="sxs-lookup"><span data-stu-id="149af-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="149af-313">Jednak w niektórych przypadkach, w celu osiągnięcia optymalnej (lub nawet uzasadnione) efektywności wykonywania czasu lub alokacji pamięci, zakres pracy może być najlepiej realizowane przy użyciu mutacji w miejscu stanu.</span><span class="sxs-lookup"><span data-stu-id="149af-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="149af-314">Jest to możliwe w zasadzie opt-in `mutable` z F# ze słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="149af-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="149af-315">Korzystanie `mutable` z w F# może czuć się w sprzeczności z czystości funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="149af-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="149af-316">Jest to zrozumiałe, ale funkcjonalna czystość wszędzie może być sprzeczna z celami wydajności.</span><span class="sxs-lookup"><span data-stu-id="149af-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="149af-317">Kompromisem jest hermetyzacja mutacji w taki sposób, że dzwoniący nie muszą dbać o to, co się dzieje, gdy nazywają funkcję.</span><span class="sxs-lookup"><span data-stu-id="149af-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="149af-318">Dzięki temu można napisać interfejs funkcjonalny za pomocą implementacji opartej na mutacji dla kodu o krytycznym znaczeniu dla wydajności.</span><span class="sxs-lookup"><span data-stu-id="149af-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="149af-319">Zawijanie kodu zmiennego w interfejsach niezmiennych</span><span class="sxs-lookup"><span data-stu-id="149af-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="149af-320">Z przezroczystości referencyjnej jako cel, ważne jest, aby napisać kod, który nie ujawnia zmienny podbrzusze funkcji krytycznych dla wydajności.</span><span class="sxs-lookup"><span data-stu-id="149af-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="149af-321">Na przykład następujący kod implementuje `Array.contains` funkcję w bibliotece podstawowej F#:</span><span class="sxs-lookup"><span data-stu-id="149af-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="149af-322">Wywołanie tej funkcji wiele razy nie zmienia podstawowej tablicy, ani nie wymaga utrzymania stanu zmiennego w jej użyciu.</span><span class="sxs-lookup"><span data-stu-id="149af-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="149af-323">Jest referencyjnie przezroczysty, mimo że prawie każdy wiersz kodu w nim używa mutacji.</span><span class="sxs-lookup"><span data-stu-id="149af-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="149af-324">Rozważ hermetyzacje zmiennych danych w klasach</span><span class="sxs-lookup"><span data-stu-id="149af-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="149af-325">W poprzednim przykładzie użyto pojedynczej funkcji do hermetyzacji operacji przy użyciu danych zapisywanych.</span><span class="sxs-lookup"><span data-stu-id="149af-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="149af-326">Nie zawsze jest to wystarczające dla bardziej złożonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="149af-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="149af-327">Należy wziąć pod uwagę następujące zestawy funkcji:</span><span class="sxs-lookup"><span data-stu-id="149af-327">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="149af-328">Ten kod jest działanie, ale udostępnia strukturę danych opartych na mutacji, które obiekty wywołujące są odpowiedzialne za utrzymanie.</span><span class="sxs-lookup"><span data-stu-id="149af-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="149af-329">To może być zawijana wewnątrz klasy bez podstawowych elementów członkowskich, które można zmienić:</span><span class="sxs-lookup"><span data-stu-id="149af-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="149af-330">`Closure1Table`hermetyzuje podstawową strukturę danych opartą na mutacji, nie zmuszając w ten sposób osób dzwoniących do utrzymania podstawowej struktury danych.</span><span class="sxs-lookup"><span data-stu-id="149af-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="149af-331">Klasy są skutecznym sposobem hermetyzacji danych i procedur, które są oparte na mutacji bez ujawniania szczegółów dla wywoływania.</span><span class="sxs-lookup"><span data-stu-id="149af-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="149af-332">Wolę `let mutable` odwoływać się do komórek</span><span class="sxs-lookup"><span data-stu-id="149af-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="149af-333">Komórki referencyjne są sposobem reprezentowania odwołania do wartości, a nie samej wartości.</span><span class="sxs-lookup"><span data-stu-id="149af-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="149af-334">Mimo że mogą być używane dla kodu o krytycznym znaczeniu dla wydajności, nie są zalecane.</span><span class="sxs-lookup"><span data-stu-id="149af-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="149af-335">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="149af-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="149af-336">Użycie komórki odniesienia teraz "zanieczyszcza" wszystkie kolejne kodu z konieczności wyłuskania i ponownego odwoływania się do danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="149af-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="149af-337">Zamiast tego `let mutable`należy wziąć pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="149af-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="149af-338">Oprócz pojedynczego punktu mutacji w środku wyrażenia lambda, wszystkie `acc` inne typy, które dotknie można to zrobić `let`w sposób, który nie różni się od użycia normalnej wartości niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="149af-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="149af-339">Ułatwi to zmianę w czasie.</span><span class="sxs-lookup"><span data-stu-id="149af-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="149af-340">Programowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="149af-340">Object programming</span></span>

<span data-ttu-id="149af-341">F# ma pełną obsługę obiektów i koncepcji zorientowanych obiektowo (OO).</span><span class="sxs-lookup"><span data-stu-id="149af-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="149af-342">Chociaż wiele koncepcji oo są potężne i przydatne, nie wszystkie z nich są idealne do użycia.</span><span class="sxs-lookup"><span data-stu-id="149af-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="149af-343">Poniższe listy zawierają wskazówki dotyczące kategorii funkcji oo na wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="149af-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="149af-344">**Należy rozważyć użycie tych funkcji w wielu sytuacjach:**</span><span class="sxs-lookup"><span data-stu-id="149af-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="149af-345">Notacja kropka`x.Length`( )</span><span class="sxs-lookup"><span data-stu-id="149af-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="149af-346">Członkowie instancji</span><span class="sxs-lookup"><span data-stu-id="149af-346">Instance members</span></span>
* <span data-ttu-id="149af-347">Konstruktory niejawne</span><span class="sxs-lookup"><span data-stu-id="149af-347">Implicit constructors</span></span>
* <span data-ttu-id="149af-348">Statyczne składowe</span><span class="sxs-lookup"><span data-stu-id="149af-348">Static members</span></span>
* <span data-ttu-id="149af-349">Notacja indeksatora (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="149af-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="149af-350">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="149af-350">Named and Optional arguments</span></span>
* <span data-ttu-id="149af-351">Interfejsy i implementacje interfejsów</span><span class="sxs-lookup"><span data-stu-id="149af-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="149af-352">**Nie sięgnij po te funkcje, ale rozsądnie zastosuj je, gdy są wygodne do rozwiązania problemu:**</span><span class="sxs-lookup"><span data-stu-id="149af-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="149af-353">Przeciążenie metody</span><span class="sxs-lookup"><span data-stu-id="149af-353">Method overloading</span></span>
* <span data-ttu-id="149af-354">Zhermetyzowane dane zmienne</span><span class="sxs-lookup"><span data-stu-id="149af-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="149af-355">Operatorzy na typach</span><span class="sxs-lookup"><span data-stu-id="149af-355">Operators on types</span></span>
* <span data-ttu-id="149af-356">Właściwości automatyczne</span><span class="sxs-lookup"><span data-stu-id="149af-356">Auto properties</span></span>
* <span data-ttu-id="149af-357">Wdrażanie `IDisposable` i wdrażanie`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="149af-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="149af-358">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="149af-358">Type extensions</span></span>
* <span data-ttu-id="149af-359">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="149af-359">Events</span></span>
* <span data-ttu-id="149af-360">Struktury</span><span class="sxs-lookup"><span data-stu-id="149af-360">Structs</span></span>
* <span data-ttu-id="149af-361">Delegaty</span><span class="sxs-lookup"><span data-stu-id="149af-361">Delegates</span></span>
* <span data-ttu-id="149af-362">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="149af-362">Enums</span></span>

<span data-ttu-id="149af-363">**Generalnie unikaj tych funkcji, chyba że musisz z nich korzystać:**</span><span class="sxs-lookup"><span data-stu-id="149af-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="149af-364">Hierarchie typów oparte na dziedziczeniu i dziedziczenie implementacji</span><span class="sxs-lookup"><span data-stu-id="149af-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="149af-365">Wartości null i`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="149af-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="149af-366">Preferuj kompozycję niż dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="149af-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="149af-367">[Skład nad dziedziczeniem](https://en.wikipedia.org/wiki/Composition_over_inheritance) jest od dawna idiom, że dobry kod F# można stosować się do.</span><span class="sxs-lookup"><span data-stu-id="149af-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="149af-368">Podstawową zasadą jest, że nie należy uwidaczniać klasy podstawowej i wymusić obiekty wywołujące dziedziczyć z tej klasy podstawowej, aby uzyskać funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="149af-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="149af-369">Użyj wyrażeń obiektów do zaimplementowania interfejsów, jeśli nie potrzebujesz klasy</span><span class="sxs-lookup"><span data-stu-id="149af-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="149af-370">[Wyrażenia obiektów](../language-reference/object-expressions.md) umożliwiają implementowanie interfejsów w locie, powiązanie zaimplementowanego interfejsu z wartością bez konieczności wykonywania tego wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="149af-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="149af-371">Jest to wygodne, zwłaszcza jeśli trzeba _tylko_ zaimplementować interfejs i nie ma potrzeby pełnej klasy.</span><span class="sxs-lookup"><span data-stu-id="149af-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="149af-372">Na przykład oto kod, który jest uruchamiany w [Jonide,](http://ionide.io/) aby zapewnić akcję poprawki kodu, `open` jeśli dodano symbol, który nie ma instrukcji dla:</span><span class="sxs-lookup"><span data-stu-id="149af-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="149af-373">Ponieważ nie ma potrzeby klasy podczas interakcji z interfejsem API kodu programu Visual Studio, wyrażenia obiektów są idealnym narzędziem do tego.</span><span class="sxs-lookup"><span data-stu-id="149af-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="149af-374">Są one również cenne dla testowania jednostkowego, gdy chcesz wycinek interfejs z procedur testowych w sposób doraźny.</span><span class="sxs-lookup"><span data-stu-id="149af-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="149af-375">Należy wziąć pod uwagę skróty tekstu, aby skrócić podpisy</span><span class="sxs-lookup"><span data-stu-id="149af-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="149af-376">[Skróty tekstu](../language-reference/type-abbreviations.md) są wygodnym sposobem przypisywania etykiety do innego typu, takiego jak podpis funkcji lub typ bardziej złożony.</span><span class="sxs-lookup"><span data-stu-id="149af-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="149af-377">Na przykład następujący alias przypisuje etykietę do tego, co jest potrzebne do zdefiniowania obliczeń z [CNTK](https://docs.microsoft.com/cognitive-toolkit/), biblioteki uczenia głębokiego:</span><span class="sxs-lookup"><span data-stu-id="149af-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="149af-378">Nazwa `Computation` jest wygodnym sposobem oznaczania dowolnej funkcji, która pasuje do podpisu, który jest aliasing.</span><span class="sxs-lookup"><span data-stu-id="149af-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="149af-379">Korzystanie z skrótów typu jak to jest wygodne i pozwala na bardziej zwięzły kod.</span><span class="sxs-lookup"><span data-stu-id="149af-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="149af-380">Unikaj używania skrótów tekstu do reprezentowania domeny</span><span class="sxs-lookup"><span data-stu-id="149af-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="149af-381">Chociaż skróty typu są wygodne do nadania nazwy sygnaturom funkcji, mogą być mylące podczas skracania innych typów.</span><span class="sxs-lookup"><span data-stu-id="149af-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="149af-382">Należy wziąć pod uwagę ten skrót:</span><span class="sxs-lookup"><span data-stu-id="149af-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="149af-383">Może to być mylące na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="149af-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="149af-384">`BufferSize`nie jest abstrakcją; to tylko inna nazwa liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="149af-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="149af-385">Jeśli `BufferSize` jest narażony w publicznym interfejsie API, można go łatwo `int`błędnie zinterpretować jako coś więcej niż tylko .</span><span class="sxs-lookup"><span data-stu-id="149af-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="149af-386">Ogólnie rzecz biorąc typy domen mają wiele atrybutów do `int`nich i nie są typy pierwotne, takie jak .</span><span class="sxs-lookup"><span data-stu-id="149af-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="149af-387">Ten skrót narusza to założenie.</span><span class="sxs-lookup"><span data-stu-id="149af-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="149af-388">Obudowa `BufferSize` (PascalCase) oznacza, że ten typ przechowuje więcej danych.</span><span class="sxs-lookup"><span data-stu-id="149af-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="149af-389">Ten alias nie oferuje większej jasności w porównaniu z dostarczaniem nazwany argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="149af-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="149af-390">Skrót nie będzie przejawiać się w skompilowanym IL; jest to tylko liczba całkowita i ten alias jest kompilacji czasu.</span><span class="sxs-lookup"><span data-stu-id="149af-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="149af-391">Podsumowując, pułapka z skrótami typu jest to, że **nie** są abstrakcje nad typami są skróty.</span><span class="sxs-lookup"><span data-stu-id="149af-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="149af-392">W poprzednim przykładzie `BufferSize` jest `int` tylko pod przykrywką, bez dodatkowych danych, ani `int` żadnych korzyści z systemu typu oprócz tego, co już ma.</span><span class="sxs-lookup"><span data-stu-id="149af-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="149af-393">Alternatywnym podejściem do używania skrótów typów do reprezentowania domeny jest użycie jednoprzypadkówowych związków dyskryminowanych.</span><span class="sxs-lookup"><span data-stu-id="149af-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="149af-394">Poprzedni przykład można modelować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="149af-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="149af-395">Jeśli piszesz kod, który `BufferSize` działa pod względem i jego wartości bazowej, należy skonstruować jeden, a nie przekazać w dowolnej dowolnych liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="149af-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="149af-396">Zmniejsza to prawdopodobieństwo omyłkowego przekazywania dowolnych liczb całkowitych `send` do `BufferSize` funkcji, ponieważ obiekt wywołujący musi skonstruować typ, aby zawinąć wartość przed wywołaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="149af-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
