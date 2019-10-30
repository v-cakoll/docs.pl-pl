---
title: Operatory przypisania — C# odwołanie
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 103bc823ab6a56d53a3f2ec05b8de9295f1de400
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039078"
---
# <a name="assignment-operators-c-reference"></a>Operatory przypisania (C# odwołanie)

Operator przypisania `=` przypisuje wartość operandu po prawej stronie do zmiennej, [Właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu [indeksatora](../../programming-guide/indexers/index.md) podaną przez jego operand po lewej stronie. Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie. Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie lub niejawnie konwertowany.

Operator przypisania `=` jest prawym przyciskiem asocjacyjnym, czyli wyrażeniem formularza

```csharp
a = b = c
```

jest oceniane jako

```csharp
a = (b = c)
```

Poniższy przykład ilustruje użycie operatora przypisania ze zmienną lokalną, właściwością i elementem indeksatora jako swój argument operacji po lewej stronie:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operator przypisania ref

Począwszy od C# 7,3, można użyć operatora przypisania ref`= ref`do ponownego [przypisania lokalnej zmiennej lokalnej lub](../keywords/ref.md#ref-locals) [ref tylko do odczytu](../keywords/ref.md#ref-readonly-locals) . Poniższy przykład ilustruje użycie operatora przypisania odwołania:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

W przypadku operatora przypisania odwołania, oba operandy muszą być tego samego typu.

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczana tylko raz.

Przypisanie złożone jest obsługiwane przez [arytmetyczne](arithmetic-operators.md#compound-assignment)operatory [logiczne logiczne](boolean-logical-operators.md#compound-assignment) [i bitowe](bitwise-and-shift-operators.md#compound-assignment) .

## <a name="null-coalescing-assignment"></a>Przypisanie do łączenia o wartości null

Począwszy od C# 8,0, można użyć operatora przypisania łączącego wartości null`??=`, aby przypisać wartość jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie jest obliczany do`null`. Aby uzyskać więcej informacji, zobacz [? =](null-coalescing-operator.md) — artykuł.

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie może [przeciążać](operator-overloading.md) operatora przypisania. Jednak typ zdefiniowany przez użytkownika może definiować niejawną konwersję na inny typ. W ten sposób wartość typu zdefiniowanego przez użytkownika może być przypisana do zmiennej, właściwości lub elementu indeksatora innego typu. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania. Jeśli jednak typ zdefiniowany przez użytkownika przeciąża operator binarny `op`, operator `op=`, jeśli istnieje, jest również niejawnie przeciążony.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji na temat `= ref`operatora przypisania odwołania, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [ref — słowo kluczowe](../keywords/ref.md)
