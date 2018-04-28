---
title: 'Wyrażenie warunkowe: if... then...else (F#)'
description: 'Dowiedz się, jak napisać wyrażenia warunkowe w języku F # do wykonywania różnych gałęziach kodu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bfb985f09be91034894e1d3eba88cebef6bb3fd4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="conditional-expressions-ifthenelse"></a>Wyrażenie warunkowe: `if...then...else`

`if...then...else` Wyrażenie uruchamia różnych gałęziach kodu i oblicza również innej wartości w zależności od danego wyrażenie warunkowe.


## <a name="syntax"></a>Składnia

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Uwagi
W poprzednich składni *wyrażenie1* jest uruchamiany, gdy wyrażenie warunkowe daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.

W przeciwieństwie do innych języków `if...then...else` konstrukcja jest wyrażenie nie instrukcję. Oznacza to, że generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, która wykonuje. Typy wartości wygenerowane w każdej gałęzi muszą być zgodne. Jeśli nie jawne `else` gałęzi, jego typ jest `unit`. W związku z tym jeśli typ `then` gałęzi jest dowolny typ innych niż `unit`, musi być `else` gałąź o taki sam typ zwracany. Gdy łańcucha `if...then...else` wyrażenia razem, można użyć słowa kluczowego `elif` zamiast `else if`; są równoważne.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia sposób użycia `if...then...else` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

