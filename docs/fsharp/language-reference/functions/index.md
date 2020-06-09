---
title: Funkcje
description: 'Dowiedz się więcej o funkcjach w języku F # oraz sposobie, w jaki język F # obsługuje typowe konstrukcje programowania funkcjonalnego.'
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596477"
---
# <a name="functions"></a><span data-ttu-id="d68fd-103">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d68fd-103">Functions</span></span>

<span data-ttu-id="d68fd-104">Funkcje są podstawową jednostką wykonywania programu w dowolnym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="d68fd-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="d68fd-105">Podobnie jak w innych językach, funkcja języka F # ma nazwę, może mieć parametry i przyjmować argumenty i ma treść.</span><span class="sxs-lookup"><span data-stu-id="d68fd-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="d68fd-106">Język F # obsługuje również konstrukcje programowania funkcjonalnego, takie jak traktowanie funkcji jako wartości, za pomocą funkcji nienazwanych w wyrażeniach, skład funkcji do tworzenia nowych funkcji, funkcji rozwinięte i niejawnej definicji funkcji w ramach częściowego zastosowania argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="d68fd-107">Można definiować funkcje za pomocą `let` słowa kluczowego lub, jeśli funkcja jest cykliczna, `let rec` kombinacja słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="d68fd-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="d68fd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d68fd-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="d68fd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d68fd-109">Remarks</span></span>

