---
title: Instrukcja foreach języka C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738814"
---
# <a name="foreach-in-c-reference"></a>foreach, w (odwołanie C#)

Instrukcja `foreach` wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu, który implementuje lub interfejs. Instrukcja `foreach` nie jest ograniczona do tych typów i może być stosowana do wystąpienia dowolnego typu, które spełnia następujące warunki:

- ma publiczną `GetEnumerator` metodę bez parametrów, której typem zwracanym jest klasa, struktura lub typ interfejsu,
- typ zwracany `GetEnumerator` metody ma `Current` właściwość publiczną `MoveNext` i metodę public <xref:System.Boolean>bez parametrów, której typem zwracanym jest .

Począwszy od języka C# 7.3, jeśli `Current` właściwość wyliczacza zwraca [wartość zwracaną odwołanie](ref.md#reference-return-values) (gdzie`ref T` `T` jest typem `ref` `ref readonly` elementu kolekcji), można zadeklarować zmienną iteracji za pomocą lub modyfikatora.

Począwszy od języka C# 8.0, `await` operator `foreach` może być stosowany do <xref:System.Collections.Generic.IAsyncEnumerable%601> instrukcji, gdy typ kolekcji implementuje interfejs. Każda iteracja pętli może zostać zawieszona, podczas gdy następny element jest pobierany asynchronicznie. Domyślnie elementy strumienia są przetwarzane w kontekście przechwycone. Jeśli chcesz wyłączyć przechwytywanie kontekstu, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> użyj metody rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [korzystania z wzorca asynchronicznego opartego](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniach .

W dowolnym momencie w bloku `foreach` instrukcji można wyrwać z pętli przy użyciu [break](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [continue](continue.md) instrukcji. Można również wyjść `foreach` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

Jeśli `foreach` instrukcja jest `null`stosowana <xref:System.NullReferenceException> do , a jest generowany. Jeśli kolekcja źródło `foreach` instrukcji jest pusta, `foreach` treść pętli nie jest wykonywana i pomijana.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy przykład pokazuje `foreach` użycie instrukcji z <xref:System.Collections.Generic.List%601> wystąpieniem typu, <xref:System.Collections.Generic.IEnumerable%601> który implementuje interfejs:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

W następnym przykładzie `foreach` użyto instrukcji <xref:System.Span%601?displayProperty=nameWithType> z wystąpieniem typu, które nie implementuje żadnych interfejsów:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

W poniższym przykładzie użyto zmiennej `ref` iteracji, aby ustawić wartość każdego elementu w tablicy stackalloc. Wersja `ref readonly` iteruje kolekcji, aby wydrukować wszystkie wartości. Deklaracja `readonly` używa niejawnej deklaracji zmiennej lokalnej. Niejawne deklaracje zmiennych `ref` mogą `ref readonly` być używane z deklaracjami lub deklaracjami, podobnie jak jawnie wpisane deklaracje zmiennych.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

Poniższy `await foreach` przykład używa do iteracji kolekcji, która generuje każdy element asynchronicznie:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [foreach instrukcji](~/_csharplang/spec/statements.md#the-foreach-statement) sekcji [specyfikacji języka języka C #,](/dotnet/csharp/language-reference/language-specification/introduction)aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [Korzystanie z foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [dla oświadczenia](for.md)
