---
title: 'Wyrażenia warunkowe: IF... następnie... Przejmi'
description: Dowiedz się, jak napisać wyrażenia F# warunkowe w programie, aby wykonać różne gałęzie kodu.
ms.date: 05/16/2016
ms.openlocfilehash: d9763f37cd9170c42e968282b54a3ce925e92591
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083031"
---
# <a name="conditional-expressions-ifthenelse"></a>Wyrażenia warunkowe:`if...then...else`

`if...then...else` Wyrażenie uruchamia różne gałęzie kodu, a także oblicza inną wartość w zależności od danego wyrażenia logicznego.

## <a name="syntax"></a>Składnia

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *wyrażenie1* działa, gdy wyrażenie logiczne zwraca `true`wartość; w przeciwnym razie jest uruchamiany *wyrażenie2* .

W przeciwieństwie do innych języków `if...then...else` konstrukcja jest wyrażeniem, a nie instrukcją. Oznacza to, że produkuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, która wykonuje. Typy wartości w każdej gałęzi muszą być zgodne. Jeśli nie istnieje jawne `else` rozgałęzienie, jego typem jest. `unit` W związku z tym, jeśli typ `then` gałęzi jest dowolnego typu innego niż `unit` `else` , musi istnieć gałąź z tym samym typem zwracanym. W przypadku łączenia `elif` `else if`wyrażeń ze sobą można użyć słowa kluczowego zamiast; są `if...then...else` one równoważne.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `if...then...else` wyrażenia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```console
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
