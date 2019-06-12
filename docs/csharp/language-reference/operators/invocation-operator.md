---
title: operator () - C# odwołania
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 032215dd2ca028af2a07fe113e7732e4d8e7ad0d
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024983"
---
# <a name="-operator-c-reference"></a>() — operator (C# odwołania)

Nawiasy, `()`, są zwykle używane dla wywołania metody lub delegata lub wyrażenia cast.

Możesz także użyć nawiasów, aby określić kolejność, w którym ma być operacji w wyrażeniu. Aby uzyskać więcej informacji, zobacz [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) części [operatory](../../programming-guide/statements-expressions-operators/operators.md) artykułu. Listy uporządkowane według poziomu pierwszeństwo operatorów, zobacz [ C# operatory](index.md).

## <a name="method-invocation"></a>Wywołanie metody

Poniższy przykład przedstawia sposób wywołania metody, z lub bez argumentów i delegata:

[!code-csharp-interactive[use for invocation](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

Można także użyć nawiasów podczas wywołujesz [Konstruktor](../../programming-guide/classes-and-structs/constructors.md) z [ `new` ](../keywords/new-operator.md) operatora.

Aby uzyskać więcej informacji o metodach, zobacz [metody](../../programming-guide/classes-and-structs/methods.md). Aby uzyskać więcej informacji na temat obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).

## <a name="cast-expression"></a>Wyrażenie CAST

Wyrażenie cast w postaci `(T)E` wywołuje operatora konwersji można przekonwertować wartości wyrażenia `E` na typ `T`. Jeśli istnieje nie jawna konwersja z typu `E` na typ `T`, wystąpi błąd kompilacji. Aby dowiedzieć się, jak definiowanie operatora konwersji, zobacz [jawne](../keywords/explicit.md) i [niejawne](../keywords/implicit.md) artykuły — słowo kluczowe.

W poniższym przykładzie pokazano konwersja typu typy liczbowe:

[!code-csharp-interactive[use for cast](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych jawne konwersje między typów liczbowych, zobacz [Tabela jawnych konwersji liczbowych](../keywords/explicit-numeric-conversions-table.md).

Aby uzyskać więcej informacji, zobacz [konwersje rzutowania i typ](../../programming-guide/types/casting-and-type-conversions.md) i [operatory konwersji](../../programming-guide/statements-expressions-operators/conversion-operators.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Operator `()` nie mogą być przeciążone.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions) i [rzutowane wyrażenia,](~/_csharplang/spec/expressions.md#cast-expressions) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
