---
title: 'Pętle: for...to — Wyrażenie (F#)'
description: 'Zobacz jak F # for... wyrażenie służy do wykonywania iteracji w pętli zakres wartości zmiennej pętli.'
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="loops-forto-expression"></a>Pętle: for...to — Wyrażenie

`for...to` Wyrażenie jest używane w celu wykonania iteracji w pętli zakres wartości zmiennej pętli.


## <a name="syntax"></a>Składnia

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Uwagi
Typ identyfikatora jest wywnioskowany na podstawie typu *start* i *Zakończ* wyrażenia. Typy wyrażeń te muszą być 32-bitowych liczb całkowitych.

Chociaż technicznie wyrażenie `for...to` przypomina tradycyjnych instrukcji w języku programowania nadrzędnych. Typ zwracany dla *treść wyrażenia* musi być `unit`. W poniższych przykładach pokazano różnych zastosowań `for...to` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Dane wyjściowe poprzedniego kodu wyglądają następująco:

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Pętle: `for...in` wyrażenia](loops-for-in-expression.md)

[Pętle: `while...do` wyrażenia](loops-while-do-expression.md)
