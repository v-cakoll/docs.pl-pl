---
title: 'Zkratka (F #)'
description: 'Więcej informacji na temat byref i byref typy w języku F #, które są używane na potrzeby programowania niskiego poziomu.'
ms.date: 09/02/2018
ms.openlocfilehash: 6131104e4325f77da84368c337f998c6b2b5309b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836884"
---
# <a name="byrefs"></a><span data-ttu-id="86c49-103">Zkratka</span><span class="sxs-lookup"><span data-stu-id="86c49-103">Byrefs</span></span>

<span data-ttu-id="86c49-104">F # zawiera dwa obszary najważniejszych funkcji, które zajmują w obszarze programowania niskiego poziomu:</span><span class="sxs-lookup"><span data-stu-id="86c49-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="86c49-105">`byref` / `inref` / `outref` Typów, które są wskaźnikami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="86c49-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="86c49-106">Mają one ograniczenia dotyczące użycia, więc, że nie można skompilować program, który jest nieprawidłowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86c49-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="86c49-107">A `byref`— takie jak struktury, która jest [struktury](structures.md) ma podobną semantyką i takim samym ograniczeniom kompilacji, jak `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="86c49-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="86c49-108">Przykładem jest <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="86c49-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="86c49-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="86c49-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="86c49-110">ByRef, inref i outref</span><span class="sxs-lookup"><span data-stu-id="86c49-110">Byref, inref, and outref</span></span>

<span data-ttu-id="86c49-111">Istnieją trzy rodzaje `byref`:</span><span class="sxs-lookup"><span data-stu-id="86c49-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="86c49-112">`inref<'T>`, wskaźnika zarządzanych do odczytywania wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="86c49-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="86c49-113">`outref<'T>`, wskaźnika zarządzanych do zapisywania wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="86c49-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="86c49-114">`byref<'T>`, wskaźnika zarządzanych do odczytywania i zapisywania podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="86c49-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="86c49-115">A `byref<'T>` mogą być przekazywane w przypadku gdy `inref<'T>` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="86c49-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="86c49-116">Podobnie `byref<'T>` mogą być przekazywane w przypadku gdy `outref<'T>` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="86c49-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="86c49-117">Za pomocą zkratka</span><span class="sxs-lookup"><span data-stu-id="86c49-117">Using byrefs</span></span>

<span data-ttu-id="86c49-118">Aby użyć `inref<'T>`, należy uzyskać wartość wskaźnika z `&`:</span><span class="sxs-lookup"><span data-stu-id="86c49-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let dt = DateTime.Now
f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="86c49-119">Można zapisać do wskaźnika za pomocą `outref<'T>` lub `byref<'T>`, należy również upewnić wartość, Pobierz wskaźnik do `mutable`.</span><span class="sxs-lookup"><span data-stu-id="86c49-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="86c49-120">Jeśli piszesz wskaźnika zamiast wczytaniem go, należy wziąć pod uwagę przy użyciu `outref<'T>` zamiast `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="86c49-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="86c49-121">Semantyka Inref</span><span class="sxs-lookup"><span data-stu-id="86c49-121">Inref semantics</span></span>

<span data-ttu-id="86c49-122">Rozważmy poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="86c49-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = s.SomeField
```

<span data-ttu-id="86c49-123">Semantycznie oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="86c49-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="86c49-124">Posiadacz `x` wskaźnika można używać go tylko odczytać wartości.</span><span class="sxs-lookup"><span data-stu-id="86c49-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="86c49-125">Dowolny wskaźnik uzyskanych do `struct` pola zagnieżdżone w obrębie `SomeStruct` podano typ `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="86c49-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="86c49-126">Oto również wartość true:</span><span class="sxs-lookup"><span data-stu-id="86c49-126">The following is also true:</span></span>

* <span data-ttu-id="86c49-127">Istnieje nie domniemanie na to, że inne wątki, lub aliasy nie ma dostęp do zapisu `x`.</span><span class="sxs-lookup"><span data-stu-id="86c49-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="86c49-128">Nie ma żadnych domniemanie, `SomeStruct` można modyfikować na mocy niniejszej `x` trwa `inref`.</span><span class="sxs-lookup"><span data-stu-id="86c49-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="86c49-129">Jednak dla języka F # wartości typów, które **są** niemodyfikowalny `this` wskaźnik wywnioskowana jest `inref`.</span><span class="sxs-lookup"><span data-stu-id="86c49-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="86c49-130">Wszystkie te reguły, które są razem oznaczają, że właściciel `inref` wskaźnik nie może modyfikować natychmiastowego zawartość pamięci wskazywany.</span><span class="sxs-lookup"><span data-stu-id="86c49-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="86c49-131">Semantyka Outref</span><span class="sxs-lookup"><span data-stu-id="86c49-131">Outref semantics</span></span>

