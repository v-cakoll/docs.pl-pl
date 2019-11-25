---
title: C# — konwencje kodowania
description: Zapoznaj się z ogólnymi wskazówkami i idiomy podczas pisania F# kodu.
ms.date: 11/04/2019
ms.openlocfilehash: 60eff6392d71caa54eeb438f2f6ba9db910f1bc1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978225"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="5e5a2-103">C# — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="5e5a2-103">F# coding conventions</span></span>

<span data-ttu-id="5e5a2-104">Następujące konwencje są formułowane z doświadczenia w pracy z F# dużymi bazami kodu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="5e5a2-105">[Pięć zasad dobrego F# kodu](index.md#five-principles-of-good-f-code) jest podstawą każdego zalecenia.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="5e5a2-106">Są one powiązane ze [ F# wskazówkami dotyczącymi projektowania składników](component-design-guidelines.md), ale mają zastosowanie F# do dowolnego kodu, a nie tylko składników, takich jak biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="5e5a2-107">Organizowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5e5a2-107">Organizing code</span></span>

<span data-ttu-id="5e5a2-108">F#oferuje dwa podstawowe sposoby organizowania kodu: moduły i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="5e5a2-109">Są one podobne, ale mają następujące różnice:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="5e5a2-110">Przestrzenie nazw są kompilowane jako przestrzenie nazw platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="5e5a2-111">Moduły są kompilowane jako klasy statyczne.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="5e5a2-112">Obszary nazw są zawsze najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-112">Namespaces are always top level.</span></span> <span data-ttu-id="5e5a2-113">Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="5e5a2-114">Przestrzenie nazw mogą obejmować wiele plików.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="5e5a2-115">Moduły nie mogą.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-115">Modules cannot.</span></span>
* <span data-ttu-id="5e5a2-116">Moduły mogą mieć `[<RequireQualifiedAccess>]` i `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="5e5a2-117">Poniższe wskazówki ułatwią ich użycie do organizowania kodu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="5e5a2-118">Preferuj obszary nazw na najwyższym poziomie</span><span class="sxs-lookup"><span data-stu-id="5e5a2-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="5e5a2-119">Dla każdego publicznego kodu, przestrzenie nazw są preferencyjne dla modułów na najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="5e5a2-120">Ponieważ są one kompilowane jako przestrzenie nazw .NET, są one konsumowane z C# powodu braku problemu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="5e5a2-121">Korzystanie z modułu najwyższego poziomu może nie wyglądać inaczej, gdy jest F#wywoływana tylko z C# , ale dla odbiorców, osoby wywołujące mogą być zaskoczenie, aby zakwalifikować`MyClass`z modułem`MyCode`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="5e5a2-122">Starannie stosuj `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="5e5a2-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="5e5a2-123">Konstrukcja `[<AutoOpen>]` może obsłużyć zanieczyszczenie zakresu tego, co jest dostępne dla obiektów wywołujących, i odpowiedzi na to, z których pochodzi element, jest "Magic".</span><span class="sxs-lookup"><span data-stu-id="5e5a2-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="5e5a2-124">Zwykle nie jest to dobry efekt.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-124">This is generally not a good thing.</span></span> <span data-ttu-id="5e5a2-125">Wyjątkiem od F# tej reguły jest sama biblioteka podstawowa (chociaż jest to również bit kontrowersyjny).</span><span class="sxs-lookup"><span data-stu-id="5e5a2-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="5e5a2-126">Jednak jest to wygodne, jeśli masz funkcje pomocnika dla publicznego interfejsu API, który ma być zorganizowany niezależnie od tego publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="5e5a2-127">Dzięki temu można oddzielić szczegóły implementacji z publicznego interfejsu API funkcji bez konieczności pełnego kwalifikowania pomocnika przy każdym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="5e5a2-128">Ponadto udostępnianie metod rozszerzających i konstruktorów wyrażeń na poziomie przestrzeni nazw może być starannie wyrażone `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="5e5a2-129">Użyj `[<RequireQualifiedAccess>]` za każdym razem, gdy nazwy mogą występować w konflikcie lub można je łatwo odczytać</span><span class="sxs-lookup"><span data-stu-id="5e5a2-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="5e5a2-130">Dodanie `[<RequireQualifiedAccess>]` atrybutu do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu wymagają jawnego kwalifikowanego dostępu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="5e5a2-131">Na przykład moduł `Microsoft.FSharp.Collections.List` ma ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="5e5a2-132">Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="5e5a2-133">Wymaganie dostępu kwalifikowanego może znacznie zwiększyć długoterminową konserwację i możliwość rozwijania biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="5e5a2-134">Sortuj instrukcje `open` topologically</span><span class="sxs-lookup"><span data-stu-id="5e5a2-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="5e5a2-135">W F#programie porządek deklaracji, w tym instrukcje `open`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="5e5a2-136">Jest to w odróżnieniu C#od tego, czy efekt`using`i`using static`jest niezależny od kolejności tych instrukcji w pliku.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="5e5a2-137">W F#programie elementy otwierane w zakresie mogą zasłaniać inne już obecne.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="5e5a2-138">Oznacza to, że zmiana kolejności instrukcji `open` może zmienić znaczenie kodu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="5e5a2-139">W związku z tym żadne dowolne sortowanie wszystkich instrukcji `open` (na przykład alfanumerycznie) nie jest zalecane, Lest generować różne zachowanie, które może być oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="5e5a2-140">Zamiast tego zalecamy, aby posortować je [topologically](https://en.wikipedia.org/wiki/Topological_sorting); oznacza to, że należy zamówić instrukcje `open` w kolejności, w jakiej są zdefiniowane _warstwy_ systemu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="5e5a2-141">Można również rozważyć sortowanie alfanumeryczne w różnych warstwach topologiczny.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="5e5a2-142">Oto przykład sortowania topologiczny dla publicznego pliku interfejsu API usługi F# kompilatora:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="5e5a2-143">Należy zauważyć, że podział wiersza oddziela warstwy topologiczny, przy czym każda warstwa jest sortowana alfanumerycznie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="5e5a2-144">To przejrzyste organizuje kod bez przypadkowego przesłaniania wartości.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="5e5a2-145">Użyj klas, aby zawierać wartości, które mają efekty uboczne</span><span class="sxs-lookup"><span data-stu-id="5e5a2-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="5e5a2-146">Istnieje wiele przypadków, w których inicjowanie wartości może mieć efekty uboczne, takie jak utworzenie wystąpienia kontekstu dla bazy danych lub innego zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="5e5a2-147">Zachęcamy do inicjowania takich elementów w module i używania jej w kolejnych funkcjach:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="5e5a2-148">Jest to często niewłaściwy pomysł z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="5e5a2-149">Najpierw konfiguracja aplikacji jest wypychana do bazy kodu z `dep1` i `dep2`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="5e5a2-150">Jest to trudne do utrzymania w dużych bazach kodu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="5e5a2-151">Drugie, statycznie zainicjowane dane nie powinny zawierać wartości, które nie są bezpieczne dla wątków, jeśli składnik będzie używał wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="5e5a2-152">Jest to wyraźnie naruszone przez `dep3`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="5e5a2-153">Na koniec Inicjalizacja modułu kompiluje się do konstruktora statycznego dla całej jednostki kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="5e5a2-154">Jeśli w tym module wystąpi błąd w programie Let-Bound Value, manifestuje jako `TypeInitializationException`, który następnie jest buforowany przez cały okres istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="5e5a2-155">Może to być trudne do zdiagnozowania.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="5e5a2-156">Zazwyczaj występuje wyjątek wewnętrzny, który można spróbować, ale jeśli nie istnieje, nie ma informacji o tym, co to jest główna przyczyna.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="5e5a2-157">Zamiast tego wystarczy użyć prostej klasy do przechowywania zależności:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="5e5a2-158">Zapewnia to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-158">This enables the following:</span></span>

1. <span data-ttu-id="5e5a2-159">Wypychanie dowolnego stanu zależnego poza interfejsem API.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="5e5a2-160">Konfigurację można teraz wykonać poza interfejsem API.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="5e5a2-161">Błędy podczas inicjowania wartości zależnych nie mogą być manifestem jako `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="5e5a2-162">Interfejs API jest teraz łatwiejszy do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="5e5a2-163">Zarządzanie błędami</span><span class="sxs-lookup"><span data-stu-id="5e5a2-163">Error management</span></span>

