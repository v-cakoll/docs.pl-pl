---
title: Instrukcja "foreach" języka C#
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 4af431d29e538c1516efeaad3008eaa3b2229ece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104244"
---
# <a name="foreach-in-c-reference"></a>foreach, in (odwołanie w C#)

`foreach`Instrukcja wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs lub, jak pokazano w poniższym przykładzie:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

`foreach`Instrukcja nie jest ograniczona do tych typów. Można jej użyć z wystąpieniem dowolnego typu, który spełnia następujące warunki:

- Typ ma publiczną metodę bez parametrów `GetEnumerator` , której typem zwracanym jest Klasa, struktura lub typ interfejsu,
- zwracany typ `GetEnumerator` metody ma właściwość publiczną `Current` i publiczną metodę bez parametrów, `MoveNext` której typem zwracanym jest <xref:System.Boolean> .

Poniższy przykład używa `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsów:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

Począwszy od języka C# 7,3, jeśli właściwość modułu wyliczającego `Current` zwróci [wartość zwracaną odwołania](ref.md#reference-return-values) ( `ref T` gdzie `T` jest typem elementu kolekcji), można zadeklarować zmienną iteracji z `ref` `ref readonly` modyfikatorem or, jak pokazano w poniższym przykładzie:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

Począwszy od języka C# 8,0, można użyć `await foreach` instrukcji, aby wykorzystać asynchroniczny strumień danych, czyli typ kolekcji implementującej <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs. Każda iteracja pętli może zostać zawieszona, podczas gdy następny element jest pobierany asynchronicznie. Poniższy przykład pokazuje, jak używać `await foreach` instrukcji:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

Domyślnie elementy strumienia są przetwarzane w przechwyconym kontekście. Jeśli chcesz wyłączyć przechwytywanie kontekstu, użyj <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metody rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz [Używanie wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md). Aby uzyskać więcej informacji o strumieniach asynchronicznych, zobacz sekcję " [strumienie asynchroniczne](../../whats-new/csharp-8.md#asynchronous-streams) " [w artykule Co nowego w języku C# 8,0](../../whats-new/csharp-8.md) .

W dowolnym momencie w `foreach` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) . Możesz również wyjść z `foreach` pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .

Jeśli `foreach` instrukcja jest zastosowana do `null` , <xref:System.NullReferenceException> jest zgłaszany. Jeśli kolekcja źródłowa `foreach` instrukcji jest pusta, treść `foreach` pętli nie zostanie wykonana i pominięta.

## <a name="type-of-an-iteration-variable"></a>Typ zmiennej iteracji

Możesz użyć `var` słowa kluczowego, aby zezwolić kompilatorowi na wnioskowanie typu zmiennej iteracji w `foreach` instrukcji, jak pokazano w poniższym kodzie:

```csharp
foreach (var item in collection) { }
```

Można również jawnie określić typ zmiennej iteracji, jak pokazano w poniższym kodzie:

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

W poprzednim formularzu typ `T` elementu kolekcji musi być niejawnie lub jawnie konwertowany na typ `V` zmiennej iteracji. Jeśli jawna konwersja z elementu `T` do `V` nie powiedzie się w czasie wykonywania, `foreach` instrukcja zgłosi <xref:System.InvalidCastException> . Na przykład, jeśli `T` jest typem klasy niezapieczętowanej, `V` może być dowolnego typu interfejsu, nawet tego, który `T` nie implementuje. W czasie wykonywania, typ elementu kolekcji może być tym, który pochodzi od `T` i faktycznie implementuje `V` . Jeśli tak się nie dzieje, <xref:System.InvalidCastException> jest zgłaszany.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Używanie instrukcji foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for, instrukcja](for.md)
