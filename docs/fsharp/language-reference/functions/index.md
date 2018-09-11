---
title: Funkcje (F#)
description: 'Więcej informacji na temat funkcji w F # oraz jak F # obsługuje typowych konstrukcji programowania funkcjonalnego.'
ms.date: 05/16/2016
ms.openlocfilehash: 717eba7e69398048d229173e07ccc376797171bb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262168"
---
# <a name="functions"></a><span data-ttu-id="53c4c-103">Funkcje</span><span class="sxs-lookup"><span data-stu-id="53c4c-103">Functions</span></span>

<span data-ttu-id="53c4c-104">Funkcje są podstawową jednostką wykonywanie programu w dowolnym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="53c4c-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="53c4c-105">Tak jak w innych językach funkcja języka F # o nazwie, mogą mieć parametry i argumenty take i ma treść.</span><span class="sxs-lookup"><span data-stu-id="53c4c-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="53c4c-106">F # obsługuje również konstrukcji programowania funkcjonalnego, takich jak traktowanie funkcje jako wartości, przy użyciu funkcji bez nazwy w wyrażeniach kompozycja funkcji w celu utworzenia nowych funkcji, funkcje rozwinięte i definicję niejawną funkcji za pomocą częściowego Stosowanie argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="53c4c-107">Funkcje są definiowane za pomocą `let` — słowo kluczowe, lub, jeśli funkcja jest cykliczna, `let rec` kombinacja słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="53c4c-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="53c4c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="53c4c-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="53c4c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53c4c-109">Remarks</span></span>

<span data-ttu-id="53c4c-110">*Nazwy funkcji* jest identyfikatorem, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="53c4c-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="53c4c-111">*Listy parametrów* składa się z kolejnymi parametry, które są rozdzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="53c4c-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="53c4c-112">Można określić jawnego typu dla każdego parametru, zgodnie z opisem w sekcji parametrów.</span><span class="sxs-lookup"><span data-stu-id="53c4c-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="53c4c-113">Jeśli nie określisz typ określonego argumentu, kompilator spróbuje wywnioskować typu w treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="53c4c-114">*Treści funkcji* składa się z wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="53c4c-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="53c4c-115">Wyrażenie, które stanowi treści funkcji jest zazwyczaj wyrażeniem złożonym, składający się z liczby wyrażeń, które skutkują ostatniego wyrażenia, która jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="53c4c-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="53c4c-116">*Zwracanego typu* jest dwukropek następuje typu i jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="53c4c-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="53c4c-117">Jeśli nie zostanie jawnie typ wartości zwracanej, kompilator Określa typ zwracany z ostatniego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="53c4c-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="53c4c-118">Jest definicją prostej funkcji podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="53c4c-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="53c4c-119">W poprzednim przykładzie nazwą funkcji jest `f`, argument jest `x`, która ma typ `int`, treści funkcji jest `x + 1`, i wartość zwracana jest typu `int`.</span><span class="sxs-lookup"><span data-stu-id="53c4c-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="53c4c-120">Funkcje mogą zostać oznaczone jako `inline`.</span><span class="sxs-lookup"><span data-stu-id="53c4c-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="53c4c-121">Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="53c4c-121">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="53c4c-122">Zakres</span><span class="sxs-lookup"><span data-stu-id="53c4c-122">Scope</span></span>

<span data-ttu-id="53c4c-123">Na dowolnym poziomie zakresu innego niż zakres modułu nie jest błąd, aby ponownie użyć nazwy wartości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="53c4c-124">Ponowne użycie nazwy później zgłoszonej nazwy zasłania nazwa zadeklarowanej wcześniej.</span><span class="sxs-lookup"><span data-stu-id="53c4c-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="53c4c-125">Jednak w zakresie najwyższego poziomu w module, nazwy muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="53c4c-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="53c4c-126">Na przykład poniższy kod generuje błąd, gdy się pojawi się w zakresie modułu, ale nie w przypadku, gdy się pojawi się wewnątrz funkcji:</span><span class="sxs-lookup"><span data-stu-id="53c4c-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="53c4c-127">Ale poniższy kod jest dopuszczalne na dowolnym poziomie zakresu:</span><span class="sxs-lookup"><span data-stu-id="53c4c-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="53c4c-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="53c4c-128">Parameters</span></span>

<span data-ttu-id="53c4c-129">Nazwy parametrów są wyświetlane po nazwie funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="53c4c-130">Typ parametru, można określić, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="53c4c-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="53c4c-131">Jeśli zostanie określony, następuje nazwa parametru i jest oddzielone od nazwy dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="53c4c-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="53c4c-132">Jeżeli pominięto typu dla parametru typu parametru jest wnioskowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="53c4c-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="53c4c-133">Na przykład w poniższej definicji funkcji argument `x` jest wnioskowany typ `int` ponieważ 1 jest kolumną typu `int`.</span><span class="sxs-lookup"><span data-stu-id="53c4c-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="53c4c-134">Jednak kompilator nawiązania funkcji jako ogólny, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="53c4c-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="53c4c-135">Na przykład należy zwrócić uwagę następujący kod:</span><span class="sxs-lookup"><span data-stu-id="53c4c-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="53c4c-136">Funkcja tworzy spójną kolekcję z jednym argumentem dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="53c4c-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="53c4c-137">Ponieważ typ nie jest określony, funkcja może służyć za pomocą dowolnego typu argumentu.</span><span class="sxs-lookup"><span data-stu-id="53c4c-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="53c4c-138">Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="53c4c-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="53c4c-139">Funkcja fragmentów</span><span class="sxs-lookup"><span data-stu-id="53c4c-139">Function Bodies</span></span>

<span data-ttu-id="53c4c-140">Treść funkcji może zawierać definicje zmiennych lokalnych i funkcje.</span><span class="sxs-lookup"><span data-stu-id="53c4c-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="53c4c-141">Takie zmienne i funkcje są w zakresie treści bieżącej funkcji, ale nie poza nim.</span><span class="sxs-lookup"><span data-stu-id="53c4c-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="53c4c-142">Jeśli masz włączoną opcją uproszczone składni, należy użyć wcięcia do wskazywania definicję w treści funkcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="53c4c-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="53c4c-143">Aby uzyskać więcej informacji, zobacz [wytycznych formatowanie kodu](../code-formatting-guidelines.md) i [Pełna składnia](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="53c4c-143">For more information, see [Code Formatting Guidelines](../code-formatting-guidelines.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="53c4c-144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="53c4c-144">Return Values</span></span>

<span data-ttu-id="53c4c-145">Kompilator używa ostatniego wyrażenia w treści funkcji do określenia typu i wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="53c4c-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="53c4c-146">Kompilator może wywnioskować typ ostatniego wyrażenia z poprzednich wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="53c4c-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="53c4c-147">W funkcji `cylinderVolume`, jak pokazano w poprzedniej sekcji, a typ `pi` jest określana na podstawie typ literału `3.14159` jako `float`.</span><span class="sxs-lookup"><span data-stu-id="53c4c-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="53c4c-148">Kompilator używa typ `pi` można określić typu wyrażenia `h * pi * r * r` jako `float`.</span><span class="sxs-lookup"><span data-stu-id="53c4c-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="53c4c-149">W związku z tym, ogólną zwracany typ funkcji jest `float`.</span><span class="sxs-lookup"><span data-stu-id="53c4c-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="53c4c-150">Aby jawnie określić wartość zwracaną, pisanie kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="53c4c-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="53c4c-151">Ponieważ kod został napisany powyżej, kompilator stosuje **float** do całej funkcji; Jeśli chodziło Ci o dotyczą również typy parametrów, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="53c4c-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="53c4c-152">Wywołanie funkcji</span><span class="sxs-lookup"><span data-stu-id="53c4c-152">Calling a Function</span></span>

<span data-ttu-id="53c4c-153">Możesz wywołać funkcji, określając nazwę funkcji, następuje spacja i następnie żadnych argumentów, które są rozdzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="53c4c-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="53c4c-154">Na przykład, aby wywołać funkcję **cylinderVolume** i przypisz wynik do wartości **obj.**, należy napisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="53c4c-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="53c4c-155">Częściowe stosowanie argumentów</span><span class="sxs-lookup"><span data-stu-id="53c4c-155">Partial Application of Arguments</span></span>

<span data-ttu-id="53c4c-156">Jeśli podasz mniej niż określoną liczbę argumentów, utworzysz nową funkcję, która oczekuje, że pozostałe argumenty.</span><span class="sxs-lookup"><span data-stu-id="53c4c-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="53c4c-157">Ta metoda obsługi argumentów jest określany jako *currying* i jest to cecha funkcjonalności języków programowania, takich jak F #.</span><span class="sxs-lookup"><span data-stu-id="53c4c-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="53c4c-158">Załóżmy, że pracujesz z dwóch rozmiarach potoku: jedna z nich ma promieniu **2.0** , a druga ma promieniu **3.0**.</span><span class="sxs-lookup"><span data-stu-id="53c4c-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="53c4c-159">Można utworzyć funkcji, które określają ilość potoku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="53c4c-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="53c4c-160">Następnie będzie podać dodatkowy argument, zgodnie z potrzebami dla różnych długości potoku dwóch różnych rozmiarów:</span><span class="sxs-lookup"><span data-stu-id="53c4c-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="53c4c-161">Funkcje rekursywne</span><span class="sxs-lookup"><span data-stu-id="53c4c-161">Recursive Functions</span></span>

<span data-ttu-id="53c4c-162">*Funkcje rekursywne* funkcji, które wywołują się.</span><span class="sxs-lookup"><span data-stu-id="53c4c-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="53c4c-163">Wymagają one, że podajesz **"rec"** następujące słowa kluczowego **umożliwiają** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="53c4c-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="53c4c-164">Wywołania funkcji cykliczne w treści funkcji, tak samo, jak powodowałoby wywołanie każde wywołanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="53c4c-165">Oblicza następujących funkcji recursive *n*<sup>th</sup> Fibonacci numer.</span><span class="sxs-lookup"><span data-stu-id="53c4c-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="53c4c-166">Sekwencja numer Fibonacci wiadomo, że od momentu antyków i sekwencja, w którym każdy kolejny numer to suma poprzednich dwóch liczb w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="53c4c-167">Niektóre funkcje rekursywne może przepełnienie stosu program lub wykonać nieefektywnie, jeśli nie napiszesz ich ostrożnie i z świadomości technik specjalnych, takich jak użycie akumulatory i kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="53c4c-168">Wartości funkcji</span><span class="sxs-lookup"><span data-stu-id="53c4c-168">Function Values</span></span>

<span data-ttu-id="53c4c-169">W języku F # wszystkie funkcje są traktowane jako wartości. w rzeczywistości są one znane jako *funkcji wartości*.</span><span class="sxs-lookup"><span data-stu-id="53c4c-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="53c4c-170">Ponieważ funkcje są wartościami, ich może służyć jako argumenty do innych funkcji lub w innych kontekstach których wartości są używane.</span><span class="sxs-lookup"><span data-stu-id="53c4c-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="53c4c-171">Poniżej znajduje się przykład funkcji, która przyjmuje wartość funkcji jako argumentem:</span><span class="sxs-lookup"><span data-stu-id="53c4c-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="53c4c-172">Należy określić typ wartości funkcji za pomocą `->` tokenu.</span><span class="sxs-lookup"><span data-stu-id="53c4c-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="53c4c-173">Po lewej stronie token ten jest typem argumentu, a po prawej stronie jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="53c4c-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="53c4c-174">W poprzednim przykładzie `apply1` jest funkcją, która przyjmuje funkcję `transform` jako argument, gdzie `transform` jest funkcją, która przyjmuje liczbę całkowitą i zwraca inną liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="53c4c-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="53c4c-175">Poniższy kod przedstawia sposób użycia `apply1`:</span><span class="sxs-lookup"><span data-stu-id="53c4c-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="53c4c-176">Wartość `result` będzie 101 po uruchomieniu poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="53c4c-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="53c4c-177">Wiele argumentów są rozdzielone przez kolejne `->` tokenów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="53c4c-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="53c4c-178">Wynik to 200.</span><span class="sxs-lookup"><span data-stu-id="53c4c-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="53c4c-179">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="53c4c-179">Lambda Expressions</span></span>

<span data-ttu-id="53c4c-180">A *wyrażenia lambda* jest funkcją bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="53c4c-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="53c4c-181">W poprzednich przykładach, zamiast definiować nazwane funkcje **przyrostu** i **mul**, można użyć wyrażenia lambda w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="53c4c-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="53c4c-182">Wyrażenia lambda są definiowane za pomocą `fun` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="53c4c-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="53c4c-183">Wyrażenia lambda przypomina definicji funkcji, chyba że zamiast `=` tokenu, `->` token jest używany do oddzielania na liście argumentów od treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="53c4c-184">Tak jak w definicji funkcji regularnych typy argumentów można wywnioskować lub jawnie określony, a zwracany typ wyrażenia lambda jest wnioskowany z typu ostatniego wyrażenia w treści.</span><span class="sxs-lookup"><span data-stu-id="53c4c-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="53c4c-185">Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda: `fun` — słowo kluczowe](../functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="53c4c-185">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="53c4c-186">Kompozycja funkcji i przetwarzanie potokowe</span><span class="sxs-lookup"><span data-stu-id="53c4c-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="53c4c-187">Funkcje w języku F # może składać się z innych funkcji.</span><span class="sxs-lookup"><span data-stu-id="53c4c-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="53c4c-188">Kompozycja dwie funkcje **function1** i **function2** jest inną funkcję, która reprezentuje stosowania **function1** po zastosowaniu **function2**:</span><span class="sxs-lookup"><span data-stu-id="53c4c-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="53c4c-189">Wynik jest 202.</span><span class="sxs-lookup"><span data-stu-id="53c4c-189">The result is 202.</span></span>

<span data-ttu-id="53c4c-190">Przetwarzanie potokowe umożliwia wywołania funkcji zostaną połączone jako kolejne czynności.</span><span class="sxs-lookup"><span data-stu-id="53c4c-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="53c4c-191">Przetwarzanie potokowe działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="53c4c-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="53c4c-192">Wynik jest ponownie 202.</span><span class="sxs-lookup"><span data-stu-id="53c4c-192">The result is again 202.</span></span>

<span data-ttu-id="53c4c-193">Operatory kompozycji mają dwie funkcje i zwrócić funkcję; z kolei operatorów potoku funkcji i argument i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="53c4c-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="53c4c-194">Poniższy przykład kodu pokazuje różnicę między operatorów potoku i kompozycji, pokazując różnice w sygnatur funkcji i użycia.</span><span class="sxs-lookup"><span data-stu-id="53c4c-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="53c4c-195">Przeładowywanie funkcji</span><span class="sxs-lookup"><span data-stu-id="53c4c-195">Overloading Functions</span></span>

<span data-ttu-id="53c4c-196">Możesz doprowadzić do przeciążenia metody typu, ale nie działa.</span><span class="sxs-lookup"><span data-stu-id="53c4c-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="53c4c-197">Aby uzyskać więcej informacji, zobacz [metody](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="53c4c-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53c4c-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53c4c-198">See also</span></span>

- [<span data-ttu-id="53c4c-199">Wartości</span><span class="sxs-lookup"><span data-stu-id="53c4c-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="53c4c-200">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="53c4c-200">F# Language Reference</span></span>](../index.md)
