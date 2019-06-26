---
title: New operator - C# odwołania
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402512"
---
# <a name="new-operator-c-reference"></a>New — operator (C# odwołania)

`new` Operatora, tworzy nowe wystąpienie typu.

Można również użyć `new` słowo kluczowe as [modyfikator deklaracji elementu członkowskiego](../keywords/new-modifier.md) lub [ograniczenie typu ogólnego](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Wywołanie konstruktora

Aby utworzyć nowe wystąpienie typu, zwykle wywołuje jedną z [konstruktory](../../programming-guide/classes-and-structs/constructors.md) z tego typu za pomocą `new` operator:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Możesz użyć [Inicjator obiektu lub kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) z `new` operator do tworzenia instancji i zainicjować obiektu w jednej instrukcji, co ilustruje poniższy przykład:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Do utworzenia tablicy

Możesz także użyć `new` operatora do utworzenia wystąpienia tablicy, co ilustruje poniższy przykład:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Składnia inicjalizacji tablicy należy użyć do utworzenia instancji tablicy i wypełnić je z elementami w jednej instrukcji. Poniższy przykład pokazuje różne sposoby, jak można to zrobić:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Podczas tworzenia wystąpienia typu anonimowego

Aby utworzyć wystąpienie [typu anonimowego](../../programming-guide/classes-and-structs/anonymous-types.md), użyj `new` operatora i obiekt składni inicjatora:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Niszczenie wystąpień typu

Nie masz do likwidacji wcześniej utworzony typ wystąpienia. Wystąpień typów wartości i odwołań są niszczone, automatycznie. Wystąpienia typu wartości są niszczone, tak szybko, jak jest niszczony, kontekst, w którym się znajdują. Wystąpienia typu referencyjnego są niszczone [modułu zbierającego elementy bezużyteczne](../../../standard/garbage-collection/index.md) na nieokreślony czas, po usunięciu ostatniego odwołania do nich.

Dla typów, które zawierają zasoby niezarządzane na przykład dojście do pliku, zaleca się stosować deterministyczne oczyszczania aby upewnić się, jak najszybciej zwolnienie zasobów, które zawierają. Aby uzyskać więcej informacji, zobacz <xref:System.IDisposable?displayProperty=nameWithType> dokumentacja interfejsu API i [za pomocą instrukcji](../keywords/using-statement.md) artykułu.

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie mogą przeciążać `new` operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operatora new](~/_csharplang/spec/expressions.md#the-new-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
