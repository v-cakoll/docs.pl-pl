---
title: Dopasowanie wzorca (F#)
description: 'Dowiedz się, jak wzorce są używane w języku F # do porównywania danych o strukturze logicznej Rozłóż danych na elementów składowych i wyodrębnienia informacji z danych.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 31a5b321e5daecdc3add9a205d60b63b2c00ccd2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="pattern-matching"></a><span data-ttu-id="5f253-103">Dopasowanie wzorca</span><span class="sxs-lookup"><span data-stu-id="5f253-103">Pattern Matching</span></span>

<span data-ttu-id="5f253-104">Wzorce są reguły przekształcania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5f253-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="5f253-105">Są one używane w całej języka F # do porównywania danych za pomocą struktury logicznej lub struktury, Rozłóż danych na elementów składowych lub wyodrębnienia informacji z danych na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="5f253-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>


## <a name="remarks"></a><span data-ttu-id="5f253-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f253-106">Remarks</span></span>
<span data-ttu-id="5f253-107">Wzorce są używane w wielu konstrukcji języka, takich jak `match` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5f253-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="5f253-108">Są one używane podczas przetwarzania argumentów funkcji w `let` powiązań, wyrażenia lambda w programy obsługi wyjątków, skojarzone z `try...with` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5f253-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="5f253-109">Aby uzyskać więcej informacji, zobacz [wyrażenia dopasowania](match-expressions.md), [let — powiązania](functions/let-bindings.md), [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md), i [wyjątkami: `try...with` Wyrażenie](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="5f253-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="5f253-110">Na przykład w `match` wyrażenie *wzorzec* jest poniżej symbol potoku.</span><span class="sxs-lookup"><span data-stu-id="5f253-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="5f253-111">Każdy wzorzec działa jako regułę do przekształcania danych wejściowych w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="5f253-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="5f253-112">W `match` wyrażenia, każdy wzorzec jest zbadać z kolei jeśli danych wejściowych jest zgodny z wzorcem.</span><span class="sxs-lookup"><span data-stu-id="5f253-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="5f253-113">Jeśli dopasowanie zostanie znaleziony, jest wykonywany wynik wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5f253-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="5f253-114">Jeśli nie, jest testowany następnego reguł wzorca.</span><span class="sxs-lookup"><span data-stu-id="5f253-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="5f253-115">Kiedy opcjonalne *warunku* opisanej w części [wyrażenia dopasowania](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5f253-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="5f253-116">W poniższej tabeli przedstawiono obsługiwane wzorce.</span><span class="sxs-lookup"><span data-stu-id="5f253-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="5f253-117">W czasie wykonywania danych wejściowych jest testowana każdego z następujących wzorce w kolejności podanej w tabeli i wzorce są stosowane rekursywnie z najpierw do ostatniego pojawiających się w kodzie i od lewej do prawej wzorców w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="5f253-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="5f253-118">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5f253-118">Name</span></span>|<span data-ttu-id="5f253-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5f253-119">Description</span></span>|<span data-ttu-id="5f253-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f253-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="5f253-121">Stałe wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-121">Constant pattern</span></span>|<span data-ttu-id="5f253-122">Wszelkie liczbowe, znak, lub literału ciągu, stała wyliczenia lub identyfikatora literału zdefiniowanego</span><span class="sxs-lookup"><span data-stu-id="5f253-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="5f253-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="5f253-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="5f253-124">Identyfikator — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-124">Identifier pattern</span></span>|<span data-ttu-id="5f253-125">Wartość działania case rozróżnianą Unię, etykiety wyjątków lub w przypadku — aktywny wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="5f253-126">Variable — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-126">Variable pattern</span></span>|<span data-ttu-id="5f253-127">*Identyfikator*</span><span class="sxs-lookup"><span data-stu-id="5f253-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="5f253-128">`as` wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-128">`as` pattern</span></span>|<span data-ttu-id="5f253-129">*wzorzec* jako *identyfikator*</span><span class="sxs-lookup"><span data-stu-id="5f253-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="5f253-130">LUB wzorca</span><span class="sxs-lookup"><span data-stu-id="5f253-130">OR pattern</span></span>|<span data-ttu-id="5f253-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="5f253-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="5f253-132">I wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-132">AND pattern</span></span>|<span data-ttu-id="5f253-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="5f253-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="5f253-134">Cons — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-134">Cons pattern</span></span>|<span data-ttu-id="5f253-135">*Identyfikator* :: *identyfikator listy*</span><span class="sxs-lookup"><span data-stu-id="5f253-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="5f253-136">List — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-136">List pattern</span></span>|<span data-ttu-id="5f253-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="5f253-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="5f253-138">Array — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-138">Array pattern</span></span>|<span data-ttu-id="5f253-139">[&#124; *pattern_1*;...; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="5f253-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="5f253-140">Parenthesized — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-140">Parenthesized pattern</span></span>|<span data-ttu-id="5f253-141">( *wzorzec* )</span><span class="sxs-lookup"><span data-stu-id="5f253-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="5f253-142">Tuple — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-142">Tuple pattern</span></span>|<span data-ttu-id="5f253-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="5f253-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="5f253-144">Record — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-144">Record pattern</span></span>|<span data-ttu-id="5f253-145">{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="5f253-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="5f253-146">Wildcard — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-146">Wildcard pattern</span></span>|<span data-ttu-id="5f253-147">_</span><span class="sxs-lookup"><span data-stu-id="5f253-147">_</span></span>|`_`|
|<span data-ttu-id="5f253-148">Wzorzec wraz z adnotacji typu</span><span class="sxs-lookup"><span data-stu-id="5f253-148">Pattern together with type annotation</span></span>|<span data-ttu-id="5f253-149">*wzorzec* : *typu*</span><span class="sxs-lookup"><span data-stu-id="5f253-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="5f253-150">Typ test — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-150">Type test pattern</span></span>|<span data-ttu-id="5f253-151">:?</span><span class="sxs-lookup"><span data-stu-id="5f253-151">:?</span></span> <span data-ttu-id="5f253-152">*Typ* [jako *identyfikator* ]</span><span class="sxs-lookup"><span data-stu-id="5f253-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="5f253-153">Null — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-153">Null pattern</span></span>|<span data-ttu-id="5f253-154">null</span><span class="sxs-lookup"><span data-stu-id="5f253-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="5f253-155">Wzorce stałej</span><span class="sxs-lookup"><span data-stu-id="5f253-155">Constant Patterns</span></span>
<span data-ttu-id="5f253-156">Wzorce stałej są stałe wyliczenie alfanumeryczne, znak i literałów ciągu (z nazwą typu wyliczenia uwzględnione).</span><span class="sxs-lookup"><span data-stu-id="5f253-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="5f253-157">A `match` wyrażenie, które tylko stałe wzorce można porównać do instrukcji case w innych językach.</span><span class="sxs-lookup"><span data-stu-id="5f253-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="5f253-158">Dane wejściowe jest porównywana z wartością literału i wzorzec jest zgodny, jeśli wartości są równe.</span><span class="sxs-lookup"><span data-stu-id="5f253-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="5f253-159">Typ literału musi być zgodny z typem danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5f253-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="5f253-160">Poniższy przykład przedstawia użycie literału wzorców i używa również zmiennej wzoru i lub.</span><span class="sxs-lookup"><span data-stu-id="5f253-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="5f253-161">Innym przykładem deseniu literału to wzorzec oparty na stałe wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5f253-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="5f253-162">Należy określić nazwę typu wyliczenia używania stałe wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5f253-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="5f253-163">Identyfikator wzorce</span><span class="sxs-lookup"><span data-stu-id="5f253-163">Identifier Patterns</span></span>
<span data-ttu-id="5f253-164">Jeśli wzorzec jest ciąg znaków, który wchodzi w skład prawidłowy identyfikator, formularz identyfikatora Określa, jak jest dopasowywany wzorzec.</span><span class="sxs-lookup"><span data-stu-id="5f253-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="5f253-165">Jeśli identyfikator jest dłuższy niż jeden znak i rozpoczyna się wielką literę, kompilator próbuje dopasować je do wzorca identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5f253-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="5f253-166">Identyfikator dla tego wzorca może być wartością atrybutu literałowego, przypadek Unii rozłącznej, identyfikator wyjątku lub case — aktywny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="5f253-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="5f253-167">Przypadku nieznalezienia nie dopasowania identyfikatora, dopasowania nie powiedzie się i następnego reguł wzorca wzorcu zmiennej jest porównywany z danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5f253-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="5f253-168">Wzorce Unii rozłącznych może być prosty o nazwie przypadków albo mogą mieć wartości lub spójnych kolekcji zawierający wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="5f253-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="5f253-169">Jeśli istnieje wartość, należy określić identyfikator dla wartości.</span><span class="sxs-lookup"><span data-stu-id="5f253-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="5f253-170">W przypadku spójnej kolekcji należy podać wzorzec krotki z identyfikatora dla każdego elementu spójnej kolekcji lub identyfikatora nazwą pola dla jednego lub więcej o nazwie pól union.</span><span class="sxs-lookup"><span data-stu-id="5f253-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="5f253-171">Przykłady kodu w tej sekcji przykłady.</span><span class="sxs-lookup"><span data-stu-id="5f253-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="5f253-172">`option` Typu jest rozróżnianą Unię z dwóch przypadków `Some` i `None`.</span><span class="sxs-lookup"><span data-stu-id="5f253-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="5f253-173">Jeden przypadek (`Some`) ma wartość, ale druga (`None`) jest nazwane przypadku.</span><span class="sxs-lookup"><span data-stu-id="5f253-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="5f253-174">W związku z tym `Some` musi mieć zmiennej wartość skojarzoną z `Some` , ale `None` musi występować samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="5f253-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="5f253-175">W poniższym kodzie zmiennej `var1` znajduje się wartość, która uzyskuje się przez dopasowanie do `Some` case.</span><span class="sxs-lookup"><span data-stu-id="5f253-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="5f253-176">W poniższym przykładzie `PersonName` rozróżnianą Unię zawiera kombinację ciągów znaków, które reprezentują możliwe formy nazwy.</span><span class="sxs-lookup"><span data-stu-id="5f253-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="5f253-177">Przypadków Unii rozłącznych są `FirstOnly`, `LastOnly`, i `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="5f253-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="5f253-178">Dla rozłączne, które mają nazwane pola należy używać znak równości (=), aby wyodrębnić wartość pola o nazwie.</span><span class="sxs-lookup"><span data-stu-id="5f253-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="5f253-179">Rozważmy na przykład rozróżnianą Unię z deklaracją podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="5f253-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="5f253-180">Można użyć nazwanego pola w wyrażeniu dopasowania wzorca w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5f253-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="5f253-181">Korzystanie z nazwane pole jest opcjonalne, więc w poprzednim przykładzie zarówno `Circle(r)` i `Circle(radius = r)` mają ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="5f253-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="5f253-182">Podczas określania wielu pól, użyj średnika (;) jako separatora.</span><span class="sxs-lookup"><span data-stu-id="5f253-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="5f253-183">Wzorce aktywne umożliwiają definiowanie bardziej złożonych dopasowanie wzorca niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5f253-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="5f253-184">Aby uzyskać więcej informacji na temat aktywne wzorce, zobacz [aktywne wzorce](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="5f253-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="5f253-185">Przypadek, w którym wyjątek stanowi identyfikator jest używany podczas dopasowywania w kontekście obsługi wyjątków do wzorca.</span><span class="sxs-lookup"><span data-stu-id="5f253-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="5f253-186">Informacje o wzorzec dopasowany w obsłudze wyjątków, zobacz [wyjątkami: `try...with` wyrażenia](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="5f253-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>


## <a name="variable-patterns"></a><span data-ttu-id="5f253-187">Wzorce zmiennych</span><span class="sxs-lookup"><span data-stu-id="5f253-187">Variable Patterns</span></span>
<span data-ttu-id="5f253-188">Variable — wzorzec przypisuje wartość filtrowanego na nazwę zmiennej, która jest dostępna do użycia w wyrażeniu wykonywania z prawej strony `->` symbolu.</span><span class="sxs-lookup"><span data-stu-id="5f253-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="5f253-189">Variable — wzorzec wyłącznie pasuje do żadnych danych, ale wzorce zmiennych często pojawiają się w innych wzorcach, dlatego włączenie bardziej złożonych struktur przykład spójnych kolekcji i tablic, aby być rozłożone na zmienne.</span><span class="sxs-lookup"><span data-stu-id="5f253-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="5f253-190">W poniższym przykładzie pokazano zmiennej wzorca w wzorzec spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5f253-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="5f253-191">AS — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-191">as Pattern</span></span>
<span data-ttu-id="5f253-192">`as` Wzorzec jest wzorzec, który ma `as` klauzuli dołączone do niego.</span><span class="sxs-lookup"><span data-stu-id="5f253-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="5f253-193">`as` Klauzuli wiąże wprowadzona wartość nazwę używaną w wyrażeniu wykonywania `match` wyrażenia, lub, w którym ten wzorzec jest używany w przypadku `let` powiązanie, nazwa zostanie dodany jako powiązanie do zakresu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5f253-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="5f253-194">W poniższym przykładzie użyto `as` wzorca.</span><span class="sxs-lookup"><span data-stu-id="5f253-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="5f253-195">LUB wzorca</span><span class="sxs-lookup"><span data-stu-id="5f253-195">OR Pattern</span></span>
<span data-ttu-id="5f253-196">Wzorzec lub jest używana, gdy dane wejściowe może dopasować wielu wzorców, i chcesz wykonać ten sam kod w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="5f253-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="5f253-197">Typy wzorzec lub obu stron muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="5f253-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="5f253-198">W poniższym przykładzie pokazano lub wzorzec.</span><span class="sxs-lookup"><span data-stu-id="5f253-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="5f253-199">I wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-199">AND Pattern</span></span>
<span data-ttu-id="5f253-200">Wzorzec i musi być zgodna dwa wzorce w danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5f253-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="5f253-201">Typy obie strony wzorca i muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="5f253-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="5f253-202">Poniższy przykład przypomina `detectZeroTuple` pokazano [Tuple — wzorzec](https://msdn.microsoft.com/library/#tuple) dalszej części tego tematu, ale tutaj zarówno `var1` i `var2` są uzyskiwane jako wartości przy użyciu wzorca i.</span><span class="sxs-lookup"><span data-stu-id="5f253-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="5f253-203">Cons — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-203">Cons Pattern</span></span>
<span data-ttu-id="5f253-204">Wzorzec wad służy do Rozłóż listy na pierwszym elementem *head*oraz listę zawierającą wszystkie pozostałe elementy *tail*.</span><span class="sxs-lookup"><span data-stu-id="5f253-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="5f253-205">List — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-205">List Pattern</span></span>
<span data-ttu-id="5f253-206">List — wzorzec umożliwia listy, aby być rozłożone na liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="5f253-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="5f253-207">List — wzorzec sam może dopasować tylko listy określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="5f253-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="5f253-208">Array — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-208">Array Pattern</span></span>
<span data-ttu-id="5f253-209">Array — wzorzec podobny wzorzec listy i może służyć do dekompozycji tablice o określonej długości.</span><span class="sxs-lookup"><span data-stu-id="5f253-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="5f253-210">Parenthesized — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-210">Parenthesized Pattern</span></span>
<span data-ttu-id="5f253-211">Mogą być grupowane nawiasów wokół wzorców w celu osiągnięcia żądanej łączność.</span><span class="sxs-lookup"><span data-stu-id="5f253-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="5f253-212">W poniższym przykładzie nawiasy są używane do kontrolowania łączność między wzoru i i wad.</span><span class="sxs-lookup"><span data-stu-id="5f253-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="5f253-213">Tuple — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-213">Tuple Pattern</span></span>
<span data-ttu-id="5f253-214">Tuple — wzorzec jest zgodny z danych wejściowych w postaci spójnej kolekcji i umożliwia spójnej kolekcji być rozłożone na jego elementy składowe przy użyciu wzorca dopasowania zmienne dla każdej pozycji w spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5f253-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="5f253-215">W poniższym przykładzie pokazano wzorzec spójnej kolekcji i używa również wzorce literału, wzorce zmiennych i wzorcu symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="5f253-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="5f253-216">Record — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-216">Record Pattern</span></span>
<span data-ttu-id="5f253-217">Wzorzec rekord jest używany do dekompozycji rekordów Wyodrębnij wartości pól.</span><span class="sxs-lookup"><span data-stu-id="5f253-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="5f253-218">Wzorzec nie musi odwoływać się do wszystkich pól rekordu; wszystkie pola pominięcia po prostu nie uczestniczą w odpowiadającym i nie są wyodrębniane.</span><span class="sxs-lookup"><span data-stu-id="5f253-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="5f253-219">Wildcard — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-219">Wildcard Pattern</span></span>
<span data-ttu-id="5f253-220">Wzorzec wieloznaczny jest reprezentowany przez znak podkreślenia (`_`) znaków, a wszystkie dane wejściowe, podobnie jak wzorcu zmiennej jest zgodna z tą różnicą, że dane wejściowe są usuwane zamiast przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5f253-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="5f253-221">Wzorzec wieloznaczny jest często używana w innych wzorcach jako symbol zastępczy wartości, które nie są wymagane w wyrażeniu po prawej stronie `->` symbolu.</span><span class="sxs-lookup"><span data-stu-id="5f253-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="5f253-222">Wzorzec wieloznaczny jest również często używane na końcu Lista wzorców odpowiadające niedopasowane udziału.</span><span class="sxs-lookup"><span data-stu-id="5f253-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="5f253-223">Wzorzec wieloznaczny jest przedstawiona w wiele przykładów kodu, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="5f253-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="5f253-224">Zobacz poprzedni kod na jednym z przykładów.</span><span class="sxs-lookup"><span data-stu-id="5f253-224">See the preceding code for one example.</span></span>


## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="5f253-225">Wzorce, które mają adnotacje typu</span><span class="sxs-lookup"><span data-stu-id="5f253-225">Patterns That Have Type Annotations</span></span>
<span data-ttu-id="5f253-226">Wzorce może mieć adnotacji typu.</span><span class="sxs-lookup"><span data-stu-id="5f253-226">Patterns can have type annotations.</span></span> <span data-ttu-id="5f253-227">Te przypominają innych adnotacji typu i przewodnik wnioskowania podobnie jak inne adnotacji typu.</span><span class="sxs-lookup"><span data-stu-id="5f253-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="5f253-228">Wymagane są nawiasów wokół adnotacji typu w wzorce.</span><span class="sxs-lookup"><span data-stu-id="5f253-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="5f253-229">Poniższy kod przedstawia wzorzec, który ma adnotację typu.</span><span class="sxs-lookup"><span data-stu-id="5f253-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="5f253-230">Typ Test — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-230">Type Test Pattern</span></span>
<span data-ttu-id="5f253-231">Wzorzec testu typu jest używany do dopasowywania przed typem danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5f253-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="5f253-232">Typ danych wejściowych jest dopasowanie do (lub typu pochodnego) typu określonego we wzorcu dopasowania zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5f253-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="5f253-233">W poniższym przykładzie pokazano wzorzec testu typu.</span><span class="sxs-lookup"><span data-stu-id="5f253-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="5f253-234">Null — wzorzec</span><span class="sxs-lookup"><span data-stu-id="5f253-234">Null Pattern</span></span>
<span data-ttu-id="5f253-235">Null — wzorzec zgodna z wartością null może wystąpić podczas pracy z typami zezwalających na wartość null.</span><span class="sxs-lookup"><span data-stu-id="5f253-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="5f253-236">Wzorce wartości null są często używane podczas współpracy z kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5f253-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="5f253-237">Na przykład wartość zwracaną przez interfejs API programu .NET mogą być dane wejściowe `match` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5f253-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="5f253-238">Można sterować przepływem programu na podstawie, czy wartość zwracana jest wartość null, a także na innych właściwości zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5f253-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="5f253-239">Null — wzorzec umożliwia uniemożliwić propagowanie z resztą programu wartości null.</span><span class="sxs-lookup"><span data-stu-id="5f253-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="5f253-240">W poniższym przykładzie użyto wzoru null i zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5f253-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="5f253-241">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f253-241">See Also</span></span>
[<span data-ttu-id="5f253-242">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="5f253-242">Match Expressions</span></span>](match-expressions.md)

[<span data-ttu-id="5f253-243">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="5f253-243">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="5f253-244">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="5f253-244">F# Language Reference</span></span>](index.md)
