---
title: Parametry i argumenty (F#)
description: 'Więcej informacji na temat Obsługa języka F # do definiowania parametrów i przekazanie argumentów do funkcji, metody i właściwości.'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037303"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="91a81-103">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="91a81-103">Parameters and Arguments</span></span>

<span data-ttu-id="91a81-104">W tym temacie opisano obsługę języka, aby Definiowanie parametrów i przekazanie argumentów do funkcji, metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="91a81-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="91a81-105">Zawiera informacje dotyczące sposobu przekazywania według odwołania i jak definiowanie i korzystanie z metod, które może potrwać zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="91a81-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="91a81-106">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="91a81-106">Parameters and Arguments</span></span>

<span data-ttu-id="91a81-107">Termin *parametru* służy do opisywania nazw dla wartości, które powinny być dostarczane.</span><span class="sxs-lookup"><span data-stu-id="91a81-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="91a81-108">Termin *argument* jest używany dla wartości podanych dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="91a81-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="91a81-109">Parametry można określić w spójnej kolekcji lub rozwinięte formularza lub kombinację dwóch.</span><span class="sxs-lookup"><span data-stu-id="91a81-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="91a81-110">Argument jest przekazywany przy użyciu nazwy parametru jawnego.</span><span class="sxs-lookup"><span data-stu-id="91a81-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="91a81-111">Parametry metod można określone jako opcjonalne i podanej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="91a81-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="91a81-112">Parametr wzorców</span><span class="sxs-lookup"><span data-stu-id="91a81-112">Parameter Patterns</span></span>

<span data-ttu-id="91a81-113">Ogólnie rzecz biorąc, parametrów przekazana do funkcji i metod są wzorce rozdzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="91a81-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="91a81-114">Oznacza to, że w zasadzie dowolnego wzorce szczegółowo [wyrażenia dopasowań](match-expressions.md) może służyć w liście parametrów dla funkcji lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="91a81-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="91a81-115">Metody zazwyczaj formularz krotki przekazywanie argumentów.</span><span class="sxs-lookup"><span data-stu-id="91a81-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="91a81-116">Uzyskuje lepszy wynik z perspektywy innych językach .NET, ponieważ w formularzu krotki pasuje do sposobu argumenty są przekazywane do metody .NET.</span><span class="sxs-lookup"><span data-stu-id="91a81-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="91a81-117">Rozwinięte formularza jest najczęściej używana przy użyciu funkcji utworzonych za pomocą `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="91a81-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="91a81-118">Poniższym pseudokodzie pokazano przykłady argumenty rozwinięte i spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="91a81-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="91a81-119">Połączone formularze są możliwe w przypadku, gdy niektóre argumenty są w spójnych kolekcjach, a niektóre nie są.</span><span class="sxs-lookup"><span data-stu-id="91a81-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="91a81-120">Inne wzorce można również listami parametrów, ale jeśli wzorzec parametr nie jest zgodna wszystkich możliwych danych wejściowych, przyczyną może być niekompletna dopasowania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="91a81-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="91a81-121">Wyjątek `MatchFailureException` jest generowany, gdy wartość argumentu jest niezgodna z wzorców określonych na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="91a81-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="91a81-122">Kompilator generuje ostrzeżenie, gdy wzorzec parametr umożliwia niekompletne dopasowania.</span><span class="sxs-lookup"><span data-stu-id="91a81-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="91a81-123">Co najmniej jedno inne wzorzec jest często przydatne w przypadku list parametrów, a to wzór symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="91a81-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="91a81-124">Używasz wzór symboli wieloznacznych na liście parametrów, gdy chcesz po prostu ignoruje wszelkie argumenty, które są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="91a81-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="91a81-125">Poniższy kod ilustruje sposób używania wzorca symbol wieloznaczny, na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="91a81-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="91a81-126">Wzór symboli wieloznacznych może być przydatne w każdym przypadku, gdy nie ma potrzeby przekazanych argumentów, na przykład główny punkt wejścia do programu, gdy nie jest konieczne w argumentach wiersza polecenia, które zwykle są dostarczane jako tablicę ciągów, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="91a81-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="91a81-127">Inne wzorce, które są czasami używane w argumentach są `as` wzorzec i wzorce identyfikatorów skojarzonych z sumy rozłączne i wzorców.</span><span class="sxs-lookup"><span data-stu-id="91a81-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="91a81-128">Można użyć wzorca złożenia dyskryminowanego pojedynczym przypadku w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="91a81-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="91a81-129">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="91a81-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="91a81-130">Wzorce aktywne może być przydatne jako parametry, na przykład, podczas transformowania argument na żądany format, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91a81-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="91a81-131">Możesz użyć `as` wzorzec do przechowywania pasującą wartość jako wartość lokalnego pokazany w następującym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="91a81-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="91a81-132">Inny wzorzec, który jest czasami używana jest funkcja, która pozostawia ostatni argument nienazwane, zapewniając jako treści funkcji, wyrażenie lambda, która natychmiast wykonuje dopasowanie wzorca niejawnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="91a81-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="91a81-133">Przykładem jest poniższy wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="91a81-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="91a81-134">Ten kod definiuje funkcję, która przyjmuje listę ogólnych i zwraca `true` Jeśli lista jest pusta, i `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="91a81-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="91a81-135">Korzystanie z takich technik może uczynić kod czytelność.</span><span class="sxs-lookup"><span data-stu-id="91a81-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="91a81-136">Od czasu do czasu wzorców, które obejmują niekompletne dopasowania są przydatne, na przykład, jeśli wiesz, że tylko trzy elementy listy w programie, mogą korzystania z wzorca podobnie do następującej listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="91a81-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="91a81-137">Użycie wzorce mające niekompletne dopasowania najlepiej jest zarezerwowana do szybkiego tworzenia prototypów i inne zastosowania tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="91a81-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="91a81-138">Kompilator zgłosi ostrzeżenie dla tego kodu.</span><span class="sxs-lookup"><span data-stu-id="91a81-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="91a81-139">Takie wzorce nie obejmują generalnie w przypadku wszystkich możliwych danych wejściowych i dlatego nie są odpowiednie dla składnika API.</span><span class="sxs-lookup"><span data-stu-id="91a81-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="91a81-140">Argumenty nazwane</span><span class="sxs-lookup"><span data-stu-id="91a81-140">Named Arguments</span></span>

<span data-ttu-id="91a81-141">Argumenty dla metod, można określić za pomocą pozycji na liście argumentów rozdzielonych przecinkami lub one mogą być przekazywane do metody jawnie, podając nazwę, w którym następuje znak równości i wartości, które mają być przekazane w.</span><span class="sxs-lookup"><span data-stu-id="91a81-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="91a81-142">Jeśli zostanie określony, podając nazwę, może znajdować się w innej kolejności z używanym w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="91a81-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="91a81-143">Argumenty nazwane może uczynić kod bardziej czytelne i bardziej potężnej niektórych typów zmian w interfejsie API, takie jak zmiany kolejności parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="91a81-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="91a81-144">Argumenty nazwane są dozwolone tylko w przypadku metod, nie dla `let`-powiązane funkcje, wartości funkcji lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="91a81-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="91a81-145">Poniższy przykład kodu demonstruje użycie argumentów nazwanych.</span><span class="sxs-lookup"><span data-stu-id="91a81-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="91a81-146">W wywołaniu konstruktora klasy można ustawić wartości właściwości klasy przy użyciu składni podobnej do nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="91a81-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="91a81-147">Poniższy przykład pokazuje tej składni.</span><span class="sxs-lookup"><span data-stu-id="91a81-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="91a81-148">Aby uzyskać więcej informacji, zobacz [Konstruktorzy (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="91a81-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="91a81-149">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="91a81-149">Optional Parameters</span></span>

<span data-ttu-id="91a81-150">Można określić opcjonalny parametr dla metody, przy użyciu znaku zapytania przed nazwą parametru.</span><span class="sxs-lookup"><span data-stu-id="91a81-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="91a81-151">Następujące parametry opcjonalne są interpretowane jako typów opcji języka F #, dzięki czemu można tworzyć zapytania je w zwykły sposób, że zapytania są typy opcji za pomocą `match` wyrażenie `Some` i `None`.</span><span class="sxs-lookup"><span data-stu-id="91a81-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="91a81-152">Następujące parametry opcjonalne są dozwolone tylko w elementach członkowskich, nie na funkcje nie powstały przy użyciu `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="91a81-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="91a81-153">Można również użyć funkcji `defaultArg`, który ustawia domyślną wartość opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="91a81-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="91a81-154">`defaultArg` Funkcja przyjmuje opcjonalny parametr jako pierwszy argument i wartość domyślną, jako drugiego.</span><span class="sxs-lookup"><span data-stu-id="91a81-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="91a81-155">Poniższy przykład ilustruje użycie parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="91a81-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="91a81-156">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="91a81-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="91a81-157">Przekazywanie poprzez odwołanie</span><span class="sxs-lookup"><span data-stu-id="91a81-157">Passing by Reference</span></span>

<span data-ttu-id="91a81-158">Przekazywanie F # wartości według odwołania polega na [zkratka](byrefs.md), które są typami wskaźnika zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="91a81-158">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="91a81-159">Wskazówki dla jakiego typu użycia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="91a81-159">Guidance for which type to use is as follows:</span></span>

* <span data-ttu-id="91a81-160">Użyj `inref<'T>` Jeśli wymagane jest tylko do odczytu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="91a81-160">Use `inref<'T>` if you only need to read the pointer.</span></span>
* <span data-ttu-id="91a81-161">Użyj `outref<'T>` Jeśli wymagane jest tylko do zapisu do wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="91a81-161">Use `outref<'T>` if you only need to write to the pointer.</span></span>
* <span data-ttu-id="91a81-162">Użyj `byref<'T>` Chcąc odczytywać i zapisywać wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="91a81-162">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

<span data-ttu-id="91a81-163">Ponieważ tego parametru jest wskaźnik, a wartość jest modyfikowalna, wszelkie zmiany wartości są zachowywane po wykonaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="91a81-163">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="91a81-164">Spójna kolekcja można użyć jako wartości zwracanej, do przechowywania wszelkich `out` parametry metody biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="91a81-164">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="91a81-165">Alternatywnie możesz traktować `out` jako parametr `byref` parametru.</span><span class="sxs-lookup"><span data-stu-id="91a81-165">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="91a81-166">Poniższy przykład kodu ilustruje obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="91a81-166">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="91a81-167">Parameter — Tablice</span><span class="sxs-lookup"><span data-stu-id="91a81-167">Parameter Arrays</span></span>

<span data-ttu-id="91a81-168">Czasami jest konieczne jest określenie funkcji, która przyjmuje dowolną liczbę parametrów typu heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="91a81-168">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="91a81-169">Nie jest praktyczne utworzyć wszystkie możliwe metody przeciążone do konta dla wszystkich typów, które mogłyby zostać użyte.</span><span class="sxs-lookup"><span data-stu-id="91a81-169">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="91a81-170">Implementacje platformy .NET zapewnia obsługę takich metod za pomocą funkcji tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="91a81-170">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="91a81-171">Z dowolnej liczby parametrów można podać metodę, która przyjmuje jeho signatura tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="91a81-171">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="91a81-172">Parametry są umieszczane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="91a81-172">The parameters are put into an array.</span></span> <span data-ttu-id="91a81-173">Określa typ elementów tablicy, typy parametrów, które mogą być przekazywane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="91a81-173">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="91a81-174">Jeśli zdefiniujesz tablicy parametrów za pomocą `System.Object` jako typ elementu następnie kod klienta można przekazać wartości dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="91a81-174">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="91a81-175">W języku F # tablice parametrów mogą można zdefiniować tylko w metodach.</span><span class="sxs-lookup"><span data-stu-id="91a81-175">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="91a81-176">Nie można ich używać w autonomicznej lub funkcji, które są definiowane w modułach.</span><span class="sxs-lookup"><span data-stu-id="91a81-176">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="91a81-177">Tablica parametrów są definiowane za pomocą `ParamArray` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="91a81-177">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="91a81-178">`ParamArray` Atrybut można stosować tylko do ostatniego parametru.</span><span class="sxs-lookup"><span data-stu-id="91a81-178">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="91a81-179">Poniższy kod ilustruje obie wywołanie metody .NET, która przyjmuje tablicy parametrów i definicji typu w F #, który ma metodę, która przyjmuje tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="91a81-179">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="91a81-180">Po uruchomieniu w projekcie, dane wyjściowe poprzedniego kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="91a81-180">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="91a81-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91a81-181">See also</span></span>

- [<span data-ttu-id="91a81-182">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="91a81-182">Members</span></span>](members/index.md)
