---
title: operatory true i false — odwołanie do języka C#
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 5ccd08a348478902bbbac36e99acf7ffc1fc814b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846223"
---
# <a name="true-and-false-operators-c-reference"></a>operatory true i false (odwołanie do języka C#)

Operator `true` zwraca wartość `true` [bool,](../builtin-types/bool.md) aby wskazać, że jego operand jest zdecydowanie true. Operator `false` zwraca `bool` wartość, `true` aby wskazać, że jego operand jest zdecydowanie false. `true` Podmioty `false` gospodarcze i podmioty gospodarcze nie są gwarantowane wzajemnego uzupełniania się. Oznacza to, `true` że `false` zarówno operator, jak i operator może zwrócić `bool` wartość `false` dla tego samego operandu. Jeśli typ definiuje jeden z dwóch operatorów, należy również zdefiniować inny operator.

> [!TIP]
> Użyj `bool?` tego typu, jeśli trzeba obsługiwać logikę trójwartościową (na przykład podczas pracy z bazami danych, które obsługują typ logiczny o trzech wartościach). C# zapewnia `&` `|` i operatorów, które obsługują logiki trójwartościowej z `bool?` operands. Aby uzyskać więcej informacji, zobacz [nullable logicznych operatorów logicznych](boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logicznych operatorów logicznych.](boolean-logical-operators.md)

## <a name="boolean-expressions"></a>Wyrażenia logiczne

`true` Typ ze zdefiniowanym operatorem może być typem wyniku kontrolującego wyrażenia warunkowego w [if](../keywords/if-else.md), [do](../keywords/do.md), [podczas](../keywords/while.md)gdy , i [dla](../keywords/for.md) instrukcji i w [operatorze warunkowym `?:` ](conditional-operator.md). Aby uzyskać więcej informacji, zobacz sekcję [Wyrażenia logiczne](~/_csharplang/spec/expressions.md#boolean-expressions) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="user-defined-conditional-logical-operators"></a>Operatory logiczne warunkowe zdefiniowane przez użytkownika

Jeśli typ ze zdefiniowanymi `true` i `false` operatorami [przeciąża](operator-overloading.md) [logiczny operator](boolean-logical-operators.md#logical-or-operator-) `|` OR lub operator `&` [logiczny AND](boolean-logical-operators.md#logical-and-operator-) w określony sposób, [warunkowy operator logiczny OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` lub [operator warunkowego logicznego](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`AND, można ocenić odpowiednio dla argumentów tego typu. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne warunkowe zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="example"></a>Przykład

Poniższy przykład przedstawia typ, który `true` `false` definiuje zarówno i operatorów. Typ również przeciążenia logicznego operatora `&` AND `&&` w taki sposób, że operator może być również oceniane dla operandów tego typu.

[!code-csharp[true and false operators example](snippets/TrueFalseOperators.cs)]

Zwróć uwagę na zachowanie `&&` zwarcia operatora. Gdy `GetFuelLaunchStatus` metoda `LaunchStatus.Red`zwraca, argument po prawej `&&` stronie operatora nie jest oceniany. To dlatego, `LaunchStatus.Red` że jest zdecydowanie fałszywe. Wtedy wynik logicznego i nie zależy od wartości operand po prawej stronie. Dane wyjściowe przykładu są następujące:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
