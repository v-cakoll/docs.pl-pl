---
title: 'Wyrażenia dopasowania (F #)'
description: 'Dowiedz się, jak wyrażenie dopasowania F # zapewnia rozgałęziania formant, który jest oparty na porównaniu wyrażenia zestaw wzorców.'
ms.date: 04/19/2018
ms.openlocfilehash: e4cb82f20fe82bff562736557c2346562c557f59
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221847"
---
# <a name="match-expressions"></a><span data-ttu-id="4b523-103">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="4b523-103">Match expressions</span></span>

<span data-ttu-id="4b523-104">`match` Wyrażenie zawiera rozgałęziania formant, który jest oparty na porównaniu wyrażenia zestaw wzorców.</span><span class="sxs-lookup"><span data-stu-id="4b523-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b523-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b523-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4b523-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b523-106">Remarks</span></span>

<span data-ttu-id="4b523-107">Wyrażenia dopasowania wzorca umożliwiają złożonych gałęzi na podstawie porównania wyrażeniu testowym zestaw wzorców.</span><span class="sxs-lookup"><span data-stu-id="4b523-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="4b523-108">W `match` wyrażenie *wyrażeniu testowym* jest porównywany z każdego wzorca pozycji, a po znalezieniu dopasowania odpowiedniego *wynik wyrażenia* jest obliczane i jest wartością wynikową zwracane jako wartość wyrażenia dopasowania.</span><span class="sxs-lookup"><span data-stu-id="4b523-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="4b523-109">Funkcja pokazano w poprzedniej składni dopasowania wzorca jest wyrażenie lambda, w których wzorzec dopasowywania odbywa się natychmiast na argumentu.</span><span class="sxs-lookup"><span data-stu-id="4b523-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="4b523-110">Wzorzec dopasowywania funkcja pokazano w poprzedniej składni jest odpowiednikiem następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="4b523-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="4b523-111">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4b523-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="4b523-112">Cały zestaw wzorców powinno obejmować wszystkich możliwych dopasowań zmienna wejściowa.</span><span class="sxs-lookup"><span data-stu-id="4b523-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="4b523-113">Często używasz wzór symboli wieloznacznych (`_`) jako ostatni wzorzec do dopasowania wszelkie wcześniej niedopasowane wartości wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4b523-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="4b523-114">Poniższy kod ilustruje kilka sposobów, w którym `match` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="4b523-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="4b523-115">Dokumentacja i przykłady wszystkie możliwe wzorców, które mogą być używane, zobacz [dopasowywania do wzorca](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="4b523-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="4b523-116">Osłony na temat wzorców</span><span class="sxs-lookup"><span data-stu-id="4b523-116">Guards on patterns</span></span>

<span data-ttu-id="4b523-117">Możesz użyć `when` klauzulę, aby określić dodatkowy warunek zmiennej musi spełniać zgodnego ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="4b523-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="4b523-118">Takie klauzuli nazywa się *je przed nieprzewidzianymi*.</span><span class="sxs-lookup"><span data-stu-id="4b523-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="4b523-119">Następujące wyrażenie `when` — słowo kluczowe nie jest oceniany, chyba że dokonania dopasowania do wzorca, skojarzone z tym guard.</span><span class="sxs-lookup"><span data-stu-id="4b523-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="4b523-120">Poniższy przykład ilustruje użycie guard do określania zakresu liczbowego dla zmiennej wzorca.</span><span class="sxs-lookup"><span data-stu-id="4b523-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="4b523-121">Należy pamiętać, że wiele warunków są połączone za pomocą operatorów logicznych.</span><span class="sxs-lookup"><span data-stu-id="4b523-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="4b523-122">Należy pamiętać, że ponieważ nie można użyć wartości innej niż literałami we wzorcu, należy użyć `when` klauzuli, jeśli zajdzie potrzeba porównania część dane wejściowe względem wartości.</span><span class="sxs-lookup"><span data-stu-id="4b523-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="4b523-123">Jest to pokazane w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4b523-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="4b523-124">Należy pamiętać, że jeśli — wzorzec jest objęte strażnik, osłony dotyczy **wszystkich** wzorców, a nie tylko ostatni z nich.</span><span class="sxs-lookup"><span data-stu-id="4b523-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="4b523-125">Na przykład, biorąc pod uwagę następujący kod, osłony `when a > 12` ma zastosowanie do obu `A a` i `B a`:</span><span class="sxs-lookup"><span data-stu-id="4b523-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4b523-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b523-126">See also</span></span>

- [<span data-ttu-id="4b523-127">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="4b523-127">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="4b523-128">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="4b523-128">Active Patterns</span></span>](active-patterns.md)  
- [<span data-ttu-id="4b523-129">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="4b523-129">Pattern Matching</span></span>](pattern-matching.md)  
