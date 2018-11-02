---
title: 'Wyjątki: failwith — Funkcja (F#)'
description: 'Dowiedz się, jak funkcja failwith "—" generuje wyjątek F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 69a2eb69e0157d3bde8cb8884cb0ae960634dddc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863432"
---
# <a name="exceptions-the-failwith-function"></a>Wyjątki: failwith — Funkcja

`failwith` Funkcja generuje wyjątek F #.

## <a name="syntax"></a>Składnia

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Uwagi

*Ciąg komunikatu o błędzie* w poprzedniej składni jest ciągiem literału lub wartości typu `string`. Staje się `Message` właściwości wyjątku.

Wyjątek, który jest generowany przez `failwith` jest `System.Exception` wyjątek, który jest odwołaniem o nazwie `Failure` w kodzie języka F #. Poniższy kod ilustruje sposób korzystania z `failwith` do zgłoszenia wyjątku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)
- [Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)
- [Wyjątki: `raise` — funkcja](the-raise-function.md)
