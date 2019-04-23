---
title: F#konwencje kodowania
description: Informacje ogólne wytyczne i idiomy podczas zapisywania F# kodu.
ms.date: 05/14/2018
ms.openlocfilehash: 1ef016184180eb8d233295e8985903e07693ad26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186748"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="80c3f-103">F#konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="80c3f-103">F# coding conventions</span></span>

<span data-ttu-id="80c3f-104">Poniższe konwencje są formułowane z doświadczenia w pracy z dużymi F# bazach kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="80c3f-105">[Zasadami pięciu dobrze F# kodu](index.md#five-principles-of-good-f-code) stanowiących poszczególne zalecenia.</span><span class="sxs-lookup"><span data-stu-id="80c3f-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="80c3f-106">Są one związane z [ F# wytyczne dotyczące projektowania składnika](component-design-guidelines.md), ale są odpowiednie dla dowolnego F# kodu i nie tylko składniki, takie jak biblioteki.</span><span class="sxs-lookup"><span data-stu-id="80c3f-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="80c3f-107">Organizowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80c3f-107">Organizing code</span></span>

<span data-ttu-id="80c3f-108">F#oferuje dwa podstawowe sposoby organizowania kodu: modułów i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80c3f-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="80c3f-109">Te są podobne, ale różnią się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="80c3f-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="80c3f-110">Przestrzenie nazw są kompilowane jako obszary nazw .NET.</span><span class="sxs-lookup"><span data-stu-id="80c3f-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="80c3f-111">Moduły są kompilowane jako klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="80c3f-112">Przestrzenie nazw są zawsze najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-112">Namespaces are always top level.</span></span> <span data-ttu-id="80c3f-113">Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="80c3f-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="80c3f-114">Przestrzenie nazw może obejmować wiele plików.</span><span class="sxs-lookup"><span data-stu-id="80c3f-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="80c3f-115">Nie można modułów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-115">Modules cannot.</span></span>
* <span data-ttu-id="80c3f-116">Moduły mogą być dekorowane za pomocą `[<RequireQualifiedAccess>]` i `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="80c3f-117">Poniższe wskazówki mogą pomóc w ich użyć do organizowania kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="80c3f-118">Preferuj przestrzeni nazw na najwyższym poziomie</span><span class="sxs-lookup"><span data-stu-id="80c3f-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="80c3f-119">Dla dowolnego publicznie konsumpcyjnych kodu przestrzenie nazw są preferencyjne modułów na najwyższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="80c3f-120">Ponieważ są one kompilowane jako obszary nazw .NET, są one może być używany przez C# nie problemu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="80c3f-121">Przy użyciu modułu najwyższego poziomu mogą pojawiać się różne, gdy zostanie wywołana tylko z F#, ale w przypadku C# konsumentów, wywołań może oczekiwano, konfigurując zakwalifikować się `MyClass` z `MyCode` modułu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="80c3f-122">Stosowanie starannie `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="80c3f-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="80c3f-123">`[<AutoOpen>]` Konstrukcji można charakteryzują się zakres co jest dostępne dla kodu wywołującego, a odpowiedź na coś, z której pochodzi to "Magia".</span><span class="sxs-lookup"><span data-stu-id="80c3f-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="80c3f-124">To zwykle nie jest dobrym znakiem.</span><span class="sxs-lookup"><span data-stu-id="80c3f-124">This is generally not a good thing.</span></span> <span data-ttu-id="80c3f-125">Wyjątkiem od tej reguły jest F# podstawowej biblioteki, sama (mimo że ten fakt jest również nieco kontrowersyjny).</span><span class="sxs-lookup"><span data-stu-id="80c3f-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="80c3f-126">Jednak to udogodnienie Jeśli masz funkcjonalność pomocnika dla publicznego interfejsu API, którą chcesz zorganizować niezależnie od tego publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="80c3f-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="80c3f-127">Dzięki temu można szczegółów klarownie implementacji oddzielne z publicznego interfejsu API funkcji bez konieczności pełnej kwalifikacji pomocnika za każdym razem, należy wywołać.</span><span class="sxs-lookup"><span data-stu-id="80c3f-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="80c3f-128">Ponadto udostępnianie rozszerzenie metod i konstruktorów wyrażeń na poziomie przestrzeni nazw mogą być starannie wyrównywać wyrażone za pomocą `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="80c3f-129">Użyj `[<RequireQualifiedAccess>]` zawsze, gdy nazwy mogą powodować konflikt lub uważasz, że ułatwia z czytelność</span><span class="sxs-lookup"><span data-stu-id="80c3f-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="80c3f-130">Dodawanie `[<RequireQualifiedAccess>]` atrybut do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów moduł wymaga jawnego kwalifikowana dostępu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="80c3f-131">Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="80c3f-132">Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="80c3f-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="80c3f-133">Wymagające dostępu kwalifikowana może znacznie zwiększyć długoterminowe łatwość konserwacji i evolvability biblioteki.</span><span class="sxs-lookup"><span data-stu-id="80c3f-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="80c3f-134">Sortuj `open` instrukcji topologically</span><span class="sxs-lookup"><span data-stu-id="80c3f-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="80c3f-135">W F#, kolejność deklaracji jest ważna, łącznie z `open` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="80c3f-136">Jest to w przeciwieństwie do języka C#, gdy efekt `using` i `using static` jest niezależna od kolejności te instrukcje w pliku.</span><span class="sxs-lookup"><span data-stu-id="80c3f-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="80c3f-137">W F#, elementy otwarte w zakresie można w tle inne osoby już istnieje.</span><span class="sxs-lookup"><span data-stu-id="80c3f-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="80c3f-138">Oznacza to, że zmiana kolejności `open` instrukcji może zmienić znaczenie kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="80c3f-139">W wyniku tego wszystkie dowolnego sortowania wszystkich `open` instrukcji (na przykład alfanumerycznie) ogólnie nie zaleca się, co najmniej wygenerować różne zachowanie, które można by oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="80c3f-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="80c3f-140">Zamiast tego zaleca się je posortować [topologically](https://en.wikipedia.org/wiki/Topological_sorting); oznacza to, że kolejność swoje `open` instrukcji w kolejności, w którym _warstwy_ systemu są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="80c3f-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="80c3f-141">Wykonując alfanumeryczne, sortowanie w różnych warstwach topologii mogą być również uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="80c3f-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="80c3f-142">Na przykład poniżej przedstawiono topologii sortowania dla F# pliku publicznego interfejsu API usługi kompilatora:</span><span class="sxs-lookup"><span data-stu-id="80c3f-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="80c3f-143">Należy pamiętać, że podział wiersza oddziela warstwy topologii z poszczególnymi warstwami posortowana alfanumerycznie później.</span><span class="sxs-lookup"><span data-stu-id="80c3f-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="80c3f-144">Kod zostanie prawidłowo organizuje bez przypadkowo przesłanianie wartości.</span><span class="sxs-lookup"><span data-stu-id="80c3f-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="80c3f-145">Używanie klas do zawierają wartości, które mają skutki uboczne</span><span class="sxs-lookup"><span data-stu-id="80c3f-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="80c3f-146">Istnieje wiele razy podczas inicjowania wartość może mieć efekty uboczne, takie jak utworzenie wystąpienia kontekstu do bazy danych lub innego zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="80c3f-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="80c3f-147">Jest kuszące, aby zainicjować takich elementów w module i używać go w kolejnych funkcji:</span><span class="sxs-lookup"><span data-stu-id="80c3f-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="80c3f-148">Jest to często to zły pomysł kilka możliwych przyczyn:</span><span class="sxs-lookup"><span data-stu-id="80c3f-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="80c3f-149">Po pierwsze Konfiguracja aplikacji są przesyłane do bazy kodu z `dep1` i `dep2`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="80c3f-150">Jest to trudne utrzymanie w większych bazach kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="80c3f-151">Drugi, statycznie zainicjowane danych nie może zawierać wartości, które nie są bezpieczne dla wątków, jeśli sam składnik użyje wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="80c3f-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="80c3f-152">Jest to wyraźnie naruszona przez `dep3`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="80c3f-153">Na koniec inicjowania modułu kompiluje w konstruktorze statycznym jednostki całej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="80c3f-154">W przypadku dowolnego błędu podczas inicjowania umożliwiają granica wartości w tym module, manifesty go jako `TypeInitializationException` który następnie jest buforowana przez cały okres istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="80c3f-155">Może to być trudny do zdiagnozowania.</span><span class="sxs-lookup"><span data-stu-id="80c3f-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="80c3f-156">Zazwyczaj jest wyjątek wewnętrzny, który może próbować poprawić, ale jeśli nie istnieje, to nie ma żadnych informacją jest główną przyczynę.</span><span class="sxs-lookup"><span data-stu-id="80c3f-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="80c3f-157">Po prostu użyj prostą klasę do przechowywania zależności:</span><span class="sxs-lookup"><span data-stu-id="80c3f-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="80c3f-158">Dzięki temu następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="80c3f-158">This enables the following:</span></span>

