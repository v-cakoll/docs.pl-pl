---
title: Typy wyjątków
description: Dowiedz się, jak zdefiniować i zastosować F# typów wyjątków.
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772726"
---
# <a name="exception-types"></a>Typy wyjątków

Istnieją dwie kategorie wyjątków w F#: typy wyjątków .NET i F# typów wyjątków. W tym temacie opisano sposób definiowania i używania F# typów wyjątków.

## <a name="syntax"></a>Składnia

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *typ wyjątku* jest nazwą nowego F# typ wyjątku i *typ argumentu* reprezentuje typ argumentu, który może być podany zgłosić wyjątek tego typu. Można określić wiele argumentów za pomocą typu krotki *typ argumentu*.

Definicję typowej F# wyjątek jest podobny do następującego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Wyjątek tego typu można wygenerować za pomocą `raise` funkcji w następujący sposób.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Możesz użyć F# typ wyjątku, bezpośrednio z filtrami, które w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ wyjątku, który zdefiniujesz z `exception` — słowo kluczowe w F# to nowy typ, który dziedziczy z `System.Exception`.

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Wyjątki: `raise` — funkcja](the-raise-function.md)
- [Hierarchia wyjątków](https://msdn.microsoft.com/library/z4c5tckx.aspx)