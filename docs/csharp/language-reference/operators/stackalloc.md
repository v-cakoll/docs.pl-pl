---
title: operator stackalloc — C# odwołania
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 3be4e827e75e4e26a34d9ed70423af5aa317e7fb
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025001"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc — operator (C# odwołania)

`stackalloc` Operator przydziela blok pamięci na stosie. Stos przydzielony blok pamięci, utworzony podczas wykonywania metody jest automatycznie odrzucane po powrocie z tej metody. Nie można jawnie zwolnić pamięć alokowaną `stackalloc` operatora. Blok pamięci przydzielony stos nie jest podlegają [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypinane z [ `fixed` instrukcji](../keywords/fixed-statement.md).

Możesz przypisać wynik `stackalloc` operatora zmiennej jednego z następujących typów:

- Począwszy od C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Nie trzeba stosować [niebezpieczne](../keywords/unsafe.md) kontekstu po przypisaniu stosu przydzielony blok pamięci, aby <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> zmiennej.

  Podczas pracy z tych typów, można użyć `stackalloc` wyrażenia w [warunkowego](conditional-operator.md) lub wyrażenia przypisania, co ilustruje poniższy przykład:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > Firma Microsoft zaleca używanie <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> typy do pracy z na stosie pamięci, jeśli to możliwe.

- A [typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Jak pokazano na poprzednim przykładzie, należy użyć `unsafe` kontekście podczas pracy z typami wskaźników.

Zawartość nowo przydzielonego pamięci jest niezdefiniowane. Począwszy od C# 7.3, można użyć składni inicjatora tablicy definiowanie zawartości nowo alokacji pamięci. W poniższym przykładzie pokazano różne sposoby, aby to zrobić:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Zabezpieczenia

Korzystanie z `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu, w środowisku uruchomieniowym języka (wspólnego CLR). W przypadku wykrycia przepełnienie buforu tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo, że złośliwy kod jest wykonywany zakończenia procesu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [alokacji stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Wskaźnik związane z operatorów](pointer-related-operators.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