<span data-ttu-id="5e5a2-164">Zarządzanie błędami w dużych systemach jest złożone i złożonych Endeavor, a nie ma żadnych znaków w języku Silver w celu zapewnienia, że systemy są odporne na uszkodzenia i działają prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="5e5a2-165">Poniższe wskazówki powinny oferować wskazówki dotyczące nawigowania w tym trudnej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="5e5a2-166">Reprezentuje przypadki błędów i niedozwolony stan w typach wewnętrznych dla domeny</span><span class="sxs-lookup"><span data-stu-id="5e5a2-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="5e5a2-167">W przypadku F# [Unii rozłącznych](../language-reference/discriminated-unions.md)można reprezentować wadliwy stan programu w systemie typów.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="5e5a2-168">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="5e5a2-169">W takim przypadku istnieją trzy znane sposoby, że wycofanie pieniędzy z konta bankowego może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="5e5a2-170">Każdy przypadek błędu jest reprezentowany w typie i w ten sposób może być traktowany bezpiecznie w całym programie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="5e5a2-171">Ogólnie rzecz biorąc, jeśli można modelować różne sposoby, w których coś może **się nie powieść** w domenie, kod obsługi błędu nie jest już traktowany jako element, który należy zastanowić oprócz zwykłego przepływu programu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="5e5a2-172">Jest to po prostu część normalnego przepływu programu i nie jest uważana za **wyjątkową**.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="5e5a2-173">Istnieją dwie podstawowe korzyści:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="5e5a2-174">Jest to łatwiejsze w obsłudze, ponieważ zmienia się w miarę upływu czasu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="5e5a2-175">Przypadki błędów są łatwiejsze do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="5e5a2-176">Użyj wyjątków, gdy błędy nie mogą być reprezentowane za pomocą typów</span><span class="sxs-lookup"><span data-stu-id="5e5a2-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="5e5a2-177">Nie wszystkie błędy mogą być reprezentowane w domenie problemu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="5e5a2-178">Tego rodzaju błędy mają *wyjątkowe* cechy, a tym samym możliwość podniesienia i przechwycenia wyjątków w F#.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="5e5a2-179">Najpierw zaleca się zapoznanie się ze [wskazówkami dotyczącymi projektowania wyjątków](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="5e5a2-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="5e5a2-180">Mają one również zastosowanie do F#.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-180">These are also applicable to F#.</span></span>

