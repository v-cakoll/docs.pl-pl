---
title: Byrefs
description: Dowiedz się więcej o byref i byref-jak typy w F#, które są używane do programowania niskiego poziomu.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187051"
---
# <a name="byrefs"></a><span data-ttu-id="b0883-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="b0883-103">Byrefs</span></span>

<span data-ttu-id="b0883-104">F# ma dwa główne obszary funkcji, które zajmują się w przestrzeni programowania niskiego poziomu:</span><span class="sxs-lookup"><span data-stu-id="b0883-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="b0883-105">`byref` / `inref` Typy, / `outref` które są wskaźnikami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="b0883-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="b0883-106">Mają ograniczenia dotyczące użycia, dzięki czemu nie można skompilować program, który jest nieprawidłowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0883-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="b0883-107">-jak `byref`struct, który jest [strukturą,](structures.md) która ma podobną semantykę `byref<'T>`i te same ograniczenia czasu kompilacji co .</span><span class="sxs-lookup"><span data-stu-id="b0883-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="b0883-108">Jednym z <xref:System.Span%601>przykładów jest .</span><span class="sxs-lookup"><span data-stu-id="b0883-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0883-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0883-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="b0883-110">Byref, inref i outref</span><span class="sxs-lookup"><span data-stu-id="b0883-110">Byref, inref, and outref</span></span>

<span data-ttu-id="b0883-111">Istnieją trzy formy: `byref`</span><span class="sxs-lookup"><span data-stu-id="b0883-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="b0883-112">`inref<'T>`, wskaźnik zarządzany do odczytu wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="b0883-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="b0883-113">`outref<'T>`, wskaźnik zarządzany do zapisu do wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="b0883-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="b0883-114">`byref<'T>`, wskaźnik zarządzany do odczytu i zapisu wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="b0883-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="b0883-115">A `byref<'T>` mogą być `inref<'T>` przekazywane, gdzie oczekuje się.</span><span class="sxs-lookup"><span data-stu-id="b0883-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="b0883-116">Podobnie `byref<'T>` można przekazać, gdzie `outref<'T>` oczekuje się.</span><span class="sxs-lookup"><span data-stu-id="b0883-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="b0883-117">Korzystanie z byrefs</span><span class="sxs-lookup"><span data-stu-id="b0883-117">Using byrefs</span></span>

<span data-ttu-id="b0883-118">Aby użyć `inref<'T>`, musisz uzyskać wartość `&`wskaźnika z:</span><span class="sxs-lookup"><span data-stu-id="b0883-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="b0883-119">Aby zapisać wskaźnik za `outref<'T>` pomocą `byref<'T>`lub , należy również zrobić wartość `mutable`chwycić wskaźnik do .</span><span class="sxs-lookup"><span data-stu-id="b0883-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="b0883-120">Jeśli piszesz tylko wskaźnik zamiast go `outref<'T>` czytać, `byref<'T>`rozważ użycie zamiast .</span><span class="sxs-lookup"><span data-stu-id="b0883-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="b0883-121">Semantyka inref</span><span class="sxs-lookup"><span data-stu-id="b0883-121">Inref semantics</span></span>

<span data-ttu-id="b0883-122">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="b0883-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="b0883-123">Semantycznie oznacza to, co następuje:</span><span class="sxs-lookup"><span data-stu-id="b0883-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="b0883-124">Posiadacz wskaźnika `x` może go używać tylko do odczytu wartości.</span><span class="sxs-lookup"><span data-stu-id="b0883-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="b0883-125">Każdy wskaźnik uzyskany do `struct` `SomeStruct` pól zagnieżdżonych w danym typu `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="b0883-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="b0883-126">Prawdą jest również:</span><span class="sxs-lookup"><span data-stu-id="b0883-126">The following is also true:</span></span>

* <span data-ttu-id="b0883-127">Nie ma żadnych implikacji, że inne wątki lub aliasy nie mają dostępu do zapisu . `x`</span><span class="sxs-lookup"><span data-stu-id="b0883-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="b0883-128">Nie ma implikacji, `SomeStruct` która jest niezmienna `x` ze `inref`względu na to, że jest .</span><span class="sxs-lookup"><span data-stu-id="b0883-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="b0883-129">Jednak dla typów wartości **are** F#, które `this` są niezmienne, wskaźnik `inref`jest wywnioskować, aby być .</span><span class="sxs-lookup"><span data-stu-id="b0883-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="b0883-130">Wszystkie te reguły razem oznacza, `inref` że posiadacz wskaźnika nie może modyfikować natychmiastowej zawartości pamięci jest wskazywany.</span><span class="sxs-lookup"><span data-stu-id="b0883-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="b0883-131">Semantyka Outref</span><span class="sxs-lookup"><span data-stu-id="b0883-131">Outref semantics</span></span>

