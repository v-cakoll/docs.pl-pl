---
title: 'Pętle: for...to — Wyrażenie'
description: Zobacz, F# jak... do wyrażenia jest używany do iteracji w pętli względem zakresu wartości zmiennej pętli.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626625"
---
# <a name="loops-forto-expression"></a>Pętle: for...to — Wyrażenie

`for...to` Wyrażenie służy do iteracji w pętli względem zakresu wartości zmiennej pętli.

## <a name="syntax"></a>Składnia

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Uwagi

Typ identyfikatora jest wywnioskowany na podstawie typu wyrażeń *początkowych* i końcowych. Typy tych wyrażeń muszą być 32-bitowymi liczbami całkowitymi.

Choć technicznie wyrażenie `for...to` jest bardziej podobne do tradycyjnej instrukcji w języku programowania bezwzględnie. Typem zwracanym dla *wyrażenia Body* musi być `unit`. W poniższych przykładach pokazano różne zastosowania `for...to` wyrażenia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Dane wyjściowe poprzedniego kodu wyglądają następująco:

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętli `for...in`Wyrażenia](loops-for-in-expression.md)
- [Pętli `while...do`Wyrażenia](loops-while-do-expression.md)
