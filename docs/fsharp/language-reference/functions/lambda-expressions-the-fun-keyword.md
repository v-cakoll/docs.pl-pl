---
title: 'Wyrażenia lambda: fun — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak używać słowa kluczowego "fun" F # do definiowania wyrażenia lambda, czyli funkcji anonimowej.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f2f15a1b482ce3971d0b3d5ffc4f6dcc9ccf1569
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Wyrażenia lambda: fun — Słowo kluczowe (F#)

`fun` — Słowo kluczowe jest używane do definiowania wyrażenia lambda, oznacza to, że funkcja anonimowa.


## <a name="syntax"></a>Składnia

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Uwagi
*Listy parametrów* zazwyczaj składa się z nazwy i, opcjonalnie, typy parametrów. Ogólnie rzecz biorąc *listy parametrów* może składać się z dowolnym wzorce F #. Aby uzyskać pełną listę wzorców możliwe, zobacz [dopasowanie wzorca](../pattern-matching.md). Listę prawidłowych parametrów obejmują następujące przykłady.

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

*Wyrażenie* treść funkcji ostatniego wyrażenia generuje wartość zwracaną. Przykłady wyrażeń lambda prawidłowe są następujące:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a>Korzystając z wyrażenia Lambda
Wyrażenia lambda są szczególnie przydatne, jeśli chcesz wykonywać operacje na listę lub innych kolekcji i aby uniknąć dodatkowej pracy definiowania funkcji. Wartości funkcji jako argumenty zająć wiele funkcji biblioteki F # i może być szczególnie łatwe w użyciu wyrażenia lambda w takich przypadkach. Poniższy kod dotyczy elementów listy wyrażenia lambda. W takim przypadku funkcja anonimowa dodaje 1 do każdego elementu listy.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>Zobacz też
[Funkcje](index.md)
