---
title: Typy wyjątków (F#)
description: 'Dowiedz się, jak definiowanie i korzystanie z wyjątkiem typów F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858824"
---
# <a name="exception-types"></a>Typy wyjątków

Istnieją dwie kategorie wyjątków w języku F #: typy wyjątków .NET i typy wyjątków F #. W tym temacie opisano sposób definiowania i używania typów wyjątków F #.

## <a name="syntax"></a>Składnia

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *typ wyjątku* nazywa się nowych typów języka F # wyjątek, i *typ argumentu* reprezentuje typ argumentu, który może być podany zgłosić wyjątek tego typu. Można określić wiele argumentów za pomocą typu krotki *typ argumentu*.

Typowe definicji, dla wyjątku F # jest podobny do następującego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Wyjątek tego typu można wygenerować za pomocą `raise` funkcji w następujący sposób.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Typ wyjątku F # można użyć bezpośrednio w filtry w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ wyjątku, który zdefiniujesz z `exception` — słowo kluczowe w języku F # to nowy typ, który dziedziczy z `System.Exception`.

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Wyjątki: `raise` — funkcja](the-raise-function.md)
- [Hierarchia wyjątków](https://msdn.microsoft.com/library/z4c5tckx.aspx)
