---
title: 'Pętle: while...do — Wyrażenie'
description: Zobacz jak podczas... zrobić wyrażenie jest używany do wykonywania iteracji wykonywanie (pętli), gdy spełniony jest warunek określony test.
ms.date: 05/16/2016
ms.openlocfilehash: d2a77e0bfefe3b6b026012e6b2938ba670326bcf
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613014"
---
# <a name="loops-whiledo-expression"></a>Pętle: while...do — Wyrażenie

`while...do` Wyrażenie jest używany do wykonywania iteracji wykonywanie (pętli), gdy spełniony jest warunek określony test.

## <a name="syntax"></a>Składnia

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Uwagi

*Wyrażeniu testowym* jest oceniany; Jeśli `true`, *wyrażenie treści* jest wykonywane i ponownie obliczone wyrażenie testu. *Wyrażenie treści* musi mieć typ `unit`. Jeśli wyrażenie testu jest `false`, zakończenia iteracji.

Poniższy przykład ilustruje użycie `while...do` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Dane wyjściowe poprzedniego kodu jest strumienia liczb losowych z zakresu od 1 do 20, za ostatni wynosi 10.

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Możesz użyć `while...do` w sekwencji, wyrażenia i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `while...do` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętle: `for...in` Wyrażenie](loops-for-in-expression.md)
- [Pętle: `for...to` Wyrażenie](loops-for-to-expression.md)