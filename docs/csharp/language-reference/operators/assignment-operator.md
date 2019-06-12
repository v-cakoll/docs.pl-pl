---
title: = — operator - C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 6b8f67f32287b18a9e4ac8f0fa822f6ca4919e7f
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025265"
---
# <a name="-operator-c-reference"></a>= — operator (C# odwołania)

Operator przypisania `=` wartość jego prawostronny operand jest przypisywany do zmiennej, [właściwość](../../programming-guide/classes-and-structs/properties.md), lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) elementu przez jej argument po lewej stronie. Wynikiem wyrażenia przypisania jest wartość przypisana do lewostronny operand. Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie, albo niejawnie przekonwertować do niego.

Operator przypisania ma łączność do prawej strony, oznacza to, że wyrażenie formularza

```csharp
a = b = c
```

jest wykonywane jako

```csharp
a = (b = c)
```

Poniższy przykład ilustruje użycie operatora przypisania do przypisywania wartości do zmiennej lokalnej, właściwości i elementu indeksatora:

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a>operator przypisania REF

Począwszy od C# 7.3, można użyć operatora przypisania `= ref` do ponownego przypisania [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej. Poniższy przykład ilustruje użycie operatora przypisania:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

W przypadku operatora przypisania typ operandu po lewej stronie i prawy operand musi być taka sama.

Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie mogą przeciążać operatora przypisania. Typ zdefiniowany przez użytkownika można jednak zdefiniować niejawną konwersję do innego typu. Dzięki temu wartość typu zdefiniowanego przez użytkownika można przypisać do zmiennej, właściwość lub indeksator elementu innego typu. Aby uzyskać więcej informacji, zobacz [niejawne](../keywords/implicit.md) artykułu — słowo kluczowe.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przypisanie proste](~/_csharplang/spec/expressions.md#simple-assignment) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [ref keyword](../keywords/ref.md)
