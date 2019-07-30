---
title: do — Powiązania
description: Dowiedz się F# , w jaki sposób wiązanie "do" służy do wykonywania kodu bez definiowania funkcji ani wartości.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630539"
---
# <a name="do-bindings"></a>do — Powiązania

`do` Powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości. Ponadto, aby można było używać powiązań w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Uwagi

Użyj powiązania `do` , gdy chcesz wykonać kod niezależnie od definicji funkcji lub wartości. Wyrażenie w `do` powiązaniu musi zwracać `unit`. Kod w powiązaniu najwyższego poziomu `do` jest wykonywany po zainicjowaniu modułu. Słowo kluczowe `do` jest opcjonalne.

Atrybuty mogą być stosowane do powiązań najwyższego `do` poziomu. Na przykład jeśli program korzysta z międzyoperacyjności modelu COM, możesz chcieć zastosować `STAThread` atrybut do programu. Można to zrobić przy użyciu atrybutu dla `do` powiązania, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](../index.md)
- [Funkcje](index.md)