1. <span data-ttu-id="80c3f-159">Wypychanie dowolny stan zależne spoza sam interfejs API.</span><span class="sxs-lookup"><span data-stu-id="80c3f-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="80c3f-160">Teraz można przeprowadzić konfigurację poza interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="80c3f-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="80c3f-161">Błędy podczas inicjowania wartości zależne nie są może być przedstawiany jako `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="80c3f-162">Interfejs API jest teraz łatwiejsze do testowania.</span><span class="sxs-lookup"><span data-stu-id="80c3f-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="80c3f-163">Błąd zarządzania</span><span class="sxs-lookup"><span data-stu-id="80c3f-163">Error management</span></span>

<span data-ttu-id="80c3f-164">Zarządzanie błędami w dużych systemach jest pozwala złożone i rozmowach i nie ma żadnych silver punktorów w celu zapewnienia systemy są odporne na uszkodzenia i zachowywać się również.</span><span class="sxs-lookup"><span data-stu-id="80c3f-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="80c3f-165">Poniższe wskazówki powinno oferować się ze wskazówkami zawartymi w przechodząc miejsce to trudne.</span><span class="sxs-lookup"><span data-stu-id="80c3f-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="80c3f-166">Reprezentuje przypadków błędów i stan niedozwolony w typach wewnętrznej do Twojej domeny</span><span class="sxs-lookup"><span data-stu-id="80c3f-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="80c3f-167">Za pomocą [sumy rozłączne](../language-reference/discriminated-unions.md), F# daje możliwość reprezentuje stan programu wadliwe w Twoim systemie typu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="80c3f-168">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80c3f-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="80c3f-169">W tym przypadku istnieją trzy sposoby znane, których wycofanie pieniądze z konta bankowego może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="80c3f-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="80c3f-170">Każdy przypadek błędu jest reprezentowana w typie, a ten sposób można przetwarzać bezpiecznie w całym programie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="80c3f-171">Ogólnie rzecz biorąc, jeśli można modelować różne sposoby szukają mogą **się nie powieść** w domenie, następnie dodanymi komentarzami kodu jest już traktowany jako coś muszą radzić sobie z oprócz zwykłego przepływu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="80c3f-172">Jest po prostu część przepływu normalnego programu, a nie traktowane jako **wyjątkowych**.</span><span class="sxs-lookup"><span data-stu-id="80c3f-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="80c3f-173">Istnieją dwie podstawowe korzyści, w tym:</span><span class="sxs-lookup"><span data-stu-id="80c3f-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="80c3f-174">Jest łatwiejsze w konserwacji zgodnie z domeny zmienia się wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="80c3f-175">W przypadku wystąpienia błędów są łatwiejsze do testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="80c3f-176">Użyj wyjątków, kiedy nie może być reprezentowana błędy typów</span><span class="sxs-lookup"><span data-stu-id="80c3f-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="80c3f-177">Nie wszystkie błędy mogą być reprezentowane w domenie problem.</span><span class="sxs-lookup"><span data-stu-id="80c3f-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="80c3f-178">Te rodzaje błędów są *wyjątkowych* pochylone, w związku z tym możliwości pozyskiwania i przechwytywania wyjątków w F#.</span><span class="sxs-lookup"><span data-stu-id="80c3f-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="80c3f-179">Po pierwsze, zaleca się przeczytanie [wytyczne dotyczące projektowania wyjątek](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="80c3f-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="80c3f-180">Te dotyczą również F#.</span><span class="sxs-lookup"><span data-stu-id="80c3f-180">These are also applicable to F#.</span></span>

<span data-ttu-id="80c3f-181">Głównym tworzy dostępne w F# dla celów zgłaszania wyjątków należy rozważyć w następującej kolejności priorytetu:</span><span class="sxs-lookup"><span data-stu-id="80c3f-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="80c3f-182">Funkcja</span><span class="sxs-lookup"><span data-stu-id="80c3f-182">Function</span></span> | <span data-ttu-id="80c3f-183">Składnia</span><span class="sxs-lookup"><span data-stu-id="80c3f-183">Syntax</span></span> | <span data-ttu-id="80c3f-184">Cel</span><span class="sxs-lookup"><span data-stu-id="80c3f-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="80c3f-185">Wywołuje `System.ArgumentNullException` o nazwie określony argument.</span><span class="sxs-lookup"><span data-stu-id="80c3f-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="80c3f-186">Wywołuje `System.ArgumentException` z nazwą określonego argumentu i wiadomość.</span><span class="sxs-lookup"><span data-stu-id="80c3f-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="80c3f-187">Wywołuje `System.InvalidOperationException` z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="80c3f-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="80c3f-188">Mechanizm ogólnego przeznaczenia zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="80c3f-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="80c3f-189">Wywołuje `System.Exception` z określonym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="80c3f-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="80c3f-190">Wywołuje `System.Exception` komunikatem określona przez ciąg formatu i jego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="80c3f-191">Użyj `nullArg`, `invalidArg` i `invalidOp` jako mechanizm do zgłoszenia `ArgumentNullException`, `ArgumentException` i `InvalidOperationException` po zidentyfikowaniu odpowiednich.</span><span class="sxs-lookup"><span data-stu-id="80c3f-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="80c3f-192">`failwith` i `failwithf` funkcje ogólnie należy unikać, ponieważ pobierają one base `Exception` typu określonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="80c3f-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="80c3f-193">Zgodnie [wytyczne dotyczące projektowania wyjątek](../../standard/design-guidelines/exceptions.md), należy podnieść bardziej szczegółowe wyjątki, kiedy tylko można.</span><span class="sxs-lookup"><span data-stu-id="80c3f-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="80c3f-194">Przy użyciu składni obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="80c3f-194">Using exception-handling syntax</span></span>

<span data-ttu-id="80c3f-195">F#obsługuje wyjątek wzorce za pośrednictwem `try...with` składni:</span><span class="sxs-lookup"><span data-stu-id="80c3f-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="80c3f-196">Uzgadnianie funkcji do wykonania w przypadku wyjątku z dopasowaniem wzorca mogą być nieco trudne, jeśli chcesz zachować zgodność czystego kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="80c3f-197">Jeden sposób obsługi to jest użycie [wzorców](../language-reference/active-patterns.md) jako środek do funkcji grupy otaczającego przypadki błędów, z wyjątkiem samej.</span><span class="sxs-lookup"><span data-stu-id="80c3f-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="80c3f-198">Na przykład użytkownik może zużywałoby interfejsu API, który po jego zgłasza wyjątek, otacza cenne informacje metadanych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="80c3f-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="80c3f-199">Rozpakowanie przydatne wartości w treści przechwycony wyjątek wewnątrz — aktywny wzorzec i zwraca, czy wartość może być pomocny w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="80c3f-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="80c3f-200">Nie należy używać obsługi wyjątków zastąpić monadic błędów</span><span class="sxs-lookup"><span data-stu-id="80c3f-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="80c3f-201">Wyjątki są postrzegane jako nieco taboo w programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="80c3f-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="80c3f-202">W rzeczywistości wyjątki narusza czystość, dzięki czemu można bezpiecznie należy wziąć pod uwagę ich nie całkiem funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="80c3f-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="80c3f-203">Jednak to ignoruje rzeczywistość, której kod należy uruchomić i że środowisko uruchomieniowe, które mogą wystąpić błędy.</span><span class="sxs-lookup"><span data-stu-id="80c3f-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="80c3f-204">Ogólnie rzecz biorąc można napisać kod, przy założeniu, że większość elementów są pure ani total, aby zminimalizować nieprzyjemnych niespodzianek.</span><span class="sxs-lookup"><span data-stu-id="80c3f-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="80c3f-205">Warto wziąć pod uwagę następujące podstawowe zalety/aspekty wyjątki względem ich istotności i stosowności środowisko uruchomieniowe platformy .NET i wielu języków ekosystemu jako całości:</span><span class="sxs-lookup"><span data-stu-id="80c3f-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="80c3f-206">Zawierają one szczegółowych informacji diagnostycznych, który jest bardzo pomocne przy debugowaniu problemu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="80c3f-207">Są one dobrze rozumiane przez środowisko uruchomieniowe i innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="80c3f-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="80c3f-208">One może zmniejszyć znaczące standardowy w porównaniu z kodem, który wykracza poza drodze do *uniknąć* wyjątki przez zaimplementowanie pewien podzbiór semantyki ich na podstawie zapytań ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="80c3f-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="80c3f-209">Ten punkt trzeci ma krytyczne znaczenie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-209">This third point is critical.</span></span> <span data-ttu-id="80c3f-210">Proste i złożone operacji kończy się niepowodzeniem, należy używać wyjątków może spowodować radzenia sobie ze strukturami następująco:</span><span class="sxs-lookup"><span data-stu-id="80c3f-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="80c3f-211">Łatwo co może prowadzić do delikatna kodu, takich jak dopasowania do wzorca w "stringly wpisane" błędy:</span><span class="sxs-lookup"><span data-stu-id="80c3f-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="80c3f-212">Ponadto może być kuszące wchłonąć każdy wyjątek, wymaganą dla funkcji "prosta", która zwraca typ "wrażeń":</span><span class="sxs-lookup"><span data-stu-id="80c3f-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="80c3f-213">Niestety `tryReadAllText` może zgłosić liczne wyjątki, w oparciu o wiele rzeczy, które mogą wystąpić w systemie plików, a ten kod natychmiast odrzuca wszelkie informacje na temat co może rzeczywiście być pójdzie w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="80c3f-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="80c3f-214">Jeśli ten kod można zastąpić typu wyniku, jesteś do analizowania komunikatów "stringly wpisane" Błąd:</span><span class="sxs-lookup"><span data-stu-id="80c3f-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="80c3f-215">I wprowadzania do samego obiektu wyjątku w `Error` Konstruktor tylko wymusza prawidłowo radzenia sobie z typu wyjątku w witrynie wywołania, a nie w funkcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="80c3f-216">Spowoduje to skutecznie tworzy zaznaczone wyjątków, które są bardzo unfun radzenia sobie z jako obiekt wywołujący interfejs API.</span><span class="sxs-lookup"><span data-stu-id="80c3f-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="80c3f-217">Jest dobrą alternatywą do powyższych przykładach catch *określonych* wyjątków i zwrócenia zrozumiałą wartość w kontekście tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="80c3f-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="80c3f-218">Jeśli zmodyfikujesz `tryReadAllText` funkcji w następujący sposób, `None` ma więcej znaczenie:</span><span class="sxs-lookup"><span data-stu-id="80c3f-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="80c3f-219">Zamiast działa jako przechwytującą cały, ta funkcja będzie teraz poprawnie obsługiwać przypadku jeśli plik nie został znaleziony i przypisać tym znaczenie zwrotu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="80c3f-220">Ta wartość zwracana można mapować do tego przypadku błąd podczas nie odrzucanie żadnych informacji kontekstowych lub wymuszanie wywołań, aby poradzić sobie z przypadkiem, które mogą nie być odpowiednie w tym momencie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="80c3f-221">Typy takie jak `Result<'Success, 'Error>` są odpowiednie dla podstawowe operacje, których nie są zagnieżdżone, a F# opcjonalne typy są idealne dla reprezentujący, gdy coś można albo zwracany *coś* lub *nic*.</span><span class="sxs-lookup"><span data-stu-id="80c3f-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="80c3f-222">One zamiennika dla wyjątków, nie są jednak i nie może być używany w celu podjęcia do zastąpienia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="80c3f-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="80c3f-223">Zamiast ich powinny dotyczyć rozsądnie adres konkretnych aspektów wyjątków i zasady dotyczące zarządzania błędów względami docelowych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="80c3f-224">Aplikacja częściowa i programowanie bez punktu</span><span class="sxs-lookup"><span data-stu-id="80c3f-224">Partial application and point-free programming</span></span>

<span data-ttu-id="80c3f-225">F#obsługuje aplikacja częściowa i różne sposoby programowania w stylu bez punktu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="80c3f-226">Może to być przydatne w przypadku ponownego użycia kodu w ramach modułu lub wykonania elementu, ale zwykle nie jest coś do udostępnić publicznie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="80c3f-227">Ogólnie rzecz biorąc programowanie bez punktu jest kapitałowymi w i samego siebie i można dodać cognitive dużą przeszkodę dla osób, które nie są pracować w stylu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="80c3f-228">Nie należy używać aplikacja częściowa i currying w publicznych interfejsów API</span><span class="sxs-lookup"><span data-stu-id="80c3f-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="80c3f-229">Z wyjątkiem mały Użyj częściowe aplikacji w publicznych interfejsów API może być mylące dla klientów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="80c3f-230">Zazwyczaj `let`-powiązane wartości w F# kodu są **wartości**, a nie **funkcji wartości**.</span><span class="sxs-lookup"><span data-stu-id="80c3f-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="80c3f-231">Łączenie ze sobą, wartości i wartości funkcji może spowodować zapisywanie niewielką liczbę wierszy kodu w zamian za znacznej liczby cognitive obciążenie, zwłaszcza, jeśli połączone przy użyciu operatorów, takich jak `>>` do redagowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="80c3f-232">Należy wziąć pod uwagę wpływ narzędzi do programowania bez punktu</span><span class="sxs-lookup"><span data-stu-id="80c3f-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="80c3f-233">Funkcje rozwinięte etykiety nie ich argumentów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="80c3f-234">Ma to wpływ narzędzi.</span><span class="sxs-lookup"><span data-stu-id="80c3f-234">This has tooling implications.</span></span> <span data-ttu-id="80c3f-235">Należy wziąć pod uwagę następujące dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="80c3f-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="80c3f-236">Oba są prawidłowe funkcje, ale `funcWithApplication` jest funkcją rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="80c3f-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="80c3f-237">Po umieszczeniu ich typów w edytorze widzisz taki komunikat:</span><span class="sxs-lookup"><span data-stu-id="80c3f-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="80c3f-238">W witrynie wywołania etykietek narzędzi w narzędzia, takiego jak Visual Studio nie zapewni istotnych informacji o tym, co `string` i `int` faktycznie reprezentują typów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="80c3f-239">Jeśli napotkasz bezpłatne punkt kodu, takich jak `funcWithApplication` jest w użyciu publicznie, zaleca się zrobić pełnym rozszerzeniu η, aby narzędzi można wybrać w górę w nazw opisowych dla argumentów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="80c3f-240">Ponadto debugowanie kodu bez punktu może stanowić wyzwanie, jeśli jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="80c3f-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="80c3f-241">Narzędzia do debugowania opierają się na wartościach powiązany z nazw (na przykład `let` powiązania) tak, aby sprawdzić wartości pośrednich midway przez wykonanie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="80c3f-242">Jeśli Twój kod nie ma żadnych wartości, aby sprawdzić, nie ma nic do debugowania.</span><span class="sxs-lookup"><span data-stu-id="80c3f-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="80c3f-243">W przyszłości, narzędzia debugowania, może się rozwijać syntetyzować te wartości opartym o ścieżki wykonanych wcześniej, ale nie jest dobry pomysł, aby zabezpieczyć postawienie na *potencjalnych* debugowania funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="80c3f-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="80c3f-244">Należy wziąć pod uwagę częściowego stosowania jako technika zmniejszyć wewnętrzny standardowy</span><span class="sxs-lookup"><span data-stu-id="80c3f-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="80c3f-245">W przeciwieństwie do wcześniejszego punktu aplikacja częściowa to narzędzie nagraliście w celi zmniejszenia standardowy wewnątrz aplikacji lub bardziej podstawy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="80c3f-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="80c3f-246">Może być przydatne w przypadku implementacji interfejsów API bardziej skomplikowane, gdzie standardowy jest często bolesne radzenia sobie z testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="80c3f-247">Na przykład ilustruje poniższy kod, jak można osiągnąć jakie najbardziej pozorowania struktury nadaj możesz bez przełączania zewnętrzna zależność od takiego framework i konieczności uczenia się z odpowiednimi tworzony na zamówienie interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="80c3f-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="80c3f-248">Na przykład należy wziąć pod uwagę następujące topografii rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="80c3f-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="80c3f-249">`ImplementationLogic.fsproj` może udostępniać takie jak kod:</span><span class="sxs-lookup"><span data-stu-id="80c3f-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="80c3f-250">Testy jednostkowe `Transactions.doTransaction` w `ImplementationLogic.Tests.fspoj` jest proste:</span><span class="sxs-lookup"><span data-stu-id="80c3f-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="80c3f-251">Częściowe stosowanie `doTransaction` z kontekstem pozorowania obiekt umożliwia wywołanie funkcji we wszystkich testów jednostkowych, bez konieczności utworzenia kontekstu pozorowane każdorazowo:</span><span class="sxs-lookup"><span data-stu-id="80c3f-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="80c3f-252">Ta technika nie powinny być powszechnie stosowane do całej bazie kodu, ale jest dobrym sposobem zmniejszenia standardowy skomplikowane elementy wewnętrzne i te elementy wewnętrzne testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="80c3f-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="80c3f-253">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="80c3f-253">Access control</span></span>

<span data-ttu-id="80c3f-254">F#udostępnia wiele opcji [kontroli dostępu](../language-reference/access-control.md), dziedziczone od co to jest dostępne w środowisku uruchomieniowym .NET.</span><span class="sxs-lookup"><span data-stu-id="80c3f-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="80c3f-255">Nie są one po prostu użyteczne dla typów — można ich użyć zbyt dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="80c3f-256">Preferuj non -`public` typów i elementów członkowskich, dopóki nie będą one potrzebne do być publicznie w użyciu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="80c3f-257">Zmniejsza to także jakie kilku klientów do.</span><span class="sxs-lookup"><span data-stu-id="80c3f-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="80c3f-258">Dokładamy wszelkich starań zachować wszystkie funkcje Pomocnika `private`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="80c3f-259">Rozważ użycie `[<AutoOpen>]` na prywatny moduł funkcji pomocnika, gdy staną się wiele.</span><span class="sxs-lookup"><span data-stu-id="80c3f-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="80c3f-260">Wnioskowanie o typie i typami ogólnymi</span><span class="sxs-lookup"><span data-stu-id="80c3f-260">Type inference and generics</span></span>

<span data-ttu-id="80c3f-261">Wnioskowanie o typie mogą pomóc w pisaniu mnóstwo standardowy.</span><span class="sxs-lookup"><span data-stu-id="80c3f-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="80c3f-262">I automatyczna Generalizacja w F# kompilatora może pomóc, dzięki czemu można tworzyć bardziej ogólnymi kodu przy użyciu prawie żadnego dodatkowego wysiłku z Twojej strony.</span><span class="sxs-lookup"><span data-stu-id="80c3f-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="80c3f-263">Jednak te funkcje nie są powszechnie dobre.</span><span class="sxs-lookup"><span data-stu-id="80c3f-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="80c3f-264">Warto nadać nazwy argumentów za pomocą jawnych typów w publicznych interfejsów API i nie należy polegać na wnioskowanie o typie dla tego.</span><span class="sxs-lookup"><span data-stu-id="80c3f-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="80c3f-265">Jest to spowodowane tym, że **możesz** powinna mieć kontrolę nad kształt interfejsu API, nie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="80c3f-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="80c3f-266">Mimo że kompilator może wykonać zadanie poprawnie na wnioskowanie typów dla Ciebie, istnieje możliwość mają kształtu zmiany interfejsu API, jeśli elementy wewnętrzne, które opiera się na zostały zmienione typy.</span><span class="sxs-lookup"><span data-stu-id="80c3f-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="80c3f-267">Może to być, co chcesz zrobić, ale prawie na pewno będzie skutkować istotne zmiany interfejsu API niższego rzędu konsumentów będzie miał do czynienia z.</span><span class="sxs-lookup"><span data-stu-id="80c3f-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="80c3f-268">Zamiast tego należy jawnie kontrolować kształt publicznego interfejsu API, następnie można sterować tymi przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="80c3f-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="80c3f-269">W warunkach DDD to może być uważane za warstwę przeciwdegradacyjną.</span><span class="sxs-lookup"><span data-stu-id="80c3f-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="80c3f-270">Należy rozważyć nadanie znaczącą nazwę, aby argumenty ogólne.</span><span class="sxs-lookup"><span data-stu-id="80c3f-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="80c3f-271">Chyba, że piszesz naprawdę rodzajowy kod, który nie jest specyficzna dla danej domeny, nazwę opisową może pomóc inni programiści zrozumienie domeny, które działają w.</span><span class="sxs-lookup"><span data-stu-id="80c3f-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="80c3f-272">Na przykład, parametru typu o nazwie `'Document` w kontekście interakcji z dokumentem bazy danych zrozumiałe, typów dokumentu ogólnego można zaakceptować według funkcji lub elementu członkowskiego, w którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="80c3f-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="80c3f-273">Należy wziąć pod uwagę nazywanie parametrów typu ogólnego, za pomocą PascalCase.</span><span class="sxs-lookup"><span data-stu-id="80c3f-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="80c3f-274">Jest ogólny sposób, aby wykonywały na platformie .NET, dlatego zalecane jest, że używasz PascalCase zamiast snake_case lub camelCase.</span><span class="sxs-lookup"><span data-stu-id="80c3f-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="80c3f-275">Na koniec automatyczna Generalizacja nie zawsze jest boon dla osób, które są nowe F# lub dużej bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="80c3f-276">Jest cognitive obciążenie za pomocą składników, które są rodzajowe.</span><span class="sxs-lookup"><span data-stu-id="80c3f-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="80c3f-277">Ponadto jeśli automatycznie uogólnionego funkcje nie są używane z różnymi typami danych wejściowych (umożliwiają tylko, jeśli są one przeznaczone do użycia jako takie), a następnie daje żadnych korzyści rzeczywistych do nich jest ogólny w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="80c3f-278">Zawsze należy rozważyć, jeśli kod, który zapisuje się faktycznie będą korzystać z ogólnych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="80c3f-279">Wydajność</span><span class="sxs-lookup"><span data-stu-id="80c3f-279">Performance</span></span>

