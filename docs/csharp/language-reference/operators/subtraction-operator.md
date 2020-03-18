---
title: '- i -= operatory - odwołanie c#'
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
ms.openlocfilehash: 2017aade92e8d7ad2af7101a107122fa8d7b9e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847654"
---
# <a name="--and---operators-c-reference"></a>- i -= operatory (odwołanie do Języka C#)

`-` Operatory `-=` i są obsługiwane przez wbudowane [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) i typy [delegatów.](../builtin-types/reference-types.md#the-delegate-type)

Aby uzyskać informacje na `-` temat operatora arytmetycznego, zobacz [Operatory nieparzyste plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) oraz [Operator odejmowania —](arithmetic-operators.md#subtraction-operator--) sekcje operatora [arytmetycznego.](arithmetic-operators.md)

## <a name="delegate-removal"></a>Delegowanie usuwania

W przypadku argumentów tego samego typu `-` [delegata](../builtin-types/reference-types.md#the-delegate-type) operator zwraca wystąpienie delegata, które jest obliczane w następujący sposób:

- Jeśli oba argumenty są niezer- null, a lista wywoławczo-wywołania argumentu po prawej stronie jest właściwą ciągłą podlistą listy wywołania operandu po lewej stronie, wynikiem operacji jest nowa lista wywołań, która jest uzyskiwana przez usunięcie argumentu po prawej stronie. z listy wywoławczej argumentu po lewej stronie. Jeśli lista operandu po prawej stronie jest zgodna z wieloma sąsiadującymi podlistami na liście operandu po lewej stronie, usuwana jest tylko najbardziej pasująca lista podrzędna po prawej stronie. Jeśli usunięcie spowoduje usunięcie pustej `null`listy, wynikiem jest .

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- Jeśli lista wywołań operandu po prawej stronie nie jest właściwą ciągłą podlistą listy wywołania operandu po lewej stronie, wynikiem operacji jest argument po lewej stronie. Na przykład usunięcie delegata, który nie jest częścią delegata multiemisji nie robi nic i powoduje niezmienionego delegata multiemisji.

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  W poprzednim przykładzie również pokazuje, że podczas usuwania delegata delegata wystąpienia są porównywane. Na przykład delegatów, które są produkowane z oceny identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe. Aby uzyskać więcej informacji na temat równości delegatów, zobacz [delegowanie operatorów równości specyfikacji](~/_csharplang/spec/expressions.md#delegate-equality-operators) [języka C#.](~/_csharplang/spec/introduction.md)

- Jeśli argument po lewej `null`stronie jest , wynik `null`operacji jest . Jeśli argument po prawej `null`stronie jest , wynikiem operacji jest po lewej stronie operand.

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

Aby połączyć delegatów, należy użyć [ `+` operatora](addition-operator.md#delegate-combination).

Aby uzyskać więcej informacji na temat typów pełnomocników, zobacz [Delegatów](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operator przypisania odejmowania -=

Wyrażenie używające `-=` operatora, takie jak

```csharp
x -= y
```

jest równoważny

```csharp
x = x - y
```

chyba `x` że jest oceniana tylko raz.

W poniższym przykładzie przedstawiono `-=` użycie operatora:

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

Operator służy `-=` również do określania metody obsługi zdarzeń, aby usunąć po anulowaniu subskrypcji [ze zdarzenia](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i zniej subskrybować je.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `-` może [przeciążać](operator-overloading.md) operatora. Gdy operator `-` binarny jest `-=` przeciążony, operator jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie `-=` może jawnie przeciążać operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [+ i += operatory](addition-operator.md)
