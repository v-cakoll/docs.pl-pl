---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak F # "do" powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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

