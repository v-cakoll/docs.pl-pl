---
title: "do — Powiązania (F#)"
description: "Dowiedz się, jak F # \"do\" powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
[Dokumentacja języka F #](../index.md)

[Funkcje](index.md)

