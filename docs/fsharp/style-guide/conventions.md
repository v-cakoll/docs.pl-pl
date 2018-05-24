---
title: 'Konwencje kodowania F #'
description: 'Informacje ogólne wytyczne i idioms podczas zapisywania w kodzie języka F #.'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="f-coding-conventions"></a><span data-ttu-id="635fd-103">Konwencje kodowania F #</span><span class="sxs-lookup"><span data-stu-id="635fd-103">F# coding conventions</span></span>

<span data-ttu-id="635fd-104">Następujące konwencje są formułowane z doświadczenia w pracy z dużą F # codebases.</span><span class="sxs-lookup"><span data-stu-id="635fd-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="635fd-105">[Pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code) są podstawę poszczególne zalecenia.</span><span class="sxs-lookup"><span data-stu-id="635fd-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="635fd-106">Są one związane z [F # składnika zaleceń dotyczących projektowania](component-design-guidelines.md), ale są stosowane do dowolnego kodzie języka F #, nie tylko składniki, takie jak biblioteki.</span><span class="sxs-lookup"><span data-stu-id="635fd-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="635fd-107">Organizowanie kodu</span><span class="sxs-lookup"><span data-stu-id="635fd-107">Organizing code</span></span>

<span data-ttu-id="635fd-108">Dwa podstawowe sposoby organizowanie kodu funkcje F #: moduły i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="635fd-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="635fd-109">Te są podobne, ale różnią się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="635fd-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="635fd-110">Przestrzenie nazw są kompilowane jako przestrzenie nazw .NET.</span><span class="sxs-lookup"><span data-stu-id="635fd-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="635fd-111">Moduły są kompilowane jako klasy statyczne.</span><span class="sxs-lookup"><span data-stu-id="635fd-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="635fd-112">Przestrzenie nazw są zawsze najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="635fd-112">Namespaces are always top level.</span></span> <span data-ttu-id="635fd-113">Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="635fd-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="635fd-114">Przestrzenie nazw może obejmować wiele plików.</span><span class="sxs-lookup"><span data-stu-id="635fd-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="635fd-115">Nie można modułów.</span><span class="sxs-lookup"><span data-stu-id="635fd-115">Modules cannot.</span></span>
* <span data-ttu-id="635fd-116">Moduły mogą być oznaczone `[<RequireQualifiedAccess>]` i `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="635fd-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="635fd-117">Poniższe wskazówki ułatwiają ich używać do organizowania kodu.</span><span class="sxs-lookup"><span data-stu-id="635fd-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="635fd-118">Preferowane jest przestrzeni nazw na najwyższym poziomie</span><span class="sxs-lookup"><span data-stu-id="635fd-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="635fd-119">Dla żadnego kodu publicznie eksploatacyjny przestrzenie nazw są preferencyjne modułów na najwyższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="635fd-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="635fd-120">Ponieważ są one kompilowane jako przestrzenie nazw .NET, są one dostępne w języku C# nie problem.</span><span class="sxs-lookup"><span data-stu-id="635fd-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="635fd-121">Za pomocą modułu najwyższego poziomu mogą nie być wyświetlane inaczej wywoływane tylko z F #, ale C# konsumentów, może oczekiwano wywołań, pozwalając na kwalifikować się `MyClass` z `MyCode` modułu.</span><span class="sxs-lookup"><span data-stu-id="635fd-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="635fd-122">Starannie Zastosuj `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="635fd-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="635fd-123">`[<AutoOpen>]` Konstrukcja można charakteryzują się zakres co jest dostępne dla kodu wywołującego, a odpowiedź na coś, z której pochodzi to "magicznych".</span><span class="sxs-lookup"><span data-stu-id="635fd-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="635fd-124">Zwykle nie jest to dobrze, że.</span><span class="sxs-lookup"><span data-stu-id="635fd-124">This is generally not a good thing.</span></span> <span data-ttu-id="635fd-125">Wyjątek od tej reguły jest biblioteki podstawowej F #, sama (chociaż ten fakt również jest nieco kontrowersyjna).</span><span class="sxs-lookup"><span data-stu-id="635fd-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="635fd-126">Jednak jest on udogodnienie, jeśli masz funkcji pomocnika dla publiczny interfejs API, który ma zostać organizowanie oddzielnie z tym publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="635fd-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="635fd-127">Dzięki temu można szczegóły implementacji oddzielne bezpośrednio z publiczny interfejs API funkcji bez konieczności pełnej kwalifikacji pomocnika za każdym razem, należy wywołać.</span><span class="sxs-lookup"><span data-stu-id="635fd-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="635fd-128">Ponadto udostępnia metody rozszerzenia i konstruktorów wyrażeń na poziomie przestrzeni nazw może być starannie wyrażona z `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="635fd-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="635fd-129">Użyj `[<RequireQualifiedAccess>]` podczas każdego może powodować konflikt nazw lub uważasz, że ułatwia czytelności</span><span class="sxs-lookup"><span data-stu-id="635fd-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="635fd-130">Dodawanie `[<RequireQualifiedAccess>]` modułu dla atrybutu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu, wymaga jawnego kwalifikowana dostępu.</span><span class="sxs-lookup"><span data-stu-id="635fd-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="635fd-131">Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="635fd-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="635fd-132">Jest to przydatne, gdy wartości w module i funkcje mają nazwy, które mogą powodować konflikt z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="635fd-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="635fd-133">Wymagających dostępu kwalifikowaną może znacznie zwiększyć długoterminowej utrzymanie i evolvability biblioteki.</span><span class="sxs-lookup"><span data-stu-id="635fd-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="635fd-134">Sortuj `open` instrukcje topologically</span><span class="sxs-lookup"><span data-stu-id="635fd-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="635fd-135">W języku F #, ma znaczenie kolejności zgłoszeń, łącznie z `open` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="635fd-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="635fd-136">Jest to w przeciwieństwie do języka C#, gdzie efekt `using` i `using static` jest niezależna od kolejności tych instrukcji w pliku.</span><span class="sxs-lookup"><span data-stu-id="635fd-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="635fd-137">W języku F # elementy otwarte w zakresie można w tle innych jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="635fd-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="635fd-138">Oznacza to, że zmiana kolejności `open` instrukcje może zmienić znaczenie kodu.</span><span class="sxs-lookup"><span data-stu-id="635fd-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="635fd-139">W rezultacie, wszystkie dowolnego sortowanie wszystkich `open` instrukcje (na przykład alfanumerycznie) zwykle nie jest zalecane, co najmniej Generowanie inaczej, które mogą wymagać.</span><span class="sxs-lookup"><span data-stu-id="635fd-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="635fd-140">Zamiast tego zaleca się je posortować [topologically](https://en.wikipedia.org/wiki/Topological_sorting); oznacza to, że kolejność Twojej `open` instrukcje w kolejności, w jakiej _warstwy_ systemu są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="635fd-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="635fd-141">Podczas sortowania w różnych warstwach topologiczne alfanumeryczne mogą być również uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="635fd-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="635fd-142">Na przykład poniżej przedstawiono topologiczne sortowania dla języka F # kompilatora publicznego interfejsu API pliku usługi:</span><span class="sxs-lookup"><span data-stu-id="635fd-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="635fd-143">Należy pamiętać, że podział wiersza oddziela topologiczne warstwy z każdej warstwy sortowane alfanumerycznie później.</span><span class="sxs-lookup"><span data-stu-id="635fd-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="635fd-144">Kod zostanie prawidłowo organizuje bez przypadkowo przesłanianie wartości.</span><span class="sxs-lookup"><span data-stu-id="635fd-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="635fd-145">Klasy służą do zawierają wartości, które ma efekty uboczne</span><span class="sxs-lookup"><span data-stu-id="635fd-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="635fd-146">Istnieje wiele razy podczas inicjowania wartość może mieć efekty uboczne, takich jak tworzenie wystąpień kontekstu do bazy danych lub innego zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="635fd-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="635fd-147">Jest kuszące zainicjować takich elementów w module i użyć go w kolejnych funkcje:</span><span class="sxs-lookup"><span data-stu-id="635fd-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="635fd-148">To jest często dobrym pomysłem kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="635fd-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="635fd-149">Po pierwsze, konfiguracji aplikacji zostanie przypisany do codebase z `dep1` i `dep2`.</span><span class="sxs-lookup"><span data-stu-id="635fd-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="635fd-150">To jest trudne w utrzymaniu w się, że codebases większy.</span><span class="sxs-lookup"><span data-stu-id="635fd-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="635fd-151">Drugi, statycznie zainicjowane danych nie może zawierać wartości, które nie są bezpieczne dla wątków, jeśli sam składnika będzie używać wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="635fd-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="635fd-152">Jest to wyraźnie naruszone przez `dep3`.</span><span class="sxs-lookup"><span data-stu-id="635fd-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="635fd-153">Na koniec inicjowania modułu kompiluje w konstruktorze statycznym kompilacji całej jednostki.</span><span class="sxs-lookup"><span data-stu-id="635fd-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="635fd-154">W przypadku błędu podczas inicjowania let granica wartości w module, manifesty go jako `TypeInitializationException` który następnie jest buforowana przez cały czas ich istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="635fd-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="635fd-155">Może to być trudne do diagnozowania.</span><span class="sxs-lookup"><span data-stu-id="635fd-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="635fd-156">Zazwyczaj jest wyjątek wewnętrzny, który można spróbować przyczyny o, ale jeśli nie ma, to nie ma żadnych informuje jest główną przyczynę.</span><span class="sxs-lookup"><span data-stu-id="635fd-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="635fd-157">Po prostu użyj prostą klasę do przechowywania zależności:</span><span class="sxs-lookup"><span data-stu-id="635fd-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="635fd-158">Umożliwia to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="635fd-158">This enables the following:</span></span>

