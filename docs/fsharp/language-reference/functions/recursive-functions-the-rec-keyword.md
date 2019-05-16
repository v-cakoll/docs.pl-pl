---
title: 'Funkcje rekursywne: Rec — słowo kluczowe'
description: Dowiedz się, jak F# — słowo kluczowe "rec" służy do definiowania funkcji recursive za pomocą słowa kluczowego "let".
ms.date: 05/16/2016
ms.openlocfilehash: 86eaf1c8a5566d8b9cbc4dcb72f945e2497e5439
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645303"
---
# <a name="recursive-functions-the-rec-keyword"></a>Funkcje rekursywne: Rec — słowo kluczowe

`rec` — Słowo kluczowe jest używany razem z `let` — słowo kluczowe do definiowania funkcji recursive.

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

Funkcje rekursywne, funkcje, które wywołują się, są identyfikowane jawnie w F# języka. Spowoduje to udostępnienie identyfikator, który jest definiowany w zakresie funkcji.

Poniższy kod ilustruje funkcji recursive, które oblicza *n*<sup>th</sup> Fibonacci numer.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> W praktyce tak jak w powyższym kodzie jest marnotrawstwa czasu pamięci i procesora, ponieważ spowodowałoby to przeprowadzanie ponownego obliczania wcześniej obliczanej wartości.

Metody są niejawnie cykliczne w obrębie typu; nie ma potrzeby można dodać `rec` — słowo kluczowe. Powiązania Let w klasach nie są niejawnie cykliczne.

## <a name="mutually-recursive-functions"></a>Funkcje wzajemnie rekursywne

Funkcje są czasami *wzajemnie cyklicznego*, co oznacza, że wywołania tworzą koła, gdzie jedna funkcja wywołuje drugą która z kolei wywołuje pierwsza strona, z dowolnej liczby wywołań między. Takie funkcje, należy zdefiniować razem do jednej `let` powiązania, za pomocą `and` — słowo kluczowe, aby połączyć je ze sobą.

W poniższym przykładzie przedstawiono dwóch wzajemnie funkcji rekursywnych.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