<span data-ttu-id="80c3f-280">F#wartości są niezmienne domyślnie, co pozwala uniknąć niektórych rodzajów błędów (szczególnie tych dotyczących współbieżności i równoległości).</span><span class="sxs-lookup"><span data-stu-id="80c3f-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="80c3f-281">Jednak w niektórych przypadkach, w celu osiągnięcia optymalnej (lub nawet uzasadnione) skuteczność czas wykonywania lub alokacji pamięci zakresu pracy może najlepiej zaimplementować przy użyciu mutacji w miejscu stanu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="80c3f-282">Jest to możliwe w zgłoszenie zgody na uczestnictwo w podstawie F# z `mutable` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="80c3f-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="80c3f-283">Jednak użycie `mutable` w F# może mieć wrażenie kłóci czystości funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="80c3f-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="80c3f-284">To jest w dobrym stanie, jeśli dostosowano oczekiwań z czystości [referencyjną przezroczystości](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="80c3f-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="80c3f-285">Przezroczystość referencyjnej — nie czystości — jest jej celem, podczas zapisywania F# funkcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="80c3f-286">Umożliwia to zapisywanie funkcjonalności interfejsu za pośrednictwem implementacji opartej na mutacji wydajności kodu krytycznego.</span><span class="sxs-lookup"><span data-stu-id="80c3f-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="80c3f-287">Zawijania mutable kodu za pomocą niezmienialnych interfejsów</span><span class="sxs-lookup"><span data-stu-id="80c3f-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="80c3f-288">Z przezroczystością referencyjną jako cel ważne jest aby napisać kod, który nie ujawnia mutable underbelly newralgicznym dla wydajności funkcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="80c3f-289">Na przykład, poniższy kod implementuje `Array.contains` działa w programach F# podstawowej biblioteki:</span><span class="sxs-lookup"><span data-stu-id="80c3f-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="80c3f-290">Wywołanie tej funkcji wiele razy nie zmienia się tablica bazowa, ani nie wymaga zachować wszystkie modyfikowalny stan, w jego wykorzystanie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="80c3f-291">Jest referentially przezroczyste, mimo że prawie każdy wiersz kodu w nim używa mutacji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="80c3f-292">Należy wziąć pod uwagę enkapsulacji mutable danych w klasach</span><span class="sxs-lookup"><span data-stu-id="80c3f-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="80c3f-293">W powyższym przykładzie użyto jednej funkcji do hermetyzacji operacje przy użyciu tych danych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="80c3f-294">Nie zawsze jest to wystarczające dla bardziej złożonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="80c3f-295">Należy wziąć pod uwagę następujące zestawy funkcji:</span><span class="sxs-lookup"><span data-stu-id="80c3f-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="80c3f-296">Ten kod jest wydajna, ale udostępnia struktury danych mutacji, że obiekty wywołujące odpowiedzialność.</span><span class="sxs-lookup"><span data-stu-id="80c3f-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="80c3f-297">Może to zostać zawinięty wewnątrz klasy bez członków podstawowych, które można zmienić:</span><span class="sxs-lookup"><span data-stu-id="80c3f-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="80c3f-298">`Closure1Table` hermetyzuje wewnętrzna struktura danych mutacji, a tym samym nie wymuszanie obiekty wywołujące do obsługi podstawowej struktury danych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="80c3f-299">Klasy są wydajnym sposobem hermetyzacji danych i procedur, które są oparte na mutacji bez narażania szczegółowe informacje dotyczące obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="80c3f-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="80c3f-300">Preferuj `let mutable` do komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="80c3f-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="80c3f-301">Komórki odwołań są sposobem reprezentowania odwołania do wartości, a nie z samą wartość.</span><span class="sxs-lookup"><span data-stu-id="80c3f-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="80c3f-302">Mimo że mogą one służyć do kodu wrażliwego na wydajność, zwykle nie są zalecane.</span><span class="sxs-lookup"><span data-stu-id="80c3f-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="80c3f-303">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="80c3f-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="80c3f-304">Używanie komórek odwołań teraz "pollutes" wszystkie kolejne kodu z konieczności cofnięcia odwołania i ponownie odwoływać się do danych bazowych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="80c3f-305">Zamiast tego należy wziąć pod uwagę `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="80c3f-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="80c3f-306">Oprócz pojedynczy punkt mutacji w trakcie wykonywania wyrażenia lambda wszystkie inny kod, który dotyka `acc` to zrobić w taki sposób, który nie różni się do użycia jako normalny `let`-granica wartości niezmienne.</span><span class="sxs-lookup"><span data-stu-id="80c3f-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="80c3f-307">Ułatwi zmiany wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="80c3f-308">Programowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="80c3f-308">Object programming</span></span>