<span data-ttu-id="5e5a2-181">Główne konstrukcje dostępne w F# celu podniesienia wyjątków należy uwzględnić w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="5e5a2-182">Funkcja</span><span class="sxs-lookup"><span data-stu-id="5e5a2-182">Function</span></span> | <span data-ttu-id="5e5a2-183">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e5a2-183">Syntax</span></span> | <span data-ttu-id="5e5a2-184">Cel</span><span class="sxs-lookup"><span data-stu-id="5e5a2-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="5e5a2-185">Podnosi `System.ArgumentNullException` z określoną nazwą argumentu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="5e5a2-186">Podnosi `System.ArgumentException` z określoną nazwą argumentu i komunikatem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="5e5a2-187">Podnosi `System.InvalidOperationException` z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="5e5a2-188">Mechanizm ogólnego przeznaczenia do zgłaszania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="5e5a2-189">Podnosi `System.Exception` z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="5e5a2-190">Wywołuje `System.Exception` z komunikatem określonym przez ciąg formatu i jego dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="5e5a2-191">Użyj `nullArg`, `invalidArg` i `invalidOp` jako mechanizm do rzutowania `ArgumentNullException`, `ArgumentException` i `InvalidOperationException` w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="5e5a2-192">Należy generalnie unikać `failwith` i `failwithf`, ponieważ powodują one wystąpienie podstawowego `Exception` typu, a nie konkretnego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="5e5a2-193">Zgodnie z [zaleceniami dotyczącymi projektowania wyjątków](../../standard/design-guidelines/exceptions.md), możesz w razie potrzeby zgłosić bardziej szczegółowe wyjątki.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="5e5a2-194">Używanie składni obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="5e5a2-194">Using exception-handling syntax</span></span>