1. <span data-ttu-id="635fd-159">Wypychanie każdy stan zależnych poza samego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="635fd-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="635fd-160">Teraz można konfiguracji poza interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="635fd-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="635fd-161">Błędy podczas inicjowania dla wartości zależnych nie są może być przedstawiany jako `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="635fd-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="635fd-162">Interfejs API jest teraz łatwiejsze testowanie.</span><span class="sxs-lookup"><span data-stu-id="635fd-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="635fd-163">Błąd zarządzania</span><span class="sxs-lookup"><span data-stu-id="635fd-163">Error management</span></span>

<span data-ttu-id="635fd-164">Błąd zarządzania w dużych systemach jest pozwala złożone i nuanced i nie ma żadnych silver punktory w celu zapewnienia systemy są odpornej na uszkodzenia i zachowywać się również.</span><span class="sxs-lookup"><span data-stu-id="635fd-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="635fd-165">Poniższe wskazówki powinno oferować wskazówki przechodzenia to miejsce trudne.</span><span class="sxs-lookup"><span data-stu-id="635fd-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="635fd-166">W przypadku wystąpienia błędów i stan niedozwolony w typach wewnętrznej do domeny</span><span class="sxs-lookup"><span data-stu-id="635fd-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="635fd-167">Z [Suma rozłączna unie](../language-reference/discriminated-unions.md), F # daje możliwość reprezentuje stan uszkodzony programu w systemie typów.</span><span class="sxs-lookup"><span data-stu-id="635fd-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="635fd-168">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="635fd-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="635fd-169">W takim przypadku istnieją trzy sposoby znane, których wycofanie pieniędzy z konta bankowego może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="635fd-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="635fd-170">Każdy przypadek błędu jest reprezentowana w typie, a w związku z tym można przetwarzać bezpiecznie w programie.</span><span class="sxs-lookup"><span data-stu-id="635fd-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="635fd-171">Ogólnie rzecz biorąc, jeśli modelu różne sposoby szukają można **niepowodzenie** w domenie, następnie kod obsługi błędów jest już traktowany jako element musi dotyczyć oprócz zwykłego przepływu.</span><span class="sxs-lookup"><span data-stu-id="635fd-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="635fd-172">Jest po prostu część przepływu normalnego programu, a nie omówiono **wyjątkowych**.</span><span class="sxs-lookup"><span data-stu-id="635fd-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="635fd-173">Istnieją dwie główne korzyści wynikające z to:</span><span class="sxs-lookup"><span data-stu-id="635fd-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="635fd-174">Jest łatwiejsze w obsłudze, ponieważ domeny zmienia się wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="635fd-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="635fd-175">W przypadku wystąpienia błędów są łatwiejsze do testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="635fd-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="635fd-176">Użyj wyjątków, jeśli błędy nie może być reprezentowana typów</span><span class="sxs-lookup"><span data-stu-id="635fd-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="635fd-177">Nie wszystkie błędy mogą być reprezentowane w domeny problemu.</span><span class="sxs-lookup"><span data-stu-id="635fd-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="635fd-178">Tego rodzaju błędów są *wyjątkowych* charakter, dlatego możliwość pozyskiwania i przechwytywanie wyjątków w języku F #.</span><span class="sxs-lookup"><span data-stu-id="635fd-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="635fd-179">Po pierwsze zaleca się przeczytanie [zaleceń dotyczących projektowania wyjątek](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="635fd-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="635fd-180">Są to również zastosowanie do F #.</span><span class="sxs-lookup"><span data-stu-id="635fd-180">These are also applicable to F#.</span></span>

<span data-ttu-id="635fd-181">Główne konstrukcje, dostępne w języku F # na potrzeby występowanie wyjątków należy rozważyć w podanej poniżej kolejności preferencji:</span><span class="sxs-lookup"><span data-stu-id="635fd-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="635fd-182">Funkcja</span><span class="sxs-lookup"><span data-stu-id="635fd-182">Function</span></span> | <span data-ttu-id="635fd-183">Składnia</span><span class="sxs-lookup"><span data-stu-id="635fd-183">Syntax</span></span> | <span data-ttu-id="635fd-184">Cel</span><span class="sxs-lookup"><span data-stu-id="635fd-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="635fd-185">Zgłasza `System.ArgumentNullException` o nazwie określonego argumentu.</span><span class="sxs-lookup"><span data-stu-id="635fd-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="635fd-186">Wywołuje `System.ArgumentException` z nazwą określony argument i komunikatu.</span><span class="sxs-lookup"><span data-stu-id="635fd-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="635fd-187">Wywołuje `System.InvalidOperationException` z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="635fd-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="635fd-188">Mechanizm ogólnego przeznaczenia zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="635fd-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="635fd-189">Wywołuje `System.Exception` z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="635fd-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="635fd-190">Zgłasza `System.Exception` komunikatem określona przez ciąg formatu i jego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="635fd-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="635fd-191">Użyj `nullArg`, `invalidArg` i `invalidOp` jako mechanizm throw `ArgumentNullException`, `ArgumentException` i `InvalidOperationException` w odpowiednim przypadku.</span><span class="sxs-lookup"><span data-stu-id="635fd-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="635fd-192">`failwith` i `failwithf` funkcje ogólnie należy unikać, ponieważ ich podnieść podstawowym `Exception` wpisz określony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="635fd-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="635fd-193">Zgodnie [zaleceń dotyczących projektowania wyjątek](../../standard/design-guidelines/exceptions.md), aby zgłaszał bardziej szczegółowe wyjątki, które można wykonywać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="635fd-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="635fd-194">Przy użyciu składni Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="635fd-194">Using exception-handling syntax</span></span>

<span data-ttu-id="635fd-195">F # obsługuje wzorce wyjątek za pośrednictwem `try...with` składni:</span><span class="sxs-lookup"><span data-stu-id="635fd-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="635fd-196">Uzgadnianie funkcja do wykonania w wypadku wyjątków o dopasowanie wzorca mogą być nieco trudnych, jeśli chcesz zachować czysty kod.</span><span class="sxs-lookup"><span data-stu-id="635fd-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="635fd-197">Jeden sposób obsługi to jest użycie [aktywne wzorce](../language-reference/active-patterns.md) jako środek do funkcji grupy otaczającego przypadek błędu, z wyjątkiem samej siebie.</span><span class="sxs-lookup"><span data-stu-id="635fd-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="635fd-198">Na przykład użytkownik może korzystać z interfejs API, który po zgłasza wyjątek, umieszcza cenne informacje w metadanych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="635fd-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="635fd-199">Odkodowywania wartość przydatne w treści przechwycony wyjątek wewnątrz aktywnego wzorca i zwracanie, czy wartość może być pomocny w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="635fd-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="635fd-200">Nie używaj monadic obsługę błędów do zastąpienia wyjątków</span><span class="sxs-lookup"><span data-stu-id="635fd-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="635fd-201">Wyjątki są widoczne jako nieco taboo w programowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="635fd-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="635fd-202">W rzeczywistości wyjątki narusza czystości, więc bezpiecznie wziąć pod uwagę ich nie całkiem funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="635fd-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="635fd-203">Jednak to ignoruje rzeczywistości gdzie uruchomić kod i że środowiska uruchomieniowego, które mogą wystąpić błędy.</span><span class="sxs-lookup"><span data-stu-id="635fd-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="635fd-204">Ogólnie rzecz biorąc przy założeniu, że większości zadań nie są pure ani całkowity, aby zminimalizować nieprzyjemny niespodzianki należy napisać kod.</span><span class="sxs-lookup"><span data-stu-id="635fd-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="635fd-205">Należy wziąć pod uwagę następujące podstawowe sile/aspekty wyjątków względem ich znaczenie i właściwości środowisko uruchomieniowe platformy .NET i wielu języków ekosystemu jako całość:</span><span class="sxs-lookup"><span data-stu-id="635fd-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="635fd-206">Zawierają szczegółowe informacje diagnostyczne, które jest bardzo przydatne, gdy debugowanie problemu.</span><span class="sxs-lookup"><span data-stu-id="635fd-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="635fd-207">Są one przejrzyste przez środowisko uruchomieniowe i innych języków platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="635fd-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="635fd-208">Mogą zmniejszać znaczących umożliwiającego w porównaniu z kodem wykraczające poza jego sposobem *uniknąć* wyjątki zaimplementowanie niektórych podzbiór ich semantyki na podstawie ad hoc.</span><span class="sxs-lookup"><span data-stu-id="635fd-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="635fd-209">Bardzo ważne jest ten punkt trzecich.</span><span class="sxs-lookup"><span data-stu-id="635fd-209">This third point is critical.</span></span> <span data-ttu-id="635fd-210">Proste operacji złożonych można użyć wyjątki może spowodować zajmowanie struktur w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="635fd-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="635fd-211">Łatwo a to może prowadzić do słabe kodu jak dopasowania wzorca w "stringly wpisane" błędy:</span><span class="sxs-lookup"><span data-stu-id="635fd-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="635fd-212">Ponadto może być kuszące jest swallow żadnych wyjątków w desire dla funkcji "prosty", który zwraca typ "wrażeń":</span><span class="sxs-lookup"><span data-stu-id="635fd-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="635fd-213">Niestety `tryReadAllText` może zgłosić wiele wyjątków opartych na różnych rzeczy, które mogą wystąpić w systemie plików i ten kod nieobecności odrzuca żadnych informacji o co może być przechodzenia do niewłaściwej w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="635fd-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="635fd-214">Jeśli typ wyniku możesz zastąpić ten kod, następnie wszystko do analizowania komunikat "stringly wpisane" Błąd:</span><span class="sxs-lookup"><span data-stu-id="635fd-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="635fd-215">I wprowadzania sam obiekt wyjątku w `Error` Konstruktor tylko wymusza prawidłowo radzenia sobie z typ wyjątku, w miejsce wywołania, a nie w funkcji.</span><span class="sxs-lookup"><span data-stu-id="635fd-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="635fd-216">Spowoduje to skutecznie tworzy zaznaczone wyjątki, które są bardzo unfun radzenia sobie z jako obiekt wywołujący interfejs API.</span><span class="sxs-lookup"><span data-stu-id="635fd-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="635fd-217">Dobrą alternatywą do powyższe przykłady ma catch *określonych* wyjątków i przywracać odpowiednią wartość w kontekście tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="635fd-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="635fd-218">Jeśli zmodyfikujesz `tryReadAllText` działa w następujący sposób `None` ma więcej znaczenie:</span><span class="sxs-lookup"><span data-stu-id="635fd-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="635fd-219">Zamiast działać jako catch-all, ta funkcja zostanie teraz poprawnie obsługiwać przypadku plik nie został znaleziony i przypisanie tego znaczenie do powrotu.</span><span class="sxs-lookup"><span data-stu-id="635fd-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="635fd-220">Zwrócona wartość można mapować do tego przypadku błędu podczas nie odrzuca wszystkie informacje kontekstowe lub wymuszania wywołań radzenia sobie z przypadkiem, które nie mogą być użyteczne w tym momencie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="635fd-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="635fd-221">Typy, takich jak `Result<'Success, 'Error>` są odpowiednie dla podstawowe operacje, których nie są one zagnieżdżone i F # opcjonalne typy są idealne w przypadku reprezentujący, gdy coś można albo zwrot *coś* lub *nic*.</span><span class="sxs-lookup"><span data-stu-id="635fd-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="635fd-222">One zastępuje wyjątki, nie są jednak i nie może być używany w próba do zastąpienia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="635fd-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="635fd-223">Zamiast ich powinny być stosowane rozważnie aspektów określonego adresu wyjątków i błędów zasad zarządzania w sposób docelowych.</span><span class="sxs-lookup"><span data-stu-id="635fd-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="635fd-224">Aplikacja częściowa i bez punktu programowania</span><span class="sxs-lookup"><span data-stu-id="635fd-224">Partial application and point-free programming</span></span>

<span data-ttu-id="635fd-225">F # obsługuje aplikacja częściowa i w związku z tym różne sposoby program w stylu bez punktu.</span><span class="sxs-lookup"><span data-stu-id="635fd-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="635fd-226">Może to być przydatne do ponownego użycia kodu w module lub wykonania elementu, ale zazwyczaj nie jest element zostać udostępniona publicznie.</span><span class="sxs-lookup"><span data-stu-id="635fd-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="635fd-227">Ogólnie rzecz biorąc bez punktu programowania nie jest mocy w i samego siebie i można dodać kognitywnych dużą przeszkodę dla osób, które nie są zanurzony w stylu.</span><span class="sxs-lookup"><span data-stu-id="635fd-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="635fd-228">Nie należy używać aplikacja częściowa i currying w publicznych interfejsach API</span><span class="sxs-lookup"><span data-stu-id="635fd-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="635fd-229">Z wyjątkiem małego korzystanie z częściowa aplikacji w publicznych interfejsach API może być mylące dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="635fd-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="635fd-230">Zazwyczaj `let`-są powiązane wartości w kodzie języka F # **wartości**, a nie **funkcji wartości**.</span><span class="sxs-lookup"><span data-stu-id="635fd-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="635fd-231">Zmieszanie wartości i wartości funkcji może spowodować zapisywanie niewielką liczbę wierszy kodu w zamian dość nieco kognitywnych obciążenie, zwłaszcza, jeśli takie jak połączeniu z operatorami `>>` utworzenie funkcji.</span><span class="sxs-lookup"><span data-stu-id="635fd-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="635fd-232">Należy wziąć pod uwagę wpływ narzędzi do programowania za wolny od punktu</span><span class="sxs-lookup"><span data-stu-id="635fd-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="635fd-233">Funkcje rozwinięte nie etykiety ich argumentów.</span><span class="sxs-lookup"><span data-stu-id="635fd-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="635fd-234">Ma to wpływ narzędzi.</span><span class="sxs-lookup"><span data-stu-id="635fd-234">This has tooling implications.</span></span> <span data-ttu-id="635fd-235">Należy wziąć pod uwagę następujące dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="635fd-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="635fd-236">Oba są prawidłowe funkcje, ale `funcWithApplication` jest funkcją rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="635fd-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="635fd-237">Po umieszczeniu na ich typów w edytorze, zobacz to:</span><span class="sxs-lookup"><span data-stu-id="635fd-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="635fd-238">W witrynie wywołania etykietki narzędzi w narzędzia, takiego jak Visual Studio nie zapewni przydatne informacje dotyczące co `string` i `int` faktycznie stanowi typów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="635fd-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="635fd-239">Jeśli wystąpią bez punktu kodu, takie jak `funcWithApplication` jest publicznie eksploatacyjny, zaleca się wykonywać pełnym rozszerzeniu η narzędzi można wybrać w górę na łatwy do rozpoznania nazwy argumentów.</span><span class="sxs-lookup"><span data-stu-id="635fd-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="635fd-240">Ponadto debugowanie kodu bez punktu może być wyzwaniem, jeśli jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="635fd-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="635fd-241">Narzędzia debugowania zależą od wartości powiązany z nazwy (na przykład `let` powiązań), aby sprawdzić wartości pośrednich połowie poprzez wykonanie.</span><span class="sxs-lookup"><span data-stu-id="635fd-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="635fd-242">Gdy kodu nie zawiera żadnych wartości do zbadania, nie ma nic do debugowania.</span><span class="sxs-lookup"><span data-stu-id="635fd-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="635fd-243">W przyszłości, narzędzia debugowania mogą rozwijać syntetyzować te wartości oparte na ścieżkach poprzednio wykonane, ale nie jest dobrym pomysłem jest zabezpieczenie sieci trafień na *potencjalne* debugowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="635fd-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="635fd-244">Należy wziąć pod uwagę aplikacja częściowa jako technika zmniejszyć umożliwiającego wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="635fd-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="635fd-245">W przeciwieństwie do poprzedniego punktu aplikacja częściowa jest narzędziem cudowne zmniejszenia umożliwiającego wewnątrz aplikacji lub lepszy mechanizmów wewnętrznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="635fd-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="635fd-246">Może być przydatna do implementacji interfejsów API bardziej skomplikowany, gdzie standardowy jest często słabe radzenia sobie z testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="635fd-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="635fd-247">Na przykład w poniższym kodzie jak można wykonać jakie najbardziej mocking platform zapewniają bez konieczności przełączania zależności zewnętrznej na takie framework i konieczności uczenia się z odpowiednimi tworzony na zamówienie interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="635fd-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="635fd-248">Na przykład wziąć pod uwagę następujące topografii rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="635fd-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="635fd-249">`ImplementationLogic.fsproj` może udostępniać kod takich jak:</span><span class="sxs-lookup"><span data-stu-id="635fd-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="635fd-250">Testy jednostkowe `Transactions.doTransaction` w `ImplementationLogic.Tests.fspoj` jest prosty:</span><span class="sxs-lookup"><span data-stu-id="635fd-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="635fd-251">Częściowo stosowania `doTransaction` z kontekstem mocking obiekt umożliwia wywołanie funkcji we wszystkich testów jednostkowych bez konieczności tworzenia kontekstu mocked zawsze:</span><span class="sxs-lookup"><span data-stu-id="635fd-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="635fd-252">Ta technika nie powinny być powszechnie stosowane do całego baza kodu, ale jest to dobry sposób na zmniejszyć umożliwiającego wewnętrzne skomplikowane i te ustawienia wewnętrzne testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="635fd-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="635fd-253">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="635fd-253">Access control</span></span>

<span data-ttu-id="635fd-254">F # udostępnia wiele opcji [kontrola dostępu](../language-reference/access-control.md), dziedziczone z co to jest dostępne w środowisku wykonawczym .NET.</span><span class="sxs-lookup"><span data-stu-id="635fd-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="635fd-255">Nie są użyteczne tylko dla typów — można je Użyj zbyt dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="635fd-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="635fd-256">Preferowane jest inne niż`public` typów i członków, dopóki nie należy ich być publicznie dostępne.</span><span class="sxs-lookup"><span data-stu-id="635fd-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="635fd-257">Zmniejsza to także kilka jakie konsumentów do</span><span class="sxs-lookup"><span data-stu-id="635fd-257">This also minimizes what consumers couple to</span></span>
* <span data-ttu-id="635fd-258">Dokładamy wszelkich starań zachować wszystkie funkcje pomocnicze `private`.</span><span class="sxs-lookup"><span data-stu-id="635fd-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="635fd-259">Rozważ użycie `[<AutoOpen>]` na modułu prywatnego funkcji pomocnika, jeśli staną się wiele.</span><span class="sxs-lookup"><span data-stu-id="635fd-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="635fd-260">Wnioskowanie o typie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="635fd-260">Type inference and generics</span></span>

<span data-ttu-id="635fd-261">Wnioskowanie o typie można zapisać możesz wpisać dużo standardowego.</span><span class="sxs-lookup"><span data-stu-id="635fd-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="635fd-262">I automatyczna Generalizacja w kompilatorze języka F # ułatwia pisanie bardziej ogólnym kodu z prawie nie dodatkowego nakładu pracy ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="635fd-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="635fd-263">Jednak te funkcje nie są powszechnie dobra.</span><span class="sxs-lookup"><span data-stu-id="635fd-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="635fd-264">Warto nadać nazwy argumentów jawnego typów w publicznych interfejsach API i nie należy polegać na wnioskowanie o typie dla tego.</span><span class="sxs-lookup"><span data-stu-id="635fd-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="635fd-265">Jest to spowodowane tym, że **można** powinna być w formancie kształtu interfejsu API, nie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="635fd-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="635fd-266">Kompilator może wykonać przeprowadzać zadania na wnioskowanie typów dla Ciebie, jest możliwe kształtu zmiany interfejsu API wewnętrzne, które opiera się na zmiany typów.</span><span class="sxs-lookup"><span data-stu-id="635fd-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="635fd-267">Może to być, co ma, ale prawie na pewno spowoduje na istotne zmiany interfejsu API niższego rzędu konsumentów będzie miał radzenia sobie z.</span><span class="sxs-lookup"><span data-stu-id="635fd-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="635fd-268">Zamiast tego należy jawnie kontrolować kształt publiczny interfejs API, następnie można sterować te zmiany podziału.</span><span class="sxs-lookup"><span data-stu-id="635fd-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="635fd-269">W kategoriach DDD to można można traktować jako warstwa przed uszkodzeniem.</span><span class="sxs-lookup"><span data-stu-id="635fd-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="635fd-270">Należy wziąć pod uwagę, zapewniając łatwy do rozpoznania nazwy argumentów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="635fd-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="635fd-271">Jeśli piszesz naprawdę ogólnego kod, który nie jest specyficzne dla konkretnej domeny zrozumiałą nazwę może pomóc w innych programistów opis domeny, które działają w.</span><span class="sxs-lookup"><span data-stu-id="635fd-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="635fd-272">Na przykład, parametru typu o nazwie `'Document` w kontekście interakcji z dokumentem bazy danych, ułatwia jaśniejszy, że typy dokumentu typu ogólnego może zostać zaakceptowane przez funkcji lub elementu członkowskiego, w przypadku korzystania z.</span><span class="sxs-lookup"><span data-stu-id="635fd-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="635fd-273">Należy rozważyć nazw parametrów typu ogólnego z PascalCase.</span><span class="sxs-lookup"><span data-stu-id="635fd-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="635fd-274">Jest to ogólne sposób, aby wykonać czynności w .NET, dlatego zalecane jest, że używasz PascalCase zamiast snake_case lub (camelcase).</span><span class="sxs-lookup"><span data-stu-id="635fd-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="635fd-275">Na koniec automatyczna Generalizacja nie zawsze jest zwiększa dla osób, które są nowe w F # lub duże codebase.</span><span class="sxs-lookup"><span data-stu-id="635fd-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="635fd-276">Brak kognitywnych obciążenie przy użyciu składników, które są ogólne.</span><span class="sxs-lookup"><span data-stu-id="635fd-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="635fd-277">Ponadto jeśli automatycznie uogólniony funkcje nie są używane z różnych typów wejściowych (umożliwiają tylko, jeśli są one przeznaczone do użycia jako takie), a następnie rozwiązanie nie przynosi żadnych rzeczywistych do nich ogólnego w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="635fd-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="635fd-278">Zawsze należy rozważyć, jeśli kod, który pisania faktycznie będą korzystać z ogólnym.</span><span class="sxs-lookup"><span data-stu-id="635fd-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="635fd-279">Wydajność</span><span class="sxs-lookup"><span data-stu-id="635fd-279">Performance</span></span>

