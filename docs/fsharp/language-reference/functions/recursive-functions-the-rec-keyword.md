---
title: 'Funkcje cykliczne: Rec — słowo kluczowe'
description: Dowiedz się F# , w jaki sposób słowo kluczowe "Rec" jest używane z słowem kluczowym "let" w celu zdefiniowania funkcji cyklicznej.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630651"
---
# <a name="recursive-functions-the-rec-keyword"></a>Funkcje cykliczne: Rec — słowo kluczowe

Słowo kluczowe jest używane razem `let` ze słowem kluczowym w celu zdefiniowania funkcji cyklicznej. `rec`

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

Funkcje cykliczne, funkcje, które wywołują siebie, są jawnie F# identyfikowane w języku. Dzięki temu identyfikator jest definiowany w zakresie funkcji.

Poniższy kod ilustruje funkcję cykliczną, która oblicza n-<sup>ty</sup> numer Fibonacci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> W praktyce kod taki jak powyżej to wasteful pamięci i czasu procesora, ponieważ obejmuje on ponownie obliczenie poprzednio obliczonych wartości.

Metody są niejawnie cykliczne w obrębie typu; nie ma potrzeby dodawania `rec` słowa kluczowego. Zezwól na powiązania w klasach niejawnie cyklicznie.

## <a name="mutually-recursive-functions"></a>Funkcje wzajemnie cykliczne

Czasami funkcje są *wzajemnie cykliczne*, co oznacza, że wywołuje postać okręgu, w którym jedna funkcja wywołuje inną funkcję, która z kolei wywołuje pierwszy, z dowolną liczbą wywołań między. Należy zdefiniować takie funkcje razem w jednym `let` powiązaniu, `and` używając słowa kluczowego, aby połączyć je ze sobą.

Poniższy przykład pokazuje dwie funkcje wzajemnie cykliczne.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
