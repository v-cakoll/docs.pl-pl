---
title: '- and-= operatory- C# Reference'
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
ms.openlocfilehash: cf642fcac7233d27f2ed9052829c145038e93419
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038872"
---
# <a name="--and---operators-c-reference"></a>-and-= — operatoryC# (odwołanie)

Operatory `-` i `-=` są obsługiwane przez wbudowane typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) oraz typy [delegatów](../builtin-types/reference-types.md#the-delegate-type) .

Aby uzyskać informacje o operatorze arytmetycznej `-`, zobacz [operatory jednoargumentowe Plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator odejmowania —](arithmetic-operators.md#subtraction-operator--) sekcje w artykule [Operatory arytmetyczne](arithmetic-operators.md) .

## <a name="delegate-removal"></a>Usuwanie delegata

Dla operandów tego samego typu [delegata](../builtin-types/reference-types.md#the-delegate-type) operator `-` zwraca wystąpienie delegata, które jest obliczane w następujący sposób:

- Jeśli oba operandy mają wartość inną niż null, a lista wywołań operandu po prawej stronie jest właściwą ciągłą podlistą listy wywołań operandu po lewej stronie, wynik operacji jest nową listą wywołań, która jest uzyskiwana przez usunięcie argumentów operacji po prawej stronie wpisy z listy wywołań operandu po lewej stronie. Jeśli lista argumentów operacji po prawej stronie jest zgodna z wieloma ciągłymi podlistami na liście operandów po lewej stronie, usuwana jest tylko podlista dopasowania do prawej. Jeśli usunięcie spowoduje powstanie pustej listy, wynik jest `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Jeśli lista wywołań operandu po prawej stronie nie jest prawidłową ciągłą podlistą listy wywołań operandu po lewej stronie, wynik operacji jest argumentem po lewej stronie. Na przykład usunięcie delegata, który nie jest częścią delegata multiemisji, ma wartość Nothing i skutkuje niezmienionym delegatem multiemisji.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  W poprzednim przykładzie pokazano również, że podczas porównywania wystąpień delegatów usuwania delegatów. Na przykład Delegaty wytwarzane z oceny identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe. Aby uzyskać więcej informacji o równość delegowania, zobacz sekcję [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

- Jeśli argument operacji po lewej stronie jest `null`, wynik operacji jest `null`. Jeśli argument operacji po prawej stronie jest `null`, wynik operacji jest argumentem po lewej stronie.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Aby połączyć delegatów, użyj [operatora`+`](addition-operator.md#delegate-combination).

Aby uzyskać więcej informacji na temat typów delegatów, zobacz [delegats](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operator przypisania odejmowania — =

Wyrażenie używające operatora `-=`, takie jak

```csharp
x -= y
```

jest równoważny

```csharp
x = x - y
```

z tą różnicą, że `x` jest obliczana tylko raz.

Poniższy przykład ilustruje użycie operatora `-=`:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Możesz również użyć operatora `-=`, aby określić metodę programu obsługi zdarzeń do usunięcia podczas anulowania subskrypcji [zdarzenia](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [How to: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operator `-`. Gdy operator `-` binarny jest przeciążony, operator `-=` jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora `-=`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcje [jednoargumentowe minus](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Operatory + i + =](addition-operator.md)