<span data-ttu-id="d68fd-110">*Nazwa funkcji* jest identyfikatorem, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="d68fd-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="d68fd-111">*Lista parametrów* składa się z kolejnych parametrów, które są rozdzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="d68fd-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="d68fd-112">Można określić typ jawny dla każdego parametru, zgodnie z opisem w sekcji parametry.</span><span class="sxs-lookup"><span data-stu-id="d68fd-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="d68fd-113">Jeśli nie określisz określonego typu argumentu, kompilator próbuje wywnioskować typ z treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="d68fd-114">*Treść funkcji* składa się z wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d68fd-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="d68fd-115">Wyrażenie, które składa się z treści funkcji jest zwykle wyrażeniem złożonym składającym się z szeregu wyrażeń, które skutkują w ostatecznym wyrażeniu, które jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="d68fd-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="d68fd-116">*Typ zwracany* jest dwukropek, po którym następuje typ i jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d68fd-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="d68fd-117">Jeśli nie określisz jawnie typu wartości zwracanej, kompilator określi typ zwracany z wyrażenia końcowego.</span><span class="sxs-lookup"><span data-stu-id="d68fd-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="d68fd-118">Prosta definicja funkcji jest podobna do następującej:</span><span class="sxs-lookup"><span data-stu-id="d68fd-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="d68fd-119">W poprzednim przykładzie nazwa funkcji to `f` , argument ma `x` Typ, `int` treść funkcji jest `x + 1` , a zwracana wartość jest typu `int` .</span><span class="sxs-lookup"><span data-stu-id="d68fd-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="d68fd-120">Funkcje mogą być oznaczone `inline` .</span><span class="sxs-lookup"><span data-stu-id="d68fd-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="d68fd-121">Aby uzyskać informacje na temat `inline` , zobacz [funkcje wbudowane](inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d68fd-121">For information about `inline`, see [Inline Functions](inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="d68fd-122">Zakres</span><span class="sxs-lookup"><span data-stu-id="d68fd-122">Scope</span></span>

<span data-ttu-id="d68fd-123">Na dowolnym poziomie zakresu innym niż zakres modułu nie jest to błąd, aby ponownie użyć wartości lub nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="d68fd-124">Jeśli ponownie używasz nazwy, nazwa zadeklarowana w dalszej części zaciemnienia nazwy zadeklarowanej wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d68fd-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="d68fd-125">Jednak w zakresie najwyższego poziomu w module nazwy muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="d68fd-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="d68fd-126">Na przykład poniższy kod generuje błąd, gdy pojawia się on w zakresie modułu, ale nie gdy pojawia się wewnątrz funkcji:</span><span class="sxs-lookup"><span data-stu-id="d68fd-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="d68fd-127">Jednak następujący kod jest akceptowalny na dowolnym poziomie zakresu:</span><span class="sxs-lookup"><span data-stu-id="d68fd-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="d68fd-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="d68fd-128">Parameters</span></span>

<span data-ttu-id="d68fd-129">Nazwy parametrów są wyświetlane po nazwie funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="d68fd-130">Możesz określić typ dla parametru, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d68fd-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="d68fd-131">Jeśli określisz typ, następuje jego nazwa i jest oddzielona od nazwy średnikami.</span><span class="sxs-lookup"><span data-stu-id="d68fd-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="d68fd-132">W przypadku pominięcia typu parametru typ parametru zostanie wywnioskowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d68fd-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="d68fd-133">Na przykład w poniższej definicji funkcji argument `x` jest wywnioskowany jako typ, `int` ponieważ 1 jest typu `int` .</span><span class="sxs-lookup"><span data-stu-id="d68fd-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="d68fd-134">Jednak kompilator podejmie próbę przeprowadzenia funkcji jako ogólnej, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d68fd-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="d68fd-135">Na przykład Zwróć uwagę na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d68fd-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="d68fd-136">Funkcja tworzy krotkę z jednego argumentu dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="d68fd-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="d68fd-137">Ponieważ typ nie jest określony, funkcja może być używana z dowolnym typem argumentu.</span><span class="sxs-lookup"><span data-stu-id="d68fd-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="d68fd-138">Aby uzyskać więcej informacji, zobacz [Automatyczne uogólnianie](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="d68fd-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="d68fd-139">Funkcja fragmentów</span><span class="sxs-lookup"><span data-stu-id="d68fd-139">Function Bodies</span></span>

<span data-ttu-id="d68fd-140">Treść funkcji może zawierać definicje zmiennych lokalnych i funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="d68fd-141">Takie zmienne i funkcje są w zakresie treści bieżącej funkcji, ale nie poza nią.</span><span class="sxs-lookup"><span data-stu-id="d68fd-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="d68fd-142">Po włączeniu opcji składnia uproszczona należy użyć wcięcia, aby wskazać, że definicja znajduje się w treści funkcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d68fd-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="d68fd-143">Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące formatowania kodu](../../style-guide/formatting.md) i [Pełna składnia](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="d68fd-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="d68fd-144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d68fd-144">Return Values</span></span>

<span data-ttu-id="d68fd-145">Kompilator używa końcowego wyrażenia w treści funkcji, aby określić wartość zwracaną i typ.</span><span class="sxs-lookup"><span data-stu-id="d68fd-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="d68fd-146">Kompilator może wywnioskować typ wyrażenia końcowego z poprzednich wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d68fd-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="d68fd-147">W funkcji `cylinderVolume` pokazanej w poprzedniej sekcji Typ `pi` jest określany na podstawie typu literału, `3.14159` który ma być `float` .</span><span class="sxs-lookup"><span data-stu-id="d68fd-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="d68fd-148">Kompilator używa typu, `pi` Aby określić typ wyrażenia, `h * pi * r * r` które ma być `float` .</span><span class="sxs-lookup"><span data-stu-id="d68fd-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="d68fd-149">W związku z tym, całkowity typ zwracany funkcji to `float` .</span><span class="sxs-lookup"><span data-stu-id="d68fd-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="d68fd-150">Aby jawnie określić wartość zwracaną, napisz kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d68fd-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="d68fd-151">Ponieważ kod jest pisany powyżej, kompilator stosuje **zmiennoprzecinkowe** do całej funkcji; Jeśli zamierzasz zastosować ją również do typów parametrów, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="d68fd-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="d68fd-152">Wywołanie funkcji</span><span class="sxs-lookup"><span data-stu-id="d68fd-152">Calling a Function</span></span>

<span data-ttu-id="d68fd-153">Możesz wywoływać funkcje, określając nazwę funkcji, a następnie spację, a następnie wszelkie argumenty oddzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="d68fd-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="d68fd-154">Na przykład, aby wywołać funkcję **cylinderVolume** i przypisać wynik do wartości **vol**, Napisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d68fd-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="d68fd-155">Częściowe stosowanie argumentów</span><span class="sxs-lookup"><span data-stu-id="d68fd-155">Partial Application of Arguments</span></span>

<span data-ttu-id="d68fd-156">Jeśli podasz mniej niż określoną liczbę argumentów, utworzysz nową funkcję, która oczekuje pozostałych argumentów.</span><span class="sxs-lookup"><span data-stu-id="d68fd-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="d68fd-157">Ta metoda obsługi argumentów jest określana jako *currying* i jest cechą języków programowania funkcjonalnego, takich jak F #.</span><span class="sxs-lookup"><span data-stu-id="d68fd-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="d68fd-158">Załóżmy na przykład, że pracujesz z dwoma rozmiarami potoku: jeden ma promień **2,0** , a drugi ma promień **3,0**.</span><span class="sxs-lookup"><span data-stu-id="d68fd-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="d68fd-159">Można utworzyć funkcje, które określają ilość potoku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d68fd-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="d68fd-160">Następnie należy podać dodatkowy argument w miarę potrzeby dla różnych długości potoku dwóch różnych rozmiarów:</span><span class="sxs-lookup"><span data-stu-id="d68fd-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="d68fd-161">Funkcje rekursywne</span><span class="sxs-lookup"><span data-stu-id="d68fd-161">Recursive Functions</span></span>

<span data-ttu-id="d68fd-162">*Funkcje cykliczne* to funkcje, które wywołują siebie.</span><span class="sxs-lookup"><span data-stu-id="d68fd-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="d68fd-163">Wymagają one określenia słowa kluczowego **Rec** po słowie kluczowym **Let** .</span><span class="sxs-lookup"><span data-stu-id="d68fd-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="d68fd-164">Wywołaj funkcję cykliczną z poziomu treści funkcji tak samo jak w przypadku wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="d68fd-165">Następująca funkcja cykliczna oblicza n- *n*<sup>ty</sup> numer Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="d68fd-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="d68fd-166">Sekwencja numerów Fibonacci była znana od czasu zamknięcia i jest sekwencją, w której każdy kolejny numer jest sumą poprzednich dwóch numerów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="d68fd-167">Niektóre funkcje cykliczne mogą przepełniać stosy programu lub działać niewydajnie, jeśli nie napiszesz ich z opieką i z świadomością technik specjalnych, takich jak korzystanie z akumulatorów i kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="d68fd-168">Wartości funkcji</span><span class="sxs-lookup"><span data-stu-id="d68fd-168">Function Values</span></span>

<span data-ttu-id="d68fd-169">W języku F # wszystkie funkcje są uznawane za wartości; w rzeczywistości są one nazywane *wartościami funkcji*.</span><span class="sxs-lookup"><span data-stu-id="d68fd-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="d68fd-170">Ponieważ funkcje są wartościami, mogą one być używane jako argumenty do innych funkcji lub w innych kontekstach, w których są używane wartości.</span><span class="sxs-lookup"><span data-stu-id="d68fd-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="d68fd-171">Poniżej znajduje się przykład funkcji, która przyjmuje wartość funkcji jako argument:</span><span class="sxs-lookup"><span data-stu-id="d68fd-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="d68fd-172">Należy określić typ wartości funkcji za pomocą `->` tokenu.</span><span class="sxs-lookup"><span data-stu-id="d68fd-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="d68fd-173">Po lewej stronie tego tokenu jest typem argumentu, a po prawej stronie jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="d68fd-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="d68fd-174">W poprzednim przykładzie `apply1` jest funkcją, która przyjmuje funkcję `transform` jako argument, gdzie `transform` jest funkcją, która przyjmuje liczbę całkowitą i zwraca kolejną liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="d68fd-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="d68fd-175">Poniższy kod przedstawia sposób użycia `apply1` :</span><span class="sxs-lookup"><span data-stu-id="d68fd-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="d68fd-176">Wartość `result` będzie 101 po powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d68fd-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="d68fd-177">Wiele argumentów jest oddzielonych kolejnymi `->` tokenami, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d68fd-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="d68fd-178">Wynikiem jest 200.</span><span class="sxs-lookup"><span data-stu-id="d68fd-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="d68fd-179">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="d68fd-179">Lambda Expressions</span></span>

<span data-ttu-id="d68fd-180">*Wyrażenie lambda* jest funkcją bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="d68fd-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="d68fd-181">W poprzednich przykładach, zamiast definiować nazwane funkcje **Increment** i **MUL**, można użyć wyrażeń lambda w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d68fd-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="d68fd-182">Wyrażenia lambda można definiować za pomocą `fun` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="d68fd-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="d68fd-183">Wyrażenie lambda przypomina definicję funkcji, z tą różnicą, że zamiast `=` tokenu token `->` jest używany do rozdzielenia listy argumentów z treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="d68fd-184">Podobnie jak w przypadku definicji funkcji regularnych, typy argumentów można wywnioskować lub określić jawnie, a zwracany typ wyrażenia lambda jest wywnioskowany na podstawie typu ostatniego wyrażenia w treści.</span><span class="sxs-lookup"><span data-stu-id="d68fd-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="d68fd-185">Aby uzyskać więcej informacji, zobacz [wyrażenia lambda: `fun` słowo kluczowe](lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="d68fd-185">For more information, see [Lambda Expressions: The `fun` Keyword](lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="d68fd-186">Kompozycja funkcji i przetwarzanie potokowe</span><span class="sxs-lookup"><span data-stu-id="d68fd-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="d68fd-187">Funkcje w języku F # mogą składać się z innych funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="d68fd-188">Skład dwóch funkcji **function1** i **function2** jest kolejną funkcją, która reprezentuje aplikację **function1** , a następnie aplikację **function2**:</span><span class="sxs-lookup"><span data-stu-id="d68fd-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="d68fd-189">Wynikiem jest 202.</span><span class="sxs-lookup"><span data-stu-id="d68fd-189">The result is 202.</span></span>

<span data-ttu-id="d68fd-190">Przetwarzanie potokowe umożliwia łączenie się z połączeniami funkcji w ramach kolejnych operacji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="d68fd-191">Potok działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d68fd-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="d68fd-192">Wynik zostanie ponownie 202.</span><span class="sxs-lookup"><span data-stu-id="d68fd-192">The result is again 202.</span></span>

<span data-ttu-id="d68fd-193">Operatory kompozycji mają dwie funkcje i zwracają funkcję; z kolei operatory potoku przyjmują funkcję i argument i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="d68fd-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="d68fd-194">Poniższy przykład kodu pokazuje różnicę między operatorami potoku i kompozycji, pokazując różnice w sygnaturach i użyciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68fd-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

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

## <a name="overloading-functions"></a><span data-ttu-id="d68fd-195">Przeładowywanie funkcji</span><span class="sxs-lookup"><span data-stu-id="d68fd-195">Overloading Functions</span></span>

<span data-ttu-id="d68fd-196">Można przeciążać metody typu, ale nie Functions.</span><span class="sxs-lookup"><span data-stu-id="d68fd-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="d68fd-197">Aby uzyskać więcej informacji, zobacz [metody](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="d68fd-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d68fd-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d68fd-198">See also</span></span>

- [<span data-ttu-id="d68fd-199">Wartości</span><span class="sxs-lookup"><span data-stu-id="d68fd-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="d68fd-200">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="d68fd-200">F# Language Reference</span></span>](../index.md)
