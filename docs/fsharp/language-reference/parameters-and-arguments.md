---
title: Parametry i argumenty
description: Dowiedz się więcej o obsłudze języka języka F# do definiowania parametrów i przekazywania argumentów do funkcji, metod i właściwości.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400198"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="0587a-103">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="0587a-103">Parameters and Arguments</span></span>

<span data-ttu-id="0587a-104">W tym temacie opisano obsługę języka do definiowania parametrów i przekazywania argumentów do funkcji, metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="0587a-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="0587a-105">Zawiera informacje o tym, jak przekazać przez odwołanie i jak zdefiniować i używać metod, które mogą przyjmować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="0587a-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="0587a-106">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="0587a-106">Parameters and Arguments</span></span>

<span data-ttu-id="0587a-107">Termin *parametr* jest używany do opisania nazw wartości, które mają być dostarczone.</span><span class="sxs-lookup"><span data-stu-id="0587a-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="0587a-108">*Argument* terminu jest używany dla wartości podanych dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="0587a-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="0587a-109">Parametry mogą być określone w krotki lub curried formie lub w jakiejś kombinacji tych dwóch.</span><span class="sxs-lookup"><span data-stu-id="0587a-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="0587a-110">Argumenty można przekazać przy użyciu jawnej nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="0587a-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="0587a-111">Parametry metod można określić jako opcjonalne i podane wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="0587a-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="0587a-112">Wzorce parametrów</span><span class="sxs-lookup"><span data-stu-id="0587a-112">Parameter Patterns</span></span>

<span data-ttu-id="0587a-113">Parametry dostarczane do funkcji i metod są ogólnie wzorami oddzielonymi spacjami.</span><span class="sxs-lookup"><span data-stu-id="0587a-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="0587a-114">Oznacza to, że w zasadzie każdy z wzorców opisanych w [Dopasuj wyrażenia](match-expressions.md) może być używany na liście parametrów dla funkcji lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0587a-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="0587a-115">Metody zwykle używają krotki formularza przekazywania argumentów.</span><span class="sxs-lookup"><span data-stu-id="0587a-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="0587a-116">Osiąga to jaśniejszy wynik z punktu widzenia innych języków platformy .NET, ponieważ formularz krotki odpowiada sposób, w jaki argumenty są przekazywane w metodach .NET.</span><span class="sxs-lookup"><span data-stu-id="0587a-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="0587a-117">Curried formularz jest najczęściej używany z `let` funkcjami utworzonymi przy użyciu powiązań.</span><span class="sxs-lookup"><span data-stu-id="0587a-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="0587a-118">Poniższy pseudokod przedstawia przykłady argumentów krotki i curried.</span><span class="sxs-lookup"><span data-stu-id="0587a-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="0587a-119">Połączone formularze są możliwe, gdy niektóre argumenty są w krotek, a niektóre nie są.</span><span class="sxs-lookup"><span data-stu-id="0587a-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="0587a-120">Inne wzorce mogą być również używane na listach parametrów, ale jeśli wzorzec parametrów nie pasuje do wszystkich możliwych danych wejściowych, może istnieć niekompletne dopasowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0587a-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="0587a-121">Wyjątek `MatchFailureException` jest generowany, gdy wartość argumentu nie jest zgodna z wzorcami określonymi na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="0587a-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="0587a-122">Kompilator generuje ostrzeżenie, gdy wzorzec parametrów pozwala na niekompletne dopasowania.</span><span class="sxs-lookup"><span data-stu-id="0587a-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="0587a-123">Co najmniej jeden inny wzorzec jest często przydatne dla list parametrów i to jest wzorzec symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="0587a-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="0587a-124">Wzorzec symboli wieloznacznych jest używany na liście parametrów, jeśli chcesz po prostu zignorować wszystkie argumenty, które są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="0587a-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="0587a-125">Poniższy kod ilustruje użycie wzorca symboli wieloznacznych na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="0587a-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="0587a-126">Wzorzec symboli wieloznacznych może być przydatne, gdy nie są potrzebne argumenty przekazywane w, takich jak w głównym punkcie wejścia do programu, gdy nie są zainteresowani argumentów wiersza polecenia, które są zwykle dostarczane jako tablicy ciąg, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0587a-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="0587a-127">Inne wzorce, które są czasami `as` używane w argumentach są wzorzec i wzorce identyfikatorów skojarzone z dyskryminowanych związków i wzorców aktywnych.</span><span class="sxs-lookup"><span data-stu-id="0587a-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="0587a-128">Wzorzec unii dyskryminowanej pojedynczego przypadku można użyć w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="0587a-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="0587a-129">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0587a-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="0587a-130">Aktywne wzorce mogą być przydatne jako parametry, na przykład podczas przekształcania argumentu w żądany format, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0587a-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="0587a-131">`as` Wzorzec służy do przechowywania dopasowanej wartości jako wartości lokalnej, jak pokazano w poniższym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="0587a-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="0587a-132">Innym wzorcem, który jest używany od czasu do czasu jest funkcja, która pozostawia ostatni argument bez nazwy, zapewniając, jako treść funkcji, wyrażenie lambda, które natychmiast wykonuje dopasowanie wzorca na argument niejawny.</span><span class="sxs-lookup"><span data-stu-id="0587a-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="0587a-133">Przykładem tego jest następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="0587a-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="0587a-134">Ten kod definiuje funkcję, która przyjmuje `true` listę rodzajową i `false` zwraca, jeśli lista jest pusta i w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="0587a-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="0587a-135">Korzystanie z takich technik może utrudnić odczytanie kodu.</span><span class="sxs-lookup"><span data-stu-id="0587a-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="0587a-136">Od czasu do czasu wzorce, które obejmują niekompletne dopasowania są przydatne, na przykład, jeśli wiadomo, że listy w programie mają tylko trzy elementy, można użyć wzorca, takiego jak następujące na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="0587a-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="0587a-137">Użycie wzorców, które mają niekompletne dopasowania, najlepiej jest zarezerwowane do szybkiego tworzenia prototypów i innych zastosowań tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="0587a-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="0587a-138">Kompilator wyda ostrzeżenie dla takiego kodu.</span><span class="sxs-lookup"><span data-stu-id="0587a-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="0587a-139">Takie wzorce nie mogą obejmować ogólnego przypadku wszystkich możliwych wejść i dlatego nie są odpowiednie dla składników interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0587a-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="0587a-140">Nazwane argumenty</span><span class="sxs-lookup"><span data-stu-id="0587a-140">Named Arguments</span></span>

