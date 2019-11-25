---
title: 'Pętle: for...to — Wyrażenie'
description: Zobacz, F# jak... do wyrażenia jest używany do iteracji w pętli względem zakresu wartości zmiennej pętli.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283902"
---
# <a name="loops-forto-expression"></a>Pętle: for...to — Wyrażenie

Wyrażenie `for...to` służy do iteracji w pętli względem zakresu wartości zmiennej pętli.

## <a name="syntax"></a>Składnia

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Uwagi

Typ identyfikatora jest wywnioskowany na podstawie typu wyrażeń *początkowych* i *końcowych* . Typy tych wyrażeń muszą być 32-bitowymi liczbami całkowitymi.

Choć technicznie wyrażenie `for...to` jest bardziej podobne do tradycyjnej instrukcji w bezwzględnym języku programowania. Zwracany typ dla *wyrażenia Body* musi być `unit`. W poniższych przykładach pokazano różne zastosowania wyrażenia `for...to`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Dane wyjściowe poprzedniego kodu wyglądają następująco:

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętle: wyrażenie `for...in`](loops-for-in-expression.md)
- [Pętle: wyrażenie `while...do`](loops-while-do-expression.md)
