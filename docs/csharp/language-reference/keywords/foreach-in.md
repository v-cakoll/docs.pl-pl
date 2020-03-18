---
title: C# foreach instrukcji
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: dbe4f4e95c2b99f1be47885e39d51db81ba3a97d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173708"
---
# <a name="foreach-in-c-reference"></a>foreach, w (odwołanie C#)

Instrukcja `foreach` wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu, który implementuje lub interfejsu. Instrukcja `foreach` nie jest ograniczona do tych typów i może być stosowana do wystąpienia dowolnego typu, który spełnia następujące warunki:

- ma publiczną `GetEnumerator` metodę bezparametrową, której typem zwracania jest klasa, struktura lub typ interfejsu,
- zwracany typ `GetEnumerator` metody ma `Current` właściwość publiczną i `MoveNext` publiczną metodę <xref:System.Boolean>bezparametrową, której typem zwracania jest .

Począwszy od C# 7.3, `Current` jeśli właściwość wyliczającego zwraca wartość [zwracaną odwołanie](ref.md#reference-return-values) (gdzie`ref T` `T` jest typem elementu `ref` kolekcji), można zadeklarować zmienną iteracji za pomocą lub `ref readonly` modyfikatora.

Począwszy od Języka C# `await` 8.0, operator `foreach` może być stosowany do <xref:System.Collections.Generic.IAsyncEnumerable%601> instrukcji, gdy typ kolekcji implementuje interfejs. Każda iteracja pętli może zostać zawieszona, gdy następny element jest pobierany asynchronicznie. Domyślnie elementy strumienia są przetwarzane w kontekście przechwyconego. Jeśli chcesz wyłączyć przechwytywanie kontekstu, należy użyć metody <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł na [temat korzystania z wzorca asynchronicznego opartego](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniu .

W dowolnym momencie `foreach` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break](break.md) lub przejść do następnej iteracji w pętli przy użyciu [instrukcji continue.](continue.md) Możesz również wyjść `foreach` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

Jeśli `foreach` instrukcja jest `null`stosowana <xref:System.NullReferenceException> do , a jest wyrzucany. Jeśli źródło kolekcji `foreach` instrukcji jest pusta, `foreach` treść pętli nie jest wykonywana i pomijane.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie `foreach` przedstawiono użycie instrukcji <xref:System.Collections.Generic.List%601> z wystąpieniem <xref:System.Collections.Generic.IEnumerable%601> typu, który implementuje interfejs:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

W następnym przykładzie `foreach` użyto instrukcji <xref:System.Span%601?displayProperty=nameWithType> z wystąpieniem typu, który nie implementuje żadnych interfejsów:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

W poniższym `ref` przykładzie użyto zmiennej iteracji, aby ustawić wartość każdego elementu w tablicy stackalloc. Wersja `ref readonly` iteruje kolekcję, aby wydrukować wszystkie wartości. Deklaracja `readonly` używa niejawnej deklaracji zmiennej lokalnej. Niejawne deklaracje zmiennych `ref` `ref readonly` mogą być używane z jedną lub deklaracjami, podobnie jak jawnie wpisywane deklaracje zmiennych.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

W poniższym `await foreach` przykładzie użyto do iterate kolekcji, która generuje każdy element asynchronicznie:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcja instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Korzystanie z foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [dla oświadczenia](for.md)
