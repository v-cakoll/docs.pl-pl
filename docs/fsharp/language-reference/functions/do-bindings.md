---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak języka F # czy powiązanie jest używana do wykonywania kodu bez definiowania funkcji lub wartość.'
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700326"
---
# <a name="do-bindings"></a>do — Powiązania

A `do` powiązania jest używany do wykonywania kodu bez definiowania funkcji lub wartości. Ponadto wykonaj powiązań mogą być używane w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Uwagi

Użyj `do` powiązanie wykonać kod, niezależnie od definicji funkcji lub wartości. Wyrażenie w `do` powiązania musi zwracać `unit`. Kod w najwyższego poziomu `do` powiązania jest wykonywany, gdy moduł został zainicjowany. Słowo kluczowe `do` jest opcjonalne.

Atrybuty mogą być stosowane do najwyższego poziomu `do` powiązania. Na przykład, jeśli program używa Usługa międzyoperacyjna modelu COM, warto zastosować `STAThread` atrybutu do programu. Można to zrobić za pomocą atrybutu na `do` powiązania, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](../index.md)
- [Funkcje](index.md)