<span data-ttu-id="b0883-132">Celem `outref<'T>` jest wskazanie, że wskaźnik powinien być tylko zapisywany.</span><span class="sxs-lookup"><span data-stu-id="b0883-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="b0883-133">Nieoczekiwanie `outref<'T>` pozwala na odczyt wartości źródłowej pomimo jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="b0883-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="b0883-134">Ma to na celu zgodność.</span><span class="sxs-lookup"><span data-stu-id="b0883-134">This is for compatibility purposes.</span></span> <span data-ttu-id="b0883-135">Semantycznie, `outref<'T>` nie `byref<'T>`różni się od .</span><span class="sxs-lookup"><span data-stu-id="b0883-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="b0883-136">Interop z C\#</span><span class="sxs-lookup"><span data-stu-id="b0883-136">Interop with C\#</span></span>

<span data-ttu-id="b0883-137">C# obsługuje `in ref` `out ref` i słowa kluczowe, `ref` oprócz zwraca.</span><span class="sxs-lookup"><span data-stu-id="b0883-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="b0883-138">W poniższej tabeli pokazano, jak F# interpretuje, co elewuje c#:</span><span class="sxs-lookup"><span data-stu-id="b0883-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="b0883-139">Konstrukcja języka C#</span><span class="sxs-lookup"><span data-stu-id="b0883-139">C# construct</span></span>|<span data-ttu-id="b0883-140">Wnioskowanie F#</span><span class="sxs-lookup"><span data-stu-id="b0883-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="b0883-141">`ref`zwracawartość</span><span class="sxs-lookup"><span data-stu-id="b0883-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="b0883-142">`ref readonly`zwracawartość</span><span class="sxs-lookup"><span data-stu-id="b0883-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="b0883-143">`in ref`Parametr</span><span class="sxs-lookup"><span data-stu-id="b0883-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="b0883-144">`out ref`Parametr</span><span class="sxs-lookup"><span data-stu-id="b0883-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="b0883-145">W poniższej tabeli przedstawiono, co f# emituje:</span><span class="sxs-lookup"><span data-stu-id="b0883-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="b0883-146">Konstrukcja Języka F#</span><span class="sxs-lookup"><span data-stu-id="b0883-146">F# construct</span></span>|<span data-ttu-id="b0883-147">Emitowana konstrukcja</span><span class="sxs-lookup"><span data-stu-id="b0883-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="b0883-148">Argument `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="b0883-148">`inref<'T>` argument</span></span>|<span data-ttu-id="b0883-149">`[In]`atrybut na argument</span><span class="sxs-lookup"><span data-stu-id="b0883-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="b0883-150">`inref<'T>`Zwraca</span><span class="sxs-lookup"><span data-stu-id="b0883-150">`inref<'T>` return</span></span>|<span data-ttu-id="b0883-151">`modreq`atrybut na wartości</span><span class="sxs-lookup"><span data-stu-id="b0883-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="b0883-152">`inref<'T>`w abstrakcyjnym gnieździe lub implementacji</span><span class="sxs-lookup"><span data-stu-id="b0883-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="b0883-153">`modreq`na argument lub powrót</span><span class="sxs-lookup"><span data-stu-id="b0883-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="b0883-154">Argument `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="b0883-154">`outref<'T>` argument</span></span>|<span data-ttu-id="b0883-155">`[Out]`atrybut na argument</span><span class="sxs-lookup"><span data-stu-id="b0883-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="b0883-156">Reguły wnioskowania i przeciążenia typu</span><span class="sxs-lookup"><span data-stu-id="b0883-156">Type inference and overloading rules</span></span>

<span data-ttu-id="b0883-157">Typ `inref<'T>` jest wywnioskowany przez kompilator F# w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="b0883-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="b0883-158">Parametr .NET lub typ zwracany, który ma atrybut. `IsReadOnly`</span><span class="sxs-lookup"><span data-stu-id="b0883-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="b0883-159">Wskaźnik `this` na typ struktury, który nie ma pól zmiennoskowych.</span><span class="sxs-lookup"><span data-stu-id="b0883-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="b0883-160">Adres lokalizacji pamięci pochodzące z `inref<_>` innego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="b0883-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="b0883-161">Gdy niejawny `inref` adres niejawnego jest podejmowana, `SomeType` przeciążenie z argumentem typu `inref<SomeType>`jest preferowane przeciążenia z argumentem typu .</span><span class="sxs-lookup"><span data-stu-id="b0883-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="b0883-162">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b0883-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="b0883-163">W obu przypadkach przeciążenia biorąc `System.DateTime` są rozwiązywane, `inref<System.DateTime>`a nie przeciążenia biorąc .</span><span class="sxs-lookup"><span data-stu-id="b0883-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="b0883-164">Struktury podobne do Byref</span><span class="sxs-lookup"><span data-stu-id="b0883-164">Byref-like structs</span></span>