<span data-ttu-id="635fd-280">F # wartości są niezmienne domyślnie, dzięki czemu można uniknąć niektórych klas usterek (szczególnie tych dotyczących współbieżności i równoległości).</span><span class="sxs-lookup"><span data-stu-id="635fd-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="635fd-281">Jednak w niektórych przypadkach, aby osiągnąć optymalną (lub nawet uzasadnione) skuteczność czas wykonania lub przydziału pamięci zakresu pracy mogą najlepiej można implementować przy użyciu mutacji w miejscu stanu.</span><span class="sxs-lookup"><span data-stu-id="635fd-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="635fd-282">Jest to możliwe w zasadzie opcjonalnych w języku F # z `mutable` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="635fd-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="635fd-283">Jednak użycie `mutable` w języku F # mogą uznać kłóci czystości funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="635fd-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="635fd-284">Jest to poprawnie, jeśli oczekiwań z czystości [referencyjnej przezroczystość](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="635fd-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="635fd-285">Przezroczystość referencyjnej — nie czystości — jest jej celem podczas zapisywania funkcje F #.</span><span class="sxs-lookup"><span data-stu-id="635fd-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="635fd-286">Umożliwia to pisanie funkcjonalności interfejsu na podstawie mutacji implementację kodu krytycznego wydajności.</span><span class="sxs-lookup"><span data-stu-id="635fd-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="635fd-287">Zawijanie modyfikowalną kodu w niezmienne interfejsów</span><span class="sxs-lookup"><span data-stu-id="635fd-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="635fd-288">Z referencyjnej przezroczystości jako cel, bardzo ważne jest napisanie kodu, który nie ujawnia modyfikowalną underbelly krytyczne wydajności funkcji.</span><span class="sxs-lookup"><span data-stu-id="635fd-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="635fd-289">Na przykład poniższy kod implementuje `Array.contains` funkcji biblioteki podstawowej F #:</span><span class="sxs-lookup"><span data-stu-id="635fd-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="635fd-290">Wiele razy podczas wywoływania tej funkcji nie zmienia tabeli podstawowej, ani nie wymaga do utrzymania każdy stan modyfikowalną podczas używania go.</span><span class="sxs-lookup"><span data-stu-id="635fd-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="635fd-291">Jest referentially niewidoczne, mimo że prawie każdego wiersza kodu w niej używa mutacji.</span><span class="sxs-lookup"><span data-stu-id="635fd-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="635fd-292">Należy wziąć pod uwagę hermetyzując modyfikowalną danych w klasach</span><span class="sxs-lookup"><span data-stu-id="635fd-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="635fd-293">Poprzedni przykład metodę jednej funkcji hermetyzacji operacje przy użyciu tych danych.</span><span class="sxs-lookup"><span data-stu-id="635fd-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="635fd-294">To nie zawsze jest wystarczająca dla bardziej złożonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="635fd-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="635fd-295">Należy wziąć pod uwagę następujące zestawy funkcji:</span><span class="sxs-lookup"><span data-stu-id="635fd-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="635fd-296">Ten kod jest wydajność, ale udostępnia ona struktury danych opartych na mutacji odpowiedzialny za konserwację czy obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="635fd-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="635fd-297">Może to być zawijany wewnątrz klasy bez członków podstawowych, które można zmienić:</span><span class="sxs-lookup"><span data-stu-id="635fd-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="635fd-298">`Closure1Table` hermetyzuje struktury danych opartych na mutacji, a tym samym nie wymuszania obiekty wywołujące do obsługi podstawowej struktury danych.</span><span class="sxs-lookup"><span data-stu-id="635fd-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="635fd-299">Klasy są zaawansowane metody hermetyzacji danych i procedur, które są oparte na mutacji bez narażania szczegóły dotyczące obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="635fd-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="635fd-300">Preferowane jest `let mutable` do komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="635fd-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="635fd-301">Komórki odwołań służą do reprezentowania odwołania do wartości, a nie z samą wartość.</span><span class="sxs-lookup"><span data-stu-id="635fd-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="635fd-302">Mimo że można nimi dla kodu wrażliwego na wydajność, one zazwyczaj nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="635fd-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="635fd-303">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="635fd-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="635fd-304">Użyj komórka odwołania teraz "pollutes" wszystkie kolejne kodu z konieczności cofnięcia odwołania i ponownie odwołują się dane.</span><span class="sxs-lookup"><span data-stu-id="635fd-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="635fd-305">Zamiast tego należy wziąć pod uwagę `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="635fd-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="635fd-306">Jako uzupełnienie pojedynczy punkt mutacji w trakcie wykonywania wyrażenia lambda, wszystkie inne kodu, który dotyka `acc` to zrobić w taki sposób, który nie różni się do użycia jako normalny `let`-powiązana wartość niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="635fd-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="635fd-307">Ułatwi zmiany w czasie.</span><span class="sxs-lookup"><span data-stu-id="635fd-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="635fd-308">Obiekt programowania</span><span class="sxs-lookup"><span data-stu-id="635fd-308">Object programming</span></span>

