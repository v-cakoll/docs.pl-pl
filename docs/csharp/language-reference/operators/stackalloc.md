---
title: operator stackalloc — odwołanie do języka C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846258"
---
# <a name="stackalloc-operator-c-reference"></a>operator stackalloc (odwołanie do języka C#)

Operator `stackalloc` przydziela blok pamięci na stosie. Stos przydzielonego bloku pamięci utworzonego podczas wykonywania metody jest automatycznie odrzucany po zwrocie tej metody. Nie można jawnie zwolnić `stackalloc` pamięci przydzielonej operatorowi. Blok pamięci przydzielonej stosnie nie podlega [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty za pomocą [ `fixed` instrukcji](../keywords/fixed-statement.md).

Wynik `stackalloc` operatora można przypisać do zmiennej jednego z następujących typów:

- Począwszy od Języka C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu podczas przypisywania stosu <xref:System.Span%601> przydzielonego bloku pamięci do lub <xref:System.ReadOnlySpan%601> zmiennej.

  Podczas pracy z tymi typami `stackalloc` można użyć wyrażenia w wyrażeniach [warunkowych](conditional-operator.md) lub przypisanych, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  Począwszy od języka C# 8.0, można użyć `stackalloc` wyrażenia <xref:System.Span%601> <xref:System.ReadOnlySpan%601> wewnątrz innych wyrażeń, gdy lub zmienna jest dozwolone, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Zaleca się <xref:System.Span%601> <xref:System.ReadOnlySpan%601> używanie lub typy do pracy z pamięcią przydzieloną stosu, gdy jest to możliwe.

- [Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Jak pokazano w poprzednim przykładzie, `unsafe` należy użyć kontekstu podczas pracy z typami wskaźników.

  W przypadku typów wskaźników można użyć `stackalloc` wyrażenia tylko w deklaracji zmiennej lokalnej do zainicjowania zmiennej.

Zawartość nowo przydzielonej pamięci jest niezdefiniowana. Począwszy od C# 7.3, można użyć składni inicjatora tablicy do definiowania zawartości nowo przydzielonej pamięci. W poniższym przykładzie przedstawiono różne sposoby, aby to zrobić:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

W `stackalloc T[E]`wyrażeniu musi `T` być `E` [typem niezarządzanym](../builtin-types/unmanaged-types.md) i musi być wyrażeniem typu [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Zabezpieczenia

Użycie `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu w czasie wykonywania języka wspólnego (CLR). W przypadku wykrycia przepełnienia buforu proces jest zakończony tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [alokacji stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) sekcji [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i [zezwolenie w `stackalloc` kontekstach zagnieżdżonych](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) uwaga propozycji funkcji.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory związane ze wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
