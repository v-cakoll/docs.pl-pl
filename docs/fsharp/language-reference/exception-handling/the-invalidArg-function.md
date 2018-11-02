---
title: 'Wyjątki: invalidArg — Funkcja (F#)'
description: 'Dowiedz się, jak funkcja "invalidarg —" języka F # generuje wyjątek argumentu.'
ms.date: 05/16/2016
ms.openlocfilehash: 8bf65fae9392a88205e3cdec8b7d7a3ff42f8416
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44180322"
---
# <a name="exceptions-the-invalidarg-function"></a>Wyjątki: invalidArg — Funkcja

`invalidArg` Funkcja generuje wyjątek argumentu.

## <a name="syntax"></a>Składnia

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Uwagi

Nazwa parametru w poprzedniej składni jest ciąg zawierający nazwę parametru, którego argument był nieprawidłowy. *Ciąg komunikatu o błędzie* jest ciągiem literału lub wartości typu `string`. Staje się `Message` własności obiektu wyjątku.

Wyjątku, generowanych przez `invalidArg` jest `System.ArgumentException` wyjątku. Poniższy kod ilustruje sposób korzystania z `invalidArg` do zgłoszenia wyjątku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Dane wyjściowe są następujące polecenie, następuje ślad stosu (nie pokazane).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)
- [Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)
- [Wyjątki: `raise` — funkcja](the-raise-function.md)
- [Wyjątki: `failwith` — funkcja](the-failwith-function.md)
