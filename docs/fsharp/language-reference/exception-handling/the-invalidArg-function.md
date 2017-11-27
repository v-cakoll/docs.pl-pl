---
title: "Wyjątki: invalidArg — Funkcja (F#)"
description: "Dowiedz się, jak funkcja invalidarg \"—\" F # generuje wyjątku argumentu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d375b704-6b27-493e-bd1d-ee217a53c4b5
ms.openlocfilehash: 107bef361a6bd034e3d6a2227e18cf64b1b04576
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