<span data-ttu-id="5e5a2-195">F#obsługuje wzorce wyjątków za pośrednictwem składni`try...with`:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="5e5a2-196">Uzgadnianie funkcjonalności do wykonania w celu przeprowadzenia wyjątku z dopasowaniem do wzorca może być nieprzerwaną lewę, jeśli chcesz zachować czysty kod.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="5e5a2-197">Jednym z nich jest użycie [aktywnych wzorców](../language-reference/active-patterns.md) jako środka do pogrupowania funkcjonalności otaczającej przypadek błędu z samym wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="5e5a2-198">Na przykład może być zużywany interfejs API, który zgłasza wyjątek, w metadanych wyjątku ujmuje cenne informacje.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="5e5a2-199">Odpakowanie przydatnej wartości w treści przechwyconego wyjątku wewnątrz aktywnego wzorca i zwrócenie tej wartości może być przydatne w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="5e5a2-200">Nie używaj obsługi błędów monadic w celu zastąpienia wyjątków</span><span class="sxs-lookup"><span data-stu-id="5e5a2-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="5e5a2-201">Wyjątki są widoczne jako dość Taboo w programowaniu funkcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="5e5a2-202">W rzeczywistości wyjątki naruszają czystość, dlatego można bezpiecznie rozważyć ich niedziałanie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="5e5a2-203">Jednak ignoruje to stan, w którym należy uruchomić kod, i mogą wystąpić błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="5e5a2-204">Ogólnie rzecz biorąc Napisz kod w założeniu, że większość rzeczy nie jest czysta ani łączna, aby zminimalizować nieprzyjemne niespodziewane.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="5e5a2-205">Ważne jest, aby wziąć pod uwagę następujące podstawowe zalety/aspekty wyjątków w odniesieniu do ich znaczenia i adekwatności w środowisku uruchomieniowym .NET i ekosystemie wielu języków jako całości:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="5e5a2-206">Zawierają one szczegółowe informacje diagnostyczne, które są bardzo przydatne podczas debugowania problemu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="5e5a2-207">Są one dobrze zrozumiałe dla środowiska uruchomieniowego i innych języków .NET.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="5e5a2-208">Umożliwiają one zredukowanie znaczącego standardu w porównaniu z kodem, który jest używany do *uniknięcia* wyjątków przez implementację pewnego podzestawu semantyki na zasadzie ad hoc.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="5e5a2-209">Ten trzeci punkt jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-209">This third point is critical.</span></span> <span data-ttu-id="5e5a2-210">W przypadku nieskomplikowanych operacji złożonych użycie wyjątków może skutkować użyciem struktur takich jak:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="5e5a2-211">Dzięki czemu można łatwo prowadzić do delikatnego rozróżnienia kodu, takiego jak dopasowanie wzorca dla błędów typu "String-Type":</span><span class="sxs-lookup"><span data-stu-id="5e5a2-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="5e5a2-212">Ponadto może być skłonny do połknięcia dowolnego wyjątku w przypadku funkcji "Simple" zwracającej typ "Nice":</span><span class="sxs-lookup"><span data-stu-id="5e5a2-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="5e5a2-213">Niestety, `tryReadAllText` może zgłosić wiele wyjątków na podstawie wyposażono rzeczy, które mogą wystąpić w systemie plików, a ten kod odrzuca wszystkie informacje o tym, co może być w stanie błędnym w Twoim środowisku.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="5e5a2-214">Jeśli zastąpisz ten kod z typem wyniku, wrócisz do analizy komunikatu o błędzie "stringd-Type":</span><span class="sxs-lookup"><span data-stu-id="5e5a2-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="5e5a2-215">I umieszczenie obiektu Exception w konstruktorze `Error` tylko wymusza prawidłowe rozpatrywanie przy użyciu typu wyjątku w miejscu wywołania, a nie w funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="5e5a2-216">W ten sposób można utworzyć zaznaczone wyjątki, które są wielowątkowy bardzo unfun, jako wywołujący interfejs API.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="5e5a2-217">Dobrym alternatywą dla powyższych przykładów jest przechwycenie *określonych* wyjątków i zwrócenie wartości znaczących w kontekście tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="5e5a2-218">Jeśli zmodyfikujesz funkcję `tryReadAllText` w następujący sposób, `None` ma więcej znaczenia:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="5e5a2-219">Ta funkcja będzie teraz prawidłowo obsługiwana w przypadku, gdy nie można jej odnaleźć i przypisać do zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="5e5a2-220">Ta wartość zwracana może być mapowana na ten przypadek błędu, podczas gdy nie są usuwane żadne informacje kontekstowe lub wymuszanie wywoływania w przypadku, gdy nie ma znaczenia w tym momencie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="5e5a2-221">Typy takie jak `Result<'Success, 'Error>` są odpowiednie dla operacji podstawowych, gdy nie są zagnieżdżone, F# a typy opcjonalne są idealny do reprezentowania, gdy coś może zwrócić *coś* lub *nic*.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="5e5a2-222">Nie są one zastępowane wyjątkami, ale nie powinny być używane w próbie zastąpienia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="5e5a2-223">Zamiast tego należy je stosować w sposób rozsądny do rozwiązywania określonych aspektów zasad dotyczących zarządzania wyjątkami i błędami.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="5e5a2-224">Programowanie częściowej aplikacji i bez punktu</span><span class="sxs-lookup"><span data-stu-id="5e5a2-224">Partial application and point-free programming</span></span>

