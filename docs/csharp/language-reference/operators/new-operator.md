---
title: nowy operator — odwołanie do języka C#
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 84131bc503a106961419a27fc4e3e0f2d82306a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846236"
---
# <a name="new-operator-c-reference"></a>nowy operator (odwołanie do Języka C#)

Operator `new` tworzy nowe wystąpienie typu.

Można również użyć `new` słowa kluczowego jako [modyfikatora deklaracji elementów członkowskich](../keywords/new-modifier.md) lub [ograniczenia typu ogólnego](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Wywołanie konstruktora

Aby utworzyć nowe wystąpienie typu, zazwyczaj wywołać jeden z [konstruktorów](../../programming-guide/classes-and-structs/constructors.md) `new` tego typu przy użyciu operatora:

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

Można użyć [inicjatora](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` obiektu lub kolekcji z operatorem do tworzenia wystąpienia i inicjowania obiektu w jednej instrukcji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Tworzenie tablicy

Operator służy `new` również do tworzenia wystąpienia tablicy, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

Składnia inicjowania tablicy służy do tworzenia wystąpienia tablicy i wypełniania go elementami w jednej instrukcji. W poniższym przykładzie pokazano różne sposoby wykonywania tego działania:

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

Aby uzyskać więcej informacji o tablicach, zobacz [Tablice](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Tworzenie wystąpienia typów anonimowych

Aby utworzyć wystąpienie [typu anonimowego,](../../programming-guide/classes-and-structs/anonymous-types.md)należy użyć składni `new` operatora i inicjatora obiektów:

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Niszczenie wystąpień typu

Nie trzeba niszczyć wcześniej utworzonych wystąpień typu. Wystąpienia typów odwołań i wartości są niszczone automatycznie. Wystąpienia typów wartości są niszczone, gdy kontekst, który je zawiera, zostanie zniszczony. Wystąpienia typów odwołań są niszczone przez [moduł zbierający elementy bezużyteczne](../../../standard/garbage-collection/index.md) w nieokreślonym czasie po usunięciu ostatniego odwołania do nich.

W przypadku wystąpień typu, które zawierają zasoby niezarządzane, na przykład dojście do plików, zaleca się stosowanie deterministycznego oczyszczania, aby upewnić się, że zasoby, które zawierają, są zwalniane tak szybko, jak to możliwe. Aby uzyskać więcej <xref:System.IDisposable?displayProperty=nameWithType> informacji, zobacz odwołanie interfejsu API i [using statement](../keywords/using-statement.md) artykułu.

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `new` nie może przeciążać operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję nowy operator](~/_csharplang/spec/expressions.md#the-new-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
