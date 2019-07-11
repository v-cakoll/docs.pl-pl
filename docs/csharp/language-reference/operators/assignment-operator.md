---
title: = — operator - C# odwołania
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 1277b35723777760deebb6606ddc90bd21e654ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744119"
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

Poniższy przykład ilustruje użycie operatora przypisania, za pomocą zmiennej lokalnej, właściwości i elementu indeksatora jako jej argument po lewej stronie:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operator przypisania REF

Począwszy od C# 7.3, można użyć operatora przypisania `= ref` do ponownego przypisania [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej. Poniższy przykład ilustruje użycie operatora przypisania:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

W przypadku operatora przypisania typ obu argumentów musi być taka sama.

Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="compound-assignment"></a>Przydział złożony

Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

odpowiada wyrażeniu

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczany tylko raz.

Przypisania złożonego jest obsługiwana przez [arytmetyczne](arithmetic-operators.md#compound-assignment), [Boolean logiczna](boolean-logical-operators.md#compound-assignment), i [bitowe logicznej- and -shift](bitwise-and-shift-operators.md#compound-assignment) operatorów.

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie mogą przeciążać operatora przypisania. Typ zdefiniowany przez użytkownika można jednak zdefiniować niejawną konwersję do innego typu. Dzięki temu wartość typu zdefiniowanego przez użytkownika można przypisać do zmiennej, właściwość lub indeksator elementu innego typu. Aby uzyskać więcej informacji, zobacz [konwersja zdefiniowana przez użytkownika operatory](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [ref keyword](../keywords/ref.md)