<span data-ttu-id="b0883-165">`byref` / `outref` Oprócz / trio, można zdefiniować własne struktury, które mogą `byref`przylegać do -jak semantyka. `inref`</span><span class="sxs-lookup"><span data-stu-id="b0883-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="b0883-166">Odbywa się to <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> za pomocą atrybutu:</span><span class="sxs-lookup"><span data-stu-id="b0883-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="b0883-167">`IsByRefLike`nie oznacza `Struct`.</span><span class="sxs-lookup"><span data-stu-id="b0883-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="b0883-168">Oba muszą być obecne na typie.</span><span class="sxs-lookup"><span data-stu-id="b0883-168">Both must be present on the type.</span></span>

<span data-ttu-id="b0883-169">Struktura`byref`"-like" w języku F# jest typem wartości powiązanym ze stosem.</span><span class="sxs-lookup"><span data-stu-id="b0883-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="b0883-170">Nigdy nie jest przydzielany na zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="b0883-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="b0883-171">Struktura `byref`-like jest przydatna w programowaniu o wysokiej wydajności, ponieważ jest wymuszana z zestawem silnych kontroli dotyczących okresu istnienia i braku przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="b0883-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="b0883-172">Zasady są następujące:</span><span class="sxs-lookup"><span data-stu-id="b0883-172">The rules are:</span></span>

* <span data-ttu-id="b0883-173">Mogą być używane jako parametry funkcji, parametry metody, zmienne lokalne, zwraca metoda.</span><span class="sxs-lookup"><span data-stu-id="b0883-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="b0883-174">Nie mogą być statyczne lub wystąpienia elementów członkowskich klasy lub normalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="b0883-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="b0883-175">Nie mogą być przechwytywane`async` przez dowolną konstrukcję zamknięcia (metody lub wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="b0883-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="b0883-176">Nie można ich używać jako parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b0883-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="b0883-177">Ten ostatni punkt ma kluczowe znaczenie dla programowania `|>` w stylu potoku F#, podobnie jak funkcja ogólna, która parametryzuje jego typy danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b0883-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="b0883-178">Ograniczenie to może `|>` być złagodzone w przyszłości, ponieważ jest wbudowane i nie wykonuje żadnych wywołań do funkcji ogólnych niewbudowanych w jego treści.</span><span class="sxs-lookup"><span data-stu-id="b0883-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="b0883-179">Chociaż reguły te zdecydowanie ograniczają użycie, robią to, aby spełnić obietnicę obliczeń o wysokiej wydajności w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="b0883-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="b0883-180">Zwroty Byref</span><span class="sxs-lookup"><span data-stu-id="b0883-180">Byref returns</span></span>

<span data-ttu-id="b0883-181">Byref zwraca z funkcji F# lub elementów członkowskich mogą być produkowane i używane.</span><span class="sxs-lookup"><span data-stu-id="b0883-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="b0883-182">Podczas korzystania `byref`z -returning metody, wartość jest niejawnie wyłusk.</span><span class="sxs-lookup"><span data-stu-id="b0883-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="b0883-183">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b0883-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="b0883-184">Aby zwrócić wartość byref, zmienna, która zawiera wartość musi żyć dłużej niż bieżący zakres.</span><span class="sxs-lookup"><span data-stu-id="b0883-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="b0883-185">Ponadto, aby zwrócić byref, użyj `&value` (gdzie wartość jest zmienna, która żyje dłużej niż bieżący zakres).</span><span class="sxs-lookup"><span data-stu-id="b0883-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="b0883-186">Aby uniknąć niejawne wywanie, takie jak `&x` przekazywanie `x` odwołania za pośrednictwem wielu wywołań łańcuchowych, użyj (gdzie jest wartość).</span><span class="sxs-lookup"><span data-stu-id="b0883-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="b0883-187">Można również bezpośrednio przypisać do `byref`zwrotu .</span><span class="sxs-lookup"><span data-stu-id="b0883-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="b0883-188">Należy wziąć pod uwagę następujący (bardzo imperatyw) program:</span><span class="sxs-lookup"><span data-stu-id="b0883-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

<span data-ttu-id="b0883-189">Jest to produkt wyjściowy:</span><span class="sxs-lookup"><span data-stu-id="b0883-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="b0883-190">Zakres dla byrefs</span><span class="sxs-lookup"><span data-stu-id="b0883-190">Scoping for byrefs</span></span>

<span data-ttu-id="b0883-191">Wartość `let`-bound nie może mieć odwołania przekracza zakres, w którym została zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b0883-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="b0883-192">Na przykład nie zezwala się na następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b0883-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="b0883-193">Zapobiega to uzyskiwanie różnych wyników w zależności od tego, czy skompilować z optymalizacji, czy nie.</span><span class="sxs-lookup"><span data-stu-id="b0883-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