<span data-ttu-id="635fd-309">F # ma pełną obsługę obiektów i koncepcje zorientowane obiektowo (OO).</span><span class="sxs-lookup"><span data-stu-id="635fd-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="635fd-310">Mimo że wiele pojęć OO są wydajne i przydatne, nie wszystkie z nich są idealne do użycia.</span><span class="sxs-lookup"><span data-stu-id="635fd-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="635fd-311">Poniższe listy oferują wskazówki dotyczące kategorii funkcji OO na wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="635fd-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="635fd-312">**Rozważ użycie tych funkcji w wielu sytuacjach:**</span><span class="sxs-lookup"><span data-stu-id="635fd-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="635fd-313">Kropkowego (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="635fd-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="635fd-314">Elementy członkowskie wystąpień</span><span class="sxs-lookup"><span data-stu-id="635fd-314">Instance members</span></span>
* <span data-ttu-id="635fd-315">Niejawne konstruktory</span><span class="sxs-lookup"><span data-stu-id="635fd-315">Implicit constructors</span></span>
* <span data-ttu-id="635fd-316">Statyczne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="635fd-316">Static members</span></span>
* <span data-ttu-id="635fd-317">Notacja indeksatora (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="635fd-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="635fd-318">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="635fd-318">Named and Optional arguments</span></span>
* <span data-ttu-id="635fd-319">Interfejsy i implementacje interfejsu</span><span class="sxs-lookup"><span data-stu-id="635fd-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="635fd-320">**Nie najpierw uzyskać dostęp do tych funkcji, ale należy rozważnie zastosować je, jeśli są one wygodny do rozwiązania problemu:**</span><span class="sxs-lookup"><span data-stu-id="635fd-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="635fd-321">Przeciążenie metody</span><span class="sxs-lookup"><span data-stu-id="635fd-321">Method overloading</span></span>
* <span data-ttu-id="635fd-322">Hermetyzowany modyfikowalną danych</span><span class="sxs-lookup"><span data-stu-id="635fd-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="635fd-323">Operatory dla typów</span><span class="sxs-lookup"><span data-stu-id="635fd-323">Operators on types</span></span>
* <span data-ttu-id="635fd-324">Właściwości auto</span><span class="sxs-lookup"><span data-stu-id="635fd-324">Auto properties</span></span>
* <span data-ttu-id="635fd-325">Implementowanie `IDisposable` i `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="635fd-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="635fd-326">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="635fd-326">Type extensions</span></span>
* <span data-ttu-id="635fd-327">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="635fd-327">Events</span></span>
* <span data-ttu-id="635fd-328">Struktury</span><span class="sxs-lookup"><span data-stu-id="635fd-328">Structs</span></span>
* <span data-ttu-id="635fd-329">Delegaty</span><span class="sxs-lookup"><span data-stu-id="635fd-329">Delegates</span></span>
* <span data-ttu-id="635fd-330">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="635fd-330">Enums</span></span>

<span data-ttu-id="635fd-331">**Ogólnie należy unikać tych funkcji, chyba że należy użyć:**</span><span class="sxs-lookup"><span data-stu-id="635fd-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="635fd-332">Hierarchii dziedziczenia na podstawie typu i dziedziczenie implementacji</span><span class="sxs-lookup"><span data-stu-id="635fd-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="635fd-333">Wartości null i `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="635fd-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="635fd-334">Preferuj kompozycji przed dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="635fd-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="635fd-335">[Kompozycja za pośrednictwem dziedziczenia](https://en.wikipedia.org/wiki/Composition_over_inheritance) jest idiom długotrwałe, który dobrej kodzie języka F # można stosować się do.</span><span class="sxs-lookup"><span data-stu-id="635fd-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="635fd-336">Podstawowe zasadą jest, że należy nie uwidacznia klasy podstawowej i wymusić wywołującym dziedziczą z tej klasy podstawowej, aby funkcje.</span><span class="sxs-lookup"><span data-stu-id="635fd-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="635fd-337">Implementować interfejsów, jeśli klasa nie ma potrzeby za pomocą wyrażeń obiektu</span><span class="sxs-lookup"><span data-stu-id="635fd-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="635fd-338">[Obiekt wyrażenia](../language-reference/object-expressions.md) umożliwiają implementować interfejsów na bieżąco, powiązanie z zaimplementowanym interfejsem wartość bez konieczności zrobić wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="635fd-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="635fd-339">Opcja ta jest przydatna, zwłaszcza, jeśli użytkownik _tylko_ musi implementować interfejs i nie potrzebują pełnego klasy.</span><span class="sxs-lookup"><span data-stu-id="635fd-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="635fd-340">Na przykład, w tym miejscu jest kod, który jest uruchamiany w [Ionide](http://ionide.io/) zapewnienie Akcja poprawki kodu, jeśli dodano symbol, który nie ma `open` instrukcji dla:</span><span class="sxs-lookup"><span data-stu-id="635fd-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="635fd-341">Ponieważ nie jest konieczne dla klasy, gdy korzysta z API do kodu programu Visual Studio, wyrażenia obiektów są idealne narzędzie to.</span><span class="sxs-lookup"><span data-stu-id="635fd-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="635fd-342">Są one również przydatna do testowania, jeśli chcesz zastąpić klasą zastępczą interfejsu testujące w sposób ad hoc jednostek.</span><span class="sxs-lookup"><span data-stu-id="635fd-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="635fd-343">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="635fd-343">Type Abbreviations</span></span>

<span data-ttu-id="635fd-344">[Skróty typów](../language-reference/type-abbreviations.md) to wygodny sposób można przypisywać etykietę do innego typu, na przykład sygnatura funkcji lub bardziej złożonej typu.</span><span class="sxs-lookup"><span data-stu-id="635fd-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="635fd-345">Na przykład następujący alias przypisuje etykietę co jest potrzebne do definiowania obliczeń z [CNTK](https://www.microsoft.com/cognitive-toolkit/), bezpośrednich uczenia biblioteki:</span><span class="sxs-lookup"><span data-stu-id="635fd-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="635fd-346">`Computation` Nazwa to wygodny sposób do oznaczania każda funkcja, która odpowiada podpis jest aliasów.</span><span class="sxs-lookup"><span data-stu-id="635fd-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="635fd-347">Za pomocą skrótów typu takie jest wygodne i umożliwia bardziej zwięzły kodu.</span><span class="sxs-lookup"><span data-stu-id="635fd-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="635fd-348">Unikaj skrótów typu do reprezentowania domeny</span><span class="sxs-lookup"><span data-stu-id="635fd-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="635fd-349">Chociaż skróty typów jest wygodną metodą nadanie nazwy do sygnatury funkcji, mogą być mylące podczas używanie innych typów.</span><span class="sxs-lookup"><span data-stu-id="635fd-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="635fd-350">Należy wziąć pod uwagę ten skrót:</span><span class="sxs-lookup"><span data-stu-id="635fd-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="635fd-351">Może to być mylące na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="635fd-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="635fd-352">`BufferSize` nie jest klasą abstrakcyjną; jest po prostu inną nazwę dla liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="635fd-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="635fd-353">Jeśli `BufferSize` jest widoczna w publiczny interfejs API go łatwo zostać błędnie zinterpretowane oznacza więcej niż tylko `int`.</span><span class="sxs-lookup"><span data-stu-id="635fd-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="635fd-354">Ogólnie rzecz biorąc, typy domeny ma wiele atrybutów do nich i nie są typy pierwotne, takie jak `int`.</span><span class="sxs-lookup"><span data-stu-id="635fd-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="635fd-355">Ten skrót narusza tego założeń.</span><span class="sxs-lookup"><span data-stu-id="635fd-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="635fd-356">Wielkość liter w wyrazie `BufferSize` (PascalCase) oznacza, że ten typ zawiera więcej danych.</span><span class="sxs-lookup"><span data-stu-id="635fd-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="635fd-357">Ten alias nie oferuje zwiększenia przejrzystości w porównaniu z dostarczanie nazwany argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="635fd-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="635fd-358">Skrót nie zostanie powiadomiony IL skompilowanych; jest tylko całkowitą i ten alias jest konstrukcję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="635fd-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="635fd-359">Podsumowując, niedogodności z skróty typów te są **nie** abstrakcje przez typy są ich używanie.</span><span class="sxs-lookup"><span data-stu-id="635fd-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="635fd-360">W poprzednim przykładzie `BufferSize` jest po prostu `int` w obszarze obejmuje, z żadnych dodatkowych danych ani żadnych korzyści z systemu typu poza co `int` ma już.</span><span class="sxs-lookup"><span data-stu-id="635fd-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
