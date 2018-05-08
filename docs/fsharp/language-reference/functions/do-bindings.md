---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak F # "do" powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości.'
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="do-bindings"></a>do — Powiązania

A `do` powiązanie jest używane do wykonywania kodu bez definiowania funkcji lub wartości. Również, czy powiązania może być używany w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).


## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Uwagi
Użyj `do` powiązanie umożliwia wykonanie kodu niezależnie od definicji funkcji lub wartości. Wyrażenie w `do` powiązania musi zwracać `unit`. Kod w najwyższego poziomu `do` powiązania jest wykonywany podczas inicjowania modułu. Słowo kluczowe `do` jest opcjonalna.

Atrybuty można zastosować do najwyższego poziomu `do` powiązania. Na przykład, jeśli jest używana usługa międzyoperacyjna modelu COM, można zastosować `STAThread` atrybutu do programu. Można to zrobić przy użyciu atrybutu na `do` powiązanie, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](../index.md)

[Funkcje](index.md)

