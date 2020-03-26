---
title: wyrażenie stackalloc — odwołanie do języka C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546604"
---
# <a name="stackalloc-expression-c-reference"></a>wyrażenie stackalloc (odwołanie do języka C#)

Wyrażenie `stackalloc` przydziela blok pamięci na stosie. Blok pamięci przydzielony stos utworzony podczas wykonywania metody jest automatycznie odrzucany, gdy ta metoda zwraca. Nie można jawnie zwolnić `stackalloc`pamięci przydzielonej za pomocą programu . Blok pamięci przydzielony do stosu nie podlega [wyrzucaniu elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty [ `fixed` za](../keywords/fixed-statement.md)pomocą instrukcji .

Wynik `stackalloc` wyrażenia można przypisać do zmiennej jednego z następujących typów:

- Począwszy od C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu podczas przypisywania bloku pamięci <xref:System.Span%601> <xref:System.ReadOnlySpan%601> przydzielonego stosu do lub zmiennej.

  Podczas pracy z tymi typami `stackalloc` można użyć wyrażenia w wyrażeniach [warunkowych](conditional-operator.md) lub przypisanych, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  Począwszy od języka C# 8.0, można użyć `stackalloc` wyrażenia <xref:System.Span%601> <xref:System.ReadOnlySpan%601> wewnątrz innych wyrażeń, gdy jest dozwolone lub zmiennej, jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Zaleca się <xref:System.Span%601> <xref:System.ReadOnlySpan%601> używanie lub typy do pracy z pamięcią przydzieloną do stosu, gdy tylko jest to możliwe.

- [Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano w poniższym przykładzie:

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Jak pokazano w poprzednim przykładzie, `unsafe` należy użyć kontekstu podczas pracy z typami wskaźników.

  W przypadku typów wskaźników można użyć `stackalloc` wyrażenia tylko w deklaracji zmiennej lokalnej, aby zainicjować zmienną.

Ilość pamięci dostępnej na stosie jest ograniczona. Jeśli przydzielić zbyt dużo pamięci <xref:System.StackOverflowException> na stosie, a jest wyrzucany. Aby tego uniknąć, postępuj zgodnie z poniższymi zasadami:

- Ogranicz ilość pamięci `stackalloc`przydzielanej za pomocą:

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  Ponieważ ilość pamięci dostępnej na stosie zależy od środowiska, w którym kod jest wykonywany, zachowawczego podczas definiowania rzeczywistej wartości dopuszczalnej.

- Unikaj `stackalloc` używania wewnętrznych pętli. Przydzielić blok pamięci poza pętlę i użyć go ponownie wewnątrz pętli.

Zawartość nowo przydzielonej pamięci jest niezdefiniowana. Należy go zainicjować przed użyciem. Na przykład można użyć <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> metody, która ustawia wszystkie elementy `T`na domyślną wartość typu .

Począwszy od języka C# 7.3, można użyć składni inicjatora tablicy do definiowania zawartości pamięci nowo przydzielonej. W poniższym przykładzie przedstawiono różne sposoby, aby to zrobić:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

W `stackalloc T[E]`wyrażeniu musi `T` być `E` [typem niezarządzanym](../builtin-types/unmanaged-types.md) i musi być wartością [int](../builtin-types/integral-numeric-types.md) nieujemną.

## <a name="security"></a>Zabezpieczenia

Użycie funkcji `stackalloc` automatycznego wykrywania przepełnienia buforu w czasie wykonywania języka wspólnego (CLR). Jeśli zostanie wykryte przepełnienie buforu, proces zostanie zakończony tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Alokacja stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i [Zezwolenie `stackalloc` w kontekstach zagnieżdżonych](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) uwaga propozycji funkcji.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory związane ze wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
- [Dos i nie stosalloc](https://vcsjones.dev/2020/02/24/stackalloc/)
