---
title: 'Wyrażenia lambda: fun — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak zdefiniować wyrażenia lambda jest funkcją anonimową przy użyciu słowa kluczowego "fun" F #.'
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515291"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Wyrażenia lambda: fun — Słowo kluczowe (F#)

`fun` — Słowo kluczowe jest używane do definiowania Wyrażenie lambda, oznacza to, że funkcja anonimowa.

## <a name="syntax"></a>Składnia

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Uwagi

*Listy parametrów* zwykle składa się z nazwy i, opcjonalnie, typy parametrów. Ogólnie rzecz biorąc *listy parametrów* może składać się z dowolnym wzorców F #. Aby uzyskać pełną listę możliwości wzorców, zobacz [dopasowywania do wzorca](../pattern-matching.md). Listy prawidłowych parametrów zawierają następujące przykłady.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*Wyrażenie* treści funkcji ostatniego wyrażenia, które generuje wartość zwracaną. Przykłady wyrażeń lambda prawidłowe są następujące:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Korzystając z wyrażenia Lambda

Wyrażenia lambda są szczególnie przydatne, jeśli chcesz wykonywać operacje na liście lub inna kolekcja i chcesz uniknąć dodatkowej pracy definiowania funkcji. Wiele funkcji biblioteki F # pobierają wartości funkcji jako argumentów i może być szczególnie wygodne, można użyć wyrażenia lambda w tych przypadkach. Następujący kod dotyczy elementów listy, wyrażenia lambda. W takim przypadku funkcja anonimowa dodaje 1 dla każdego elementu listy.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
