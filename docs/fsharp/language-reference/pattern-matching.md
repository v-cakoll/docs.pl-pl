---
title: Dopasowanie wzorca (F#)
description: 'Dowiedz się, jak wzorce są używane w języku F # do porównywania danych ze struktury logicznej, rozkładania danych do części składowych lub wyodrębnienia informacji z danych.'
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269376"
---
# <a name="pattern-matching"></a><span data-ttu-id="b8bce-103">Dopasowanie wzorca</span><span class="sxs-lookup"><span data-stu-id="b8bce-103">Pattern Matching</span></span>

<span data-ttu-id="b8bce-104">Wzorce są regułami dotyczącymi przekształcania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="b8bce-105">Są one używane w całym języku F # do porównywania danych ze strukturą logiczną lub strukturami, rozkładania danych do części składowych lub wyodrębnienia informacji z danych na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="b8bce-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8bce-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8bce-106">Remarks</span></span>

<span data-ttu-id="b8bce-107">Wzorce są stosowane w wielu konstrukcjach języka, takich jak `match` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b8bce-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="b8bce-108">Są one używane podczas przetwarzania argumentów funkcji w `let` powiązania, wyrażeń lambda i procedurach obsługi wyjątków, skojarzone z `try...with` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b8bce-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="b8bce-109">Aby uzyskać więcej informacji, zobacz [wyrażenia dopasowań](match-expressions.md), [let — powiązania](functions/let-bindings.md), [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md), i [wyjątkami: `try...with` Wyrażenie](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="b8bce-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="b8bce-110">Na przykład w `match` wyrażenie *wzorzec* następuje symbol potoku.</span><span class="sxs-lookup"><span data-stu-id="b8bce-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="b8bce-111">Każdy deseń działa jako reguła przekształcania danych wejściowych w jakiś sposób.</span><span class="sxs-lookup"><span data-stu-id="b8bce-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="b8bce-112">W `match` wyrażenia, każdy wzorzec jest badany kolejno, można sprawdzić, czy dane wejściowe jest zgodny ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="b8bce-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="b8bce-113">Jeśli zostanie znalezione dopasowanie, wynik wyrażenia jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="b8bce-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="b8bce-114">Jeśli nie zostanie znalezione dopasowanie, bada się następną regułę wzorca.</span><span class="sxs-lookup"><span data-stu-id="b8bce-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="b8bce-115">Opcjonalne, jeśli *warunek* część została wyjaśniona w [wyrażenia dopasowań](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b8bce-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="b8bce-116">Obsługiwane wzorce przedstawiono w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b8bce-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="b8bce-117">W czasie wykonywania dane wejściowe są testowane w odniesieniu do każdego z następujących wzorów w określonej kolejności w tabeli, a wzory są stosowane cyklicznie, od pierwszych do ostatniego w jakiej występują w kodzie i od lewej do prawej dla wzorca w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="b8bce-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="b8bce-118">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b8bce-118">Name</span></span>|<span data-ttu-id="b8bce-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b8bce-119">Description</span></span>|<span data-ttu-id="b8bce-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8bce-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="b8bce-121">Wzór stałej</span><span class="sxs-lookup"><span data-stu-id="b8bce-121">Constant pattern</span></span>|<span data-ttu-id="b8bce-122">Wszelkie wartości numeryczne, znak lub literał ciągu znaków, stała wyliczenia lub zdefiniowany identyfikator literału</span><span class="sxs-lookup"><span data-stu-id="b8bce-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="b8bce-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="b8bce-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="b8bce-124">Wzorzec identyfikatora</span><span class="sxs-lookup"><span data-stu-id="b8bce-124">Identifier pattern</span></span>|<span data-ttu-id="b8bce-125">Wartość case złożenia dyskryminowanego, etykieta wyjątku lub przypadek aktywnego wzoru</span><span class="sxs-lookup"><span data-stu-id="b8bce-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="b8bce-126">Wzór zmiennej</span><span class="sxs-lookup"><span data-stu-id="b8bce-126">Variable pattern</span></span>|<span data-ttu-id="b8bce-127">*Identyfikator*</span><span class="sxs-lookup"><span data-stu-id="b8bce-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="b8bce-128">`as` Wzorzec</span><span class="sxs-lookup"><span data-stu-id="b8bce-128">`as` pattern</span></span>|<span data-ttu-id="b8bce-129">*wzorzec* jako *identyfikator*</span><span class="sxs-lookup"><span data-stu-id="b8bce-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="b8bce-130">Wzorzec lub</span><span class="sxs-lookup"><span data-stu-id="b8bce-130">OR pattern</span></span>|<span data-ttu-id="b8bce-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="b8bce-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="b8bce-132">Wzorzec i</span><span class="sxs-lookup"><span data-stu-id="b8bce-132">AND pattern</span></span>|<span data-ttu-id="b8bce-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="b8bce-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="b8bce-134">Wzór wad</span><span class="sxs-lookup"><span data-stu-id="b8bce-134">Cons pattern</span></span>|<span data-ttu-id="b8bce-135">*Identyfikator* :: *identyfikator listy*</span><span class="sxs-lookup"><span data-stu-id="b8bce-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="b8bce-136">Wzorzec listy</span><span class="sxs-lookup"><span data-stu-id="b8bce-136">List pattern</span></span>|<span data-ttu-id="b8bce-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="b8bce-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="b8bce-138">Wzorzec tablicy</span><span class="sxs-lookup"><span data-stu-id="b8bce-138">Array pattern</span></span>|<span data-ttu-id="b8bce-139">[&#124; *pattern_1*;...; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="b8bce-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="b8bce-140">Wzorzec ujęty w nawiasy</span><span class="sxs-lookup"><span data-stu-id="b8bce-140">Parenthesized pattern</span></span>|<span data-ttu-id="b8bce-141">( *wzorzec* )</span><span class="sxs-lookup"><span data-stu-id="b8bce-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="b8bce-142">Wzór krotki</span><span class="sxs-lookup"><span data-stu-id="b8bce-142">Tuple pattern</span></span>|<span data-ttu-id="b8bce-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="b8bce-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="b8bce-144">Rejestruj wzorzec</span><span class="sxs-lookup"><span data-stu-id="b8bce-144">Record pattern</span></span>|<span data-ttu-id="b8bce-145">{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="b8bce-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="b8bce-146">Wzór symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="b8bce-146">Wildcard pattern</span></span>|<span data-ttu-id="b8bce-147">_</span><span class="sxs-lookup"><span data-stu-id="b8bce-147">_</span></span>|`_`|
|<span data-ttu-id="b8bce-148">Wzorzec wraz ze wskazaniem typu</span><span class="sxs-lookup"><span data-stu-id="b8bce-148">Pattern together with type annotation</span></span>|<span data-ttu-id="b8bce-149">*wzorzec* : *typu*</span><span class="sxs-lookup"><span data-stu-id="b8bce-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="b8bce-150">Wpisz wzór testu</span><span class="sxs-lookup"><span data-stu-id="b8bce-150">Type test pattern</span></span>|<span data-ttu-id="b8bce-151">:?</span><span class="sxs-lookup"><span data-stu-id="b8bce-151">:?</span></span> <span data-ttu-id="b8bce-152">*Typ* [jako *identyfikator* ]</span><span class="sxs-lookup"><span data-stu-id="b8bce-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="b8bce-153">Wzorzec zerowy</span><span class="sxs-lookup"><span data-stu-id="b8bce-153">Null pattern</span></span>|<span data-ttu-id="b8bce-154">null</span><span class="sxs-lookup"><span data-stu-id="b8bce-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="b8bce-155">Wzory stałych</span><span class="sxs-lookup"><span data-stu-id="b8bce-155">Constant Patterns</span></span>

<span data-ttu-id="b8bce-156">Wzorce stałych są liczbowych, znaków i literały ciągu stałych wyliczenia (z uwzględnioną nazwą typu wyliczenia).</span><span class="sxs-lookup"><span data-stu-id="b8bce-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="b8bce-157">A `match` wyrażenie, które ma tylko stałe wzorce można porównać do wyrażenia CASE w innych językach.</span><span class="sxs-lookup"><span data-stu-id="b8bce-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="b8bce-158">Dane wejściowe są porównywane z wartością literału a wzór pasuje, jeśli wartości są równe.</span><span class="sxs-lookup"><span data-stu-id="b8bce-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="b8bce-159">Typ literału musi być zgodny z typem danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="b8bce-160">Poniższy przykład pokazuje użycie wzorów literału i używa również wzór zmiennej oraz wzoru OR.</span><span class="sxs-lookup"><span data-stu-id="b8bce-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="b8bce-161">Innym przykładem wzorca literału jest wzorzec oparty na wyliczeniu stałych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="b8bce-162">Należy określić nazwę typu wyliczenia, gdy używasz stałych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b8bce-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="b8bce-163">Wzorce identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="b8bce-163">Identifier Patterns</span></span>

<span data-ttu-id="b8bce-164">Jeśli wzorzec jest ciągiem znaków, który wchodzi w skład prawidłowy identyfikator, forma identyfikatora Określa, jak odbywa się dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="b8bce-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="b8bce-165">Jeśli identyfikator ma więcej niż jeden znak i rozpoczyna się od wielkiej litery, kompilator próbuje wykonać dopasowanie do wzorca identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="b8bce-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="b8bce-166">Identyfikator dla tego wzoru może być wartością oznakowaną za pomocą atrybutu literał, dyskryminowanego przypadku złożenia, identyfikatora wyjątku lub przypadek aktywnego wzoru.</span><span class="sxs-lookup"><span data-stu-id="b8bce-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="b8bce-167">Jeśli pasujący identyfikator nie zostanie znaleziony, dopasowanie nie powiedzie się i Następna reguła wzorca — wzorzec zmiennych są porównywane w danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="b8bce-168">Rozróżniane wzorce połączeń mogą być proste o nazwie przypadków lub mogą mieć wartość, lub krotkę zawierającą wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="b8bce-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="b8bce-169">W przypadku wartości, należy określić identyfikator dla wartości.</span><span class="sxs-lookup"><span data-stu-id="b8bce-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="b8bce-170">W przypadku spójnej kolekcji musisz podać wzorzec spójnej kolekcji za pomocą identyfikatora dla każdego elementu spójnej kolekcji lub identyfikatorem o nazwie pola dla jednego lub więcej nazwanych pól złożenia.</span><span class="sxs-lookup"><span data-stu-id="b8bce-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="b8bce-171">Zobacz przykłady kodu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b8bce-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="b8bce-172">`option` Typ jest złożeniem dyskryminowanym, które posiada dwa przypadki, `Some` i `None`.</span><span class="sxs-lookup"><span data-stu-id="b8bce-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="b8bce-173">Jeden przypadek (`Some`) ma wartość, ale drugi (`None`) jest tylko nazwanym przypadkiem.</span><span class="sxs-lookup"><span data-stu-id="b8bce-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="b8bce-174">W związku z tym `Some` musi mieć zmienną dla wartości skojarzonej z `Some` wielkości liter, ale `None` musi się pojawiać samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b8bce-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="b8bce-175">W poniższym kodzie zmiennej `var1` jest podana wartość uzyskana przez dopasowanie do `Some` przypadek.</span><span class="sxs-lookup"><span data-stu-id="b8bce-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="b8bce-176">W poniższym przykładzie `PersonName` złożenia dyskryminowanego znajdują się różne ciągi i znaki, które reprezentują możliwe formy nazw.</span><span class="sxs-lookup"><span data-stu-id="b8bce-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="b8bce-177">Przypadki złożeń dyskryminowanych są `FirstOnly`, `LastOnly`, i `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="b8bce-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="b8bce-178">Dla sum rozłącznych, które mają pola nazwane możesz użyć znaku równości (=) do wyodrębnienia wartość nazwanego pola.</span><span class="sxs-lookup"><span data-stu-id="b8bce-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="b8bce-179">Rozważmy na przykład sumę rozłączną z deklaracją jak następująca.</span><span class="sxs-lookup"><span data-stu-id="b8bce-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="b8bce-180">Można użyć nazwanych pól w wyrażeniu dopasowania wzorca w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b8bce-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="b8bce-181">Korzystanie z nazwanego pola jest opcjonalne, więc w poprzednim przykładzie, zarówno `Circle(r)` i `Circle(radius = r)` mają ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="b8bce-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="b8bce-182">Podczas określania wielu pól, użyj średnika (;) jako separatora.</span><span class="sxs-lookup"><span data-stu-id="b8bce-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="b8bce-183">Aktywne wzorce umożliwiają zdefiniowanie bardziej złożonego niestandardowego wzorca dopasowania.</span><span class="sxs-lookup"><span data-stu-id="b8bce-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="b8bce-184">Aby uzyskać więcej informacji na temat wzorców, zobacz [wzorców](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="b8bce-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="b8bce-185">Przypadek, w którym identyfikator jest wyjątkiem jest używany podczas dopasowywania wzorca w kontekście obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b8bce-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="b8bce-186">Aby uzyskać informacje o dopasowywaniu do wzorca w obsługę wyjątków, zobacz [wyjątkami: `try...with` wyrażenie](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="b8bce-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="b8bce-187">Wzory zmiennej</span><span class="sxs-lookup"><span data-stu-id="b8bce-187">Variable Patterns</span></span>

<span data-ttu-id="b8bce-188">Wzór zmiennej przypisuje wartość dopasowaną do nazwy zmiennej, która jest dostępna do użytku w wyrażeniu wykonywania znajdującym się po prawej stronie `->` symboli.</span><span class="sxs-lookup"><span data-stu-id="b8bce-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="b8bce-189">Sam wzorzec zmiennej nie pasuje do żadnych danych, ale wzorce zmiennej często pojawiają się w innych wzorcach, zatem bardziej złożonych struktur, takich jak tablice, aby być rozłożone na zmienne i kolekcje.</span><span class="sxs-lookup"><span data-stu-id="b8bce-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="b8bce-190">Poniższy przykład ukazuje wzór zmiennej w ramach wzorca krotki.</span><span class="sxs-lookup"><span data-stu-id="b8bce-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="b8bce-191">jako wzorzec</span><span class="sxs-lookup"><span data-stu-id="b8bce-191">as Pattern</span></span>

<span data-ttu-id="b8bce-192">`as` Wzorzec jest wzorem, który ma `as` dołączoną klauzulę.</span><span class="sxs-lookup"><span data-stu-id="b8bce-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="b8bce-193">`as` Klauzuli wiąże pasującą wartość nazwy, które mogą być używane w wyrażeniu wykonywania wyrażenia `match` wyrażenie, lub, w przypadku, gdy ten wzór jest używany w `let` powiązania, nazwa jest dodawana jako wiązanie do zakresu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b8bce-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="b8bce-194">W poniższym przykładzie użyto `as` wzorca.</span><span class="sxs-lookup"><span data-stu-id="b8bce-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="b8bce-195">Wzorzec lub</span><span class="sxs-lookup"><span data-stu-id="b8bce-195">OR Pattern</span></span>

<span data-ttu-id="b8bce-196">Wzór OR jest używany, gdy dane wejściowe można dopasować do wielu wzorców, a chcesz wykonać w wyniku tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="b8bce-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="b8bce-197">Typy obu stron wzorca OR muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="b8bce-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="b8bce-198">Poniższy przykład demonstruje wzorzec OR.</span><span class="sxs-lookup"><span data-stu-id="b8bce-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="b8bce-199">Wzorzec i</span><span class="sxs-lookup"><span data-stu-id="b8bce-199">AND Pattern</span></span>

<span data-ttu-id="b8bce-200">Wzór AND wymaga, że dane wejściowe są zgodne dwa wzorce.</span><span class="sxs-lookup"><span data-stu-id="b8bce-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="b8bce-201">Typy obu stron wzorca AND muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="b8bce-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="b8bce-202">Poniższy przykład jest jaki jak `detectZeroTuple` objętego [wzór krotki](https://msdn.microsoft.com/library/#tuple) sekcję w dalszej części tego tematu, ale tutaj zarówno `var1` i `var2` są uzyskiwane jako wartości za pomocą wzorca.</span><span class="sxs-lookup"><span data-stu-id="b8bce-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="b8bce-203">Wzór wad</span><span class="sxs-lookup"><span data-stu-id="b8bce-203">Cons Pattern</span></span>

<span data-ttu-id="b8bce-204">Wzór minusów służy do rozkładania listy na pierwszy element *head*i listę, która zawiera wszystkie pozostałe elementy *tail*.</span><span class="sxs-lookup"><span data-stu-id="b8bce-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="b8bce-205">Wzorzec listy</span><span class="sxs-lookup"><span data-stu-id="b8bce-205">List Pattern</span></span>

<span data-ttu-id="b8bce-206">Wzór listy umożliwia rozkładanie do liczby elementów list.</span><span class="sxs-lookup"><span data-stu-id="b8bce-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="b8bce-207">Sam wzorzec listy może odnosić się tylko do list o określonej liczbie elementów.</span><span class="sxs-lookup"><span data-stu-id="b8bce-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="b8bce-208">Wzorzec tablicy</span><span class="sxs-lookup"><span data-stu-id="b8bce-208">Array Pattern</span></span>

<span data-ttu-id="b8bce-209">Wzór tablicy przypomina wzór listy i może służyć do rozkładania tablic o określonej długości.</span><span class="sxs-lookup"><span data-stu-id="b8bce-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="b8bce-210">Wzorzec ujęty w nawiasy</span><span class="sxs-lookup"><span data-stu-id="b8bce-210">Parenthesized Pattern</span></span>

<span data-ttu-id="b8bce-211">Nawiasy mogą być grupowane wokół wzorców, aby osiągnąć pożądaną łączność.</span><span class="sxs-lookup"><span data-stu-id="b8bce-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="b8bce-212">W poniższym przykładzie nawiasy są używane do kontrolowania łączność między wzorcem and wzorcem cons.</span><span class="sxs-lookup"><span data-stu-id="b8bce-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="b8bce-213">Wzór krotki</span><span class="sxs-lookup"><span data-stu-id="b8bce-213">Tuple Pattern</span></span>

<span data-ttu-id="b8bce-214">Wzorzec krotki pasuje do danych wejściowych w formularzu krotki i umożliwia spójnej kolekcji być rozłożone na elementy składowe za pomocą zmiennych dla każdej pozycji w krotce pasujących do wzorca.</span><span class="sxs-lookup"><span data-stu-id="b8bce-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="b8bce-215">Poniższy przykład pokazuje wzór krotki i używa również wzorów literału, wzorów zmiennej oraz wzoru symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="b8bce-216">Rejestruj wzorzec</span><span class="sxs-lookup"><span data-stu-id="b8bce-216">Record Pattern</span></span>

<span data-ttu-id="b8bce-217">Wzór rejestrowania jest używany do rozkładania rekordów w celu wyodrębnienia wartości pól.</span><span class="sxs-lookup"><span data-stu-id="b8bce-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="b8bce-218">Wzorzec nie będzie musiał odwoływać się do wszystkich pól rekordu; wszelkie pominięte pola po prostu nie biorą udziału w dopasowywania i nie zostały wyodrębnione.</span><span class="sxs-lookup"><span data-stu-id="b8bce-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="b8bce-219">Wzór symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="b8bce-219">Wildcard Pattern</span></span>

<span data-ttu-id="b8bce-220">Wzór symboli wieloznacznych jest reprezentowany przez znak podkreślenia (`_`) znak i pasuje do żadnych danych, podobnie jak wzór zmiennej, z tą różnicą, że dane wejściowe są odrzucane zamiast bycia przypisywanymi do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b8bce-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="b8bce-221">Wzór symboli wieloznacznych jest często używana w ramach innych wzorów jako symbol zastępczy dla wartości, które nie są potrzebne w wyrażeniu na prawo od `->` symboli.</span><span class="sxs-lookup"><span data-stu-id="b8bce-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="b8bce-222">Wzór symboli wieloznacznych jest też często używany na końcu listy wzorców do dopasowywania niedopasowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="b8bce-223">Wzór symboli wieloznacznych jest demonstrowany w wielu przykładach kodu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="b8bce-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="b8bce-224">Zobacz kod poprzedzający dla jednego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b8bce-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="b8bce-225">Wzorce mające wskazania typów</span><span class="sxs-lookup"><span data-stu-id="b8bce-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="b8bce-226">Wzorce mogą mieć wskazania typów.</span><span class="sxs-lookup"><span data-stu-id="b8bce-226">Patterns can have type annotations.</span></span> <span data-ttu-id="b8bce-227">Te zachowują się jak inne adnotacje i prowadzą wnioskowanie jak inne adnotacje.</span><span class="sxs-lookup"><span data-stu-id="b8bce-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="b8bce-228">Nawiasy są wymagane wokół wskazań typów we wzorcach.</span><span class="sxs-lookup"><span data-stu-id="b8bce-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="b8bce-229">Poniższy kod przedstawia wzór, który ma adnotacji typu.</span><span class="sxs-lookup"><span data-stu-id="b8bce-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="b8bce-230">Wpisz wzór testu</span><span class="sxs-lookup"><span data-stu-id="b8bce-230">Type Test Pattern</span></span>

<span data-ttu-id="b8bce-231">Wpisz wzór testu jest używany do dopasowywania danych wejściowych do typu.</span><span class="sxs-lookup"><span data-stu-id="b8bce-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="b8bce-232">Typ danych wejściowych jest, aby dopasowanie zakończyło się (lub typem pochodnym) typu określonego we wzorcu, dopasowanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b8bce-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="b8bce-233">Poniższy przykład demonstruje typ wzorca testowego.</span><span class="sxs-lookup"><span data-stu-id="b8bce-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="b8bce-234">Wzorzec zerowy</span><span class="sxs-lookup"><span data-stu-id="b8bce-234">Null Pattern</span></span>

<span data-ttu-id="b8bce-235">Deseń zerowy pasuje do wartości zerowej, która może pojawić się podczas pracy z typami, które zezwalają na wartości null.</span><span class="sxs-lookup"><span data-stu-id="b8bce-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="b8bce-236">Wzorce zerowe są często używane podczas współpracy z kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8bce-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="b8bce-237">Na przykład, wartość zwracana przez interfejs API programu .NET może być dane wejściowe `match` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b8bce-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="b8bce-238">Możesz sterować przepływem programu na podstawie, czy wartość zwracana wynosi null, a także na podstawie innych cech zwróconej wartości.</span><span class="sxs-lookup"><span data-stu-id="b8bce-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="b8bce-239">Deseń zerowy można użyć, aby zapobiec propagowanie do pozostałej części programu wartości null.</span><span class="sxs-lookup"><span data-stu-id="b8bce-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="b8bce-240">Poniższy przykład używa wzoru null i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="b8bce-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="b8bce-241">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8bce-241">See also</span></span>

- [<span data-ttu-id="b8bce-242">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="b8bce-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="b8bce-243">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="b8bce-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="b8bce-244">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="b8bce-244">F# Language Reference</span></span>](index.md)
