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

Należy pamiętać, że ponieważ nie można używać wartości innych niż literały we wzorcu, muszą używać `when` klauzuli, jeśli zajdzie potrzeba porównania część danych wejściowych z określoną wartością. Przedstawiono to w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka F #](index.md)

[Wzorce aktywne](active-patterns.md)

[Dopasowanie wzorca](pattern-matching.md)
