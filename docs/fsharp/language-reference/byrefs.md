---
title: Byrefs
description: Dowiedz się więcej o typach ByRef i ByRef F#, które są używane w programowaniu niskiego poziomu.
ms.date: 11/04/2019
ms.openlocfilehash: a6d3d69c4a163be9ecef7e33c284c4a73e800405
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545128"
---
# <a name="byrefs"></a><span data-ttu-id="621fc-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="621fc-103">Byrefs</span></span>

<span data-ttu-id="621fc-104">F#Program ma dwa główne obszary funkcji, które zajmują miejsce w programowaniu na niskim poziomie:</span><span class="sxs-lookup"><span data-stu-id="621fc-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="621fc-105">`byref`/`inref`/typy `outref`, które są zarządzanymi wskaźnikami.</span><span class="sxs-lookup"><span data-stu-id="621fc-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="621fc-106">Mają ograniczenia dotyczące użycia, dzięki czemu nie można skompilować programu, który jest nieprawidłowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="621fc-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="621fc-107">Struktury podobnej do `byref`, która jest [strukturą](structures.md) , która ma podobną semantykę i te same ograniczenia czasu kompilacji co `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="621fc-108">Jeden przykład jest <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="621fc-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="621fc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="621fc-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="621fc-110">ByRef, inref i outref</span><span class="sxs-lookup"><span data-stu-id="621fc-110">Byref, inref, and outref</span></span>

<span data-ttu-id="621fc-111">Istnieją trzy formy `byref`:</span><span class="sxs-lookup"><span data-stu-id="621fc-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="621fc-112">`inref<'T>`, zarządzany wskaźnik odczytu wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="621fc-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="621fc-113">`outref<'T>`, zarządzany wskaźnik zapisu do podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="621fc-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="621fc-114">`byref<'T>`, zarządzany wskaźnik służący do odczytywania i zapisywania podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="621fc-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="621fc-115">`byref<'T>` można przekazywać, gdy oczekiwany jest `inref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="621fc-116">Podobnie `byref<'T>` można przekazywać, gdy oczekiwany jest `outref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="621fc-117">Korzystanie z ByRef</span><span class="sxs-lookup"><span data-stu-id="621fc-117">Using byrefs</span></span>

<span data-ttu-id="621fc-118">Aby użyć `inref<'T>`, należy uzyskać wartość wskaźnika z `&`:</span><span class="sxs-lookup"><span data-stu-id="621fc-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="621fc-119">Aby zapisać na wskaźniku przy użyciu `outref<'T>` lub `byref<'T>`, należy również wprowadzić wartość wskaźnika do `mutable`.</span><span class="sxs-lookup"><span data-stu-id="621fc-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="621fc-120">Jeśli chcesz tylko napisać wskaźnik zamiast odczytywania go, rozważ użycie `outref<'T>` zamiast `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="621fc-121">Semantyka Inref</span><span class="sxs-lookup"><span data-stu-id="621fc-121">Inref semantics</span></span>

<span data-ttu-id="621fc-122">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="621fc-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="621fc-123">Semantycznie:</span><span class="sxs-lookup"><span data-stu-id="621fc-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="621fc-124">Posiadacz wskaźnika `x` może go użyć tylko do odczytu wartości.</span><span class="sxs-lookup"><span data-stu-id="621fc-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="621fc-125">Każdy wskaźnik uzyskany do pól `struct` zagnieżdżonych w `SomeStruct` jest podanym typem `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="621fc-126">Spełnione są również następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="621fc-126">The following is also true:</span></span>

* <span data-ttu-id="621fc-127">Nie ma żadnego znaczenia, że inne wątki lub aliasy nie mają dostępu do zapisu do `x`.</span><span class="sxs-lookup"><span data-stu-id="621fc-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="621fc-128">Nie ma żadnych implikacji, że `SomeStruct` jest niemodyfikowalny na podstawie `x` `inref`.</span><span class="sxs-lookup"><span data-stu-id="621fc-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="621fc-129">Jednakże w przypadku F# typów wartości, które **są** niezmienne, wskaźnik `this` jest wywnioskowany jako `inref`.</span><span class="sxs-lookup"><span data-stu-id="621fc-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="621fc-130">Wszystkie te reguły razem oznaczają, że posiadacz wskaźnika `inref` może nie modyfikować natychmiastowej zawartości wskazanej pamięci.</span><span class="sxs-lookup"><span data-stu-id="621fc-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="621fc-131">Semantyka Outref</span><span class="sxs-lookup"><span data-stu-id="621fc-131">Outref semantics</span></span>

