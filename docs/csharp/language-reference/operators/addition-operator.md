---
title: + operatory += — i C# odwołania
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 258adc45fc6874cca5829479eef1196ebea1e300
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347975"
---
# <a name="-and--operators-c-reference"></a>+ i operatory += (C# odwołania)

`+` Operator jest obsługiwany przez wbudowane typy liczbowe [ciąg](../keywords/string.md) typu, i [delegować](../keywords/delegate.md) typów.

Aby uzyskać informacje o operacji arytmetycznych `+` operatora, zobacz [jednoargumentowe plus lub minus operatory](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator dodawania +](arithmetic-operators.md#addition-operator-) sekcje [operatorów arytmetycznych](arithmetic-operators.md)artykułu.

## <a name="string-concatenation"></a>{1&gt;Łączenie ciągów&lt;1}

Kiedy jeden lub obydwa operandy są typu [ciąg](../keywords/string.md), `+` operator łączy ciągów reprezentujących argumentów:

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodny sposób na ciągi formatu:

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Delegatów

Dla argumentów operacji tego samego [delegować](../keywords/delegate.md) typu `+` operator zwraca nowe wystąpienie delegata, gdy wywoływany, wywołuje argument po lewej stronie, a następnie wywołuje prawostronny operand. Jeśli którykolwiek z argumentów jest `null`, `+` operator zwraca wartość innego operandu (które mogą być również `null`). W poniższym przykładzie pokazano, jak delegaty można łączyć z `+` operator:

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Aby wykonać usuwanie delegata, użyj [ `-` operator](subtraction-operator.md#delegate-removal).

Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>+= — Operator przypisania dodawania

Usługi za pomocą wyrażenia `+=` operatora, takich jak

```csharp
x += y
```

odpowiada wyrażeniu

```csharp
x = x + y
```

z tą różnicą, że `x` jest obliczany tylko raz.
  
W poniższym przykładzie pokazano użycie `+=` operator:

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Możesz także użyć `+=` operatora, aby określić metodę programu obsługi zdarzeń podczas subskrybowania [zdarzeń](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `+` operatora. Gdy dane binarne `+` operator jest przeciążony, `+=` operator jest również niejawnie przeciążona. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć `+=` operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [jednoargumentowe plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Interpolacja ciągów](../tokens/interpolated.md)
- [Porady: łączenie wielu ciągów](../../how-to/concatenate-multiple-strings.md)
- [Delegaty](../../programming-guide/delegates/index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [— i Operatorzy-=](subtraction-operator.md)
