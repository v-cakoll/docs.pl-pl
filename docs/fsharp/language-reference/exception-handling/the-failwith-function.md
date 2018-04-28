---
title: 'Wyjątki: failwith — Funkcja (F#)'
description: 'Dowiedz się, jak funkcja failwith "—" generuje wyjątek F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: af1e3b7dc96b3b822e2e19b7bac435940d15922f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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
