---
title: Typy struktury — odwołanie do języka C#
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: b85d0df086f3ca65ed995594dd374286e1c3ba5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847732"
---
# <a name="structure-types-c-reference"></a>Typy struktury (odwołanie do języka C#)

*Typ struktury* (lub *typ struktury)* jest [typem wartości,](value-types.md) który może hermetyzować dane i powiązane funkcje. `struct` Słowo kluczowe służy do definiowania typu struktury:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Typy struktury mają *semantykę wartości*. Oznacza to, że zmienna typu struktury zawiera wystąpienie typu. Domyślnie wartości zmiennych są kopiowane przy przypisaniu, przekazywaniu argumentu do metody i zwracaniu wyniku metody. W przypadku zmiennej typu struktury jest kopiowane wystąpienie typu. Aby uzyskać więcej informacji, zobacz [Typy wartości](value-types.md).

Zazwyczaj typy struktury są używane do projektowania małych typów zorientowanych na dane, które zapewniają niewielkie lub żadne zachowanie. Na przykład .NET używa typów struktury do reprezentowania liczby (zarówno [liczba całkowita,](integral-numeric-types.md) jak i [rzeczywista),](floating-point-numeric-types.md) [wartość logiczna](bool.md), [znak Unicode](char.md), [instancja czasu](xref:System.DateTime). Jeśli koncentrujesz się na zachowaniu typu, rozważ zdefiniowanie [klasy](../keywords/class.md). Typy klas mają *semantyki referencyjnej*. Oznacza to, że zmienna typu klasy zawiera odwołanie do wystąpienia typu, a nie samego wystąpienia.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Ograniczenia z projektem typu konstrukcji

Podczas projektowania typu struktury, masz takie same możliwości jak w przypadku typu [klasy,](../keywords/class.md) z następującymi wyjątkami:

- Nie można zadeklarować konstruktora bezparametrów. Każdy typ struktury już zapewnia niejawny konstruktor bezparametrów, który tworzy [domyślną wartość](default-values.md) typu.

- Nie można zainicjować pola wystąpienia lub właściwości w jego deklaracji. Można jednak zainicjować pole [statyczne](../keywords/static.md) lub [const](../keywords/const.md) lub właściwość statyczną w jego deklaracji.

- Konstruktor typu struktury musi zainicjować wszystkie pola wystąpienia tego typu.

- Typ struktury nie może dziedziczyć z innej klasy lub typu struktury i nie może być podstawą klasy. Jednak typ struktury może implementować [interfejsy](../keywords/interface.md).

- Nie można zadeklarować [finalizatora](../../programming-guide/classes-and-structs/destructors.md) w ramach typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Wystąpienie typu konstrukcji

W języku C#, należy zainicjować zadeklarowaną zmienną, zanim będzie można jej użyć. Ponieważ zmienna typu struktury `null` nie może być (chyba że jest zmienną [typu wartości nullable),](nullable-value-types.md)należy utworzyć wystąpienie odpowiedniego typu. Istnieje kilka sposobów, aby to zrobić.

Zazwyczaj tworzy swej wystąpienia typu struktury, wywołując odpowiedni [`new`](../operators/new-operator.md) konstruktor z operatorem. Każdy typ struktury ma co najmniej jeden konstruktor. Jest to niejawny konstruktor bezparametrów, który tworzy [domyślną wartość](default-values.md) typu. Można również użyć [domyślnego](../operators/default.md) operatora lub literału do wytworzenia wartości domyślnej typu.

Jeśli wszystkie pola wystąpienia typu struktury są dostępne, można również `new` utworzyć wystąpienia bez operatora. W takim przypadku należy zainicjować wszystkie pola wystąpienia przed pierwszym użyciem wystąpienia. W poniższym przykładzie pokazano, jak to zrobić:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

W przypadku [wbudowanych typów wartości](value-types.md#built-in-value-types)użyj odpowiednich literałów, aby określić wartość typu.

## <a name="passing-structure-type-variables-by-reference"></a>Przekazywanie zmiennych typu struktury przez odwołanie

Po przekazaniu zmiennej typu struktury do metody jako argument lub zwrócić wartość typu struktury z metody, całe wystąpienie typu struktury jest kopiowany. Może to wpłynąć na wydajność kodu w scenariuszach o wysokiej wydajności, które obejmują typy dużych struktur. Można uniknąć kopiowania wartości, przekazując zmienną typu struktury przez odwołanie. Użyj [`ref`](../keywords/ref.md#passing-an-argument-by-reference)modyfikatorów parametrów , [`out`](../keywords/out-parameter-modifier.md)lub [`in`](../keywords/in-parameter-modifier.md) metody, aby wskazać, że argument musi być przekazany przez odwołanie. Użyj [ref zwraca,](../../programming-guide/classes-and-structs/ref-returns.md) aby zwrócić wynik metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [Pisanie bezpiecznego i wydajnego kodu Języka C#.](../../write-safe-efficient-code.md)

## <a name="conversions"></a>Konwersje

Dla każdego typu struktury istnieją [boks i unboxing](../../programming-guide/types/boxing-and-unboxing.md) <xref:System.ValueType?displayProperty=nameWithType> konwersji <xref:System.Object?displayProperty=nameWithType> do iz i typów. Istnieje również boks i rozpakowywanie konwersji między typem struktury i dowolnym interfejsem, który implementuje.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcja Struktury](~/_csharplang/spec/structs.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Wskazówki projektowe - Wybór między klasą a strukturą](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Wytyczne projektowe - Konstrukcja struct](../../../standard/design-guidelines/struct.md)
- [Klasy i struktury](../../programming-guide/classes-and-structs/index.md)
