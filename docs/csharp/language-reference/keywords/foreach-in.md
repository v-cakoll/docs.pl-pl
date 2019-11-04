---
title: C#Instrukcja foreach
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422799"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# odwołanie)

Instrukcja `foreach` wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje interfejs <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Instrukcje `foreach` nie są ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:

- ma publiczną metodę `GetEnumerator` bez parametrów, której typem zwracanym jest Klasa, struktura lub typ interfejsu,
- zwracany typ metody `GetEnumerator` ma Właściwość Public `Current` i publiczną metodę `MoveNext` bezparametrową, której typem zwracanym jest <xref:System.Boolean>.

Począwszy od C# 7,3, jeśli właściwość `Current` modułu wyliczającego zwróci [wartość zwracaną odwołania](ref.md#reference-return-values) (`ref T` gdzie `T` jest typem elementu kolekcji), Zmienna iteracji można zadeklarować za pomocą modyfikatora `ref` lub `ref readonly`.

W dowolnym momencie w bloku instrukcji `foreach` można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) . Możesz również wyjść z pętli `foreach` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .

Jeśli do `null`zostanie zastosowana instrukcja `foreach`, zostanie zgłoszony <xref:System.NullReferenceException>. Jeśli kolekcja źródłowa instrukcji `foreach` jest pusta, treść pętli `foreach` nie zostanie wykonana i pominięta.

## <a name="examples"></a>Przykłady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie pokazano użycie instrukcji `foreach` z wystąpieniem typu <xref:System.Collections.Generic.List%601>, który implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

W następnym przykładzie używamy instrukcji `foreach` z wystąpieniem typu <xref:System.Span%601?displayProperty=nameWithType>, który nie implementuje interfejsów:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Poniższy przykład używa zmiennej iteracji `ref`, aby ustawić wartość każdego elementu w tablicy stackalloc. Wersja `ref readonly` wykonuje iterację kolekcji w celu wydrukowania wszystkich wartości. Deklaracja `readonly` używa niejawnej deklaracji zmiennej lokalnej. Deklaracje zmiennych niejawnych mogą być używane z deklaracjami `ref` lub `ref readonly`, jak można jawnie wprowadzać deklaracje zmiennych.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Używanie instrukcji foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for — instrukcja](for.md)
