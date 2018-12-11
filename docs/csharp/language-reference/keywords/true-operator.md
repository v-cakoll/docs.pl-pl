---
title: TRUE — operator (C# odwołania)
ms.date: 12/03/2018
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 17830e5ae842255dcf71e73097779d17520b81e6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130679"
---
# <a name="true-operator-c-reference"></a>TRUE — operator (C# odwołania)

Zwraca [bool](bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true. Jeśli typ definiuje `true` operatora on również muszą definiować [false — operator](false-operator.md). `true` i `false` operatorów nie ma gwarancji uzupełniają się wzajemnie.

Na przykład, który definiuje zarówno `true` i `false` operatorów, zobacz [false — operator](false-operator.md) artykułu.

> [!TIP]
> Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu logicznego. Aby uzyskać więcej informacji, zobacz [bool? typu](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.

Jeśli typ za pomocą zdefiniowanego `true` operator [przeciążenia](operator.md) [operator logiczny OR](../operators/or-operator.md) `|` w określony sposób, [warunkowego logicznego operatora OR](../operators/conditional-or-operator.md) `||`, czyli short-circuiting, mogą być obliczane w przypadku argumentów operacji tego typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

Typ za pomocą zdefiniowanego `true` operator może być typ wyniku wyrażenia warunkowego kontroli w [Jeśli](if-else.md), [czy](do.md), [podczas](while.md), i [ Aby uzyskać](for.md) instrukcji i [operator warunkowy `?:` ](../operators/conditional-operator.md). Aby uzyskać więcej informacji, zobacz [wyrażeń logicznych](~/_csharplang/spec/expressions.md#boolean-expressions) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Operatory języka C#](../operators/index.md)
- [`true` literał](true-literal.md)