<span data-ttu-id="0587a-141">Argumenty dla metod można określić przez położenie na liście argumentów oddzielonych przecinkami lub mogą być przekazywane do metody jawnie, podając nazwę, po której następuje znak równości i wartość, która ma zostać przekazana.</span><span class="sxs-lookup"><span data-stu-id="0587a-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="0587a-142">Jeśli określono przez podanie nazwy, mogą one pojawić się w innej kolejności niż używane w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0587a-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="0587a-143">Nazwane argumenty mogą uczynić kod bardziej czytelnym i bardziej elastycznym do niektórych typów zmian w interfejsie API, takich jak zmiana kolejności parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="0587a-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="0587a-144">Nazwane argumenty są dozwolone tylko `let`dla metod, a nie dla funkcji powiązanych, wartości funkcji lub wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="0587a-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="0587a-145">Poniższy przykład kodu pokazuje użycie nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0587a-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="0587a-146">W wywołaniu konstruktora klas można ustawić wartości właściwości klasy przy użyciu składni podobnej do składni nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0587a-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="0587a-147">Poniższy przykład pokazuje tę składnię.</span><span class="sxs-lookup"><span data-stu-id="0587a-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="0587a-148">Aby uzyskać więcej informacji, zobacz [Konstruktory (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="0587a-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="0587a-149">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="0587a-149">Optional Parameters</span></span>

<span data-ttu-id="0587a-150">Można określić opcjonalny parametr dla metody za pomocą znaku zapytania przed nazwą parametru.</span><span class="sxs-lookup"><span data-stu-id="0587a-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="0587a-151">Parametry opcjonalne są interpretowane jako typ opcji F#, dzięki czemu można je wysyłać `match` w `Some` zwykły `None`sposób, w jaki są wyszukiwane typy opcji, za pomocą wyrażenia z i . .</span><span class="sxs-lookup"><span data-stu-id="0587a-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="0587a-152">Parametry opcjonalne są dozwolone tylko dla elementów `let` członkowskich, a nie na funkcje utworzone przy użyciu powiązań.</span><span class="sxs-lookup"><span data-stu-id="0587a-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="0587a-153">Istniejące wartości opcjonalne można przekazać do metody `?arg=None` `?arg=Some(3)` według `?arg=arg`nazwy parametru, takiej jak lub lub .</span><span class="sxs-lookup"><span data-stu-id="0587a-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="0587a-154">Może to być przydatne podczas tworzenia metody, która przekazuje opcjonalne argumenty do innej metody.</span><span class="sxs-lookup"><span data-stu-id="0587a-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="0587a-155">Można również użyć `defaultArg`funkcji , która ustawia domyślną wartość opcjonalnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="0587a-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="0587a-156">Funkcja `defaultArg` przyjmuje parametr opcjonalny jako pierwszy argument, a wartość domyślną jako drugą.</span><span class="sxs-lookup"><span data-stu-id="0587a-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="0587a-157">Poniższy przykład ilustruje użycie parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="0587a-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="0587a-158">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0587a-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="0587a-159">Na potrzeby c# i Visual Basic interop można `[<Optional; DefaultParameterValue<(...)>]` użyć atrybutów w F#, dzięki czemu wywołania zobaczą argument jako opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="0587a-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="0587a-160">Jest to równoważne zdefiniowaniu argumentu jako `MyMethod(int i = 3)`opcjonalnego w języku C# jak w .</span><span class="sxs-lookup"><span data-stu-id="0587a-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="0587a-161">Można również określić nowy obiekt jako domyślną wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="0587a-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="0587a-162">Na przykład `Foo` element członkowski `CancellationToken` może mieć opcjonalne jako dane wejściowe zamiast:</span><span class="sxs-lookup"><span data-stu-id="0587a-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="0587a-163">Wartość podana jako `DefaultParameterValue` argument musi być zgodna z typem parametru.</span><span class="sxs-lookup"><span data-stu-id="0587a-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="0587a-164">Na przykład następujące elementy nie są dozwolone:</span><span class="sxs-lookup"><span data-stu-id="0587a-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="0587a-165">W takim przypadku kompilator generuje ostrzeżenie i całkowicie zignoruje oba atrybuty.</span><span class="sxs-lookup"><span data-stu-id="0587a-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="0587a-166">Należy zauważyć, `null` że wartość domyślna musi być oznaczona jako typ, ponieważ w przeciwnym `[<Optional; DefaultParameterValue(null:obj)>] o:obj`razie kompilator wywnioskować niewłaściwy typ, tj.</span><span class="sxs-lookup"><span data-stu-id="0587a-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="0587a-167">Przekazywanie przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="0587a-167">Passing by Reference</span></span>

<span data-ttu-id="0587a-168">Przekazywanie wartości F# przez odwołanie obejmuje [byrefs](byrefs.md), które są typami wskaźników zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="0587a-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="0587a-169">Wskazówki dotyczące tego, jakiego typu należy użyć, są następujące:</span><span class="sxs-lookup"><span data-stu-id="0587a-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="0587a-170">Użyj, `inref<'T>` jeśli wystarczy tylko odczytać wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="0587a-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="0587a-171">Użyj, `outref<'T>` jeśli wystarczy tylko zapisać na wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="0587a-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="0587a-172">Użyj, `byref<'T>` jeśli chcesz zarówno odczytać i zapisać na wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="0587a-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="0587a-173">Ponieważ parametr jest wskaźnikiem, a wartość jest modyfikowalna, wszelkie zmiany wartości są zachowywane po wykonaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="0587a-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="0587a-174">Krotki można użyć jako wartości zwracanej `out` do przechowywania dowolnych parametrów w metodach biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="0587a-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="0587a-175">Alternatywnie można traktować `out` parametr jako `byref` parametr.</span><span class="sxs-lookup"><span data-stu-id="0587a-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="0587a-176">Poniższy przykład kodu ilustruje obie strony.</span><span class="sxs-lookup"><span data-stu-id="0587a-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="0587a-177">Parameter — Tablice</span><span class="sxs-lookup"><span data-stu-id="0587a-177">Parameter Arrays</span></span>

<span data-ttu-id="0587a-178">Od czasu do czasu konieczne jest zdefiniowanie funkcji, która przyjmuje dowolną liczbę parametrów typu heterogenicznego.</span><span class="sxs-lookup"><span data-stu-id="0587a-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="0587a-179">Nie byłoby praktyczne, aby utworzyć wszystkie możliwe przeciążone metody, aby uwzględnić wszystkie typy, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="0587a-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="0587a-180">Implementacje platformy .NET zapewniają obsługę takich metod za pośrednictwem funkcji tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="0587a-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="0587a-181">Metoda, która przyjmuje tablicę parametrów w podpisie, może być dostarczona z dowolną liczbą parametrów.</span><span class="sxs-lookup"><span data-stu-id="0587a-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="0587a-182">Parametry są umieszczane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0587a-182">The parameters are put into an array.</span></span> <span data-ttu-id="0587a-183">Typ elementów tablicy określa typy parametrów, które mogą być przekazywane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="0587a-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="0587a-184">Jeśli zdefiniujesz `System.Object` tablicę parametrów jako typ elementu, kod klienta może przekazać wartości dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="0587a-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="0587a-185">W języku F#tablice parametrów można zdefiniować tylko w metodach.</span><span class="sxs-lookup"><span data-stu-id="0587a-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="0587a-186">Nie można ich używać w autonomicznych funkcjach lub funkcjach zdefiniowanych w modułach.</span><span class="sxs-lookup"><span data-stu-id="0587a-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="0587a-187">Tablicę parametrów można `ParamArray` zdefiniować przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0587a-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="0587a-188">Atrybut `ParamArray` można zastosować tylko do ostatniego parametru.</span><span class="sxs-lookup"><span data-stu-id="0587a-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="0587a-189">Poniższy kod ilustruje zarówno wywołanie metody .NET, która przyjmuje tablicę parametrów, jak i definicję typu w języku F#, który ma metodę, która przyjmuje tablicę parametrów.</span><span class="sxs-lookup"><span data-stu-id="0587a-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="0587a-190">Po uruchomieniu w projekcie dane wyjściowe poprzedniego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="0587a-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="0587a-191">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0587a-191">See also</span></span>

- [<span data-ttu-id="0587a-192">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0587a-192">Members</span></span>](./members/index.md)
