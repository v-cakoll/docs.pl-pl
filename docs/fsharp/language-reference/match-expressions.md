---
title: 'Wyrażenia dopasowania (F #)'
description: 'Dowiedz się, jak wyrażenie dopasowania F # udostępnia rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców.'
ms.date: 04/19/2018
ms.openlocfilehash: 22cc4b7a87a60d8a5dcbe05ac5abec5560a37516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="match-expressions"></a>Wyrażenia dopasowania

`match` Wyrażenie zawiera rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców.

## <a name="syntax"></a>Składnia

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

## <a name="remarks"></a>Uwagi

Wyrażenia dopasowania wzorca pozwalają na podstawie porównania wyrażenia testu z zestawem wzorców rozgałęzianie złożonych. W `match` wyrażenie *testu wyrażenie* jest porównywany z każdego wzorca z kolei, a po znalezieniu dopasowania odpowiadającego *wynik wyrażenia* jest obliczane i wartości wynikowej zwracana wartość wyrażenia dopasowania.

Funkcja składnią poprzedniego dopasowania wzorca jest wyrażenie lambda, w którym odpowiedników natychmiast w argumencie. Funkcja składnią poprzedniego dopasowania wzorca jest odpowiednikiem poniżej.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md).

Cały zestaw wzorców powinna obejmować wszystkie możliwe dopasowania zmiennej wejściowego. Często, użyj wzorca symbolu wieloznacznego (`_`) jako ostatni wzorzec do dopasowania żadnych wcześniej niedopasowane wartości wejściowe.

Poniższy kod przedstawia kilka sposobów, w którym `match` wyrażenie jest używane. Odwołanie i przykłady wszystkie możliwe wzorców, które mogą być używane, zobacz [dopasowanie wzorca](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Osłony wzorce

Można użyć `when` klauzuli, aby określić dodatkowy warunek zmiennej muszą spełniać do dopasowania wzorca. Takie klauzuli jest określany jako *zabezpieczenia*. Poniższe wyrażenie `when` — słowo kluczowe nie jest oceniany, chyba że dokonania dopasowania do wzorca skojarzone z tym guard.

Poniższy przykład przedstawia użycie osłony do określenia zakresu numerycznego dla zmiennej wzorca. Należy pamiętać, że wiele warunków są łączone za pomocą operatorów logicznych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Należy pamiętać, że ponieważ nie można używać wartości innych niż literały we wzorcu, muszą używać `when` klauzuli, jeśli zajdzie potrzeba porównania część danych wejściowych z określoną wartością. Przedstawiono to w poniższym kodzie:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Należy pamiętać, że wzorzec jest objęta strażnik, osłony zastosowanie do **wszystkie** wzorców, nie tylko ostatnią. Na przykład, dla danego następujący kod, osłony `when a > 12` dotyczy zarówno `A a` i `B a`:

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

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka F#](index.md)  
[Wzorce aktywne](active-patterns.md)  
[Dopasowanie do wzorca](pattern-matching.md)  
