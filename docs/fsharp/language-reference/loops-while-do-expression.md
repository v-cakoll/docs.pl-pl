---
title: 'Pętle: while...do — Wyrażenie'
description: Zobacz, jak while... wyrażenie do wykonuje wykonywanie iteracji (zapętlenie), gdy określony warunek testu ma wartość true.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630751"
---
# <a name="loops-whiledo-expression"></a>Pętle: while...do — Wyrażenie

`while...do` Wyrażenie służy do wykonywania iteracji (zapętlanie), gdy określony warunek testu ma wartość true.

## <a name="syntax"></a>Składnia

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Uwagi

*Wyrażenie testowe* jest oceniane; Jeśli tak jest `true`, *wyrażenie treści* jest wykonywane, a wyrażenie testowe jest ponownie oceniane. *Wyrażenie treści* musi mieć typ `unit`. Jeśli wyrażenie testowe ma wartość `false`, iteracja zostanie zakończona.

Poniższy przykład ilustruje użycie `while...do` wyrażenia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Dane wyjściowe powyższego kodu to strumień liczb losowych z zakresu od 1 do 20, ostatni z 10.

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Można używać `while...do` w wyrażeniach sekwencji i innych wyrażeniach obliczeniowych, w tym przypadku używana jest dostosowana wersja `while...do` wyrażenia. Aby uzyskać więcej informacji, [](sequences.md)Zobacz sekwencje, [asynchroniczne przepływy pracy](asynchronous-workflows.md)i [wyrażenia obliczeń](computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętli `for...in`Wyrażenia](loops-for-in-expression.md)
- [Pętli `for...to`Wyrażenia](loops-for-to-expression.md)
