---
title: "Wyjątki: failwith — Funkcja (F#)"
description: "Dowiedz się, jak funkcja failwith \"—\" generuje wyjątek F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="exceptions-the-failwith-function"></a>Wyjątki: failwith — Funkcja

`failwith` Funkcja generuje wyjątek F #.


## <a name="syntax"></a>Składnia

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Uwagi
*Błąd komunikat ciągu* w poprzednim składni jest ciągiem w postaci literału lub wartość typu `string`. Staje się on `Message` właściwość wyjątku.

Wyjątek, który jest generowany przez `failwith` jest `System.Exception` wyjątek, który jest odwołaniem o nazwie `Failure` w kodzie języka F #. Poniższy kod przedstawia użycie `failwith` do zgłoszenia wyjątku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>Zobacz też
[Obsługa wyjątków](index.md)

[Typy wyjątków](exception-types.md)

[Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)

[Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)

[Wyjątki: `raise` — funkcja](the-raise-function.md)
