---
title: 'Instrukcje: bezpieczne rzutowanie przy użyciu dopasowania wzorca i operatory is i AS'
description: Dowiedz się, jak używać technik dopasowywania wzorców, aby bezpiecznie rzutować zmienne na inny typ. Możesz użyć dopasowania wzorca oraz operatorów is i AS, aby bezpiecznie skonwertować typy.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 764a69869b8a5b8f76e2f58aced51761af73e50e
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566285"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Instrukcje: bezpieczne rzutowanie przy użyciu dopasowania wzorca i operatory is i AS

Ponieważ obiekty są polimorficzne, istnieje możliwość, aby zmienna typu klasy bazowej była przechowywana [typu](../programming-guide/types/index.md)pochodnego. Aby uzyskać dostęp do elementów członkowskich wystąpienia typu pochodnego, konieczne jest [rzutowanie](../programming-guide/types/casting-and-type-conversions.md) wartości z powrotem na typ pochodny. Jednak rzutowanie tworzy ryzyko wyrzucania <xref:System.InvalidCastException>. C#zawiera instrukcje [dopasowania wzorca](../pattern-matching.md) , które wykonują rzut warunkowy tylko wtedy, gdy powiedzie się. C#zawiera również operatory [is](../language-reference/operators/type-testing-and-cast.md#is-operator) i [as](../language-reference/operators/type-testing-and-cast.md#as-operator) do sprawdzenia, czy wartość jest określonego typu.

Poniższy kod demonstruje instrukcję dopasowania `is` do wzorca. Zawiera metody, które testują argument metody w celu ustalenia, czy jest to jeden z możliwych zestawów typów pochodnych:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Powyższy przykład ilustruje kilka cech składni dopasowania do wzorca. Instrukcje `if (a is Mammal m)` i`if (o is Mammal m)` łączą test z przypisaniem inicjalizacji. Przypisanie występuje tylko wtedy, gdy test zakończy się pomyślnie. Zmienna `m` jest tylko w zakresie w osadzonej `if` instrukcji, w której został przypisany. Nie można uzyskać `m` dostępu dalej w tej samej metodzie. Wypróbuj ją w oknie interaktywnym.

Można także użyć tej samej składni do testowania, jeśli [Typ wartości null](../programming-guide/nullable-types/index.md) ma wartość, jak pokazano w poniższym przykładowym kodzie:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Powyższy przykład ilustruje inne funkcje dopasowania do wzorca do użycia z konwersjemi. Można testować zmienną dla wzorca o wartości null, sprawdzając odpowiednie `null` wartości. Gdy wartość środowiska uruchomieniowego zmiennej to `null` `is` , sprawdzanie instrukcji dla typu zawsze zwraca wartość `false`. Instrukcja dopasowania `is` wzorca nie zezwala na typ wartości null, `int?` np. lub `Nullable<int>`, ale można testować dla dowolnego innego typu wartości.

Powyższy przykład pokazuje również, jak używać wyrażenia dopasowania `is` do wzorca `switch` w instrukcji, gdzie zmienna może być jednym z wielu różnych typów.

Jeśli chcesz sprawdzić, czy zmienna jest danym typem, ale nie jest przypisana do nowej zmiennej, można użyć `is` operatorów i `as` dla typów referencyjnych i typów dopuszczających wartość null. Poniższy kod pokazuje, `is` jak używać instrukcji i `as` , które były częścią C# języka przed wprowadzeniem dopasowania do wzorca w celu przetestowania, jeśli zmienna jest danego typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak widać, porównując ten kod z kodem dopasowania wzorca, Składnia dopasowania wzorca zapewnia bardziej niezawodne funkcje, łącząc test i przypisanie w pojedynczej instrukcji. Jeśli to możliwe, użyj składni dopasowania wzorca.

Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
