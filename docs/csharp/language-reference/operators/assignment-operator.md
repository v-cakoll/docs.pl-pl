---
title: = odwołanie do C# operatora
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: f30b48fc6bd1e896658a7234a58409ea9a0f5e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601945"
---
# <a name="-operator-c-reference"></a>= — operatorC# (odwołanie)

Operator `=` przypisania przypisuje wartość jego operandu po prawej stronie do zmiennej, [Właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu indeksatora podanym [](../../programming-guide/indexers/index.md) przez operand z lewej strony. Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie. Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie lub niejawnie konwertowany.

Operator przypisania jest prawym przyciskiem asocjacyjnym, czyli wyrażeniem formularza

```csharp
a = b = c
```

jest wykonywane jako

```csharp
a = (b = c)
```

Poniższy przykład ilustruje użycie operatora przypisania ze zmienną lokalną, właściwością i elementem indeksatora jako swój argument operacji po lewej stronie:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operator przypisania ref

Począwszy od C# 7,3, można użyć operatora `= ref` przypisania odwołania, aby ponownie przypisać [lokalną](../keywords/ref.md#ref-locals) zmienną lokalną lub [ref tylko do odczytu](../keywords/ref.md#ref-readonly-locals) . Poniższy przykład ilustruje użycie operatora przypisania odwołania:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

W przypadku operatora przypisania ref typ obu argumentów operacji musi być taki sam.

Aby uzyskać więcej informacji, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora `op`binarnego wyrażenie złożonego przypisania formularza

```csharp
x op= y
```

odpowiada wyrażeniu

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczany tylko raz.

Przypisanie złożone jest obsługiwane przez [arytmetyczne](arithmetic-operators.md#compound-assignment)operatory logiczne logiczne [i bitowe](bitwise-and-shift-operators.md#compound-assignment) . [](boolean-logical-operators.md#compound-assignment)

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie może przeciążać operatora przypisania. Jednak typ zdefiniowany przez użytkownika może definiować niejawną konwersję na inny typ. W ten sposób wartość typu zdefiniowanego przez użytkownika może być przypisana do zmiennej, właściwości lub elementu indeksatora innego typu. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) w [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [ref keyword](../keywords/ref.md)