<span data-ttu-id="86c49-132">Celem `outref<'T>` jest, aby wskazać, że wskaźnik powinni czytać tylko z.</span><span class="sxs-lookup"><span data-stu-id="86c49-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="86c49-133">Nieoczekiwanie `outref<'T>` zezwolenia na odczytywanie podstawowych wartości niezależnie od jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="86c49-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="86c49-134">Jest to na potrzeby zgodności.</span><span class="sxs-lookup"><span data-stu-id="86c49-134">This is for compatibility purposes.</span></span> <span data-ttu-id="86c49-135">Semantycznie `outref<'T>` nie różni się od `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="86c49-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="86c49-136">Współdziałanie z języka C#</span><span class="sxs-lookup"><span data-stu-id="86c49-136">Interop with C#</span></span> #

<span data-ttu-id="86c49-137">C# obsługuje `in ref` i `out ref` słów kluczowych, oprócz `ref` zwraca.</span><span class="sxs-lookup"><span data-stu-id="86c49-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="86c49-138">W poniższej tabeli przedstawiono, jak F # interpretuje co C# emituje:</span><span class="sxs-lookup"><span data-stu-id="86c49-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="86c49-139">Konstrukcja w języku C#</span><span class="sxs-lookup"><span data-stu-id="86c49-139">C# construct</span></span>|<span data-ttu-id="86c49-140">Wnioskuje F #</span><span class="sxs-lookup"><span data-stu-id="86c49-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="86c49-141">`ref` Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="86c49-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="86c49-142">`ref readonly` Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="86c49-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="86c49-143">`in ref` Parametr</span><span class="sxs-lookup"><span data-stu-id="86c49-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="86c49-144">`out ref` Parametr</span><span class="sxs-lookup"><span data-stu-id="86c49-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="86c49-145">W poniższej tabeli przedstawiono, jakie F # emituje:</span><span class="sxs-lookup"><span data-stu-id="86c49-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="86c49-146">Konstrukcji F #</span><span class="sxs-lookup"><span data-stu-id="86c49-146">F# construct</span></span>|<span data-ttu-id="86c49-147">Konstrukcja emitowany</span><span class="sxs-lookup"><span data-stu-id="86c49-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="86c49-148">`inref<'T>` Argument</span><span class="sxs-lookup"><span data-stu-id="86c49-148">`inref<'T>` argument</span></span>|<span data-ttu-id="86c49-149">`[In]` argument atrybutu</span><span class="sxs-lookup"><span data-stu-id="86c49-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="86c49-150">`inref<'T>` Wróć</span><span class="sxs-lookup"><span data-stu-id="86c49-150">`inref<'T>` return</span></span>|<span data-ttu-id="86c49-151">`modreq` atrybut na wartość</span><span class="sxs-lookup"><span data-stu-id="86c49-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="86c49-152">`inref<'T>` w abstrakcyjny gniazdo lub wdrożenia</span><span class="sxs-lookup"><span data-stu-id="86c49-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="86c49-153">`modreq` argument lub zwracany</span><span class="sxs-lookup"><span data-stu-id="86c49-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="86c49-154">`outref<'T>` Argument</span><span class="sxs-lookup"><span data-stu-id="86c49-154">`outref<'T>` argument</span></span>|<span data-ttu-id="86c49-155">`[Out]` argument atrybutu</span><span class="sxs-lookup"><span data-stu-id="86c49-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="86c49-156">Wnioskowanie o typie i przeciążenie reguły</span><span class="sxs-lookup"><span data-stu-id="86c49-156">Type inference and overloading rules</span></span>

<span data-ttu-id="86c49-157">`inref<'T>` Typ jest wnioskowany przez kompilator F # w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="86c49-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="86c49-158">.NET parametr lub zwracany typ, który ma `IsReadOnly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="86c49-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="86c49-159">`this` Wskaźnika na typie struct, który nie ma tych pól.</span><span class="sxs-lookup"><span data-stu-id="86c49-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="86c49-160">Adres lokalizacji pamięci pochodzi z innego `inref<_>` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="86c49-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="86c49-161">Gdy niejawne adres `inref` jest przełączana, przeciążenia z nieprawidłowym argumentem typu `SomeType` jest preferowany do przeciążenia z nieprawidłowym argumentem typu `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="86c49-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="86c49-162">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86c49-162">For example:</span></span>

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

