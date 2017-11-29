---
title: "Wyrażenie warunkowe: if... then...else (F#)"
description: "Dowiedz się, jak napisać wyrażenia warunkowe w języku F # do wykonywania różnych gałęziach kodu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a>Wyrażenie warunkowe:`if...then...else`

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
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

