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
# <a name="match-expressions"></a>Wyrażenia dopasowania

`match` Wyrażenie zawiera formant rozgałęziania, który jest oparty na porównaniu z zestawem wzorców.

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

Wyrażenia dopasowania wzorców umożliwiają tworzenie rozgałęzień złożonych na podstawie porównania wyrażenia testowego z zestawem wzorców. W wyrażeniu *test-Expression* jest porównywany z każdym wzorcem z kolei i po znalezieniu dopasowania zostanie obliczone odpowiednie *wyrażenie wynikowe* , a wynikowa wartość jest zwracana jako wartość wyrażenia Match. `match`

Funkcja dopasowania wzorca pokazana w poprzedniej składni jest wyrażeniem lambda, w którym do dopasowania do wzorca jest wykonywane bezpośrednio w argumencie. Funkcja dopasowania wzorca pokazana w poprzedniej składni jest równoważna z poniższymi parametrami.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Aby uzyskać więcej informacji na temat wyrażeń lambda [, zobacz lambda Expressions: `fun` Słowo kluczowe](./functions/lambda-expressions-the-fun-keyword.md).

Cały zestaw wzorców powinien obejmować wszystkie możliwe dopasowania zmiennej wejściowej. Często używasz wzorca wieloznacznego (`_`) jako ostatniego wzorca, aby dopasować wszystkie poprzednio niedopasowane wartości wejściowe.

Poniższy kod ilustruje niektóre sposoby `match` używania wyrażenia. Aby uzyskać odwołanie i przykłady wszystkich możliwych wzorców, których można użyć, zobacz [Dopasowanie wzorców](pattern-matching.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Osłony na wzorcach

Można użyć `when` klauzuli, aby określić dodatkowy warunek, który musi spełniać zmienna, aby pasował do wzorca. Taka klauzula jest nazywana ochroną. Wyrażenie następujące po słowie kluczowym nie jest oceniane, `when` chyba że zostanie wykonane dopasowanie do wzorca skojarzonego z tą ochroną.

Poniższy przykład ilustruje użycie ochrony w celu określenia zakresu liczbowego dla wzorca zmiennej. Należy zauważyć, że wiele warunków jest połączonych przy użyciu operatorów logicznych.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Należy pamiętać, że ponieważ wartości inne niż literały nie mogą być używane we wzorcu, należy `when` użyć klauzuli, jeśli trzeba porównać część danych wejściowych z wartością. Jest to pokazane w poniższym kodzie:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Należy zauważyć, że gdy wzorzec Union jest objęty ochroną, ochrona ma zastosowanie do **wszystkich** wzorców, a nie tylko do ostatniego. Na przykład, uwzględniając Poniższy kod, ochrona `when a > 12` ma zastosowanie zarówno `A a` do, jak `B a`i:

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

- [Dokumentacja języka F#](index.md)
- [Wzorce aktywne](active-patterns.md)
- [Dopasowanie do wzorca](pattern-matching.md)
