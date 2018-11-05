---
title: 'Wyrażenie warunkowe: if... then...else (F#)'
description: 'Dowiedz się, jak napisać wyrażenie warunkowe w języku F # do wykonywania różnych gałęzi kodu.'
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44177604"
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
