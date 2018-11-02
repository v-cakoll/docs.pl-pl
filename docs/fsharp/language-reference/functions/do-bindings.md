---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak języka F # czy powiązanie jest używana do wykonywania kodu bez definiowania funkcji lub wartość.'
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "45973147"
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