<span data-ttu-id="5e5a2-225">F#obsługuje częściową aplikację, a więc różne sposoby programowania w stylu bez punktu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="5e5a2-226">Może to być przydatne w przypadku ponownego użycia kodu w ramach modułu lub implementacji elementu, ale zazwyczaj nie jest to ujawniane publicznie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="5e5a2-227">Ogólnie rzecz biorąc, programowanie bezpunktowe nie jest sprawą i sama, i może dodać znaczną barierę poznawczyą dla osób, które nie są zanurzone w stylu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="5e5a2-228">Nie używaj częściowej aplikacji i currying w publicznych interfejsach API</span><span class="sxs-lookup"><span data-stu-id="5e5a2-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="5e5a2-229">Przy małym wyjątku użycie częściowej aplikacji w publicznych interfejsach API może być mylące dla klientów.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="5e5a2-230">Zwykle wartości powiązane z `let`w F# kodzie to **wartości**, a nie **wartości funkcji**.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="5e5a2-231">Mieszanie wartości i wartości funkcji może skutkować zapisaniem niewielkiej liczby wierszy kodu w programie Exchange w celu uzyskania zbyt wielu obciążeń poznawczych, szczególnie jeśli są połączone z operatorami, takimi jak `>>`, do redagowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="5e5a2-232">Weź pod uwagę wpływ na narzędzia do programowania bez zwolnień</span><span class="sxs-lookup"><span data-stu-id="5e5a2-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="5e5a2-233">Funkcje rozwinięte nie etykietą argumentów.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="5e5a2-234">Ma to wpływ na narzędzia.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-234">This has tooling implications.</span></span> <span data-ttu-id="5e5a2-235">Należy wziąć pod uwagę następujące dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="5e5a2-236">Obie są prawidłowymi funkcjami, ale `funcWithApplication` jest funkcją rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="5e5a2-237">Po umieszczeniu wskaźnika myszy na ich typach w edytorze zostanie wyświetlony następujący komunikat:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="5e5a2-238">W witrynie wywołania etykietki narzędzi w narzędziach, takich jak Visual Studio, nie zawierają istotnych informacji dotyczących tego, co reprezentuje `string` i `int` typy danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="5e5a2-239">Jeśli napotkasz kod wolny w punktach, taki jak `funcWithApplication`, który jest ogólnie przydatny, zaleca się przeprowadzenie pełnego rozszerzenia η, dzięki czemu narzędzia mogą pobrać znaczące nazwy dla argumentów.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="5e5a2-240">Ponadto kod wolny od punktu debugowania może być wyzwaniem, jeśli nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="5e5a2-241">Narzędzia debugowania są zależne od wartości związanych z nazwami (na przykład powiązań `let`), dzięki czemu można sprawdzać wartości pośrednie w połowie wykonania.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="5e5a2-242">Gdy kod nie ma żadnych wartości do sprawdzenia, nie ma niczego do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="5e5a2-243">W przyszłości narzędzia debugowania mogą się rozwijać w celu wypróbowania tych wartości na podstawie wcześniej wykonanych ścieżek, ale nie jest dobrym pomysłem do zabezpieczania trafień w *potencjalnych* funkcjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="5e5a2-244">Rozważ użycie częściowej aplikacji jako techniki do zredukowania wewnętrznego standardowego</span><span class="sxs-lookup"><span data-stu-id="5e5a2-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="5e5a2-245">W przeciwieństwie do wcześniejszego punktu, częściowa aplikacja jest wspaniałego narzędzia do zredukowania typowego wewnątrz aplikacji lub bardziej szczegółowych wewnętrznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="5e5a2-246">Może być przydatne w przypadku testowania jednostkowego implementacji bardziej skomplikowanych interfejsów API, gdzie typowe jest często wiele rzeczy.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="5e5a2-247">Na przykład poniższy kod pokazuje, w jaki sposób można osiągnąć, jakie najważniejsze struktury zapewniają, że nie podejmuje zewnętrznej zależności od takiej struktury i trzeba poznać związany z nim interfejs API Bespoke.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="5e5a2-248">Rozważmy na przykład następujące topografie rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="5e5a2-249">`ImplementationLogic.fsproj` może uwidaczniać kod, taki jak:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="5e5a2-250">Testowanie jednostkowe `Transactions.doTransaction` w `ImplementationLogic.Tests.fsproj` jest proste:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="5e5a2-251">Częściowo stosowanie `doTransaction` z obiektem kontekstu służącego do tworzenia elementów umożliwia wywoływanie funkcji we wszystkich testach jednostkowych bez konieczności konstruowania zastosowanego kontekstu za każdym razem:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="5e5a2-252">Ta technika nie powinna być uniwersalnie stosowana do całej bazy kodu, ale jest dobrym sposobem zredukowania wzorców dla skomplikowanych danych wewnętrznych i testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="5e5a2-253">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="5e5a2-253">Access control</span></span>

<span data-ttu-id="5e5a2-254">F#ma wiele opcji [kontroli dostępu](../language-reference/access-control.md)dziedziczonych z elementów dostępnych w środowisku uruchomieniowym .NET.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="5e5a2-255">Nie można ich używać do typów — są one również dostępne dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="5e5a2-256">Preferuj typy i elementy członkowskie inne niż`public`, dopóki nie będą potrzebne do publicznego użycia.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="5e5a2-257">Pozwala to również zminimalizować liczbę użytkowników, których to dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="5e5a2-258">Staraj się zachować wszystkie `private`funkcje pomocnika.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="5e5a2-259">Należy rozważyć użycie `[<AutoOpen>]` w module prywatnym funkcji pomocnika, jeśli stają się one liczne.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="5e5a2-260">Wnioskowanie o typie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5e5a2-260">Type inference and generics</span></span>

