---
title: 'Wyjątki: invalidArg — Funkcja (F#)'
description: 'Dowiedz się, jak funkcja invalidarg "—" F # generuje wyjątku argumentu.'
ms.date: 05/16/2016
ms.openlocfilehash: 43e1b6f3f36774ac50aeff147f75f133d6e3e5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-invalidarg-function"></a>Wyjątki: invalidArg — Funkcja

`invalidArg` Funkcja generuje wyjątku argumentu.


## <a name="syntax"></a>Składnia

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Uwagi
Nazwa parametru w poprzednim składni jest ciągiem o nazwę parametru, którego argument był nieprawidłowy. *Błąd komunikat ciągu* jest ciągiem w postaci literału lub wartość typu `string`. Staje się on `Message` właściwości obiekt wyjątku.

Wyjątek, generowane przez `invalidArg` jest `System.ArgumentException` wyjątku. Poniższy kod przedstawia użycie `invalidArg` do zgłoszenia wyjątku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Dane wyjściowe są następujące polecenie, a następnie ślad stosu (tego nie pokazano).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Zobacz też
[Obsługa wyjątków](index.md)

[Typy wyjątków](exception-types.md)

[Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)

[Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)

[Wyjątki: `raise` — funkcja](the-raise-function.md)

[Wyjątki: `failwith` — funkcja](the-failwith-function.md)
