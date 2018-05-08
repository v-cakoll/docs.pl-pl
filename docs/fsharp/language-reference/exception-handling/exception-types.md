---
title: Typy wyjątków (F#)
description: 'Dowiedz się, jak zdefiniować i użyć typów wyjątków F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4462dd00ddf9524d1fd376ee1e73e81fcfd5d945
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exception-types"></a>Typy wyjątków

Istnieją dwie kategorie wyjątków w języku F #: typy wyjątków .NET i typów wyjątków F #. W tym temacie opisano sposób definiowania i użyć typów wyjątków F #.


## <a name="syntax"></a>Składnia

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Uwagi
W poprzednich składni *typu wyjątku* jest nazwą nowego F # wyjątek typu, i *typ argumentu* reprezentuje typ argumentu, który może zostać podane w przypadku zgłaszał wyjątku tego typu. Można określić wiele argumentów, za pomocą typ krotki dla *typ argumentu*.

Typowy definicji wyjątku języka F # podobny do następującego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Wystąpił wyjątek tego typu można wygenerować za pomocą `raise` działają w następujący sposób.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Typ wyjątku języka F # można użyć bezpośrednio w filtrów w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ wyjątku, który definiuje z `exception` słów kluczowych w języku F # jest nowym typem, który dziedziczy z `System.Exception`.


## <a name="see-also"></a>Zobacz też
[Obsługa wyjątków](index.md)

[Wyjątki: `raise` — funkcja](the-raise-function.md)

[Hierarchia wyjątków](https://msdn.microsoft.com/library/z4c5tckx.aspx)
