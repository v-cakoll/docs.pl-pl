---
title: FALSE — operator (odwołanie w C#)
ms.date: 12/03/2018
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 4428d88acb08246623e2deb71a9daf7fb1cca692
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152308"
---
# <a name="false-operator-c-reference"></a>FALSE — operator (odwołanie w C#)

Zwraca [bool](bool.md) wartość `true` do wskazania, że argument jest zdecydowanie false. Jeśli typ definiuje `false` operatora on również muszą definiować [true — operator](true-operator.md). `true` i `false` operatorów nie ma gwarancji uzupełniają się wzajemnie.

> [!TIP]
> Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu logicznego. Aby uzyskać więcej informacji, zobacz [bool? typu](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.

Jeśli typ za pomocą zdefiniowanego `false` operator [przeciążenia](operator.md) [logicznego operatora AND](../operators/and-operator.md) `&` w określony sposób, [warunkowego operator logiczny AND](../operators/conditional-and-operator.md) `&&`, czyli short-circuiting, mogą być obliczane w przypadku argumentów operacji tego typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

Poniższy przykład przedstawia typ, który określa zarówno `true` i `false` operatorów. Ponadto przeciąża logicznego operatora AND `&` w taki sposób, że operator `&&` mogą być obliczane dla argumentów typu.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Zwróć uwagę, zachowanie short-circuiting `&&` operatora. Gdy `GetFuelLaunchStatus` metoda zwraca `LaunchStatus.Red`, drugi operand `&&` operator nie jest oceniany. To dlatego, że `LaunchStatus.Red` ma zdecydowanie wartość false. Następnie wynik logicznego i nie zależy od wartości drugiego operandu. Dane wyjściowe z przykładu jest następująca:

```console
Getting fuel launch status...
Wait!
```

Ponadto należy zauważyć, że wyrażenie warunkowe w [operator warunkowy `?:` ](../operators/conditional-operator.md) jest `LaunchStatus` typu. Jest to możliwe, ponieważ `LaunchStatus` definiuje `true` operatora. Aby uzyskać więcej informacji, zobacz [wyrażeń logicznych](~/_csharplang/spec/expressions.md#boolean-expressions) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Operatory języka C#](../operators/index.md)
- [`false` literał](false-literal.md)