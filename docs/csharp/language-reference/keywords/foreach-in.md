---
title: Instrukcja "foreach" języka C#
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401891"
---
# <a name="foreach-in-c-reference"></a>foreach, in (odwołanie w C#)

`foreach`Instrukcja wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs lub. `foreach`Instrukcja nie jest ograniczona do tych typów i może być stosowana do wystąpienia dowolnego typu, który spełnia następujące warunki:

- ma publiczną metodę bez parametrów `GetEnumerator` , której typem zwracanym jest Klasa, struktura lub typ interfejsu,
- zwracany typ `GetEnumerator` metody ma właściwość publiczną `Current` i publiczną metodę bez parametrów, `MoveNext` której typem zwracanym jest <xref:System.Boolean> .

W większości przypadków, `foreach` iteruje `IEnumerable<T>` wyrażenie, gdzie każdy element jest typu `T` . Jednakże elementy mogą być dowolnego typu, który ma niejawną lub jawną konwersję z typu `Current` właściwości. Jeśli `Current` właściwość zwróci wartość `SomeType` , typem elementów mogą być:

- Dowolna z klas bazowych `SomeType` .
- Wszystkie interfejsy zaimplementowane przez `SomeType` .

Ponadto, jeśli `SomeType` jest `class` lub `interface` a i nie `sealed` , typ elementów może obejmować:

- Dowolny typ pochodzący od `SomeType` .
- Dowolny dowolny interfejs. Dowolny interfejs jest dozwolony, ponieważ dowolny interfejs może być zaimplementowany przez klasę pochodną lub implementującą `SomeType` .

Można zadeklarować zmienną iteracji przy użyciu dowolnego typu, który jest zgodny z poprzednimi regułami. Jeśli konwersja z `SomeType` do typu zmiennej iteracji wymaga jawnego rzutowania, operacja może zgłosić wyjątek, <xref:System.InvalidCastException> gdy konwersja zakończy się niepowodzeniem.

Począwszy od języka C# 7,3, jeśli właściwość modułu wyliczającego `Current` zwróci [wartość zwracaną odwołania](ref.md#reference-return-values) ( `ref T` gdzie `T` jest typem elementu kolekcji), można zadeklarować zmienną iteracji za pomocą `ref` `ref readonly` modyfikatora or.

Począwszy od języka C# 8,0, `await` operator może zostać zastosowany do `foreach` instrukcji, gdy typ kolekcji implementuje <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs. Każda iteracja pętli może zostać zawieszona, podczas gdy następny element jest pobierany asynchronicznie. Domyślnie elementy strumienia są przetwarzane w przechwyconym kontekście. Jeśli chcesz wyłączyć przechwytywanie kontekstu, użyj <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metody rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [konsumowania wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

W dowolnym momencie w `foreach` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) . Możesz również wyjść z `foreach` pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .

Jeśli `foreach` instrukcja jest zastosowana do `null` , <xref:System.NullReferenceException> jest zgłaszany. Jeśli kolekcja źródłowa `foreach` instrukcji jest pusta, treść `foreach` pętli nie zostanie wykonana i pominięta.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie pokazano użycie `foreach` instrukcji z wystąpieniem <xref:System.Collections.Generic.List%601> typu implementującego <xref:System.Collections.Generic.IEnumerable%601> Interfejs:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

W następnym przykładzie używa się `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsów:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

Poniższy przykład używa `ref` zmiennej iteracji w celu ustawienia wartości każdego elementu w tablicy stackalloc. `ref readonly`Wersja wykonuje iterację kolekcji w celu wydrukowania wszystkich wartości. `readonly`Deklaracja używa niejawnej deklaracji zmiennej lokalnej. Deklaracje zmiennych niejawnych mogą być używane z deklaracjami `ref` lub `ref readonly` , jak można jawnie wpisać deklaracje zmiennych.

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

Poniższy przykład używa `await foreach` do iterowania kolekcji, która generuje każdy element asynchronicznie:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz też

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Używanie instrukcji foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for, instrukcja](for.md)
