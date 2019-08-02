---
title: Funkcje pierwszoklasowe
description: Zapoznaj się z funkcjami pierwszej klasy i sposobem, w jaki są one ważne F#dla programowania funkcjonalnego w programie.
ms.date: 10/29/2018
ms.openlocfilehash: 4681d32abd59cc4aade6f4cb2d062e7888bcfbbc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629717"
---
# <a name="first-class-functions"></a><span data-ttu-id="d2982-103">Funkcje pierwszoklasowe</span><span class="sxs-lookup"><span data-stu-id="d2982-103">First-class functions</span></span>

<span data-ttu-id="d2982-104">Definiowanie cech charakterystycznych dla funkcjonalnego języka programowania jest podniesieniem funkcji do stanu pierwszej klasy.</span><span class="sxs-lookup"><span data-stu-id="d2982-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="d2982-105">Powinno być możliwe wykonywanie z funkcją, którą można wykonać przy użyciu wartości innych typów wbudowanych i można to zrobić przy użyciu porównywalnego stopnia nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="d2982-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="d2982-106">Typowe miary stanu pierwszej klasy są następujące:</span><span class="sxs-lookup"><span data-stu-id="d2982-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="d2982-107">Czy można powiązać funkcje z identyfikatorami?</span><span class="sxs-lookup"><span data-stu-id="d2982-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="d2982-108">Oznacza to, czy można nadać im nazwy?</span><span class="sxs-lookup"><span data-stu-id="d2982-108">That is, can you give them names?</span></span>

- <span data-ttu-id="d2982-109">Czy można przechowywać funkcje w strukturach danych, na przykład na liście?</span><span class="sxs-lookup"><span data-stu-id="d2982-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="d2982-110">Czy można przekazać funkcję jako argument w wywołaniu funkcji?</span><span class="sxs-lookup"><span data-stu-id="d2982-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="d2982-111">Czy można zwrócić funkcję z wywołania funkcji?</span><span class="sxs-lookup"><span data-stu-id="d2982-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="d2982-112">Ostatnie dwie miary definiują, co są znane jako *operacje wyższego rzędu* lub *funkcje wyższego rzędu*.</span><span class="sxs-lookup"><span data-stu-id="d2982-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="d2982-113">Funkcje wyższego rzędu akceptują funkcje jako argumenty i zwracają funkcje jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="d2982-114">Te operacje obsługują takie sztandarowych programowanie funkcjonalne jako funkcje mapowania i skład funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="d2982-115">Nadaj wartości nazwę</span><span class="sxs-lookup"><span data-stu-id="d2982-115">Give the Value a Name</span></span>

