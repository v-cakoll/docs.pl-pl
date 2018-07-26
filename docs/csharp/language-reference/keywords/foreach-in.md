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
ms.openlocfilehash: a6397cdc9d1e36423a14158a57ca2c1b3fe9df17
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874965"
---
# <a name="foreach-in-c-reference"></a>foreach, in (odwołanie w C#)

`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w określonym wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu. `foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:

- ma publiczny bez parametrów `GetEnumerator` metody, którego typem zwracanym jest klasy, struktury lub typ interfejsu
- zwracany typ `GetEnumerator` metoda ma publiczny `Current` właściwość i publiczny bez parametrów `MoveNext` metody, którego typem zwracanym jest <xref:System.Boolean>.

W dowolnym punkcie w `foreach` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli za pomocą [nadal](continue.md) instrukcji. Możesz również wyjść `foreach` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie pokazano użycie `foreach` instrukcję, określając wystąpienie <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

W następnym przykładzie użyto `foreach` instrukcję, określając wystąpienie <xref:System.Span%601?displayProperty=nameWithType> typ, który nie implementuje żadnych interfejsów:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Począwszy od C# 7.3, jeśli moduł wyliczający `Current` właściwość zwraca [odwoływać się do wartości zwracanej](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` gdzie `T` jest typ elementu kolekcji), można zadeklarować zmiennej iteracji `ref` lub `ref readonly` modyfikator. W poniższym przykładzie użyto `ref` Zmienna iteracji można ustawić wartości dla każdego elementu w tablicy stackalloc. `ref readonly` Wersji iteruje po kolekcji do wyświetlania wartości. `readonly` Deklaracji używa niejawne deklaracji zmiennej lokalnej. Niejawne deklaracje zmiennej może być używany z albo `ref` lub `ref readonly` deklaracji, jak można jawnie wpisane deklaracje zmiennych.

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

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