<span data-ttu-id="621fc-132">Celem `outref<'T>` jest wskazanie, że na wskaźniku należy zapisywać tylko.</span><span class="sxs-lookup"><span data-stu-id="621fc-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="621fc-133">Nieoczekiwanie, `outref<'T>` umożliwia odczytywanie wartości podstawowej pomimo jej nazwy.</span><span class="sxs-lookup"><span data-stu-id="621fc-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="621fc-134">Jest to przeznaczone do celów zgodności.</span><span class="sxs-lookup"><span data-stu-id="621fc-134">This is for compatibility purposes.</span></span> <span data-ttu-id="621fc-135">Semantyka `outref<'T>` nie różni się od `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="621fc-136">Współdziałanie z\# C</span><span class="sxs-lookup"><span data-stu-id="621fc-136">Interop with C\#</span></span>

<span data-ttu-id="621fc-137">C#Program obsługuje słowa kluczowe `in ref` i `out ref`, a także zwraca `ref`.</span><span class="sxs-lookup"><span data-stu-id="621fc-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="621fc-138">W poniższej tabeli przedstawiono, F# w jaki sposób C# interpretuje emitowane przez niego emisje:</span><span class="sxs-lookup"><span data-stu-id="621fc-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="621fc-139">C#Konstruuj</span><span class="sxs-lookup"><span data-stu-id="621fc-139">C# construct</span></span>|<span data-ttu-id="621fc-140">F#wnioskuje</span><span class="sxs-lookup"><span data-stu-id="621fc-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="621fc-141">`ref` wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="621fc-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="621fc-142">`ref readonly` wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="621fc-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="621fc-143">`in ref` parametr</span><span class="sxs-lookup"><span data-stu-id="621fc-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="621fc-144">`out ref` parametr</span><span class="sxs-lookup"><span data-stu-id="621fc-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="621fc-145">W poniższej tabeli przedstawiono, F# co emituje:</span><span class="sxs-lookup"><span data-stu-id="621fc-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="621fc-146">F#Konstruuj</span><span class="sxs-lookup"><span data-stu-id="621fc-146">F# construct</span></span>|<span data-ttu-id="621fc-147">Wyemitowana konstrukcja</span><span class="sxs-lookup"><span data-stu-id="621fc-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="621fc-148">Argument `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="621fc-148">`inref<'T>` argument</span></span>|<span data-ttu-id="621fc-149">`[In]` atrybutu w argumencie</span><span class="sxs-lookup"><span data-stu-id="621fc-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="621fc-150">`inref<'T>` Zwróć</span><span class="sxs-lookup"><span data-stu-id="621fc-150">`inref<'T>` return</span></span>|<span data-ttu-id="621fc-151">`modreq` atrybutu wartości</span><span class="sxs-lookup"><span data-stu-id="621fc-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="621fc-152">`inref<'T>` w nieabstrakcyjnym gnieździe lub implementacji</span><span class="sxs-lookup"><span data-stu-id="621fc-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="621fc-153">`modreq` argumentu lub Return</span><span class="sxs-lookup"><span data-stu-id="621fc-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="621fc-154">Argument `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="621fc-154">`outref<'T>` argument</span></span>|<span data-ttu-id="621fc-155">`[Out]` atrybutu w argumencie</span><span class="sxs-lookup"><span data-stu-id="621fc-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="621fc-156">Wnioskowanie o typie i reguły przeciążania</span><span class="sxs-lookup"><span data-stu-id="621fc-156">Type inference and overloading rules</span></span>

<span data-ttu-id="621fc-157">Typ `inref<'T>` jest wywnioskowany przez F# kompilator w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="621fc-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="621fc-158">Parametr .NET lub zwracany typ, który ma atrybut `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="621fc-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="621fc-159">`this` wskaźnik na typie struktury, który nie ma modyfikowalnych pól.</span><span class="sxs-lookup"><span data-stu-id="621fc-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="621fc-160">Adres lokalizacji pamięci pochodnej od innego wskaźnika `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="621fc-161">Gdy niejawny adres `inref` jest pobierany, do przeciążenia z argumentem typu `inref<SomeType>`jest preferowane Przeciążenie z argumentem typu `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="621fc-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="621fc-162">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="621fc-162">For example:</span></span>

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

