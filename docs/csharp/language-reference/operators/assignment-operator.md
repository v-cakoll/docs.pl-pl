---
title: = odwołanie do C# operatora
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: a450a55524f33f4f06ed077aba864e8f641a458d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924657"
---
# <a name="-operator-c-reference"></a>= — operatorC# (odwołanie)

Operator `=` przypisania przypisuje wartość jego operandu po prawej stronie do zmiennej, [Właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu [indeksatora](../../programming-guide/indexers/index.md) podanym przez operand z lewej strony. Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie. Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie lub niejawnie konwertowany.

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

Przypisanie złożone jest obsługiwane przez [arytmetyczne](arithmetic-operators.md#compound-assignment)operatory [logiczne logiczne](boolean-logical-operators.md#compound-assignment) [i bitowe](bitwise-and-shift-operators.md#compound-assignment) .

## <a name="null-coalescing-assignment"></a>Przypisanie do łączenia o wartości null

Począwszy od C# 8,0, można użyć operatora `??=` przypisania łączącego wartości null do przypisania wartości jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie ma `null`wartość. Aby uzyskać więcej informacji, zobacz [? =](null-coalescing-operator.md) — artykuł.

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie może przeciążać operatora przypisania. Jednak typ zdefiniowany przez użytkownika może definiować niejawną konwersję na inny typ. W ten sposób wartość typu zdefiniowanego przez użytkownika może być przypisana do zmiennej, właściwości lub elementu indeksatora innego typu. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) w [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [ref keyword](../keywords/ref.md)
