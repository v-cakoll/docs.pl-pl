---
title: Operatory przypisania — odwołanie do języka C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399253"
---
# <a name="assignment-operators-c-reference"></a>Operatory przydziałów (odwołanie do języka C#)

Operator `=` przypisania przypisuje wartość jego prawostronnego operandu do zmiennej, [właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu [indeksatora](../../programming-guide/indexers/index.md) podanego przez jego argument po lewej stronie. Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie. Typ argumentu po prawej stronie musi być taki sam jak typ lewego operandu lub niejawnie kabriolet do niego.

Operator `=` przypisania jest zeswany, to oznacza, że wyrażenie formularza

```csharp
a = b = c
```

jest oceniana jako

```csharp
a = (b = c)
```

W poniższym przykładzie przedstawiono użycie operatora przypisania ze zmienną lokalną, właściwością i elementem indeksatora jako jego argumentpowe po lewej stronie:

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operator przypisania ref

Począwszy od C# 7.3, można `= ref` użyć operatora przypisania ref do ponownego przypisania [ref lokalnej](../keywords/ref.md#ref-locals) lub [ref readonly](../keywords/ref.md#ref-readonly-locals) zmiennej lokalnej. W poniższym przykładzie przedstawiono użycie operatora przypisania ref:

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

W przypadku operatora przypisania ref oba jego operandy muszą być tego samego typu.

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

chyba `x` że jest oceniana tylko raz.

Przypisanie złożone jest obsługiwane przez operatory [arytmetyczne,](arithmetic-operators.md#compound-assignment) [logiczne logiczne logiczne](boolean-logical-operators.md#compound-assignment)i [bitowe logiczne i przesuwne.](bitwise-and-shift-operators.md#compound-assignment)

## <a name="null-coalescing-assignment"></a>Przypisanie łączenia wartości null

Począwszy od języka C# 8.0, można użyć operatora `??=` przypisania zerowego łączenia przypisać przypisać przypisać wartość jego operand po prawej stronie do jego `null`operand po lewej stronie tylko wtedy, gdy po lewej stronie operand ocenia . Aby uzyskać więcej informacji, zobacz [?? i ?? = artykuł operatorów.](null-coalescing-operator.md)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika nie może [przeciążać](operator-overloading.md) operatora przypisania. Jednak typ zdefiniowany przez użytkownika można zdefiniować niejawną konwersję na inny typ. W ten sposób wartość typu zdefiniowanego przez użytkownika można przypisać do zmiennej, właściwości lub elementu indeksatora innego typu. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego. Jednak jeśli typ zdefiniowany przez użytkownika `op`przeciąża operatora binarnego, `op=` operator, jeśli istnieje, jest również niejawnie przeciążony.

## <a name="c-language-specification"></a>specyfikacja języka C#

For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji `= ref`na temat operatora przypisania ref, zobacz [propozycję funkcji .](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [ref — słowo kluczowe](../keywords/ref.md)