<span data-ttu-id="621fc-163">W obu przypadkach przeciążenia pobierające `System.DateTime` są rozwiązywane, a nie przeciążenia `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="621fc-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="621fc-164">Struktury podobne do ByRef</span><span class="sxs-lookup"><span data-stu-id="621fc-164">Byref-like structs</span></span>

<span data-ttu-id="621fc-165">Oprócz `byref`/`inref`/`outref` trójka można definiować własne struktury, które mogą być zgodne z semantyką przypominającą `byref`.</span><span class="sxs-lookup"><span data-stu-id="621fc-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="621fc-166">Jest to realizowane z atrybutem <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:</span><span class="sxs-lookup"><span data-stu-id="621fc-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="621fc-167">`IsByRefLike` nie implikuje `Struct`.</span><span class="sxs-lookup"><span data-stu-id="621fc-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="621fc-168">Oba muszą być obecne w typie.</span><span class="sxs-lookup"><span data-stu-id="621fc-168">Both must be present on the type.</span></span>

<span data-ttu-id="621fc-169">Struktura "`byref`like" w F# jest typem wartości związanym ze stosem.</span><span class="sxs-lookup"><span data-stu-id="621fc-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="621fc-170">Nigdy nie jest przydzielany na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="621fc-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="621fc-171">Struktura przypominająca `byref`jest przydatna w programowaniu o wysokiej wydajności, ponieważ jest wymuszana z zestawem silnych testów dotyczących czasu istnienia i braku przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="621fc-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="621fc-172">Reguły są następujące:</span><span class="sxs-lookup"><span data-stu-id="621fc-172">The rules are:</span></span>

* <span data-ttu-id="621fc-173">Mogą one być używane jako parametry funkcji, parametry metody, zmienne lokalne, Metoda Return.</span><span class="sxs-lookup"><span data-stu-id="621fc-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="621fc-174">Nie mogą być statyczne ani składowe wystąpień klasy ani normalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="621fc-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="621fc-175">Nie mogą być przechwytywane przez żadną konstrukcję zamknięcia (`async` metody lub wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="621fc-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="621fc-176">Nie mogą być używane jako parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="621fc-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="621fc-177">Ten ostatni punkt jest decydujący F# dla programowania w stylu potoku, ponieważ `|>` jest funkcją ogólną, która parameterizes jej typy wejściowe.</span><span class="sxs-lookup"><span data-stu-id="621fc-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="621fc-178">To ograniczenie może być swobodne w przypadku `|>` w przyszłości, ponieważ jest ono wbudowane i nie wykonuje żadnych wywołań funkcji ogólnych nienależących do wiersza w treści.</span><span class="sxs-lookup"><span data-stu-id="621fc-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="621fc-179">Chociaż te reguły bardzo zdecydowanie ograniczają użycie, robią to w celu zapewnienia bezpieczeństwa obliczeń o wysokiej wydajności w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="621fc-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="621fc-180">Zwracane przez ByRef</span><span class="sxs-lookup"><span data-stu-id="621fc-180">Byref returns</span></span>

<span data-ttu-id="621fc-181">Element ByRef Return F# from Functions lub memberss może być produkowany i zużywany.</span><span class="sxs-lookup"><span data-stu-id="621fc-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="621fc-182">W przypadku używania metody zwracającej `byref`, wartość jest niejawnie wykorzystana.</span><span class="sxs-lookup"><span data-stu-id="621fc-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="621fc-183">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="621fc-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="621fc-184">Aby uniknąć niejawnego odwołania, na przykład przekazywania odwołania przez wiele wywołań łańcucha, użyj `&x` (gdzie `x` jest wartością).</span><span class="sxs-lookup"><span data-stu-id="621fc-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="621fc-185">Można również bezpośrednio przypisać do `byref`zwracanego.</span><span class="sxs-lookup"><span data-stu-id="621fc-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="621fc-186">Weź pod uwagę następujący (wysoce bezwzględny) program:</span><span class="sxs-lookup"><span data-stu-id="621fc-186">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="621fc-187">Jest to produkt wyjściowy:</span><span class="sxs-lookup"><span data-stu-id="621fc-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="621fc-188">Określanie zakresu dla ByRef</span><span class="sxs-lookup"><span data-stu-id="621fc-188">Scoping for byrefs</span></span>

<span data-ttu-id="621fc-189">Wartość powiązana z `let`nie może mieć odwołania przekroczenia zakresu, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="621fc-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="621fc-190">Na przykład następujące elementy są niedozwolone:</span><span class="sxs-lookup"><span data-stu-id="621fc-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="621fc-191">Dzięki temu można uzyskać różne wyniki w zależności od tego, czy kompilacja została skompilowana z optymalizacją.</span><span class="sxs-lookup"><span data-stu-id="621fc-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
