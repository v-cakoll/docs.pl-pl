---
title: foreach, in (odwołanie w C#)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="foreach-in-c-reference"></a>foreach, in (odwołanie w C#)

`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu. `foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:

- ma publiczny bez parametrów `GetEnumerator` metody, których typ zwracany jest klasy, struktury lub typ interfejsu
- zwracany typ `GetEnumerator` metoda ma publicznego `Current` właściwości i publiczny bez parametrów `MoveNext` metody, których typem zwracanym jest <xref:System.Boolean>.

W dowolnym punktu w `foreach` blok instrukcji, można przerwać poza pętli przy użyciu [podziału](break.md) — słowo kluczowe lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) — słowo kluczowe. Możesz również zakończyć działanie `foreach` pętli przez [przejdź do](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie przedstawiono użycie `foreach` instrukcji z wystąpieniem <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

W następnym przykładzie użyto `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsami:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Instrukcja foreach (specyfikacja języka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Używanie instrukcji foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Instrukcje iteracji](iteration-statements.md)  
[Słowa kluczowe języka C#](index.md)  
[Odwołanie w C#](../index.md)  
[Przewodnik programowania w języku C#](../../programming-guide/index.md)  