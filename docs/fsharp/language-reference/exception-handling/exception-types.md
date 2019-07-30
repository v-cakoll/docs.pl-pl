---
title: Typy wyjątków
description: Dowiedz się, jak definiować F# typy wyjątków i korzystać z nich.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630311"
---
# <a name="exception-types"></a>Typy wyjątków

Istnieją dwie kategorie wyjątków w programie F#: typy wyjątków .NET i F# typy wyjątków. W tym temacie opisano sposób definiowania typów wyjątków F# i ich używania.

## <a name="syntax"></a>Składnia

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *Typ wyjątku* jest nazwą nowego F# typu wyjątku, a *argument-type* reprezentuje typ argumentu, który może być dostarczony podczas zgłaszania wyjątku tego typu. Można określić wiele argumentów za pomocą typu krotki dla *typu argumentu*.

Typowa definicja F# wyjątku jest podobna do następującej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Wyjątek tego typu można wygenerować przy użyciu `raise` funkcji w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Możesz użyć typu F# wyjątku bezpośrednio w filtrach w `try...with` wyrażeniu, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ wyjątku zdefiniowany za pomocą `exception` słowa kluczowego w F# jest nowym typem, który dziedziczy z `System.Exception`.

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Wyjątki: `raise` funkcja](the-raise-function.md)
- [Hierarchia wyjątków](https://msdn.microsoft.com/library/z4c5tckx.aspx)
