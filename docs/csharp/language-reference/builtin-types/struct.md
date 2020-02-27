---
title: Typy struktury — C# odwołanie
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6113912f176d2d7b68c77ff2e78a361b373ca31a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634870"
---
# <a name="structure-types-c-reference"></a>Typy struktur (C# odwołanie)

*Typ struktury* (lub *Typ struktury*) jest [typem wartości](value-types.md) , który może hermetyzować dane i powiązane funkcje. Za pomocą słowa kluczowego `struct` można zdefiniować typ struktury:

[!code-csharp[struct example](~/samples/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

Typy struktury mają *semantykę wartości*. Oznacza to, że zmienna typu struktury zawiera wystąpienie typu. Domyślnie wartości zmiennych są kopiowane przy przypisywaniu, przekazywanie argumentu do metody i zwracanie wyniku metody. W przypadku zmiennej typu struktury jest kopiowane wystąpienie typu. Aby uzyskać więcej informacji, zobacz [typy wartości](value-types.md).

Zwykle typy struktury umożliwiają projektowanie małych typów skoncentrowanych na danych, które zapewniają niewielki lub nie zachowanie. Na przykład program .NET używa typów struktury do reprezentowania liczby (zarówno [liczby całkowitej](integral-numeric-types.md) , jak i [rzeczywistej](floating-point-numeric-types.md)), [wartości logicznej](bool.md), [znaku Unicode](char.md)i [wystąpienia czasu](xref:System.DateTime). Jeśli planujesz zachowanie typu, rozważ zdefiniowanie [klasy](../keywords/class.md). Typy klas mają *semantykę odwołań*. Oznacza to, że zmienna typu klasy zawiera odwołanie do wystąpienia typu, a nie samego wystąpienia.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Ograniczenia dotyczące projektowania typu struktury

Podczas projektowania typu struktury można korzystać z takich samych możliwości jak w przypadku typu [klasy](../keywords/class.md) , z następującymi wyjątkami:

- Nie można zadeklarować konstruktora bez parametrów. Każdy typ struktury zawiera już niejawny Konstruktor bez parametrów, który generuje [wartość domyślną](default-values.md) typu.

- Nie można zainicjować pola wystąpienia lub właściwości w swojej deklaracji. Można jednak zainicjować pole [static](../keywords/static.md) lub [const](../keywords/const.md) lub właściwość statyczną w swojej deklaracji.

- Konstruktor typu struktury musi inicjować wszystkie pola wystąpienia typu.

- Typ struktury nie może dziedziczyć z innego typu klasy lub struktury i nie może być podstawą klasy. Jednak typ struktury może implementować [interfejsy](../keywords/interface.md).

- Nie można zadeklarować [finalizatora](../../programming-guide/classes-and-structs/destructors.md) w obrębie typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Tworzenie wystąpienia typu struktury

W C#, musisz zainicjować zadeklarowaną zmienną, zanim będzie można jej użyć. Ponieważ zmienna typu struktury nie może być `null` (chyba że jest to zmienna [typu wartości null](nullable-value-types.md)), należy utworzyć wystąpienie odpowiedniego typu. Istnieje kilka sposobów, aby to zrobić.

Zazwyczaj tworzysz typ struktury, wywołując odpowiedni Konstruktor z operatorem [`new`](../operators/new-operator.md) . Każdy typ struktury ma co najmniej jednego konstruktora. Jest to niejawny Konstruktor bez parametrów, który tworzy [wartość domyślną](default-values.md) typu. Można również użyć operatora [domyślnego](../operators/default.md) lub literału, aby utworzyć wartość domyślną typu.

Jeśli wszystkie pola wystąpienia typu struktury są dostępne, można również utworzyć ich wystąpienie bez operatora `new`. W takim przypadku należy zainicjować wszystkie pola wystąpienia przed pierwszym użyciem wystąpienia. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp[without new](~/samples/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

W przypadku [wbudowanych typów wartości](value-types.md#built-in-value-types)Użyj odpowiednich literałów, aby określić wartość typu.

## <a name="passing-structure-type-variables-by-reference"></a>Przekazywanie zmiennych typu struktury przez odwołanie

W przypadku przekazania zmiennej typu struktury do metody jako argumentu lub zwrócenia wartości typu struktury z metody, kopiowane jest całe wystąpienie typu struktury. To może mieć wpływ na wydajność kodu w scenariuszach o wysokiej wydajności, które obejmują duże typy struktury. Można uniknąć kopiowania wartości przez przekazanie zmiennej typu struktury przez odwołanie. Użyj modyfikatorów parametrów [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)lub [`in`](../keywords/in-parameter-modifier.md) , aby wskazać, że argument musi być przekazaniem przez odwołanie. Użyj funkcji [ref](../../programming-guide/classes-and-structs/ref-returns.md) Returns, aby zwrócić wynik metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [Zapisywanie bezpiecznego i C# wydajnego kodu](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Konwersje

Dla dowolnego typu struktury istnieje konwersja [opakowania i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md) do i z typów <xref:System.ValueType?displayProperty=nameWithType> i <xref:System.Object?displayProperty=nameWithType>. Istnieje również możliwość pakowania i rozpakowywania konwersji między typem struktury i dowolnym interfejsem, który implementuje.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [struktury](~/_csharplang/spec/structs.md) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Wytyczne dotyczące projektowania — wybór między klasą a strukturą](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Wytyczne dotyczące projektowania — projekt struktury](../../../standard/design-guidelines/struct.md)
- [Klasy i struktury](../../programming-guide/classes-and-structs/index.md)
