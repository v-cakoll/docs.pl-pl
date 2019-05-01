---
title: 'Wyjątki: Failwith — funkcja'
description: Dowiedz się, jak funkcja failwith "—" generuje F# wyjątku.
ms.date: 05/16/2016
ms.openlocfilehash: 05d385ddfc98a910779a6f59949a7187c38f0812
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772687"
---
# <a name="exceptions-the-failwith-function"></a>Wyjątki: Failwith — funkcja

`failwith` Funkcja generuje F# wyjątku.

## <a name="syntax"></a>Składnia

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Uwagi

*Ciąg komunikatu o błędzie* w poprzedniej składni jest ciągiem literału lub wartości typu `string`. Staje się `Message` właściwości wyjątku.

Wyjątek, który jest generowany przez `failwith` jest `System.Exception` wyjątek, który jest odwołaniem o nazwie `Failure` w F# kodu. Poniższy kod ilustruje sposób korzystania z `failwith` do zgłoszenia wyjątku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` Wyrażenia](the-try-with-expression.md)
- [Wyjątki: `try...finally` Wyrażenia](the-try-finally-expression.md)
- [Wyjątki: `raise` — funkcja](the-raise-function.md)