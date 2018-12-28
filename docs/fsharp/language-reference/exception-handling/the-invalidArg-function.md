---
title: 'Wyjątki: Invalidarg — funkcja'
description: Dowiedz się, jak F# invalidarg "—" funkcja generuje wyjątek argumentu.
ms.date: 05/16/2016
ms.openlocfilehash: 7fd8d48b80970dbbafc0c23a478b4ccf3490f3ee
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613339"
---
# <a name="exceptions-the-invalidarg-function"></a>Wyjątki: Invalidarg — funkcja

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
- [Wyjątki: `try...with` Wyrażenia](the-try-with-expression.md)
- [Wyjątki: `try...finally` Wyrażenia](the-try-finally-expression.md)
- [Wyjątki: `raise` — funkcja](the-raise-function.md)
- [Wyjątki: `failwith` — Funkcja](the-failwith-function.md)