<span data-ttu-id="80c3f-309">F#ma pełne wsparcie dla obiektów i pojęcia zorientowane obiektowo (wprowadzaniem).</span><span class="sxs-lookup"><span data-stu-id="80c3f-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="80c3f-310">Chociaż wiele pojęć wprowadzaniem są wydajne i użyteczne, nie wszystkie z nich są idealne do użycia.</span><span class="sxs-lookup"><span data-stu-id="80c3f-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="80c3f-311">Następujące listy oferuje wskazówki dotyczące kategorii funkcji wprowadzaniem na wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="80c3f-312">**Rozważ użycie tych funkcji w wielu sytuacjach:**</span><span class="sxs-lookup"><span data-stu-id="80c3f-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="80c3f-313">Notacji z kropką (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="80c3f-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="80c3f-314">Elementy członkowskie wystąpień</span><span class="sxs-lookup"><span data-stu-id="80c3f-314">Instance members</span></span>
* <span data-ttu-id="80c3f-315">Niejawne konstruktorów</span><span class="sxs-lookup"><span data-stu-id="80c3f-315">Implicit constructors</span></span>
* <span data-ttu-id="80c3f-316">Statyczne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="80c3f-316">Static members</span></span>
* <span data-ttu-id="80c3f-317">Notacja indeksatora (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="80c3f-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="80c3f-318">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="80c3f-318">Named and Optional arguments</span></span>
* <span data-ttu-id="80c3f-319">Interfejsy i implementacje interfejsu</span><span class="sxs-lookup"><span data-stu-id="80c3f-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="80c3f-320">**Nie najpierw dotrzeć do tych funkcji, ale rozsądnie zastosować je, gdy są one wygodny w celu rozwiązania problemu:**</span><span class="sxs-lookup"><span data-stu-id="80c3f-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="80c3f-321">Przeciążenie metody</span><span class="sxs-lookup"><span data-stu-id="80c3f-321">Method overloading</span></span>
* <span data-ttu-id="80c3f-322">Encapsulated mutable danych</span><span class="sxs-lookup"><span data-stu-id="80c3f-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="80c3f-323">Operatory typów</span><span class="sxs-lookup"><span data-stu-id="80c3f-323">Operators on types</span></span>
* <span data-ttu-id="80c3f-324">Właściwości automatyczne</span><span class="sxs-lookup"><span data-stu-id="80c3f-324">Auto properties</span></span>
* <span data-ttu-id="80c3f-325">Implementowanie `IDisposable` i `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="80c3f-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="80c3f-326">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="80c3f-326">Type extensions</span></span>
* <span data-ttu-id="80c3f-327">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80c3f-327">Events</span></span>
* <span data-ttu-id="80c3f-328">Struktury</span><span class="sxs-lookup"><span data-stu-id="80c3f-328">Structs</span></span>
* <span data-ttu-id="80c3f-329">Delegaty</span><span class="sxs-lookup"><span data-stu-id="80c3f-329">Delegates</span></span>
* <span data-ttu-id="80c3f-330">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="80c3f-330">Enums</span></span>

<span data-ttu-id="80c3f-331">**Ogólnie należy unikać tych funkcji, chyba że należy użyć:**</span><span class="sxs-lookup"><span data-stu-id="80c3f-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="80c3f-332">Hierarchie dziedziczenia na podstawie typu i dziedziczenie implementacji</span><span class="sxs-lookup"><span data-stu-id="80c3f-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="80c3f-333">Wartości null i `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="80c3f-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="80c3f-334">Preferuj kompozycji przed dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="80c3f-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="80c3f-335">[Kompozycji nad dziedziczenia](https://en.wikipedia.org/wiki/Composition_over_inheritance) bardzo dobre rozwiązanie długotrwałych idiom F# kod może być zgodne.</span><span class="sxs-lookup"><span data-stu-id="80c3f-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="80c3f-336">Podstawową zasadą jest, konieczne jest dalsze nie uwidocznić klasę bazową i wymusić wywołujących dziedziczyć z tej klasy bazowej, aby uzyskać funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="80c3f-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="80c3f-337">Użyj wyrażenia obiektów do implementacji interfejsów, jeśli nie potrzebujesz, klasa</span><span class="sxs-lookup"><span data-stu-id="80c3f-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="80c3f-338">[Wyrażenia obiektów](../language-reference/object-expressions.md) umożliwiają implementować interfejsy na bieżąco, powiązanie zaimplementowanego interfejsu z wartością bez konieczności zrobić wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="80c3f-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="80c3f-339">Jest to wygodne, zwłaszcza wtedy, gdy użytkownik _tylko_ muszą implementować interfejs i nie potrzebują pełnego klasy.</span><span class="sxs-lookup"><span data-stu-id="80c3f-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="80c3f-340">Na przykład poniżej przedstawiono kod, który jest uruchamiany w [Ionide](http://ionide.io/) zapewnienie Akcja poprawki kodu, jeśli po dodaniu symboli, które nie mają `open` poufności informacji dotyczące:</span><span class="sxs-lookup"><span data-stu-id="80c3f-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="80c3f-341">Ponieważ nie ma potrzeby klasy podczas interakcji z API kodu w usłudze Visual Studio, wyrażenia obiektów są idealnym narzędziem do tego.</span><span class="sxs-lookup"><span data-stu-id="80c3f-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="80c3f-342">Są one również przydatny w przypadku testowania jednostkowego, gdy chcesz zastąpić klasą zastępczą interfejsu testujące w sposób ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="80c3f-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="80c3f-343">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="80c3f-343">Type Abbreviations</span></span>

<span data-ttu-id="80c3f-344">[Skróty typów](../language-reference/type-abbreviations.md) to wygodny sposób, aby przypisać etykietę do innego typu, takiego jak sygnatura funkcji lub bardziej złożonych typów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="80c3f-345">Na przykład, następujący alias przypisuje etykietę co jest potrzebne do definiowania obliczeń z [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), biblioteka do uczenia głębokiego:</span><span class="sxs-lookup"><span data-stu-id="80c3f-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="80c3f-346">`Computation` Nazwa jest wygodnym sposobem określenia żadnej funkcji, która pasuje do podpisu jest tworzenie aliasów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="80c3f-347">Za pomocą skróty typów, takich jak to jest wygodne i pozwala na bardziej zwięzłą kodu.</span><span class="sxs-lookup"><span data-stu-id="80c3f-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="80c3f-348">Należy unikać skróty typów do reprezentowania Twojej domeny</span><span class="sxs-lookup"><span data-stu-id="80c3f-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="80c3f-349">Chociaż skróty typów jest wygodne w przypadku nadania nazwy do sygnatury funkcji, mogą to być mylące po używanie innych typów.</span><span class="sxs-lookup"><span data-stu-id="80c3f-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="80c3f-350">Należy wziąć pod uwagę ten skrót:</span><span class="sxs-lookup"><span data-stu-id="80c3f-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="80c3f-351">Może to być mylące na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="80c3f-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="80c3f-352">`BufferSize` nie jest klasą abstrakcyjną; jest po prostu inną nazwę dla liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="80c3f-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="80c3f-353">Jeśli `BufferSize` jest uwidaczniany w publiczny interfejs API go mogą łatwo zostać błędnie zinterpretowane jako oznaczenie więcej niż tylko `int`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="80c3f-354">Ogólnie rzecz biorąc, typy domen mają wiele atrybutów do nich i nie typy pierwotne, takie jak `int`.</span><span class="sxs-lookup"><span data-stu-id="80c3f-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="80c3f-355">Ten skrót narusza tego założeń.</span><span class="sxs-lookup"><span data-stu-id="80c3f-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="80c3f-356">Wielkość liter w wyrazie `BufferSize` (PascalCase) oznacza, że ten typ posiada większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="80c3f-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="80c3f-357">Ten alias nie oferuje większą przejrzystość w porównaniu ze świadczeniem nazwany argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="80c3f-358">Skrót nie zostanie powiadomiony w skompilowanych IL; jest po prostu liczbą całkowitą, a ten alias jest konstrukcją kompilacji.</span><span class="sxs-lookup"><span data-stu-id="80c3f-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="80c3f-359">Podsumowanie niedogodności z skróty typów te są **nie** abstrakcji za pośrednictwem typów są ich używanie.</span><span class="sxs-lookup"><span data-stu-id="80c3f-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="80c3f-360">W poprzednim przykładzie `BufferSize` jest po prostu `int` dzieje się w tle, z Brak dodatkowych danych ani żadnych korzyści z system typów, oprócz co `int` ma już.</span><span class="sxs-lookup"><span data-stu-id="80c3f-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
