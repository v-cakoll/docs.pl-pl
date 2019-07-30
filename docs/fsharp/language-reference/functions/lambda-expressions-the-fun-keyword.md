---
title: 'Wyrażenia lambda: Zabawne słowo kluczowe'
description: Dowiedz się, jak F# za pomocą słowa kluczowego "zabawny" zdefiniować wyrażenie lambda, które jest funkcją anonimową.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630663"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Wyrażenia lambda: Zabawne słowo kluczowe (F#)

`fun` Słowo kluczowe jest używane do definiowania wyrażenia lambda, czyli funkcji anonimowej.

## <a name="syntax"></a>Składnia

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Uwagi

*Lista parametrów* zwykle składa się z nazw i, opcjonalnie, typów parametrów. Ogólnie rzecz biorąc, *Lista parametrów* może składać się z jakichkolwiek F# wzorców. Aby uzyskać pełną listę możliwych wzorców, zobacz [Dopasowanie wzorców](../pattern-matching.md). Lista prawidłowych parametrów zawiera następujące przykłady.

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

*Wyrażenie* jest treścią funkcji, ostatnim wyrażeniem generującym wartość zwracaną. Przykłady prawidłowych wyrażeń lambda są następujące:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Korzystając z wyrażenia Lambda

Wyrażenia lambda są szczególnie przydatne podczas wykonywania operacji na liście lub w innej kolekcji i chcą uniknąć dodatkowej pracy związanej z definiowaniem funkcji. Wiele F# funkcji biblioteki przyjmuje wartości funkcji jako argumenty i może być szczególnie wygodne do użycia wyrażenia lambda w tych przypadkach. Poniższy kod stosuje wyrażenie lambda do elementów listy. W takim przypadku funkcja anonimowa dodaje 1 do każdego elementu listy.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
