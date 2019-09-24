---
title: Dopasowanie wzorca
description: Dowiedz się, w jaki F# sposób wzorce są używane w programie, aby porównać dane ze strukturami logicznymi, rozłożyć dane na części składowe lub Wyodrębnij informacje z danych.
ms.date: 05/16/2016
ms.openlocfilehash: 0e14fa00103742bbf5f054f8c04a7669ed767e63
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216801"
---
# <a name="pattern-matching"></a><span data-ttu-id="e2287-103">Dopasowanie wzorca</span><span class="sxs-lookup"><span data-stu-id="e2287-103">Pattern Matching</span></span>

<span data-ttu-id="e2287-104">Wzorce są regułami do przekształcania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e2287-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="e2287-105">Są one używane w całym F# języku do porównywania danych ze strukturą logiczną lub strukturami, rozkładania danych do części składowych lub wyodrębniania informacji z danych na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="e2287-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2287-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2287-106">Remarks</span></span>

<span data-ttu-id="e2287-107">Wzorce są używane w wielu konstrukcjach języka, takich jak `match` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="e2287-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="e2287-108">Są one używane podczas przetwarzania argumentów dla funkcji w `let` powiązaniach, wyrażeniach lambda i w obsłudze wyjątków skojarzonych `try...with` z wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="e2287-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="e2287-109">Aby uzyskać więcej informacji, zobacz [wyrażenia dopasowania](match-expressions.md), Zezwól na [ [powiązania](./functions/let-bindings.md), wyrażenia lambda: Słowo kluczowe](./functions/lambda-expressions-the-fun-keyword.md) i[wyjątki: `fun` `try...with` Wyrażenie.](./exception-handling/the-try-with-expression.md)</span><span class="sxs-lookup"><span data-stu-id="e2287-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="e2287-110">Na przykład, w `match` wyrażeniu *wzorzec* jest zgodny z symbolem potoku.</span><span class="sxs-lookup"><span data-stu-id="e2287-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="e2287-111">Każdy wzorzec działa jako reguła do przekształcania danych wejściowych w jakiś sposób.</span><span class="sxs-lookup"><span data-stu-id="e2287-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="e2287-112">`match` W wyrażeniu każdy wzorzec jest sprawdzany z kolei, aby sprawdzić, czy dane wejściowe są zgodne ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="e2287-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="e2287-113">W przypadku znalezienia dopasowania zostanie wykonane wyrażenie wynik.</span><span class="sxs-lookup"><span data-stu-id="e2287-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="e2287-114">Jeśli dopasowanie nie zostanie znalezione, zostanie przetestowana następna reguła wzorca.</span><span class="sxs-lookup"><span data-stu-id="e2287-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="e2287-115">Wartość opcjonalna, gdy część *warunku* jest objaśniona w [wyrażeniach dopasowania](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e2287-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="e2287-116">Obsługiwane wzorce przedstawiono w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e2287-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="e2287-117">W czasie wykonywania, dane wejściowe są testowane względem każdego z następujących wzorców w kolejności wymienionej w tabeli, a wzorce są stosowane cyklicznie, od pierwszego do ostatniego, jak pojawiają się w kodzie, i od lewej do prawej dla wzorców w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e2287-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="e2287-118">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e2287-118">Name</span></span>|<span data-ttu-id="e2287-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e2287-119">Description</span></span>|<span data-ttu-id="e2287-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2287-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="e2287-121">Wzorzec stałej</span><span class="sxs-lookup"><span data-stu-id="e2287-121">Constant pattern</span></span>|<span data-ttu-id="e2287-122">Dowolny literał numeryczny, znak lub ciąg, stała wyliczenia lub zdefiniowany identyfikator literału</span><span class="sxs-lookup"><span data-stu-id="e2287-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="e2287-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="e2287-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="e2287-124">Wzorzec identyfikatora</span><span class="sxs-lookup"><span data-stu-id="e2287-124">Identifier pattern</span></span>|<span data-ttu-id="e2287-125">Wartość przypadku Unii rozłącznej, etykieta wyjątku lub przypadek aktywnego wzorca</span><span class="sxs-lookup"><span data-stu-id="e2287-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="e2287-126">Wzorzec zmiennej</span><span class="sxs-lookup"><span data-stu-id="e2287-126">Variable pattern</span></span>|<span data-ttu-id="e2287-127">*identyfikatora*</span><span class="sxs-lookup"><span data-stu-id="e2287-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="e2287-128">`as`znaczne</span><span class="sxs-lookup"><span data-stu-id="e2287-128">`as` pattern</span></span>|<span data-ttu-id="e2287-129">*wzorzec* jako *Identyfikator*</span><span class="sxs-lookup"><span data-stu-id="e2287-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="e2287-130">LUB wzorzec</span><span class="sxs-lookup"><span data-stu-id="e2287-130">OR pattern</span></span>|<span data-ttu-id="e2287-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="e2287-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="e2287-132">I wzorzec</span><span class="sxs-lookup"><span data-stu-id="e2287-132">AND pattern</span></span>|<span data-ttu-id="e2287-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="e2287-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="e2287-134">Wzorzec wad</span><span class="sxs-lookup"><span data-stu-id="e2287-134">Cons pattern</span></span>|<span data-ttu-id="e2287-135">*Identyfikator* :: *list — identyfikator*</span><span class="sxs-lookup"><span data-stu-id="e2287-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="e2287-136">Wzorzec listy</span><span class="sxs-lookup"><span data-stu-id="e2287-136">List pattern</span></span>|<span data-ttu-id="e2287-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="e2287-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="e2287-138">Wzorzec tablicy</span><span class="sxs-lookup"><span data-stu-id="e2287-138">Array pattern</span></span>|<span data-ttu-id="e2287-139">[&#124; *pattern_1*;... *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="e2287-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="e2287-140">Wzorzec w nawiasach</span><span class="sxs-lookup"><span data-stu-id="e2287-140">Parenthesized pattern</span></span>|<span data-ttu-id="e2287-141">( *wzorzec* )</span><span class="sxs-lookup"><span data-stu-id="e2287-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="e2287-142">Wzorzec krotki</span><span class="sxs-lookup"><span data-stu-id="e2287-142">Tuple pattern</span></span>|<span data-ttu-id="e2287-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="e2287-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="e2287-144">Wzorzec rekordu</span><span class="sxs-lookup"><span data-stu-id="e2287-144">Record pattern</span></span>|<span data-ttu-id="e2287-145">{ *Identifier1* = *pattern_1*;...; *identifier_n*  =  *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="e2287-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="e2287-146">Wzorzec wieloznaczny</span><span class="sxs-lookup"><span data-stu-id="e2287-146">Wildcard pattern</span></span>|<span data-ttu-id="e2287-147">\_</span><span class="sxs-lookup"><span data-stu-id="e2287-147">_</span></span>|`_`|
|<span data-ttu-id="e2287-148">Wzorzec wraz z adnotacją typu</span><span class="sxs-lookup"><span data-stu-id="e2287-148">Pattern together with type annotation</span></span>|<span data-ttu-id="e2287-149">*wzorzec* : *Typ*</span><span class="sxs-lookup"><span data-stu-id="e2287-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="e2287-150">Typ wzorca testu</span><span class="sxs-lookup"><span data-stu-id="e2287-150">Type test pattern</span></span>|<span data-ttu-id="e2287-151">:?</span><span class="sxs-lookup"><span data-stu-id="e2287-151">:?</span></span> <span data-ttu-id="e2287-152">*Typ* [AS *Identyfikator* ]</span><span class="sxs-lookup"><span data-stu-id="e2287-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="e2287-153">Wzorzec o wartości null</span><span class="sxs-lookup"><span data-stu-id="e2287-153">Null pattern</span></span>|<span data-ttu-id="e2287-154">wartość null</span><span class="sxs-lookup"><span data-stu-id="e2287-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="e2287-155">Wzorce stałe</span><span class="sxs-lookup"><span data-stu-id="e2287-155">Constant Patterns</span></span>

<span data-ttu-id="e2287-156">Wzorce stałe są literami, znakami i literałami ciągów, stałymi wyliczeniami (z uwzględnieniem nazwy typu wyliczenia).</span><span class="sxs-lookup"><span data-stu-id="e2287-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="e2287-157">`match` Wyrażenie, które ma tylko stałe wzorce, można porównać do instrukcji case w innych językach.</span><span class="sxs-lookup"><span data-stu-id="e2287-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="e2287-158">Dane wejściowe są porównywane z wartością literału, a wzorzec pasuje, jeśli wartości są równe.</span><span class="sxs-lookup"><span data-stu-id="e2287-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="e2287-159">Typ literału musi być zgodny z typem danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e2287-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="e2287-160">Poniższy przykład demonstruje użycie wzorców literałów, a także używa wzorca zmiennej i wzorca OR.</span><span class="sxs-lookup"><span data-stu-id="e2287-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="e2287-161">Innym przykładem wzorca literału jest wzorzec oparty na stałych wyliczeniach.</span><span class="sxs-lookup"><span data-stu-id="e2287-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="e2287-162">Należy określić nazwę typu wyliczeniowego w przypadku używania stałych wyliczania.</span><span class="sxs-lookup"><span data-stu-id="e2287-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="e2287-163">Wzorce identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="e2287-163">Identifier Patterns</span></span>

<span data-ttu-id="e2287-164">Jeśli wzorzec jest ciągiem znaków, który tworzy prawidłowy identyfikator, formularz identyfikatora określa sposób dopasowania wzorca.</span><span class="sxs-lookup"><span data-stu-id="e2287-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="e2287-165">Jeśli identyfikator jest dłuższy niż pojedynczy znak i zaczyna się od wielkiej litery, kompilator próbuje dopasować wzorzec identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="e2287-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="e2287-166">Identyfikatorem tego wzorca może być wartość oznaczona przy użyciu atrybutu literału, przypadku Unii rozłącznej, identyfikatora wyjątku lub aktywnego przypadku wzorca.</span><span class="sxs-lookup"><span data-stu-id="e2287-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="e2287-167">Jeśli nie znaleziono zgodnego identyfikatora, dopasowanie nie powiedzie się, a następna reguła wzorca, wzorzec zmiennej, jest porównywana z danymi wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="e2287-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="e2287-168">Wzorce Unii rozłącznych mogą być prostymi nazwanymi przypadkami lub mogą mieć wartość lub krotkę zawierającą wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="e2287-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="e2287-169">Jeśli istnieje wartość, należy określić identyfikator dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="e2287-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="e2287-170">W przypadku krotki, należy podać wzorzec krotki z identyfikatorem dla każdego elementu krotki lub identyfikatora z nazwą pola dla jednego lub więcej nazwanych pól Union.</span><span class="sxs-lookup"><span data-stu-id="e2287-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="e2287-171">Przykłady kodu można znaleźć w przykładach w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e2287-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="e2287-172">Typ jest Unią rozłączną, która ma dwa przypadki, `Some` i `None`. `option`</span><span class="sxs-lookup"><span data-stu-id="e2287-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="e2287-173">Jeden przypadek (`Some`) ma wartość, ale drugi (`None`) jest tylko nazwanym przypadkiem.</span><span class="sxs-lookup"><span data-stu-id="e2287-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="e2287-174">W związku `Some` z tym, musi mieć zmienną dla wartości skojarzonej `Some` z przypadkiem, `None` ale musi być wyświetlana sama przez siebie.</span><span class="sxs-lookup"><span data-stu-id="e2287-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="e2287-175">W poniższym kodzie zmienna `var1` otrzymuje wartość uzyskaną przez dopasowanie `Some` do wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="e2287-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="e2287-176">W poniższym przykładzie `PersonName` związek rozłącznych zawiera kombinację ciągów i znaków, które reprezentują możliwe formy nazw.</span><span class="sxs-lookup"><span data-stu-id="e2287-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="e2287-177">Przypadki rozłącznych zbiorów to `FirstOnly`, `LastOnly`i `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="e2287-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="e2287-178">W przypadku Unii rozłącznych, które mają nazwane pola, należy użyć znaku równości (=) do wyodrębnienia wartości nazwanego pola.</span><span class="sxs-lookup"><span data-stu-id="e2287-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="e2287-179">Rozważmy na przykład Unię rozłącznych z deklaracją podobną do następującej.</span><span class="sxs-lookup"><span data-stu-id="e2287-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="e2287-180">Możesz użyć nazwanych pól w wyrażeniu dopasowania wzorca w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e2287-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="e2287-181">Użycie nazwanego pola jest opcjonalne, dlatego w poprzednim przykładzie oba `Circle(r)` i `Circle(radius = r)` mają ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="e2287-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="e2287-182">Po określeniu wielu pól Użyj średnika (;) jako separator.</span><span class="sxs-lookup"><span data-stu-id="e2287-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="e2287-183">Aktywne wzorce umożliwiają zdefiniowanie bardziej złożonej niestandardowej dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="e2287-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="e2287-184">Aby uzyskać więcej informacji na temat aktywnych wzorców, zobacz [aktywne wzorce](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="e2287-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="e2287-185">Przypadek, w którym identyfikator jest wyjątek jest używany w dopasowywaniu wzorców w kontekście obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e2287-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="e2287-186">Aby uzyskać informacje na temat dopasowywania wzorców w obsłudze wyjątków, zobacz [wyjątki: `try...with` Wyrażenie.](./exception-handling/the-try-with-expression.md)</span><span class="sxs-lookup"><span data-stu-id="e2287-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="e2287-187">Wzorce zmiennych</span><span class="sxs-lookup"><span data-stu-id="e2287-187">Variable Patterns</span></span>

<span data-ttu-id="e2287-188">Wzór zmiennej przypisuje wartość dopasowaną do nazwy zmiennej, która jest następnie dostępna do użycia w wyrażeniu wykonywania na prawo od `->` symbolu.</span><span class="sxs-lookup"><span data-stu-id="e2287-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="e2287-189">Sam wzorzec zmiennej pasuje do dowolnych danych wejściowych, ale wzorce zmiennych często pojawiają się w innych wzorcach, co pozwala na bardziej złożone struktury, takie jak krotki i tablice, do rozdzielania na zmienne.</span><span class="sxs-lookup"><span data-stu-id="e2287-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="e2287-190">Poniższy przykład ilustruje wzór zmiennej w obrębie wzorca krotki.</span><span class="sxs-lookup"><span data-stu-id="e2287-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="e2287-191">jako wzorzec</span><span class="sxs-lookup"><span data-stu-id="e2287-191">as Pattern</span></span>

<span data-ttu-id="e2287-192">Wzorzec jest wzorcem `as` z dołączoną do niej klauzulą. `as`</span><span class="sxs-lookup"><span data-stu-id="e2287-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="e2287-193">Klauzula wiąże dopasowaną wartość do nazwy, która może być używana w wyrażeniu `match` wykonywania wyrażenia lub, w przypadku, gdy ten `let` wzorzec jest używany w powiązaniu, nazwa jest dodawana jako powiązanie do zakresu lokalnego. `as`</span><span class="sxs-lookup"><span data-stu-id="e2287-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="e2287-194">Poniższy przykład używa `as` wzorca.</span><span class="sxs-lookup"><span data-stu-id="e2287-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="e2287-195">LUB wzorzec</span><span class="sxs-lookup"><span data-stu-id="e2287-195">OR Pattern</span></span>

<span data-ttu-id="e2287-196">Wzorzec OR jest używany, gdy dane wejściowe mogą odpowiadać wielu wzorcem i chcesz wykonać ten sam kod w wyniku.</span><span class="sxs-lookup"><span data-stu-id="e2287-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="e2287-197">Typy obu stron wzorca OR muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="e2287-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="e2287-198">Poniższy przykład demonstruje wzorzec OR.</span><span class="sxs-lookup"><span data-stu-id="e2287-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="e2287-199">I wzorzec</span><span class="sxs-lookup"><span data-stu-id="e2287-199">AND Pattern</span></span>

<span data-ttu-id="e2287-200">Wzorzec i wymaga, aby dane wejściowe były zgodne z dwoma wzorcami.</span><span class="sxs-lookup"><span data-stu-id="e2287-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="e2287-201">Typy obu stron wzorca i muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="e2287-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="e2287-202">Poniższy przykład jest `detectZeroTuple` podobny do przedstawionego w sekcji [wzorzec krotki](https://msdn.microsoft.com/library/#tuple) w dalszej części tego tematu `var1` , ale w tym miejscu i `var2` są uzyskiwane jako wartości przy użyciu wzorca i.</span><span class="sxs-lookup"><span data-stu-id="e2287-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="e2287-203">Wzorzec wad</span><span class="sxs-lookup"><span data-stu-id="e2287-203">Cons Pattern</span></span>

<span data-ttu-id="e2287-204">Wzorzec wad służy do rozdzielania listy na pierwszy element, *nagłówek*i listę zawierającą pozostałe elementy, *ogon*.</span><span class="sxs-lookup"><span data-stu-id="e2287-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="e2287-205">Wzorzec listy</span><span class="sxs-lookup"><span data-stu-id="e2287-205">List Pattern</span></span>

<span data-ttu-id="e2287-206">Wzorzec listy umożliwia rozdzielanie list na wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="e2287-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="e2287-207">Sam wzorzec listy może pasować tylko do list o określonej liczbie elementów.</span><span class="sxs-lookup"><span data-stu-id="e2287-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="e2287-208">Wzorzec tablicy</span><span class="sxs-lookup"><span data-stu-id="e2287-208">Array Pattern</span></span>

<span data-ttu-id="e2287-209">Wzór tablicy przypomina wzorzec listy i może służyć do rozdzielania tablic o określonej długości.</span><span class="sxs-lookup"><span data-stu-id="e2287-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="e2287-210">Wzorzec w nawiasach</span><span class="sxs-lookup"><span data-stu-id="e2287-210">Parenthesized Pattern</span></span>

<span data-ttu-id="e2287-211">Nawiasy można grupować wokół wzorców w celu osiągnięcia żądanych łączność.</span><span class="sxs-lookup"><span data-stu-id="e2287-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="e2287-212">W poniższym przykładzie nawiasy są używane do kontrolowania łączność między wzorcem a i wzorcem wad.</span><span class="sxs-lookup"><span data-stu-id="e2287-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="e2287-213">Wzorzec krotki</span><span class="sxs-lookup"><span data-stu-id="e2287-213">Tuple Pattern</span></span>

<span data-ttu-id="e2287-214">Wzorzec krotki dopasowuje dane wejściowe w postaci spójnej kolekcji i umożliwia rozłożenie krotki na elementy składowe za pomocą zmiennych dopasowywania wzorców dla każdej pozycji w spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e2287-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="e2287-215">Poniższy przykład demonstruje wzorzec krotki i używa także wzorców literałów, wzorów zmiennych i wzorca symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="e2287-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="e2287-216">Wzorzec rekordu</span><span class="sxs-lookup"><span data-stu-id="e2287-216">Record Pattern</span></span>

<span data-ttu-id="e2287-217">Wzorzec rekordu służy do rozkładania rekordów w celu wyodrębnienia wartości pól.</span><span class="sxs-lookup"><span data-stu-id="e2287-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="e2287-218">Wzorzec nie musi odwoływać się do wszystkich pól rekordu; wszystkie pominięte pola tylko nie uczestniczą w dopasowaniu i nie są wyodrębniane.</span><span class="sxs-lookup"><span data-stu-id="e2287-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="e2287-219">Wzorzec wieloznaczny</span><span class="sxs-lookup"><span data-stu-id="e2287-219">Wildcard Pattern</span></span>

<span data-ttu-id="e2287-220">Wzorzec symbol wieloznaczny jest reprezentowany przez znak podkreślenia (`_`) i dopasowuje wszelkie dane wejściowe, podobnie jak wzór zmiennej, z tą różnicą, że dane wejściowe są odrzucane zamiast przypisywania do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e2287-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="e2287-221">Wzorzec symbol wieloznaczny jest często używany w innych wzorcach jako symbol zastępczy dla wartości, które nie są konieczne w wyrażeniu `->` z prawej strony symbolu.</span><span class="sxs-lookup"><span data-stu-id="e2287-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="e2287-222">Wzorzec symboli wieloznacznych jest również często używany na końcu listy wzorców w celu dopasowania do niedopasowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e2287-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="e2287-223">Wzorzec symboli wieloznacznych jest prezentowany w wielu przykładach kodu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="e2287-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="e2287-224">Zobacz poprzedni kod na jeden przykład.</span><span class="sxs-lookup"><span data-stu-id="e2287-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="e2287-225">Wzorce, które mają adnotacje typu</span><span class="sxs-lookup"><span data-stu-id="e2287-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="e2287-226">Wzorce mogą mieć adnotacje typu.</span><span class="sxs-lookup"><span data-stu-id="e2287-226">Patterns can have type annotations.</span></span> <span data-ttu-id="e2287-227">Zachowują się one tak jak inne adnotacje typu i w odróżnieniu od innych typów.</span><span class="sxs-lookup"><span data-stu-id="e2287-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="e2287-228">Nawiasy są wymagane wokół adnotacji typu w wzorcach.</span><span class="sxs-lookup"><span data-stu-id="e2287-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="e2287-229">Poniższy kod przedstawia wzorzec, który ma adnotację typu.</span><span class="sxs-lookup"><span data-stu-id="e2287-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="e2287-230">Typ wzorca testu</span><span class="sxs-lookup"><span data-stu-id="e2287-230">Type Test Pattern</span></span>

<span data-ttu-id="e2287-231">Wzorzec testu typu jest używany do dopasowania danych wejściowych do typu.</span><span class="sxs-lookup"><span data-stu-id="e2287-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="e2287-232">Jeśli typ danych wejściowych jest zgodny z (lub typem pochodnym) typu określonego we wzorcu, dopasowanie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="e2287-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="e2287-233">Poniższy przykład demonstruje wzorzec testu typu.</span><span class="sxs-lookup"><span data-stu-id="e2287-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="e2287-234">Wzorzec o wartości null</span><span class="sxs-lookup"><span data-stu-id="e2287-234">Null Pattern</span></span>

<span data-ttu-id="e2287-235">Wzorzec o wartości null jest zgodny z wartością null, która może pojawić się podczas pracy z typami, które zezwalają na wartość null.</span><span class="sxs-lookup"><span data-stu-id="e2287-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="e2287-236">Wzorce o wartości null są często używane podczas współdziałania z kodem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2287-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="e2287-237">Na przykład wartość zwracana przez interfejs API platformy .NET może być danymi wejściowymi do `match` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e2287-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="e2287-238">Można kontrolować przepływ programu w zależności od tego, czy zwracana wartość jest równa null, a także od innych cech zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="e2287-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="e2287-239">Możesz użyć wzorca o wartości null, aby zapobiec propagowaniu wartości null do reszty programu.</span><span class="sxs-lookup"><span data-stu-id="e2287-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="e2287-240">Poniższy przykład używa wzorca o wartości null i wzorca zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e2287-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="e2287-241">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2287-241">See also</span></span>

- [<span data-ttu-id="e2287-242">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="e2287-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="e2287-243">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="e2287-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="e2287-244">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e2287-244">F# Language Reference</span></span>](index.md)