<span data-ttu-id="d2982-116">Jeśli funkcja jest wartością pierwszej klasy, należy być w stanie jej nazwać, tak jak nazwy całkowite, ciągi i inne typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="d2982-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="d2982-117">Jest to określane w temacie programowanie funkcjonalnej literatury jako powiązanie identyfikatora z wartością.</span><span class="sxs-lookup"><span data-stu-id="d2982-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="d2982-118">F#`let <identifier> = <value>` [ używa`let` powiązań](../language-reference/functions/let-bindings.md) do powiązania nazw z wartościami:.</span><span class="sxs-lookup"><span data-stu-id="d2982-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="d2982-119">Poniższy kod przedstawia dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="d2982-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="d2982-120">Funkcję można nazwać równie łatwo.</span><span class="sxs-lookup"><span data-stu-id="d2982-120">You can name a function just as easily.</span></span> <span data-ttu-id="d2982-121">W poniższym przykładzie zdefiniowano funkcję o `squareIt` nazwie przez powiązanie identyfikatora `squareIt` do [wyrażenia](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`lambda.</span><span class="sxs-lookup"><span data-stu-id="d2982-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="d2982-122">Funkcja `squareIt` ma jeden parametr, `n`i zwraca kwadrat tego parametru.</span><span class="sxs-lookup"><span data-stu-id="d2982-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="d2982-123">F#zapewnia następującą bardziej zwięzłą składnię, aby osiągnąć ten sam wynik przy mniejszej liczbie znaków.</span><span class="sxs-lookup"><span data-stu-id="d2982-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="d2982-124">Poniższe przykłady używają pierwszego stylu, `let <function-name> = <lambda-expression>`aby wyróżnić podobieństwa między deklaracją funkcji a deklaracją innych typów wartości.</span><span class="sxs-lookup"><span data-stu-id="d2982-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="d2982-125">Jednak wszystkie nazwane funkcje mogą być również zapisywane ze zwięzłą składnią.</span><span class="sxs-lookup"><span data-stu-id="d2982-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="d2982-126">Niektóre przykłady są zapisywane w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="d2982-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="d2982-127">Przechowywanie wartości w strukturze danych</span><span class="sxs-lookup"><span data-stu-id="d2982-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="d2982-128">Wartość pierwszej klasy może być przechowywana w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d2982-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="d2982-129">Poniższy kod przedstawia przykłady, które przechowują wartości z list i krotek.</span><span class="sxs-lookup"><span data-stu-id="d2982-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="d2982-130">Aby sprawdzić, czy nazwa funkcji przechowywana w spójnej kolekcji wykonuje funkcję, w poniższym przykładzie są używane `fst` operatory i `snd` do wyodrębnienia pierwszego i drugiego elementu z krotki `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="d2982-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="d2982-131">Pierwszy element w krotki to `squareIt` , a drugi element to. `num`</span><span class="sxs-lookup"><span data-stu-id="d2982-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="d2982-132">Identyfikator `num` jest powiązany w poprzednim przykładzie z liczbą całkowitą 10, prawidłowym argumentem `squareIt` dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="d2982-133">Drugie wyrażenie stosuje pierwszy element w spójnej kolekcji do drugiego elementu w spójnej kolekcji: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="d2982-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="d2982-134">Podobnie, podobnie jak identyfikatory `num` i 10 Integer mogą być używane zamiennie, więc można je identyfikatorować `squareIt` i wyrażeniu `fun n -> n * n`lambda.</span><span class="sxs-lookup"><span data-stu-id="d2982-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="d2982-135">Przekaż wartość jako argument</span><span class="sxs-lookup"><span data-stu-id="d2982-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="d2982-136">Jeśli wartość ma stan pierwszej klasy w języku, można przekazać ją jako argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="d2982-137">Na przykład często przekazywać liczby całkowite i ciągi jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="d2982-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="d2982-138">Poniższy kod przedstawia liczby całkowite i ciągi przekazane jako argumenty w F#.</span><span class="sxs-lookup"><span data-stu-id="d2982-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="d2982-139">Jeśli funkcje mają stan pierwszej klasy, musi być możliwe przekazanie ich jako argumentów w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="d2982-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="d2982-140">Należy pamiętać, że jest to pierwsza cecha funkcji wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="d2982-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="d2982-141">W poniższym przykładzie funkcja `applyIt` ma dwa `op` parametry i `arg`.</span><span class="sxs-lookup"><span data-stu-id="d2982-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="d2982-142">W przypadku wysyłania w funkcji, która ma jeden parametr dla `op` i odpowiedni argument dla `arg`funkcji, funkcja zwraca wynik zastosowania `op` do `arg`.</span><span class="sxs-lookup"><span data-stu-id="d2982-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="d2982-143">W poniższym przykładzie zarówno argument funkcji, jak i argument integer są wysyłane w taki sam sposób, przy użyciu ich nazw.</span><span class="sxs-lookup"><span data-stu-id="d2982-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="d2982-144">Możliwość wysyłania funkcji jako argumentu do innej funkcji jest zależna od powszechnych streszczeń w języku programowania funkcjonalnego, takich jak operacje map lub filtrów.</span><span class="sxs-lookup"><span data-stu-id="d2982-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="d2982-145">Operacja mapy, na przykład, to funkcja wyższego rzędu, która przechwytuje obliczenia współdzielone przez funkcje, które przekładają się na listę, zrób coś do każdego elementu, a następnie Zwróć listę wyników.</span><span class="sxs-lookup"><span data-stu-id="d2982-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="d2982-146">Możesz chcieć zwiększyć każdy element na liście liczb całkowitych lub do kwadratu każdego elementu albo zmienić każdy element na liście ciągów na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="d2982-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="d2982-147">Część obliczeń podatna na błędy to proces cykliczny, który przechodzi przez listę i tworzy listę wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d2982-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="d2982-148">Ta część jest przechwytywana w funkcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="d2982-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="d2982-149">Wszystko, co musisz napisać dla określonej aplikacji, to funkcja, która ma zostać zastosowana do każdego elementu listy pojedynczo (Dodawanie, podniesienie, zmiana wielkości liter).</span><span class="sxs-lookup"><span data-stu-id="d2982-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="d2982-150">Ta funkcja jest wysyłana jako argument do funkcji mapowania, podobnie jak `squareIt` `applyIt` w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d2982-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="d2982-151">F#oferuje metody mapy dla większości typów kolekcji, w tym [listy](../language-reference/lists.md), [tablice](../language-reference/arrays.md)i [sekwencje](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="d2982-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="d2982-152">W poniższych przykładach użyto list.</span><span class="sxs-lookup"><span data-stu-id="d2982-152">The following examples use lists.</span></span> <span data-ttu-id="d2982-153">Składnia to `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="d2982-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="d2982-154">Aby uzyskać więcej informacji, zobacz [listy](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="d2982-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="d2982-155">Zwraca wartość z wywołania funkcji</span><span class="sxs-lookup"><span data-stu-id="d2982-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="d2982-156">Na koniec, jeśli funkcja ma stan pierwszej klasy w języku, musi być w stanie zwrócić ją jako wartość wywołania funkcji, tak jak w przypadku innych typów, takich jak liczby całkowite i ciągi.</span><span class="sxs-lookup"><span data-stu-id="d2982-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="d2982-157">Następujące wywołania funkcji zwracają liczby całkowite i wyświetlają je.</span><span class="sxs-lookup"><span data-stu-id="d2982-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="d2982-158">Poniższe wywołanie funkcji zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="d2982-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="d2982-159">Następujące wywołanie funkcji, zadeklarowane wewnętrznie, zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="d2982-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="d2982-160">Wyświetlana wartość to `True`.</span><span class="sxs-lookup"><span data-stu-id="d2982-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="d2982-161">Możliwość zwrócenia funkcji jako wartość wywołania funkcji jest drugą cechą funkcji wyższej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d2982-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="d2982-162">W poniższym przykładzie `checkFor` zdefiniowano jako funkcję, która przyjmuje jeden argument, `item`i zwraca nową funkcję jako wartość.</span><span class="sxs-lookup"><span data-stu-id="d2982-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="d2982-163">Zwracana funkcja przyjmuje listę jako argument, `lst`i `item` wyszukuje w `lst`.</span><span class="sxs-lookup"><span data-stu-id="d2982-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="d2982-164">Jeśli `item` jest obecny, funkcja zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="d2982-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="d2982-165">Jeśli `item` nie jest obecny, funkcja zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="d2982-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="d2982-166">Jak w poprzedniej sekcji, poniższy kod używa udostępnionej funkcji list, [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), aby przeszukać listę.</span><span class="sxs-lookup"><span data-stu-id="d2982-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="d2982-167">Poniższy kod używa `checkFor` do tworzenia nowej funkcji, która przyjmuje jeden argument, listę i wyszukuje 7 na liście.</span><span class="sxs-lookup"><span data-stu-id="d2982-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="d2982-168">Poniższy przykład używa stanu pierwszej klasy funkcji w F# , aby zadeklarować funkcję, `compose`która zwraca skład dwóch argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> <span data-ttu-id="d2982-169">W przypadku jeszcze krótszej wersji Zobacz sekcję "funkcje rozwinięte".</span><span class="sxs-lookup"><span data-stu-id="d2982-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="d2982-170">Poniższy kod wysyła dwie funkcje jako argumenty do `compose`, z których oba przyjmują jeden argument tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="d2982-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="d2982-171">Wartość zwracana jest nową funkcją, która jest składową dwóch argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> <span data-ttu-id="d2982-172">F#zawiera dwa operatory `<<` i `>>`, które tworzą funkcje.</span><span class="sxs-lookup"><span data-stu-id="d2982-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="d2982-173">Na przykład `let squareAndDouble2 = doubleIt << squareIt` jest `let squareAndDouble = compose doubleIt squareIt` odpowiednikiem w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d2982-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="d2982-174">Poniższy przykład zwraca funkcję, ponieważ wartość wywołania funkcji tworzy prostą grę do odgadnięcia.</span><span class="sxs-lookup"><span data-stu-id="d2982-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="d2982-175">Aby utworzyć grę, zadzwoń `makeGame` do wartości, do której ktoś ma się odgadnąć. `target`</span><span class="sxs-lookup"><span data-stu-id="d2982-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="d2982-176">Wartość zwracana z funkcji `makeGame` to funkcja, która przyjmuje jeden argument (wartość przypuszczenie) i określa, czy element zgadywania jest poprawny.</span><span class="sxs-lookup"><span data-stu-id="d2982-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="d2982-177">Poniższy kod wywołuje `makeGame`, wysyłając wartość `7` dla `target`.</span><span class="sxs-lookup"><span data-stu-id="d2982-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="d2982-178">Identyfikator `playGame` jest powiązany z zwróconym wyrażeniem lambda.</span><span class="sxs-lookup"><span data-stu-id="d2982-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="d2982-179">W związku `playGame` z tym, jest funkcją, która przyjmuje jako jeden argument wartość `guess`dla.</span><span class="sxs-lookup"><span data-stu-id="d2982-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="d2982-180">Funkcje rozwinięte</span><span class="sxs-lookup"><span data-stu-id="d2982-180">Curried Functions</span></span>

