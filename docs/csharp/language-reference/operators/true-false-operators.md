---
title: Operatory true i false - C# odwołania
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f4391e73b17c3700dc04240e1289b523c4bdc596
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025032"
---
# <a name="true-and-false-operators-c-reference"></a>Operatory true i false (C# odwołania)

`true` Operator zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true. `false` Operator zwraca `bool` wartość `true` do wskazania, że argument jest zdecydowanie false. `true` i `false` operatorów nie ma gwarancji uzupełniają się wzajemnie. Oznacza to, że oba `true` i `false` operator może zwrócić `bool` wartość `false` dla tego samego argumentu operacji. Jeśli typ definiuje jeden z dwóch operatorów, zdefiniuj również innego operatora.

Jeśli typ za pomocą zdefiniowanego `true` i `false` operatory [przeciążenia](../keywords/operator.md) [operator logiczny OR](boolean-logical-operators.md#logical-or-operator-) `|` lub [logicznego operatora AND](boolean-logical-operators.md#logical-and-operator-) `&` w określony sposób, [warunkowego logicznego operatora OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` lub [warunkowego logicznego operatora AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, odpowiednio, mogą być obliczane dla argumentów typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Typ za pomocą zdefiniowanego `true` operator może być typ wyniku wyrażenia warunkowego kontroli w [Jeśli](../keywords/if-else.md), [czy](../keywords/do.md), [podczas](../keywords/while.md), i [ Aby uzyskać](../keywords/for.md) instrukcji i [operator warunkowy `?:` ](conditional-operator.md). Aby uzyskać więcej informacji, zobacz [wyrażeń logicznych](~/_csharplang/spec/expressions.md#boolean-expressions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

> [!TIP]
> Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu Boolean. C#udostępnia `&` i `|` operatorów, które obsługują logiki przechowywanymi w trzech przy użyciu `bool?` argumentów operacji. Aby uzyskać więcej informacji, zobacz [Nullable logiczna operatorów logicznych](boolean-logical-operators.md#nullable-boolean-logical-operators) części [logiczna operatorów logicznych](boolean-logical-operators.md) artykułu.

Poniższy przykład przedstawia typ, który określa zarówno `true` i `false` operatorów. Ponadto przeciąża logicznego operatora AND `&` w taki sposób, że operator `&&` mogą być obliczane dla argumentów typu.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Zwróć uwagę, zachowanie short-circuiting `&&` operatora. Gdy `GetFuelLaunchStatus` metoda zwraca `LaunchStatus.Red`, drugi operand `&&` operator nie jest oceniany. To dlatego, że `LaunchStatus.Red` ma zdecydowanie wartość false. Następnie wynik logicznego i nie zależy od wartości drugiego operandu. Dane wyjściowe z przykładu jest następująca:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [TRUE — literał](../keywords/true-literal.md)
- [FALSE — literał](../keywords/false-literal.md)
