---
title: 'Wyjątki: Funkcja failwith'
description: Dowiedz się, jak funkcja "failwith —" F# generuje wyjątek.
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630326"
---
# <a name="exceptions-the-failwith-function"></a>Wyjątki: Funkcja failwith

`failwith` Funkcja generuje F# wyjątek.

## <a name="syntax"></a>Składnia

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Uwagi

*Ciąg komunikatu o błędzie* w poprzedniej składni to ciąg literału lub wartość typu `string`. Jest to właściwość wyjątku. `Message`

Wyjątek, który jest generowany przez `failwith` `System.Exception` to wyjątek, który jest odwołaniem, które ma nazwę `Failure` w F# kodzie. Poniższy kod ilustruje użycie `failwith` , aby zgłosić wyjątek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` Wyrażenie](the-try-with-expression.md)
- [Wyjątki: `try...finally` Wyrażenie](the-try-finally-expression.md)
- [Wyjątki: `raise` funkcja](the-raise-function.md)