<span data-ttu-id="d2982-181">Wiele przykładów w poprzedniej sekcji można napisać bardziej zwięzłie poprzez skorzystanie z niejawnych *currying* w F# deklaracjach funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="d2982-182">Currying to proces, który przekształca funkcję, która ma więcej niż jeden parametr w szereg osadzonych funkcji, z których każdy ma jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d2982-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="d2982-183">W F#programie funkcje, które mają więcej niż jeden parametr, są z natury rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="d2982-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="d2982-184">Na przykład `compose` z poprzedniej sekcji można pisać jak pokazano w następującym zwięzłym stylu z trzema parametrami.</span><span class="sxs-lookup"><span data-stu-id="d2982-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="d2982-185">Jednak wynik jest funkcją jednego parametru, która zwraca funkcję jednego parametru, który z kolei zwraca kolejną funkcję jednego parametru, jak pokazano w `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="d2982-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="d2982-186">Możesz uzyskać dostęp do tej funkcji na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="d2982-186">You can access this function in several ways.</span></span> <span data-ttu-id="d2982-187">Każdy z poniższych przykładów zwraca i wyświetla 18.</span><span class="sxs-lookup"><span data-stu-id="d2982-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="d2982-188">Możesz zamienić `compose4` `compose4curried` na w dowolnym z przykładów.</span><span class="sxs-lookup"><span data-stu-id="d2982-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="d2982-189">Aby sprawdzić, czy funkcja nadal działa tak jak wcześniej, wypróbuj ponownie oryginalne przypadki testowe.</span><span class="sxs-lookup"><span data-stu-id="d2982-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> <span data-ttu-id="d2982-190">Można ograniczyć currying przez załączanie parametrów w spójnych kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="d2982-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="d2982-191">Aby uzyskać więcej informacji, zobacz "wzorce parametrów" w [parametrach i argumentach](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d2982-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="d2982-192">Poniższy przykład używa niejawnego currying, aby napisać krótszą `makeGame`wersję programu.</span><span class="sxs-lookup"><span data-stu-id="d2982-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="d2982-193">Szczegóły dotyczące sposobu, `makeGame` w jaki konstrukcje i `game` zwraca funkcję są mniej jawne w tym formacie, ale można je zweryfikować przy użyciu oryginalnych przypadków testowych, które wynik jest taki sam.</span><span class="sxs-lookup"><span data-stu-id="d2982-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="d2982-194">Aby uzyskać więcej informacji na temat currying, zobacz "częściowe stosowanie argumentów" [](../language-reference/functions/index.md)w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="d2982-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="d2982-195">Identyfikatory i definicje funkcji są zamienne</span><span class="sxs-lookup"><span data-stu-id="d2982-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="d2982-196">Nazwa `num` zmiennej w poprzednich przykładach szacuje się na liczbę całkowitą 10 i nie jest to nieuzasadnione, gdzie `num` gdzie jest prawidłowy, 10 jest również prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d2982-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="d2982-197">To samo jest prawdziwe w przypadku identyfikatorów funkcji i ich wartości: wszędzie, gdzie można użyć nazwy funkcji, można użyć wyrażenia lambda, z którym jest powiązane.</span><span class="sxs-lookup"><span data-stu-id="d2982-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="d2982-198">Poniższy przykład definiuje `Boolean` funkcję o nazwie `isNegative`, a następnie używa nazwy funkcji i definicji funkcji zamiennie.</span><span class="sxs-lookup"><span data-stu-id="d2982-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="d2982-199">Następne trzy przykłady zwracają i wyświetlają `False`.</span><span class="sxs-lookup"><span data-stu-id="d2982-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="d2982-200">Aby zrobić to jeszcze jeden krok, Zastąp wartość `applyIt` powiązaną z dla. `applyIt`</span><span class="sxs-lookup"><span data-stu-id="d2982-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="d2982-201">Funkcje są wartościami pierwszej klasy w języku F\#</span><span class="sxs-lookup"><span data-stu-id="d2982-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="d2982-202">Przykłady w poprzednich sekcjach pokazują, że funkcje w F# programie spełniają kryteria dla wartości pierwszej klasy w F#:</span><span class="sxs-lookup"><span data-stu-id="d2982-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="d2982-203">Można powiązać identyfikator z definicją funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="d2982-204">Funkcję można przechowywać w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d2982-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="d2982-205">Funkcję można przekazać jako argument.</span><span class="sxs-lookup"><span data-stu-id="d2982-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="d2982-206">Funkcję można zwrócić jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2982-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="d2982-207">Aby uzyskać więcej informacji F#na temat, zobacz [ F# Dokumentacja języka](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2982-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2982-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2982-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="d2982-209">Opis</span><span class="sxs-lookup"><span data-stu-id="d2982-209">Description</span></span>

<span data-ttu-id="d2982-210">Poniższy kod zawiera wszystkie przykłady w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d2982-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="d2982-211">Kod</span><span class="sxs-lookup"><span data-stu-id="d2982-211">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="d2982-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2982-212">See also</span></span>

- [<span data-ttu-id="d2982-213">Listy</span><span class="sxs-lookup"><span data-stu-id="d2982-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="d2982-214">Krotki</span><span class="sxs-lookup"><span data-stu-id="d2982-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="d2982-215">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d2982-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="d2982-216">`let`Powiązań</span><span class="sxs-lookup"><span data-stu-id="d2982-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="d2982-217">Wyrażenia lambda: słowo kluczowe `fun`</span><span class="sxs-lookup"><span data-stu-id="d2982-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
