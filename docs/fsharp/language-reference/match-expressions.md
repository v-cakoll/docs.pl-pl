---
title: Wyrażenia dopasowania
description: Dowiedz się, jak F# wyrażenie dopasowania dostarcza rozgałęziania formant, który jest oparty na porównaniu wyrażenia zestaw wzorców.
ms.date: 04/19/2018
ms.openlocfilehash: 8972cc012d2746cb720eeed1acee403948941425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903958"
---
# <a name="match-expressions"></a>Wyrażenia dopasowania

`match` Wyrażenie zawiera rozgałęziania formant, który jest oparty na porównaniu wyrażenia zestaw wzorców.

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

Wyrażenia dopasowania wzorca umożliwiają złożonych gałęzi na podstawie porównania wyrażeniu testowym zestaw wzorców. W `match` wyrażenie *wyrażeniu testowym* jest porównywany z każdego wzorca pozycji, a po znalezieniu dopasowania odpowiedniego *wynik wyrażenia* jest obliczane i jest wartością wynikową zwracane jako wartość wyrażenia dopasowania.

Funkcja pokazano w poprzedniej składni dopasowania wzorca jest wyrażenie lambda, w których wzorzec dopasowywania odbywa się natychmiast na argumentu. Wzorzec dopasowywania funkcja pokazano w poprzedniej składni jest odpowiednikiem następujących czynności.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda: `fun` — Słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md).

Cały zestaw wzorców powinno obejmować wszystkich możliwych dopasowań zmienna wejściowa. Często używasz wzór symboli wieloznacznych (`_`) jako ostatni wzorzec do dopasowania wszelkie wcześniej niedopasowane wartości wejściowych.

Poniższy kod ilustruje kilka sposobów, w którym `match` wyrażenie jest używane. Dokumentacja i przykłady wszystkie możliwe wzorców, które mogą być używane, zobacz [dopasowywania do wzorca](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Osłony na temat wzorców

Możesz użyć `when` klauzulę, aby określić dodatkowy warunek zmiennej musi spełniać zgodnego ze wzorcem. Takie klauzuli nazywa się *je przed nieprzewidzianymi*. Następujące wyrażenie `when` — słowo kluczowe nie jest oceniany, chyba że dokonania dopasowania do wzorca, skojarzone z tym guard.

Poniższy przykład ilustruje użycie guard do określania zakresu liczbowego dla zmiennej wzorca. Należy pamiętać, że wiele warunków są połączone za pomocą operatorów logicznych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Należy pamiętać, że ponieważ nie można użyć wartości innej niż literałami we wzorcu, należy użyć `when` klauzuli, jeśli zajdzie potrzeba porównania część dane wejściowe względem wartości. Jest to pokazane w poniższym kodzie:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Należy pamiętać, że jeśli — wzorzec jest objęte strażnik, osłony dotyczy **wszystkich** wzorców, a nie tylko ostatni z nich. Na przykład, biorąc pod uwagę następujący kod, osłony `when a > 12` ma zastosowanie do obu `A a` i `B a`:

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