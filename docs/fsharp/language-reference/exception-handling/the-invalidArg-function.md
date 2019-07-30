---
title: 'Wyjątki: Funkcja invalidArg'
description: Dowiedz się F# , jak funkcja "invalidArg —" generuje wyjątek argumentu.
ms.date: 05/16/2016
ms.openlocfilehash: 010dbfe313f539093b4ee7a19984ef54500b072d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630308"
---
# <a name="exceptions-the-invalidarg-function"></a>Wyjątki: Funkcja invalidArg

`invalidArg` Funkcja generuje wyjątek argumentu.

## <a name="syntax"></a>Składnia

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Uwagi

Nazwa parametru w poprzedniej składni jest ciągiem o nazwie parametru, którego argument był nieprawidłowy. *Ciąg komunikatu o błędzie* jest ciągiem literału lub wartością typu `string`. Jest to właściwość obiektu Exception. `Message`

Wyjątek wygenerowany przez `invalidArg` `System.ArgumentException` to wyjątek. Poniższy kod ilustruje użycie `invalidArg` , aby zgłosić wyjątek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Dane wyjściowe są następujące, po których następuje ślad stosu (niepokazywany).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` Wyrażenie](the-try-with-expression.md)
- [Wyjątki: `try...finally` Wyrażenie](the-try-finally-expression.md)
- [Wyjątki: `raise` funkcja](the-raise-function.md)
- [Wyjątki: `failwith` Funkcja](the-failwith-function.md)
