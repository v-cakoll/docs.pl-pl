---
title: ?? operator - C# odwołania
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: a19b5558da36ffb11dabd1b9bec419a3623a0f17
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024988"
---
# <a name="-operator-c-reference"></a>?? Operator (C# odwołania)

Operatora łączenia wartości null `??` zwraca wartość swojego operandu po lewej stronie, jeśli nie jest `null`; w przeciwnym razie oblicza prawostronny operand i zwraca jego wynik. `??` Operator nie szacuje swojego operandu po prawej stronie, gdy lewostronny operand jest inna niż null.

Operator łączenia wartości null jest łączność do prawej strony, oznacza to, że wyrażenie formularza

```csharp
a ?? b ?? c
```

jest wykonywane jako

```csharp
a ?? (b ?? c)
```

`??` Operator może być przydatne w następujących scenariuszach:

- W wyrażeniach z [operatorów warunkowych działających z wartością null?. i?] ](member-access-operators.md#null-conditional-operators--and-), można używać operatora łączenia wartości null zapewnienie alternatywnych wyrażenie do oceny, w przypadku, gdy jest wynikiem wyrażenia warunkowe null operacji `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Podczas pracy z [typy o wartości zerowalnej](../../programming-guide/nullable-types/index.md) i musisz podać wartość bazowego typu wartości, określ wartość, aby zapewnić w przypadku, gdy wartość typu dopuszczającego wartość null jest za pomocą operatora łączenia wartości null `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Użyj <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metoda Jeśli wartość ma być używana, gdy wartość typu dopuszczającego wartość null jest `null` powinien mieć wartość domyślną typu wartości podstawowej.

- Począwszy od C# 7.0, można użyć [ `throw` wyrażenie](../keywords/throw.md#the-throw-expression) jako prawostronny operand operatora łączenia wartości null się bardziej zwięzły widok kodu sprawdzanie argumentu:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  Poprzedni przykład ilustruje też sposób używania [elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) do zdefiniowania właściwości.

## <a name="operator-overloadability"></a>Overloadability — operator

Nie można przeciążać operatora łączenia wartości null.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [null operatora łączącego](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [?. i? Operatory]](member-access-operators.md#null-conditional-operators--and-)
- [?: — operator](conditional-operator.md)
