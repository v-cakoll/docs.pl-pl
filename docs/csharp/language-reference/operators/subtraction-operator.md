---
title: '- operatory-= — i C# odwołania'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 80603107beb708e76a2c7446f300d71ede411570
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609853"
---
# <a name="--and---operators-c-reference"></a>— i Operatorzy-= (C# odwołania)

`-` Operator jest obsługiwany przez wbudowane typy liczbowe i [delegować](../keywords/delegate.md) typów.

Aby uzyskać informacje o operacji arytmetycznych `-` operatora, zobacz [jednoargumentowe plus lub minus operatory](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator odejmowania -](arithmetic-operators.md#subtraction-operator--) części [operatorów arytmetycznych](arithmetic-operators.md) artykułu.

## <a name="delegate-removal"></a>Usuwanie delegata

Dla argumentów operacji tego samego [delegować](../keywords/delegate.md) typu `-` operator zwraca wystąpienie delegata, który jest obliczany w następujący sposób:

- Jeśli oba operandy są inne niż null, a lista wywołania prawostronny operand jest właściwe ciągłych podlistę wywołania listę lewostronny operand, wynik operacji jest nową listę wywołania uzyskany przez usunięcie prawostronny operand wpisy na liście wywołania operandu po lewej stronie. Jeśli listy prawostronny operand pasuje wiele sąsiadujących podlisty liście argument po lewej stronie, tylko podlisty pasującego najdalej z prawej strony są usuwane. Jeśli wyniki usuwania w pustej listy, wynik jest `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Jeśli wywołanie listę prawostronny operand nie jest właściwe ciągłych podlistę wywołania listę lewostronny operand, wynik operacji jest lewostronny operand. Na przykład usuwanie delegata, który nie jest częścią delegatów multiemisji nie robi nic i powoduje niezmienione delegatów multiemisji.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Poprzedni przykład ilustruje też, że podczas delegata usuwania wystąpień delegata są porównywane. Na przykład, delegatów, które są tworzone z wersji ewaluacyjnej identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są takie same. Aby uzyskać więcej informacji na temat równości delegata zobacz [delegować Operatory równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) części [ C# specyfikacji języka](../language-specification/index.md).

- Jeśli argument po lewej stronie jest `null`, wynik operacji jest `null`. Jeśli argument po prawej stronie jest `null`, wynik operacji jest lewostronny operand.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Aby połączyć delegatów, należy użyć [ `+` operator](addition-operator.md#delegate-combination).

Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operator przypisania odejmowania-=

Usługi za pomocą wyrażenia `-=` operatora, takich jak

```csharp
x -= y
```

odpowiada wyrażeniu

```csharp
x = x - y
```

z tą różnicą, że `x` jest obliczany tylko raz.
  
W poniższym przykładzie pokazano użycie `-=` operator:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Możesz także użyć `-=` operatora, aby określić metodę programu obsługi zdarzeń, aby usunąć po anulowaniu subskrypcji z [zdarzeń](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika może [przeciążenia](operator-overloading.md) `-` operatora. Gdy dane binarne `-` operator jest przeciążony, `-=` operator jest również niejawnie przeciążona. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć `-=` operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [jednoargumentowy minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Delegaty](../../programming-guide/delegates/index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [+ i operatory +=](addition-operator.md)