<span data-ttu-id="5e5a2-261">Wnioskowanie o typie może zaoszczędzić, wprowadzając wiele standardowych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="5e5a2-262">I automatyczne uogólnianie w F# kompilatorze może pomóc napisać bardziej ogólny kod z niemal niezbędnym nakładem pracy.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="5e5a2-263">Te funkcje nie są jednak uniwersalne.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="5e5a2-264">Rozważ użycie etykietowania nazw argumentów z jawnymi typami w publicznych interfejsach API i nie należy polegać na wnioskach o typie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="5e5a2-265">Przyczyną tego **jest to, że należy** mieć kontrolę nad KSZTAŁTEM interfejsu API, a nie kompilatorem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="5e5a2-266">Mimo że kompilator może wykonać zadanie w odniesieniu do typów, istnieje możliwość, że kształt interfejsu API ulegnie zmianie, jeśli wewnętrzne jest zależne od zmienionego typu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="5e5a2-267">Może to być to, czego potrzebujesz, ale niemal w efekcie zostanie osiągnięty istotna zmiana interfejsu API, która będzie musiała zająć się tym klientom.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="5e5a2-268">Zamiast tego, jeśli jawnie kontrolujesz kształt publicznego interfejsu API, możesz kontrolować te zmiany.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="5e5a2-269">W DDD terminy można to traktować jako warstwę chroniącą przed uszkodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="5e5a2-270">Rozważ nadanie znaczącej nazwy argumentom ogólnym.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="5e5a2-271">O ile nie piszesz kod generyczny, który nie jest specyficzny dla konkretnej domeny, zrozumiała nazwa może pomóc innym programistom zrozumieć domenę, w której pracują.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="5e5a2-272">Na przykład parametr typu o nazwie `'Document` w kontekście współdziałania z bazą danych dokumentów sprawia, że typy dokumentów ogólnych mogą być akceptowane przez funkcję lub element członkowski, z którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="5e5a2-273">Rozważ nazewnictwo parametrów typu ogólnego za pomocą PascalCase.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="5e5a2-274">Jest to ogólny sposób wykonywania czynności w programie .NET, dlatego zaleca się użycie PascalCase zamiast snake_case lub camelCase.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="5e5a2-275">Na koniec automatyczne uogólnianie nie zawsze jest Boon dla osób, które są nowością F# lub dużą bazą kodu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="5e5a2-276">W przypadku używania składników, które są ogólne, są naliczane obciążenia poznawcze.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="5e5a2-277">Ponadto, jeśli automatycznie uogólnione funkcje nie są używane z różnymi typami danych wejściowych (pomogą, jeśli są one przeznaczone do użycia jako takie), nie ma rzeczywistej korzyści dla nich w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="5e5a2-278">Zawsze należy wziąć pod uwagę, czy kod, który piszesz, będzie faktycznie korzystał z ogólnego.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="5e5a2-279">Wydajność</span><span class="sxs-lookup"><span data-stu-id="5e5a2-279">Performance</span></span>

<span data-ttu-id="5e5a2-280">F#wartości są domyślnie niezmienne, co umożliwia uniknięcie niektórych klas błędów (szczególnie tych, które obejmują współbieżność i równoległość).</span><span class="sxs-lookup"><span data-stu-id="5e5a2-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="5e5a2-281">Jednak w niektórych przypadkach, aby osiągnąć optymalną (lub nawet rozsądną) wydajność czasu wykonywania lub alokacji pamięci, zakres pracy może być najlepiej zaimplementowany przy użyciu mutacji w miejscu stanu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="5e5a2-282">Jest to możliwe w zasadzie zgody przy F# użyciu słowa kluczowego`mutable`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="5e5a2-283">Jednakże korzystanie z `mutable` w programie F# może być szanse z czystą funkcjonalnością.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="5e5a2-284">Jest to możliwe, jeśli dostosowuje się oczekiwania od czystości do [przejrzystości referencyjnej](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="5e5a2-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="5e5a2-285">Przezroczystość referencyjna — brak czystości — jest celem końcowym F# podczas pisania funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="5e5a2-286">Dzięki temu można napisać interfejs funkcjonalny dla implementacji opartej na mutacji dla krytycznego kodu wydajności.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="5e5a2-287">Zawijaj modyfikowalny kod w niezmiennych interfejsach</span><span class="sxs-lookup"><span data-stu-id="5e5a2-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="5e5a2-288">Ze względu na przejrzystość referencyjną należy napisać kod, który nie uwidacznia modyfikowalnych niedzwonności funkcji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="5e5a2-289">Na przykład poniższy kod implementuje funkcję `Array.contains` w bibliotece F# podstawowej:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="5e5a2-290">Wywołanie tej funkcji wiele razy nie zmienia tablicy bazowej ani nie wymaga utrzymania żadnego modyfikowalnego stanu w jego użyciu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="5e5a2-291">Jest to element przezroczysty, nawet jeśli niemal każdy wiersz kodu w nim używa mutacji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="5e5a2-292">Rozważ hermetyzację modyfikowalnych danych w klasach</span><span class="sxs-lookup"><span data-stu-id="5e5a2-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="5e5a2-293">W poprzednim przykładzie użyto pojedynczej funkcji do hermetyzacji operacji przy użyciu modyfikowalnych danych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="5e5a2-294">Nie zawsze jest to wystarczające dla bardziej złożonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="5e5a2-295">Należy wziąć pod uwagę następujące zestawy funkcji:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="5e5a2-296">Ten kod jest wykonywany, ale ujawnia strukturę danych opartą na mutacji, która jest odpowiedzialna za utrzymanie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="5e5a2-297">Może być opakowany wewnątrz klasy bez podstawowych elementów członkowskich, które mogą ulec zmianie:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="5e5a2-298">`Closure1Table` hermetyzuje źródłową strukturę danych opartych na mutacji, dlatego nie wymuszają wywoływania, aby zachować podstawową strukturę danych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="5e5a2-299">Klasy to zaawansowany sposób hermetyzowania danych i procedur, które są oparte na mutacji bez uwidaczniania szczegółów dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="5e5a2-300">Preferuj `let mutable` do komórek odwołań</span><span class="sxs-lookup"><span data-stu-id="5e5a2-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="5e5a2-301">Komórki odwołań są sposobem reprezentowania odwołania do wartości, a nie samej wartości.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="5e5a2-302">Chociaż mogą one być używane w kodzie krytycznym dla wydajności, zazwyczaj nie są zalecane.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="5e5a2-303">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="5e5a2-304">Użycie komórki referencyjnej teraz spowoduje "zanieczyszczanie" jako cały kolejny kod z koniecznością wypróbowania i ponownego odwołania się do danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="5e5a2-305">Zamiast tego należy rozważyć `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="5e5a2-306">Poza pojedynczym punktem mutacji w środku wyrażenia lambda, cały inny kod, który dotyka `acc`, może to zrobić w sposób, który nie różni się od użycia normalnej `let`j wartości.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="5e5a2-307">Ułatwi to zmianę z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="5e5a2-308">Programowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="5e5a2-308">Object programming</span></span>

