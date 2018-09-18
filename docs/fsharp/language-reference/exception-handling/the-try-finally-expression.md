---
title: 'Wyjątki: try...finally — Wyrażenie (F#)'
description: 'Dowiedz się, jak F # "try... finally" wyrażenie umożliwia wykonanie kodu oczyszczania, nawet wtedy, gdy blok kodu zgłasza wyjątek.'
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970321"
---
# <a name="exceptions-the-tryfinally-expression"></a>Wyjątki: try...finally — Wyrażenie

`try...finally` Wyrażenie umożliwia wykonanie kodu oczyszczania, nawet wtedy, gdy blok kodu zgłasza wyjątek.

## <a name="syntax"></a>Składnia

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Uwagi

`try...finally` Wyrażenie może służyć do wykonywania kodu w *wyrażenie2* w poprzedniej składni, niezależnie od tego, czy wyjątek jest generowany podczas wykonywania *wyrażenie1*.

Typ *wyrażenie2* nie wpływa wartość całego wyrażenia; typ zwracany, gdy nie występuje wyjątek jest ostatnią wartość *wyrażenie1*. Gdy wystąpi wyjątek, jest zwracana żadna wartość, a przepływ sterowania przesyła do następnego dopasowania obsługi wyjątków w górę stosu wywołań. Jeśli żadna procedura obsługi wyjątku zostanie znaleziony, program zakończy działanie. Zanim wykonywany jest kod w pasującej klauzuli obsługi lub program kończy działanie, kod w `finally` gałęzi jest wykonywany.

Poniższy przykład demonstruje użycie `try...finally` wyrażenia.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Dostępne są następujące dane wyjściowe do konsoli.

```
Closing stream
Exception handled.
```

Jak widać z danych wyjściowych, strumień został zamknięty, zanim zewnętrzne wyjątek został obsłużony, a plik `test.txt` zawiera tekst `test1`, co oznacza, że bufory opróżnionych i zapisywane na dysku, nawet jeśli wyjątek przesyłane do obsługi wyjątku zewnętrznym kontrolować.

Należy pamiętać, że `try...with` konstrukcja jest oddzielnym konstrukcji z `try...finally` konstruowania. W związku z tym jeśli kod wymaga zarówno `with` bloku i `finally` bloku, należy zagnieździć dwóch konstrukcji, jak w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

W kontekście wyrażenia obliczeń, w tym wyrażenia sekwencji i asynchroniczne przepływy pracy, **try... finally** wyrażeń może mieć implementację niestandardową. Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)
