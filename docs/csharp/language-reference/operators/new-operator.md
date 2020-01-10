---
title: Nowy operator — C# odwołanie
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: beb55f0765e7f9090f0587f1d2a06cf03ea90ab8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712666"
---
# <a name="new-operator-c-reference"></a>New — OperatorC# (odwołanie)

Operator `new` tworzy nowe wystąpienie typu.

Można również użyć słowa kluczowego `new` jako [modyfikatora deklaracji składowej](../keywords/new-modifier.md) lub [ograniczenia typu ogólnego](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Wywołanie konstruktora

Aby utworzyć nowe wystąpienie typu, zazwyczaj wywoływany jest jeden z [konstruktorów](../../programming-guide/classes-and-structs/constructors.md) tego typu przy użyciu operatora `new`:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Można użyć [inicjatora obiektu lub kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) z operatorem `new`, aby utworzyć wystąpienie obiektu i zainicjować go w jednej instrukcji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Tworzenie tablicy

Możesz również użyć operatora `new`, aby utworzyć wystąpienie tablicy, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Użyj składni inicjowania tablicy, aby utworzyć wystąpienie tablicy i wypełnić je elementami w jednej instrukcji. W poniższym przykładzie pokazano różne sposoby wykonywania następujących czynności:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Tworzenie wystąpienia typów anonimowych

Aby utworzyć wystąpienie [typu anonimowego](../../programming-guide/classes-and-structs/anonymous-types.md), użyj składni operatora `new` i inicjatora obiektów:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Niszczenie wystąpień typu

Nie trzeba zniszczyć wcześniej utworzonych wystąpień typu. Wystąpienia obu typów odwołań i wartości są niszczone automatycznie. Wystąpienia typów wartości są niszczone, gdy tylko kontekst, który zawiera te elementy, zostanie zniszczony. Wystąpienia typów odwołań są niszczone przez [Moduł wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md) w nieokreślonym czasie po usunięciu ostatniego odwołania do nich.

Dla wystąpień typu, które zawierają niezarządzane zasoby, na przykład dojście do pliku, zaleca się zapełnienie deterministycznym czyszczeniem, aby upewnić się, że zasoby, które zawierają, są wystawione tak szybko, jak to możliwe. Aby uzyskać więcej informacji, zobacz Dokumentacja interfejsu API <xref:System.IDisposable?displayProperty=nameWithType> i artykuł [using instrukcji](../keywords/using-statement.md) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie może przeciążać operatora `new`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [New Operator](~/_csharplang/spec/expressions.md#the-new-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
