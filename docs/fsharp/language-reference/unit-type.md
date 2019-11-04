---
title: Typ jednostki
description: Dowiedz się F# , w jaki sposób typ "Unit" jest często używany do przechowywania wartości wymaganej przez składnię języka, gdy wartość nie jest potrzebna lub nie jest wymagana.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424031"
---
# <a name="unit-type"></a>Typ jednostki

Typ `unit` jest typem, który wskazuje brak określonej wartości; Typ `unit` ma tylko jedną wartość, która działa jako symbol zastępczy, gdy inna wartość nie istnieje lub nie jest wymagana.

## <a name="syntax"></a>Składnia

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Uwagi

Każde F# wyrażenie musi być szacowane do wartości. W przypadku wyrażeń, które nie generują wartości będącej przedmiotem zainteresowania, używana jest wartość typu `unit`. Typ `unit` jest podobny do typu `void` w językach takich jak C# i. C++

Typ `unit` ma jedną wartość, a ta wartość jest wskazywana przez `()`tokenu.

Wartość typu `unit` jest często używana w F# programowaniu do przechowywania miejsca, w którym wartość jest wymagana przez składnię języka, ale gdy wartość nie jest potrzebna lub nie jest wymagana. Przykład może być wartością zwracaną funkcji `printf`. Ponieważ ważne akcje operacji `printf` są wykonywane w funkcji, funkcja nie musi zwracać wartości rzeczywistej. W związku z tym wartość zwracana jest typu `unit`.

Niektóre konstrukcje oczekują wartości `unit`. Na przykład do wartości `unit` należy obliczyć `do` powiązanie lub dowolny kod na najwyższym poziomie modułu. Kompilator zgłasza ostrzeżenie, gdy powiązanie `do` lub kod na najwyższym poziomie modułu generuje wynik inny niż wartość `unit`, która nie jest używana, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

To ostrzeżenie jest cechą programowania funkcjonalnego; nie jest ona wyświetlana w innych językach programowania .NET. W czystym programie funkcjonalnym, w którym funkcje nie mają żadnych efektów ubocznych, końcowa wartość zwracana jest jedynym wynikiem wywołania funkcji. W związku z tym, gdy wynik jest ignorowany, jest to możliwy błąd programowania. Chociaż F# nie jest to czysto funkcjonalny język programowania, dobrym sposobem jest przestrzeganie stylu programowania funkcjonalnego, jeśli jest to możliwe.

## <a name="see-also"></a>Zobacz także

- [Podstawowy](basic-types.md)
- [Dokumentacja języka F#](index.md)