<span data-ttu-id="5e5a2-309">F#ma pełną obsługę obiektów i koncepcje zorientowane obiektowo (OO).</span><span class="sxs-lookup"><span data-stu-id="5e5a2-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="5e5a2-310">Chociaż wiele koncepcji OO są zaawansowane i przydatne, nie wszystkie z nich są idealne do użycia.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="5e5a2-311">Poniższe listy zawierają wskazówki dotyczące kategorii funkcji OO na wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="5e5a2-312">**Rozważ użycie tych funkcji w wielu sytuacjach:**</span><span class="sxs-lookup"><span data-stu-id="5e5a2-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="5e5a2-313">Notacja kropki (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="5e5a2-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="5e5a2-314">Elementy członkowskie wystąpienia</span><span class="sxs-lookup"><span data-stu-id="5e5a2-314">Instance members</span></span>
* <span data-ttu-id="5e5a2-315">Konstruktory niejawne</span><span class="sxs-lookup"><span data-stu-id="5e5a2-315">Implicit constructors</span></span>
* <span data-ttu-id="5e5a2-316">Statyczne składowe</span><span class="sxs-lookup"><span data-stu-id="5e5a2-316">Static members</span></span>
* <span data-ttu-id="5e5a2-317">Indexer — notacja (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="5e5a2-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="5e5a2-318">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="5e5a2-318">Named and Optional arguments</span></span>
* <span data-ttu-id="5e5a2-319">Interfejsy i implementacje interfejsów</span><span class="sxs-lookup"><span data-stu-id="5e5a2-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="5e5a2-320">**Nie dołączaj do tych funkcji w pierwszej kolejności, ale należy je zastosować w rozsądny sposób, jeśli są wygodne do rozwiązania problemu:**</span><span class="sxs-lookup"><span data-stu-id="5e5a2-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="5e5a2-321">Przeciążanie metody</span><span class="sxs-lookup"><span data-stu-id="5e5a2-321">Method overloading</span></span>
* <span data-ttu-id="5e5a2-322">Hermetyzowane dane modyfikowalne</span><span class="sxs-lookup"><span data-stu-id="5e5a2-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="5e5a2-323">Operatory dla typów</span><span class="sxs-lookup"><span data-stu-id="5e5a2-323">Operators on types</span></span>
* <span data-ttu-id="5e5a2-324">Właściwości autowypełniające</span><span class="sxs-lookup"><span data-stu-id="5e5a2-324">Auto properties</span></span>
* <span data-ttu-id="5e5a2-325">Implementowanie `IDisposable` i `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="5e5a2-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="5e5a2-326">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="5e5a2-326">Type extensions</span></span>
* <span data-ttu-id="5e5a2-327">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5e5a2-327">Events</span></span>
* <span data-ttu-id="5e5a2-328">Struktury</span><span class="sxs-lookup"><span data-stu-id="5e5a2-328">Structs</span></span>
* <span data-ttu-id="5e5a2-329">Delegaty</span><span class="sxs-lookup"><span data-stu-id="5e5a2-329">Delegates</span></span>
* <span data-ttu-id="5e5a2-330">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5e5a2-330">Enums</span></span>

<span data-ttu-id="5e5a2-331">**Ogólnie rzecz biorąc, należy unikać tych funkcji, chyba że trzeba ich używać:**</span><span class="sxs-lookup"><span data-stu-id="5e5a2-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="5e5a2-332">Hierarchie typów oparte na dziedziczeniu i dziedziczenie implementacji</span><span class="sxs-lookup"><span data-stu-id="5e5a2-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="5e5a2-333">Wartości null i `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="5e5a2-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="5e5a2-334">Preferuj składanie przez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="5e5a2-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="5e5a2-335">[Składanie przez dziedziczenie](https://en.wikipedia.org/wiki/Composition_over_inheritance) to długotrwała idiom, która F# może być zgodna z dobrym kodem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="5e5a2-336">Podstawowa zasada polega na tym, że nie należy ujawniać klasy bazowej i wymuszać wywoływania dziedziczenia z tej klasy podstawowej w celu uzyskania funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="5e5a2-337">Użyj wyrażeń obiektów do zaimplementowania interfejsów, jeśli nie potrzebujesz klasy</span><span class="sxs-lookup"><span data-stu-id="5e5a2-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="5e5a2-338">[Wyrażenia obiektów](../language-reference/object-expressions.md) umożliwiają zaimplementowanie interfejsów na bieżąco, powiązanie zaimplementowanego interfejsu z wartością bez konieczności wykonywania tej czynności wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="5e5a2-339">Jest to wygodne, zwłaszcza jeśli trzeba zaimplementować interfejs i nie _ma potrzeby dla_ pełnej klasy.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="5e5a2-340">Na przykład jest to kod, który jest uruchamiany w [Ionide](http://ionide.io/) , aby zapewnić akcję naprawy kodu, jeśli dodano symbol, dla którego nie masz instrukcji `open`:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="5e5a2-341">Ponieważ nie ma potrzeby stosowania klasy podczas korzystania z interfejsu API Visual Studio Code, wyrażenia obiektów są idealnym narzędziem dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="5e5a2-342">Są one również przydatne w przypadku testów jednostkowych, gdy chcesz utworzyć skrót do interfejsu z procedurami testów w trybie ad hoc.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="5e5a2-343">Rozważ użycie skrótów typów w celu skrócenia sygnatur</span><span class="sxs-lookup"><span data-stu-id="5e5a2-343">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="5e5a2-344">[Skróty typów](../language-reference/type-abbreviations.md) są wygodnym sposobem przypisywania etykiety do innego typu, takiego jak sygnatura funkcji lub bardziej złożony typ.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="5e5a2-345">Na przykład poniższy alias przypisuje etykietę do elementów potrzebnych do zdefiniowania obliczeń za pomocą [CNTK](https://docs.microsoft.com/cognitive-toolkit/), biblioteki uczenia głębokiego:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="5e5a2-346">Nazwa `Computation` jest wygodnym sposobem, aby zauważyć każdą funkcję, która jest zgodna z podpisem aliasu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="5e5a2-347">Używanie skrótów typów, takich jak takie, jest wygodne i pozwala na bardziej zwięzły kod.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="5e5a2-348">Unikaj używania skrótów typu do reprezentowania Twojej domeny</span><span class="sxs-lookup"><span data-stu-id="5e5a2-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="5e5a2-349">Chociaż skróty typów są wygodne do nadawania nazwy podpisom funkcji, mogą one być mylące, gdy abbreviating inne typy.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="5e5a2-350">Rozważmy następujący skrót:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="5e5a2-351">Może to być mylące na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="5e5a2-352">`BufferSize` nie jest abstrakcją; jest to tylko inna nazwa dla liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="5e5a2-353">Jeśli `BufferSize` jest uwidoczniona w publicznym interfejsie API, może być łatwo interpretowana jako "tylko `int`".</span><span class="sxs-lookup"><span data-stu-id="5e5a2-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="5e5a2-354">Ogólnie rzecz biorąc, typy domeny mają wiele atrybutów i nie są typami pierwotnymi, takimi jak `int`.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="5e5a2-355">Ten skrót narusza te założenia.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="5e5a2-356">Wielkość liter w `BufferSize` (PascalCase) oznacza, że ten typ zawiera więcej danych.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="5e5a2-357">Ten alias nie oferuje większej przejrzystości w porównaniu z udostępnianiem nazwanego argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="5e5a2-358">Skrót nie będzie manifestować w skompilowanej IL; jest to tylko liczba całkowita, a ten alias to konstrukcja czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="5e5a2-359">Podsumowując, Pitfall z skrótami typu polega na tym, że **nie** są abstrakcją dla typów, które są abbreviating.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="5e5a2-360">W poprzednim przykładzie `BufferSize` jest tylko `int` w obszarze okładek, bez dodatkowych danych ani żadnych korzyści z systemu typów oprócz tego, co `int` już posiadane.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="5e5a2-361">Alternatywnym podejściem do korzystania z skrótów typu do reprezentowania domeny jest użycie Unii rozłącznych o pojedynczej wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-361">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="5e5a2-362">Poprzedni przykład można modelować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-362">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="5e5a2-363">Jeśli napiszesz kod, który działa w kontekście `BufferSize` i jego wartości źródłowej, musisz utworzyć jeden, a nie przekazywać w dowolny liczbę całkowitą:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-363">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="5e5a2-364">Zmniejsza to prawdopodobieństwo błędnego przełączenia dowolnej liczby całkowitej do funkcji `send`, ponieważ obiekt wywołujący musi skonstruować typ `BufferSize`, aby otoczyć wartość przed wywołaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-364">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
