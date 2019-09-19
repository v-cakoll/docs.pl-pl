---
title: 'Wyjątki: Wyrażenie try...finally'
description: Dowiedz się F# , jak "try... Finally "wyrażenie umożliwia wykonywanie kodu czyszczącego, nawet jeśli blok kodu zgłasza wyjątek.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083007"
---
# <a name="exceptions-the-tryfinally-expression"></a>Wyjątki: Wyrażenie try...finally

`try...finally` Wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek.

## <a name="syntax"></a>Składnia

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Uwagi

Wyrażenie może służyć do wykonywania kodu w wyrażenie2 w powyższej składni, bez względu na to, czy wyjątek jest generowany podczas wykonywania elementu *wyrażenie1*. `try...finally`

Typ *wyrażenie2* nie przyczynia się do wartości całego wyrażenia; Typ zwracany, gdy wyjątek nie występuje, jest ostatnią wartością elementu *wyrażenie1*. W przypadku wystąpienia wyjątku nie jest zwracana żadna wartość i przepływ sterowania jest przesyłany do następnego dopasowania do stosu wywołań. Jeśli nie zostanie znaleziona procedura obsługi wyjątków, program zostanie przerwany. Przed wykonaniem kodu w zgodnej procedurze obsługi lub przerwaniem działania programu kod w `finally` gałęzi jest wykonywany.

Poniższy kod ilustruje użycie `try...finally` wyrażenia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Dane wyjściowe konsoli programu są następujące.

```console
Closing stream
Exception handled.
```

Jak widać na podstawie danych wyjściowych, strumień został zamknięty przed przeprowadzeniem zewnętrznego wyjątku, a plik `test.txt` zawiera tekst `test1`, który wskazuje, że bufory zostały opróżnione i zapisywana na dysku, nawet jeśli wyjątek został przesłany kontrolka na zewnętrzny program obsługi wyjątków.

Należy zauważyć, `try...with` że konstrukcja jest oddzielna konstrukcja `try...finally` od konstrukcji. W związku z tym, jeśli kod wymaga `with` zarówno bloku, `finally` jak i bloku, należy zagnieździć dwa konstrukcje, jak w poniższym przykładzie kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

W kontekście wyrażeń obliczeń, w tym wyrażeń sekwencji i asynchronicznych przepływów pracy, **spróbuj... wyrażenia finally** mogą mieć implementację niestandardową. Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Wyjątki: `try...with` Wyrażenie](the-try-with-expression.md)
