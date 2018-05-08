---
title: 'Funkcje rekursywne: rec — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak użyć słowa kluczowego "rec" F # przy użyciu słowa kluczowego "let", aby zdefiniować funkcję rekursywną.'
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-functions-the-rec-keyword"></a>Funkcje rekursywne: rec — Słowo kluczowe

`rec` — Słowo kluczowe jest używany razem z `let` słowo kluczowe, aby zdefiniować funkcję rekursywną.


## <a name="syntax"></a>Składnia

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>Uwagi
Funkcje rekursywne, funkcje, które wywołują się, są identyfikowane jawnie w języku F #. To udostępnienie identyfikatorem, który jest definiowany w zakresie funkcji.

Poniższy kod przedstawia funkcję rekursywną, który oblicza *n*th Fibonacci numer.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
W praktyce tak jak w powyższym kodzie jest niepotrzebne z pamięci i czasu procesora, ponieważ obejmuje ona więc ich ponownego obliczania wcześniej obliczanej wartości.


Metody są niejawnie cykliczne w obrębie typu; nie istnieje potrzeba aby dodać `rec` — słowo kluczowe. Powiązania Let w klasach nie są niejawnie cyklicznego.


## <a name="mutually-recursive-functions"></a>Funkcje wzajemnie rekurencyjne
Czasami funkcje są *wzajemnie rekursywne*, co oznacza, że wywołania tworzą koło, gdzie jedna funkcja wywołuje inny, która z kolei wywołuje pierwsza strona, z dowolną liczbę wywołań między nimi. Takie funkcje musi definiować razem w jednym `let` powiązanie, używając `and` — słowo kluczowe do nawiązania połączenia ze sobą.

Poniższy przykład przedstawia dwa wzajemnie funkcje rekursywne.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Zobacz też
[Funkcje](index.md)