<span data-ttu-id="86c49-163">W obu przypadkach przeciążenia, biorąc `System.DateTime` są rozwiązywane zamiast przeciążenia, biorąc `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="86c49-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="86c49-164">ByRef — podobne do struktury</span><span class="sxs-lookup"><span data-stu-id="86c49-164">Byref-like structs</span></span>

<span data-ttu-id="86c49-165">Oprócz `byref` / `inref` / `outref` Trójka, można zdefiniować własne struktur, które można stosować się do `byref`— takich jak semantyki.</span><span class="sxs-lookup"><span data-stu-id="86c49-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="86c49-166">Jest to zrobić za pomocą <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atrybutu:</span><span class="sxs-lookup"><span data-stu-id="86c49-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="86c49-167">`IsByRefLike` nie oznacza `Struct`.</span><span class="sxs-lookup"><span data-stu-id="86c49-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="86c49-168">Zarówno musi być obecny w typie.</span><span class="sxs-lookup"><span data-stu-id="86c49-168">Both must be present on the type.</span></span>

<span data-ttu-id="86c49-169">Element "`byref`— takich jak" struct w języku F # to typ wartości powiązanym ze stosu.</span><span class="sxs-lookup"><span data-stu-id="86c49-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="86c49-170">Nigdy nie zostanie przydzielona na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="86c49-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="86c49-171">A `byref`— takie jak struktura jest przydatne w przypadku programowania o wysokiej wydajności, jak są wymuszane za pomocą zestawu silne testów o okresie istnienia i -capture.</span><span class="sxs-lookup"><span data-stu-id="86c49-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="86c49-172">Dostępne są następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="86c49-172">The rules are:</span></span>

* <span data-ttu-id="86c49-173">One może służyć jako parametry funkcji, parametrów metody, zmienne lokalne, metoda zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="86c49-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="86c49-174">Nie mogą one być statyczne lub wystąpieniami elementów członkowskich klasy lub struktury normalne.</span><span class="sxs-lookup"><span data-stu-id="86c49-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="86c49-175">Nie można przechwycić według konstrukcji zamknięcia (`async` metod lub wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="86c49-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="86c49-176">Nie mogą one służyć jako parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="86c49-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="86c49-177">Ten ostatni punkt ma kluczowe znaczenie dla F # potoku programowaniu w stylu jako `|>` jest funkcja ogólna, które parametryzuje dane jego typów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="86c49-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="86c49-178">To ograniczenie może zostać złagodzone dla `|>` w przyszłości, ponieważ jest wbudowana i nie wprowadzać wszelkie wywołania-śródwierszowych ogólne funkcje w jej treści.</span><span class="sxs-lookup"><span data-stu-id="86c49-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="86c49-179">Mimo że te reguły ograniczają bardzo silnie użycia, to zrobią do spełnienia obietnicy o wysokiej wydajności obliczeniowej w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="86c49-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="86c49-180">Wartości zwracane ByRef</span><span class="sxs-lookup"><span data-stu-id="86c49-180">Byref returns</span></span>

<span data-ttu-id="86c49-181">Wartości zwracane ByRef z F # funkcji lub elementów członkowskich może być tworzone i używane.</span><span class="sxs-lookup"><span data-stu-id="86c49-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="86c49-182">Podczas używania `byref`— metodę zwracającą, wartość jest wyłuskiwany niejawnie.</span><span class="sxs-lookup"><span data-stu-id="86c49-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="86c49-183">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86c49-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="86c49-184">Aby uniknąć niejawne wyłuskania, takich jak przekazywaniem odwołań do wielu wywołań łańcuchowych, należy użyć `&x` (gdzie `x` jest wartością).</span><span class="sxs-lookup"><span data-stu-id="86c49-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="86c49-185">Możesz także bezpośrednio przypisać do zwrotu `byref`.</span><span class="sxs-lookup"><span data-stu-id="86c49-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="86c49-186">Należy wziąć pod uwagę następujący program (wysoce imperatywne):</span><span class="sxs-lookup"><span data-stu-id="86c49-186">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
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

<span data-ttu-id="86c49-187">Jest to produkt wyjściowy:</span><span class="sxs-lookup"><span data-stu-id="86c49-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="86c49-188">Wyznaczanie zakresu dla zkratka</span><span class="sxs-lookup"><span data-stu-id="86c49-188">Scoping for byrefs</span></span>

<span data-ttu-id="86c49-189">A `let`— powiązana wartość nie może zawierać odwołanie, przekracza zakres, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="86c49-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="86c49-190">Na przykład że jest niedozwolone:</span><span class="sxs-lookup"><span data-stu-id="86c49-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="86c49-191">Uniemożliwia to wprowadzenie różne wyniki w zależności od tego, jeśli kompilujesz z optymalizacjami lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="86c49-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
