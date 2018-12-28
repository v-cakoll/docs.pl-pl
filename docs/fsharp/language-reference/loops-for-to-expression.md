---
title: 'Pętle: for...to — Wyrażenie'
description: Zobacz jak F# for... wyrażenie jest używany do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.
ms.date: 05/16/2016
ms.openlocfilehash: 041e98fa4bcc140aa3cd699f6ed35bf52c8b4175
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612325"
---
# <a name="loops-forto-expression"></a>Pętle: for...to — Wyrażenie

`for...to` Wyrażenie jest używane do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.

## <a name="syntax"></a>Składnia

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Uwagi

Typ identyfikatora jest wnioskowany z typu *start* i *Zakończ* wyrażenia. Typy te wyrażenia musi być 32-bitowych liczb całkowitych.

Choć z technicznego punktu widzenia wyrażenie `for...to` przypomina tradycyjne instrukcji w języku programowania imperatywnego. Typ zwracany dla *wyrażenie treści* musi być `unit`. W poniższych przykładach pokazano różne przypadki użycia `for...to` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Dane wyjściowe poprzedniego kodu wyglądają następująco:

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętle: `for...in` Wyrażenie](loops-for-in-expression.md)
- [Pętle: `while...do` Wyrażenie](loops-while-do-expression.md)