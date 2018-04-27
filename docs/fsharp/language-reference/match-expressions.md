---
title: 'Wyrażenia dopasowania (F #)'
description: 'Dowiedz się, jak wyrażenie dopasowania F # udostępnia rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców.'
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f843e6fde98eae8a10235dd5cae38ffc10a4fb9f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="match-expressions"></a><span data-ttu-id="9e15d-103">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="9e15d-103">Match expressions</span></span>

<span data-ttu-id="9e15d-104">`match` Wyrażenie zawiera rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców.</span><span class="sxs-lookup"><span data-stu-id="9e15d-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e15d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e15d-105">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="9e15d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e15d-106">Remarks</span></span>

<span data-ttu-id="9e15d-107">Wyrażenia dopasowania wzorca pozwalają na podstawie porównania wyrażenia testu z zestawem wzorców rozgałęzianie złożonych.</span><span class="sxs-lookup"><span data-stu-id="9e15d-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="9e15d-108">W `match` wyrażenie *testu wyrażenie* jest porównywany z każdego wzorca z kolei, a po znalezieniu dopasowania odpowiadającego *wynik wyrażenia* jest obliczane i wartości wynikowej zwracana wartość wyrażenia dopasowania.</span><span class="sxs-lookup"><span data-stu-id="9e15d-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="9e15d-109">Funkcja składnią poprzedniego dopasowania wzorca jest wyrażenie lambda, w którym odpowiedników natychmiast w argumencie.</span><span class="sxs-lookup"><span data-stu-id="9e15d-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="9e15d-110">Funkcja składnią poprzedniego dopasowania wzorca jest odpowiednikiem poniżej.</span><span class="sxs-lookup"><span data-stu-id="9e15d-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="9e15d-111">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="9e15d-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="9e15d-112">Cały zestaw wzorców powinna obejmować wszystkie możliwe dopasowania zmiennej wejściowego.</span><span class="sxs-lookup"><span data-stu-id="9e15d-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="9e15d-113">Często, użyj wzorca symbolu wieloznacznego (`_`) jako ostatni wzorzec do dopasowania żadnych wcześniej niedopasowane wartości wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9e15d-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="9e15d-114">Poniższy kod przedstawia kilka sposobów, w którym `match` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="9e15d-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="9e15d-115">Odwołanie i przykłady wszystkie możliwe wzorców, które mogą być używane, zobacz [dopasowanie wzorca](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="9e15d-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="9e15d-116">Osłony wzorce</span><span class="sxs-lookup"><span data-stu-id="9e15d-116">Guards on patterns</span></span>

<span data-ttu-id="9e15d-117">Można użyć `when` klauzuli, aby określić dodatkowy warunek zmiennej muszą spełniać do dopasowania wzorca.</span><span class="sxs-lookup"><span data-stu-id="9e15d-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="9e15d-118">Takie klauzuli jest określany jako *zabezpieczenia*.</span><span class="sxs-lookup"><span data-stu-id="9e15d-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="9e15d-119">Poniższe wyrażenie `when` — słowo kluczowe nie jest oceniany, chyba że dokonania dopasowania do wzorca skojarzone z tym guard.</span><span class="sxs-lookup"><span data-stu-id="9e15d-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="9e15d-120">Poniższy przykład przedstawia użycie osłony do określenia zakresu numerycznego dla zmiennej wzorca.</span><span class="sxs-lookup"><span data-stu-id="9e15d-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="9e15d-121">Należy pamiętać, że wiele warunków są łączone za pomocą operatorów logicznych.</span><span class="sxs-lookup"><span data-stu-id="9e15d-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="9e15d-122">Należy pamiętać, że ponieważ nie można używać wartości innych niż literały we wzorcu, muszą używać `when` klauzuli, jeśli zajdzie potrzeba porównania część danych wejściowych z określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="9e15d-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="9e15d-123">Przedstawiono to w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="9e15d-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="9e15d-124">Należy pamiętać, że wzorzec jest objęta strażnik, osłony zastosowanie do **wszystkie** wzorców, nie tylko ostatnią.</span><span class="sxs-lookup"><span data-stu-id="9e15d-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="9e15d-125">Na przykład, dla danego następujący kod, osłony `when a > 12` dotyczy zarówno `A a` i `B a`:</span><span class="sxs-lookup"><span data-stu-id="9e15d-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="9e15d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e15d-126">See also</span></span>

[<span data-ttu-id="9e15d-127">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="9e15d-127">F# Language Reference</span></span>](index.md)  
[<span data-ttu-id="9e15d-128">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="9e15d-128">Active Patterns</span></span>](active-patterns.md)  
[<span data-ttu-id="9e15d-129">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="9e15d-129">Pattern Matching</span></span>](pattern-matching.md)  
