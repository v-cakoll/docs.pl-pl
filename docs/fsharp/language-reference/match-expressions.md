---
title: Wyrażenia dopasowania
description: Dowiedz się F# , jak wyrażenie Match zapewnia kontrolę rozgałęziania, która jest oparta na porównaniu z zestawem wzorców.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627609"
---
# <a name="match-expressions"></a><span data-ttu-id="d4983-103">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="d4983-103">Match expressions</span></span>

<span data-ttu-id="d4983-104">`match` Wyrażenie zawiera formant rozgałęziania, który jest oparty na porównaniu z zestawem wzorców.</span><span class="sxs-lookup"><span data-stu-id="d4983-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4983-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4983-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="d4983-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4983-106">Remarks</span></span>

<span data-ttu-id="d4983-107">Wyrażenia dopasowania wzorców umożliwiają tworzenie rozgałęzień złożonych na podstawie porównania wyrażenia testowego z zestawem wzorców.</span><span class="sxs-lookup"><span data-stu-id="d4983-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="d4983-108">W wyrażeniu *test-Expression* jest porównywany z każdym wzorcem z kolei i po znalezieniu dopasowania zostanie obliczone odpowiednie *wyrażenie wynikowe* , a wynikowa wartość jest zwracana jako wartość wyrażenia Match. `match`</span><span class="sxs-lookup"><span data-stu-id="d4983-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="d4983-109">Funkcja dopasowania wzorca pokazana w poprzedniej składni jest wyrażeniem lambda, w którym do dopasowania do wzorca jest wykonywane bezpośrednio w argumencie.</span><span class="sxs-lookup"><span data-stu-id="d4983-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="d4983-110">Funkcja dopasowania wzorca pokazana w poprzedniej składni jest równoważna z poniższymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="d4983-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="d4983-111">Aby uzyskać więcej informacji na temat wyrażeń lambda [, zobacz lambda Expressions: `fun` Słowo kluczowe](./functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="d4983-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="d4983-112">Cały zestaw wzorców powinien obejmować wszystkie możliwe dopasowania zmiennej wejściowej.</span><span class="sxs-lookup"><span data-stu-id="d4983-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="d4983-113">Często używasz wzorca wieloznacznego (`_`) jako ostatniego wzorca, aby dopasować wszystkie poprzednio niedopasowane wartości wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d4983-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="d4983-114">Poniższy kod ilustruje niektóre sposoby `match` używania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d4983-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="d4983-115">Aby uzyskać odwołanie i przykłady wszystkich możliwych wzorców, których można użyć, zobacz [Dopasowanie wzorców](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="d4983-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="d4983-116">Osłony na wzorcach</span><span class="sxs-lookup"><span data-stu-id="d4983-116">Guards on patterns</span></span>

<span data-ttu-id="d4983-117">Można użyć `when` klauzuli, aby określić dodatkowy warunek, który musi spełniać zmienna, aby pasował do wzorca.</span><span class="sxs-lookup"><span data-stu-id="d4983-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="d4983-118">Taka klauzula jest nazywana ochroną.</span><span class="sxs-lookup"><span data-stu-id="d4983-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="d4983-119">Wyrażenie następujące po słowie kluczowym nie jest oceniane, `when` chyba że zostanie wykonane dopasowanie do wzorca skojarzonego z tą ochroną.</span><span class="sxs-lookup"><span data-stu-id="d4983-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="d4983-120">Poniższy przykład ilustruje użycie ochrony w celu określenia zakresu liczbowego dla wzorca zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d4983-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="d4983-121">Należy zauważyć, że wiele warunków jest połączonych przy użyciu operatorów logicznych.</span><span class="sxs-lookup"><span data-stu-id="d4983-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="d4983-122">Należy pamiętać, że ponieważ wartości inne niż literały nie mogą być używane we wzorcu, należy `when` użyć klauzuli, jeśli trzeba porównać część danych wejściowych z wartością.</span><span class="sxs-lookup"><span data-stu-id="d4983-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="d4983-123">Jest to pokazane w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d4983-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="d4983-124">Należy zauważyć, że gdy wzorzec Union jest objęty ochroną, ochrona ma zastosowanie do **wszystkich** wzorców, a nie tylko do ostatniego.</span><span class="sxs-lookup"><span data-stu-id="d4983-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="d4983-125">Na przykład, uwzględniając Poniższy kod, ochrona `when a > 12` ma zastosowanie zarówno `A a` do, jak `B a`i:</span><span class="sxs-lookup"><span data-stu-id="d4983-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4983-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4983-126">See also</span></span>

- [<span data-ttu-id="d4983-127">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="d4983-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d4983-128">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="d4983-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="d4983-129">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="d4983-129">Pattern Matching</span></span>](pattern-matching.md)
