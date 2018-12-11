---
title: Wyrażenia obliczeń (F#)
description: Dowiedz się, jak utworzyć wygodnej składni do pisania obliczeń w F# , można sekwencyjna i połączone przy użyciu kontrolowania konstrukcje przepływów i powiązania.
ms.date: 07/27/2018
ms.openlocfilehash: b1fee11f68e99e53d19b47bef9eca6298cce2f45
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169849"
---
# <a name="computation-expressions"></a><span data-ttu-id="1af95-103">Wyrażenia obliczeń</span><span class="sxs-lookup"><span data-stu-id="1af95-103">Computation Expressions</span></span>

<span data-ttu-id="1af95-104">Wyrażenia obliczeń w F# zapewnienia wygodnej składni pisania obliczeń, które mogą być sekwencjonowania i łączyć, używając konstrukcji przepływów sterowania i powiązania.</span><span class="sxs-lookup"><span data-stu-id="1af95-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="1af95-105">W zależności od rodzaju wyrażenia obliczeń one można traktować jako sposób express monads, monoids, transformatory monad i applicative funktory.</span><span class="sxs-lookup"><span data-stu-id="1af95-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="1af95-106">Jednak w przeciwieństwie do innych języków (takie jak *zapisu czy* w Haskell), nie są powiązane z jednym pozyskiwania i nie należy polegać na makr lub innych form metaprogramowanie wykonywania wygodne i kontekstowym składni.</span><span class="sxs-lookup"><span data-stu-id="1af95-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="1af95-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="1af95-107">Overview</span></span>

<span data-ttu-id="1af95-108">Obliczenia może mieć wiele form.</span><span class="sxs-lookup"><span data-stu-id="1af95-108">Computations can take many forms.</span></span> <span data-ttu-id="1af95-109">Najczęściej używany typ wyliczenia jest jednowątkowym wykonywania, który jest łatwy do zrozumienia i modyfikować.</span><span class="sxs-lookup"><span data-stu-id="1af95-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="1af95-110">Jednak nie wszystkie rodzaje obliczeń są tak proste jak jednowątkowe wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1af95-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="1af95-111">Oto niektóre przykłady:</span><span class="sxs-lookup"><span data-stu-id="1af95-111">Some examples include:</span></span>

* <span data-ttu-id="1af95-112">Nie deterministyczne obliczeń</span><span class="sxs-lookup"><span data-stu-id="1af95-112">Non-deterministic computations</span></span>
* <span data-ttu-id="1af95-113">Asynchroniczne obliczenia</span><span class="sxs-lookup"><span data-stu-id="1af95-113">Asynchronous computations</span></span>
* <span data-ttu-id="1af95-114">Effectful obliczeń</span><span class="sxs-lookup"><span data-stu-id="1af95-114">Effectful computations</span></span>
* <span data-ttu-id="1af95-115">Generatywną obliczeń</span><span class="sxs-lookup"><span data-stu-id="1af95-115">Generative computations</span></span>

<span data-ttu-id="1af95-116">Ogólnie rzecz biorąc, istnieją *kontekstową* obliczenia, które należy wykonać w niektórych części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1af95-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="1af95-117">Pisanie kodu kontekstową może stanowić wyzwanie, ponieważ jest łatwy do obliczenia "przeciek" poza podanym kontekście bez abstrakcji, aby zapobiec temu.</span><span class="sxs-lookup"><span data-stu-id="1af95-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="1af95-118">Te elementy abstrakcji są często trudne do zapisu przez siebie, co jest dlaczego F# został uogólniony sposób przeprowadzenia tak zwane **wyrażenia obliczeń**.</span><span class="sxs-lookup"><span data-stu-id="1af95-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="1af95-119">Wyrażenia obliczeń oferuje jednolite składni i abstrakcji model dla kodowania kontekstową obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="1af95-120">Każde wyrażenie obliczeń opiera się na *konstruktora* typu.</span><span class="sxs-lookup"><span data-stu-id="1af95-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="1af95-121">Typ Konstruktor określa operacje, które są dostępne dla wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="1af95-122">Zobacz [tworzenia nowego typu z wyrażenia obliczeń](computation-expressions.md#creating-a-new-type-of-computation-expression), który przedstawia sposób tworzenia wyrażenia obliczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1af95-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="1af95-123">Omówienie składni</span><span class="sxs-lookup"><span data-stu-id="1af95-123">Syntax overview</span></span>

<span data-ttu-id="1af95-124">Wszystkie wyrażenia obliczeń mają następującą postać:</span><span class="sxs-lookup"><span data-stu-id="1af95-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="1af95-125">gdzie `builder-expr` jest nazwą typu konstruktora, który definiuje wyrażenie obliczeń i `cexper` treści wyrażenia wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="1af95-126">Na przykład `async` obliczenie wyrażenia kodu może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="1af95-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="1af95-127">Brak dostępnej specjalnych i dodatkowe składni w wyrażeniu obliczeń, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1af95-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="1af95-128">Możliwe za pomocą wyrażenia obliczeń są następujące formy wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="1af95-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="1af95-129">Każda z tych słów kluczowych i innymi standard F# słowa kluczowe są dostępne tylko w wyrażeniu obliczeń, jeśli zostały zdefiniowane w zapasowy typ konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1af95-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="1af95-130">Jedynym wyjątkiem jest `match!`, która sama jest sugar składni do użycia z `let!` następuje dopasowania do wzorca w wyniku.</span><span class="sxs-lookup"><span data-stu-id="1af95-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="1af95-131">Typ konstruktora jest obiektem, który definiuje specjalne metody, które określają sposób, w jaki fragmenty wyrażenia obliczeń są łączone; oznacza to, że jego metod kontroli zachowania wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="1af95-132">Inny sposób w celu opisania klasy, Konstruktor jest powiedzieć, umożliwia dostosowywanie operacji wielu F# konstrukcje, takie jak pętle i powiązania.</span><span class="sxs-lookup"><span data-stu-id="1af95-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="1af95-133">`let!` — Słowo kluczowe wiąże nazwę wyniku wywołania do innego wyrażenia obliczeń:</span><span class="sxs-lookup"><span data-stu-id="1af95-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="1af95-134">Jeśli powiązać wywołanie wyrażenia obliczeń, za pomocą `let`, nie będzie można uzyskać wynik wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="1af95-135">Zamiast tego możesz będzie mieć powiązana wartość *niezrealizowane* wywołanie tego wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="1af95-136">Użyj `let!` powiązać z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="1af95-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="1af95-137">`let!` jest definicją `Bind(x, f)` składowej typu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1af95-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="1af95-138">`do!` — Słowo kluczowe jest wywołanie wyrażenia obliczeń, który zwraca `unit`— takich jak typ (zdefiniowany przez `Zero` elementu członkowskiego w konstruktorze):</span><span class="sxs-lookup"><span data-stu-id="1af95-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="1af95-139">Aby uzyskać [asynchronicznego przepływu pracy](asynchronous-workflows.md), ten typ jest `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="1af95-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="1af95-140">Dla innych wyrażeń obliczeń mogą być jest typ `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="1af95-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="1af95-141">`do!` jest definiowany przez `Bind(x, f)` składowej typu konstruktora, gdzie `f` tworzy `unit`.</span><span class="sxs-lookup"><span data-stu-id="1af95-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="1af95-142">`yield` — Słowo kluczowe jest zwracanie wartości z wyrażenia obliczeń, dzięki czemu mogą być używane jako <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="1af95-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="1af95-143">Podobnie jak w przypadku [yield — słowo kluczowe w języku C#](../../csharp/language-reference/keywords/yield.md), każdy element w wyrażeniu obliczeń jest uzyskane nagrania, ponieważ jest ona postanowiliśmy.</span><span class="sxs-lookup"><span data-stu-id="1af95-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="1af95-144">`yield` jest definiowany przez `Yield(x)` składowej typu konstruktora, gdzie `x` element umożliwiające uzyskanie ponownie.</span><span class="sxs-lookup"><span data-stu-id="1af95-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="1af95-145">`yield!` — Słowo kluczowe jest spłaszczanie kolekcję wartości w wyrażeniu obliczeń:</span><span class="sxs-lookup"><span data-stu-id="1af95-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="1af95-146">Podczas oceny, wyrażenia obliczeń wywoływane przez `yield!` będzie mieć elementy zwróciło wstecz jeden po drugim, spłaszczanie wynik.</span><span class="sxs-lookup"><span data-stu-id="1af95-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="1af95-147">`yield!` jest definiowany przez `YieldFrom(x)` składowej typu konstruktora, gdzie `x` to zbiór wartości.</span><span class="sxs-lookup"><span data-stu-id="1af95-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="1af95-148">`return` — Słowo kluczowe otacza wartość w polu Typ odpowiadający wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="1af95-149">Oprócz wyrażenia obliczeń przy użyciu `yield`, jest używany do "complete" wyrażenia obliczeń:</span><span class="sxs-lookup"><span data-stu-id="1af95-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="1af95-150">`return` jest definiowany przez `Return(x)` składowej typu konstruktora, gdzie `x` element do opakowania.</span><span class="sxs-lookup"><span data-stu-id="1af95-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="1af95-151">`return!` — Słowo kluczowe zawiera wartość wyrażenia obliczeń i otacza wynik w typie odpowiadający wyrażenia obliczeń:</span><span class="sxs-lookup"><span data-stu-id="1af95-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="1af95-152">`return!` jest definiowany przez `ReturnFrom(x)` składowej typu konstruktora, gdzie `x` jest innym wyrażeniem obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="1af95-153">Począwszy od F# 4.5, `match!` — słowo kluczowe pozwala na tekście wywołania do innego obliczenie wyrażenia i wzorzec dopasowania na jego wynik:</span><span class="sxs-lookup"><span data-stu-id="1af95-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="1af95-154">Podczas wywoływania wyrażeniu obliczeń z `match!`, będzie weź pod uwagę wynik wywołania, takie jak `let!`.</span><span class="sxs-lookup"><span data-stu-id="1af95-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="1af95-155">Jest to często używane podczas wywoływania wyrażenia obliczeń, której wynikiem jest [opcjonalne](options.md).</span><span class="sxs-lookup"><span data-stu-id="1af95-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="1af95-156">Wyrażenia obliczeń wbudowane</span><span class="sxs-lookup"><span data-stu-id="1af95-156">Built-in computation expressions</span></span>

<span data-ttu-id="1af95-157">F# Podstawowej biblioteki definiuje trzy wyrażenia obliczeń wbudowane: [Wyrażenia sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażeniach zapytań](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1af95-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="1af95-158">Tworzenie nowego typu wyrażenia obliczeń</span><span class="sxs-lookup"><span data-stu-id="1af95-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="1af95-159">Można zdefiniować właściwości wyrażenia obliczeń, tworząc klasę konstruktora i definiowanie pewne specjalne metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="1af95-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="1af95-160">Klasa konstruktora Opcjonalnie można zdefiniować metody, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1af95-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="1af95-161">W poniższej tabeli opisano metody, których można użyć w klasie konstruktora przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1af95-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="1af95-162">**— Metoda**</span><span class="sxs-lookup"><span data-stu-id="1af95-162">**Method**</span></span>|<span data-ttu-id="1af95-163">**Typowe podpisy**</span><span class="sxs-lookup"><span data-stu-id="1af95-163">**Typical signature(s)**</span></span>|<span data-ttu-id="1af95-164">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1af95-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="1af95-165">Wywoływana dla `let!` i `do!` w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="1af95-166">Opakowuje wyrażeniu obliczeń w funkcji.</span><span class="sxs-lookup"><span data-stu-id="1af95-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="1af95-167">Wywoływana dla `return` w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1af95-168">Wywoływana dla `return!` w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="1af95-169">`M<'T> -> M<'T>` lub</span><span class="sxs-lookup"><span data-stu-id="1af95-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="1af95-170">Wykonuje wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="1af95-171">`M<'T> * M<'T> -> M<'T>` lub</span><span class="sxs-lookup"><span data-stu-id="1af95-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="1af95-172">Wywoływana dla sekwencjonowania w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="1af95-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` lub</span><span class="sxs-lookup"><span data-stu-id="1af95-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="1af95-174">Wywoływana dla `for...do` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="1af95-175">Wywoływana dla `try...finally` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="1af95-176">Wywoływana dla `try...with` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="1af95-177">Wywoływana dla `use` powiązania w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="1af95-178">Wywoływana dla `while...do` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="1af95-179">Wywoływana dla `yield` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1af95-180">Wywoływana dla `yield!` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="1af95-181">Wywoływana dla pusta `else` gałęzi z `if...then` wyrażeń w wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|

<span data-ttu-id="1af95-182">Wiele metod w klasie konstruktora użycia i zwracają `M<'T>` konstrukcji, która jest zwykle oddzielnie zdefiniowanego typu, który charakteryzuje rodzaju obliczeń połączone, przykładowo, `Async<'T>` asynchronicznych przepływów pracy i `Seq<'T>` w przypadku przepływów pracy sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1af95-182">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="1af95-183">Podpisy metody te je włączyć połączone i zagnieżdżone ze sobą, tak, aby obiekt przepływu pracy, zwracany z jedną konstrukcję może być przekazywany do następnej.</span><span class="sxs-lookup"><span data-stu-id="1af95-183">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="1af95-184">Po przeanalizowaniu wyrażenia obliczeń, kompilator konwertuje wyrażenie w serii zagnieżdżonych wywołań funkcji przy użyciu metod przedstawionych w powyższej tabeli i kodu w wyrażeniu obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-184">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="1af95-185">Zagnieżdżone wyrażenie ma następującą postać:</span><span class="sxs-lookup"><span data-stu-id="1af95-185">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="1af95-186">W kodzie powyżej wywołania `Run` i `Delay` są pomijane, jeśli nie są zdefiniowane w klasie Konstruktor wyrażeń obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-186">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="1af95-187">Treść wyrażenia obliczeń, w tym miejscu są oznaczone jako `{| cexpr |}`, przetłumaczyć obejmujące metod klasy konstruktora połączeń przez tłumaczenia opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1af95-187">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="1af95-188">Wyrażenia obliczeń `{| cexpr |}` jest zdefiniowanego cyklicznie zgodnie z ich gdzie `expr` jest F# wyrażenia i `cexpr` jest wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-188">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="1af95-189">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="1af95-189">Expression</span></span>|<span data-ttu-id="1af95-190">{1&gt;Translacja&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1af95-190">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|

<span data-ttu-id="1af95-191">W poprzedniej tabeli `other-expr` opisuje wyrażenie, które w przeciwnym razie nie został wymieniony w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1af95-191">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="1af95-192">Klasa konstruktora nie trzeba implementować wszystkie metody i obsługiwać wszystkich tłumaczeń wymienionych w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1af95-192">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="1af95-193">Te konstrukcje, które nie są implementowane nie są dostępne w wyrażenia obliczeń tego typu.</span><span class="sxs-lookup"><span data-stu-id="1af95-193">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="1af95-194">Na przykład, jeśli nie chcesz obsługiwać `use` słowa kluczowego w Twojej wyrażenia obliczeń, można pominąć definicji `Use` w klasie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1af95-194">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="1af95-195">Poniższy przykład kodu pokazuje wyrażenie obliczeń hermetyzujący obliczeń serię kroków, które mogą być obliczane jeden krok w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="1af95-195">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="1af95-196">A Suma rozłączna typ union `OkOrException`, koduje stanu błędu wyrażenia obliczonego do tej pory.</span><span class="sxs-lookup"><span data-stu-id="1af95-196">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="1af95-197">Ten przykład demonstruje kilka typowych wzorców, które można używać w swojej wyrażenia obliczeń, takich jak standardowy implementacje niektórych metod konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1af95-197">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step 
```

<span data-ttu-id="1af95-198">Wyrażenia obliczeń ma typu podstawowego, który zwraca wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1af95-198">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="1af95-199">Typ podstawowy może reprezentować obliczony wynik lub opóźnione obliczenie, które mogą być wykonywane lub może ona dostarczać sposób do iteracji przez kolekcję określonego typu.</span><span class="sxs-lookup"><span data-stu-id="1af95-199">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="1af95-200">W poprzednim przykładzie był typem podstawowym **ostatecznie**.</span><span class="sxs-lookup"><span data-stu-id="1af95-200">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="1af95-201">To wyrażenie sekwencji jest typem podstawowym <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1af95-201">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1af95-202">Wyrażenie zapytania, typ podstawowy jest <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1af95-202">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1af95-203">Dla asynchronicznego przepływu pracy jest typem podstawowym [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="1af95-203">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="1af95-204">`Async` Obiekt reprezentuje pracy do wykonania do obliczania wyniku.</span><span class="sxs-lookup"><span data-stu-id="1af95-204">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="1af95-205">Na przykład wywołać [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) do wykonywania obliczeń i zwracają wynik.</span><span class="sxs-lookup"><span data-stu-id="1af95-205">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="1af95-206">Operacje niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1af95-206">Custom Operations</span></span>

<span data-ttu-id="1af95-207">Można zdefiniować niestandardowe operacja na wyrażeniu obliczeń i użyć niestandardowych operacji jako operator w wyrażeniu obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-207">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="1af95-208">Na przykład może zawierać operatora zapytania "w" w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="1af95-208">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="1af95-209">Podczas definiowania operacji niestandardowej, należy zdefiniować wydajność i metod w wyrażeniu obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-209">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="1af95-210">Aby zdefiniować niestandardowe działanie, umieść go w klasę konstruktora dla wyrażenia obliczeń, a następnie Zastosuj [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="1af95-210">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="1af95-211">Ten atrybut przyjmuje ciąg jako argument, jest to nazwa, która ma być używany w niestandardowych operacji.</span><span class="sxs-lookup"><span data-stu-id="1af95-211">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="1af95-212">Ta nazwa jest dostarczany do zakresu na początku otwierającym nawiasie klamrowym wyrażenia obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1af95-212">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="1af95-213">Dlatego nie należy używać identyfikatorów, które mają taką samą nazwę jak niestandardowe działania w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="1af95-213">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="1af95-214">Na przykład należy unikać stosowanie identyfikatorów, takich jak `all` lub `last` w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="1af95-214">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="1af95-215">Rozszerzanie istniejących producenci nowe operacje niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1af95-215">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="1af95-216">Jeśli masz już klasa konstruktora, jego operacje niestandardowe można rozszerzyć z poza tym konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="1af95-216">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="1af95-217">Rozszerzenia musi być zadeklarowany w modułach.</span><span class="sxs-lookup"><span data-stu-id="1af95-217">Extensions must be declared in modules.</span></span> <span data-ttu-id="1af95-218">Przestrzenie nazw nie może zawierać elementy członkowskie rozszerzeń z wyjątkiem w tym samym pliku i tej samej grupie deklaracji przestrzeni nazw, gdy typ jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="1af95-218">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="1af95-219">Poniższy przykład pokazuje rozszerzenie istniejącej `Microsoft.FSharp.Linq.QueryBuilder` klasy.</span><span class="sxs-lookup"><span data-stu-id="1af95-219">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="1af95-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1af95-220">See also</span></span>

- [<span data-ttu-id="1af95-221">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="1af95-221">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1af95-222">Asynchroniczne przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="1af95-222">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="1af95-223">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="1af95-223">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="1af95-224">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="1af95-224">Query Expressions</span></span>](query-expressions.md)
