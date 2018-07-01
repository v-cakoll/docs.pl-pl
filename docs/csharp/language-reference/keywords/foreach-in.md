---
title: foreach, in (odwołanie w C#)
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d3ce1122c54c14b1baf35641f28d062a2855d335
ms.sourcegitcommit: 736ec4d3e2c74895b47a0d36126657b95da383c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2018
ms.locfileid: "37140271"
---
# <a name="foreach-in-c-reference"></a>foreach, in (odwołanie w C#)

`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu. `foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:

- ma publiczny bez parametrów `GetEnumerator` metody, których typ zwracany jest klasy, struktury lub typ interfejsu
- zwracany typ `GetEnumerator` metoda ma publicznego `Current` właściwości i publiczny bez parametrów `MoveNext` metody, których typem zwracanym jest <xref:System.Boolean>.

W dowolnym punktu w `foreach` blok instrukcji, można przerwać poza pętli przy użyciu [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) instrukcji. Możesz również zakończyć działanie `foreach` pętli przez [przejdź do](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie przedstawiono użycie `foreach` instrukcji z wystąpieniem <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

W następnym przykładzie użyto `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsami:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Począwszy od C# 7.3, jeśli modułu wyliczającego `Current` zwraca [odwołują się do wartości zwracanych](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` gdzie `T` jest typ elementu kolekcji), można zadeklarować zmiennej iteracji `ref` lub `ref readonly` modyfikator. W poniższym przykładzie użyto `ref` zmiennej iteracji, aby ustawić wartość każdego elementu w tablicy stackalloc. `ref readonly` Wersji iteruje po kolekcji do wyświetlania wartości. `readonly` Deklaracja korzysta z niejawnych deklaracji zmiennej lokalnej. Niejawne deklaracji zmiennych mogą być używane z albo `ref` lub `ref readonly` deklaracje, jak można jawnie wpisana deklaracji zmiennych.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Instrukcja foreach (specyfikacja języka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Używanie instrukcji foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Instrukcje iteracji](iteration-statements.md)  
[Słowa kluczowe języka C#](index.md)  
[Dokumentacja języka C#](../index.md)  
[Przewodnik programowania w języku C#](../../programming-guide/index.md)  
