---
title: Operatory true i false — C# odwołanie
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 780c63e5a8f3f0d82559565b3319fe54507e3d21
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036124"
---
# <a name="true-and-false-operators-c-reference"></a>Operatory true i false (C# odwołanie)

Operator `true` zwraca wartość [logiczną](../keywords/bool.md) `true`, aby wskazać, że jej operand ma wartość true. Operator `false` zwraca wartość `bool` `true`, aby wskazać, że jej operand ma wartość false. Operatory `true` i `false` nie są gwarantowane do uzupełniania siebie nawzajem. Oznacza to, że zarówno operator `true`, jak i `false` mogą zwrócić `bool` wartość `false` dla tego samego operandu. Jeśli typ definiuje jeden z dwóch operatorów, musi także definiować innego operatora.

> [!TIP]
> Użyj typu `bool?`, jeśli musisz obsługiwać logikę o trzech wartościach (na przykład podczas pracy z bazami danych, które obsługują wartość typu Boolean o wartości 3). C#udostępnia operatory`&`i`|`, które obsługują logikę z trzema wartościami z argumentami operacji`bool?`. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](boolean-logical-operators.md) .

## <a name="boolean-expressions"></a>Wyrażenia logiczne

Typ ze zdefiniowanym operatorem `true` może być typem wyniku kontrolnego wyrażenia warunkowego w instrukcjach [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)i [for](../keywords/for.md) oraz w [operatorze warunkowym `?:`](conditional-operator.md). Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia logiczne](~/_csharplang/spec/expressions.md#boolean-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Operatory logiczne warunkowe zdefiniowane przez użytkownika

Jeśli typ ze zdefiniowanymi `true` i operatory `false` [przeciążą](operator-overloading.md) `|` [logiczne or](boolean-logical-operators.md#logical-or-operator-) lub operator [logiczny i operator](boolean-logical-operators.md#logical-and-operator-) `&` w określony sposób, [warunkowego operatora logicznego OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` lub [ warunkowe operatory logiczne i](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, odpowiednio, można ocenić dla operandów tego typu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia typ, który definiuje operatory `true` i `false`. Typ powoduje również przeciążenia operatora logicznego i `&` w taki sposób, że operator `&&` również może być obliczany dla operandów tego typu.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Zwróć uwagę na zachowanie krótkiego obwodu operatora `&&`. Gdy metoda `GetFuelLaunchStatus` zwraca `LaunchStatus.Red`, nie jest oceniany operand z prawej strony operatora `&&`. Wynika to z faktu, że `LaunchStatus.Red` ma wartość false. Następnie wynik logiczny i nie zależy od wartości operandu po prawej stronie. Dane wyjściowe przykładu są następujące:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Literał true](../keywords/true-literal.md)
- [Literał fałszywy](../keywords/false-literal.md)
