---
title: 'Wyrażenie warunkowe: if... then... else'
description: Dowiedz się, jak napisać wyrażenie warunkowe F# do wykonywania różnych gałęzi kodu.
ms.date: 05/16/2016
ms.openlocfilehash: db2d5ce5b75ecda171f2623c986878dcee1cf4d9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641991"
---
# <a name="conditional-expressions-ifthenelse"></a>Wyrażenie warunkowe: `if...then...else`

`if...then...else` Wyrażenie uruchamia gałęziami kodu i oblicza również innej wartości w zależności od tego, wyrażenie logiczne, biorąc pod uwagę.

## <a name="syntax"></a>Składnia

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *wyrażenie1* jest uruchamiany, gdy wyrażenie logiczne, które daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.

W przeciwieństwie do innych języków `if...then...else` konstrukcji, stanowi wyrażenie nie instrukcję. Oznacza to generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, który jest wykonywany. Typy wartości, utworzone w każdej gałęzi, muszą być zgodne. Jeśli nie jawne `else` gałęzi, jego typ jest `unit`. W związku z tym jeśli typ `then` gałąź jest dowolnego typu innego niż `unit`, musi istnieć `else` gałęzi przy użyciu tego samego typu zwracanego. Podczas tworzenia łańcucha `if...then...else` wyrażeń razem, można użyć słowa kluczowego `elif` zamiast `else if`; są one równoważne.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób używania `if...then...else` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
