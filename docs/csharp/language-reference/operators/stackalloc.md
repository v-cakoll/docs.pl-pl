---
title: operator stackalloc — C# odwołanie
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 5654cae622cd94c8dad7e58fbc8a99fcf48391a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712627"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc — operatorC# (odwołanie)

Operator `stackalloc` przydziela blok pamięci na stosie. Blok pamięci przydzielony przez stos utworzony podczas wykonywania metody jest automatycznie usuwany, gdy ta metoda zwraca. Nie można jawnie zwolnić pamięci przydzieloną za pomocą operatora `stackalloc`. Przydzielony blok pamięci stosu nie podlega [wyrzucaniu elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty za pomocą [instrukcji`fixed`](../keywords/fixed-statement.md).

Wynik operatora `stackalloc` można przypisać do zmiennej jednego z następujących typów:

- Począwszy od C# 7,2, <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano na poniższym przykładzie:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu, gdy przypiszesz blok pamięci przydzielony przez stos do zmiennej <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601>.

  Podczas pracy z tymi typami można użyć wyrażenia `stackalloc` w wyrażeniach [warunkowych](conditional-operator.md) lub przypisywania, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  Począwszy od C# 8,0, można użyć wyrażenia `stackalloc` w innych wyrażeniach za każdym razem, gdy zmienna <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> jest dozwolona, jak pokazano na poniższym przykładzie:

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Zaleca się używanie typów <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> do pracy z przydzieloną pamięcią, jeśli to możliwe.

- [Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano na poniższym przykładzie:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Jak pokazano w powyższym przykładzie, należy użyć kontekstu `unsafe` podczas pracy z typami wskaźników.

  W przypadku typów wskaźnika można użyć wyrażenia `stackalloc` tylko w deklaracji zmiennej lokalnej, aby zainicjować zmienną.

Zawartość nowo przydzieloną pamięci jest niezdefiniowana. Począwszy od C# 7,3, można użyć składni inicjatora tablicy do zdefiniowania zawartości nowo przydzieloną pamięć. Poniższy przykład ilustruje różne sposoby, aby to zrobić:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

W `stackalloc T[E]`Expression `T` musi być [typem niezarządzanym](../builtin-types/unmanaged-types.md) , a `E` musi być wyrażeniem typu [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Zabezpieczenia

Użycie `stackalloc` powoduje automatyczne włączenie funkcji wykrywania przepełnienia buforu w środowisku uruchomieniowym języka wspólnego (CLR). Jeśli wykryto przepełnienie buforu, proces zostaje zakończony jak najszybciej, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zapoznaj się z sekcją [Alokacja stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) w temacie [ C# Specyfikacja języka](~/_csharplang/spec/introduction.md) i opcja [Zezwalaj `stackalloc` w przypadku zagnieżdżonych kontekstów](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory powiązane z wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
