---
title: "Wyrażenia dopasowania (F#)"
description: "Dowiedz się, jak wyrażenie dopasowania F # udostępnia rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a><span data-ttu-id="232d4-104">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="232d4-104">Match Expressions</span></span>

<span data-ttu-id="232d4-105">`match` Wyrażenie zawiera rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców.</span><span class="sxs-lookup"><span data-stu-id="232d4-105">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="232d4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="232d4-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="232d4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="232d4-107">Remarks</span></span>

<span data-ttu-id="232d4-108">Wyrażenia dopasowania wzorca pozwalają na podstawie porównania wyrażenia testu z zestawem wzorców rozgałęzianie złożonych.</span><span class="sxs-lookup"><span data-stu-id="232d4-108">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="232d4-109">W `match` wyrażenie *testu wyrażenie* jest porównywany z każdego wzorca z kolei, a po znalezieniu dopasowania odpowiadającego *wynik wyrażenia* jest obliczane i wartości wynikowej zwracana wartość wyrażenia dopasowania.</span><span class="sxs-lookup"><span data-stu-id="232d4-109">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="232d4-110">Funkcja składnią poprzedniego dopasowania wzorca jest wyrażenie lambda, w którym odpowiedników natychmiast w argumencie.</span><span class="sxs-lookup"><span data-stu-id="232d4-110">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="232d4-111">Funkcja składnią poprzedniego dopasowania wzorca jest odpowiednikiem poniżej.</span><span class="sxs-lookup"><span data-stu-id="232d4-111">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

<span data-ttu-id="232d4-112">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="232d4-112">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="232d4-113">Cały zestaw wzorców powinna obejmować wszystkie możliwe dopasowania zmiennej wejściowego.</span><span class="sxs-lookup"><span data-stu-id="232d4-113">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="232d4-114">Często, użyj wzorca symbolu wieloznacznego (`_`) jako ostatni wzorzec do dopasowania żadnych wcześniej niedopasowane wartości wejściowe.</span><span class="sxs-lookup"><span data-stu-id="232d4-114">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="232d4-115">Poniższy kod przedstawia kilka sposobów, w którym `match` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="232d4-115">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="232d4-116">Odwołanie i przykłady wszystkie możliwe wzorców, które mogą być używane, zobacz [dopasowanie wzorca](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="232d4-116">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="232d4-117">Osłony wzorce</span><span class="sxs-lookup"><span data-stu-id="232d4-117">Guards on Patterns</span></span>

<span data-ttu-id="232d4-118">Można użyć `when` klauzuli, aby określić dodatkowy warunek zmiennej muszą spełniać do dopasowania wzorca.</span><span class="sxs-lookup"><span data-stu-id="232d4-118">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="232d4-119">Takie klauzuli jest określany jako *zabezpieczenia*.</span><span class="sxs-lookup"><span data-stu-id="232d4-119">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="232d4-120">Poniższe wyrażenie `when` — słowo kluczowe nie jest oceniany, chyba że dokonania dopasowania do wzorca skojarzone z tym guard.</span><span class="sxs-lookup"><span data-stu-id="232d4-120">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="232d4-121">Poniższy przykład przedstawia użycie osłony do określenia zakresu numerycznego dla zmiennej wzorca.</span><span class="sxs-lookup"><span data-stu-id="232d4-121">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="232d4-122">Należy pamiętać, że wiele warunków są łączone za pomocą operatorów logicznych.</span><span class="sxs-lookup"><span data-stu-id="232d4-122">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="232d4-123">Należy pamiętać, że ponieważ nie można używać wartości innych niż literały we wzorcu, muszą używać `when` klauzuli, jeśli zajdzie potrzeba porównania część danych wejściowych z określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="232d4-123">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="232d4-124">Przedstawiono to w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="232d4-124">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a><span data-ttu-id="232d4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="232d4-125">See Also</span></span>

[<span data-ttu-id="232d4-126">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="232d4-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="232d4-127">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="232d4-127">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="232d4-128">Dopasowanie wzorca</span><span class="sxs-lookup"><span data-stu-id="232d4-128">Pattern Matching</span></span>](pattern-matching.md)
