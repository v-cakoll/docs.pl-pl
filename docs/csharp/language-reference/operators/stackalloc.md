---
title: operator stackalloc — C# odwołanie
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: f211acaa8c47ab42a1f7f06cff6c35570cd22b75
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433827"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc — operatorC# (odwołanie)

`stackalloc` Operator przydziela blok pamięci na stosie. Blok pamięci przydzielony przez stos utworzony podczas wykonywania metody jest automatycznie usuwany, gdy ta metoda zwraca. Nie można jawnie zwolnić pamięci przydzieloną z `stackalloc` operatorem. Przydzielony blok pamięci stosu nie podlega wyrzucaniu [elementów](../../../standard/garbage-collection/index.md) bezużytecznych i nie musi być przypięty za pomocą [ `fixed` instrukcji](../keywords/fixed-statement.md).

W `stackalloc T[E]`wyrażeniu `T` element musi być [typem](../builtin-types/unmanaged-types.md) niezarządzanym i `E` musi być wyrażeniem `int`typu.

Można przypisać wynik `stackalloc` operatora do zmiennej jednego z następujących typów:

- Począwszy od C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano na poniższym przykładzie:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Nie trzeba używać niebezpiecznego [](../keywords/unsafe.md) kontekstu, gdy przypiszesz blok pamięci przydzielony przez stos do <xref:System.Span%601> zmiennej <xref:System.ReadOnlySpan%601> lub.

  Podczas pracy z tymi typami można użyć `stackalloc` wyrażenia w wyrażeniach [warunkowych](conditional-operator.md) lub przypisywania, jak pokazano na poniższym przykładzie:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > Zalecamy używanie <xref:System.Span%601> lub typy <xref:System.ReadOnlySpan%601> do pracy z przydzieloną pamięcią stosu, jeśli jest to możliwe.

- [Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano na poniższym przykładzie:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Jak pokazano w powyższym przykładzie, należy użyć `unsafe` kontekstu podczas pracy z typami wskaźników.

Zawartość nowo przydzieloną pamięci jest niezdefiniowana. Począwszy od C# 7,3, można użyć składni inicjatora tablicy do zdefiniowania zawartości nowo przydzieloną pamięć. Poniższy przykład ilustruje różne sposoby, aby to zrobić:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Zabezpieczenia

Korzystanie z programu `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu w środowisku uruchomieniowym języka wspólnego (CLR). Jeśli wykryto przepełnienie buforu, proces zostaje zakończony jak najszybciej, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Alokacja stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory powiązane z wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
