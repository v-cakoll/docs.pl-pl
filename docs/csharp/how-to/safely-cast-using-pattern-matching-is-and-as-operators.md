---
title: Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów is i AS
description: Dowiedz się, jak używać technik dopasowywania wzorców, aby bezpiecznie rzutować zmienne na inny typ. Możesz użyć dopasowania wzorca oraz operatorów is i AS, aby bezpiecznie skonwertować typy.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 762f8135063f7256ce7a167c65013703d9249039
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973092"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów is i AS

Ponieważ obiekty są polimorficzne, istnieje możliwość, aby zmienna typu klasy bazowej była przechowywana [typu](../programming-guide/types/index.md)pochodnego. Aby uzyskać dostęp do elementów członkowskich wystąpienia typu pochodnego, konieczne jest [rzutowanie](../programming-guide/types/casting-and-type-conversions.md) wartości z powrotem na typ pochodny. Jednak rzutowanie tworzy ryzyko wyrzucania <xref:System.InvalidCastException>. C#zawiera instrukcje [dopasowania wzorca](../pattern-matching.md) , które wykonują rzut warunkowy tylko wtedy, gdy powiedzie się. C#zawiera również operatory [is](../language-reference/operators/type-testing-and-cast.md#is-operator) i [as](../language-reference/operators/type-testing-and-cast.md#as-operator) do sprawdzenia, czy wartość jest określonego typu.

Poniższy kod ilustruje dopasowanie wzorca `is` instrukcji. Zawiera metody, które testują argument metody w celu ustalenia, czy jest to jeden z możliwych zestawów typów pochodnych:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Powyższy przykład ilustruje kilka cech składni dopasowania do wzorca. Instrukcje `if (a is Mammal m)` i `if (o is Mammal m)` łączą test z przypisaniem inicjalizacji. Przypisanie występuje tylko wtedy, gdy test zakończy się pomyślnie. Zmienna `m` jest tylko w zakresie w osadzonej instrukcji `if`, w której został przypisany. Nie można uzyskać dostępu do `m` później w tej samej metodzie. Wypróbuj ją w oknie interaktywnym.

Można także użyć tej samej składni do testowania, jeśli [Typ wartości null](../language-reference/builtin-types/nullable-value-types.md) ma wartość, jak pokazano w poniższym przykładowym kodzie:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Powyższy przykład ilustruje inne funkcje dopasowania do wzorca do użycia z konwersjemi. Możesz przetestować zmienną dla wzorca o wartości null, sprawdzając, czy wartość `null`. Gdy wartość środowiska uruchomieniowego zmiennej jest `null`, sprawdzanie instrukcji `is` dla typu zawsze zwraca `false`. Zgodna ze wzorcem instrukcja `is` nie zezwala na typ wartości null, na przykład `int?` lub `Nullable<int>`, ale można testować dla dowolnego innego typu wartości. Wzorce `is` z poprzedniego przykładu nie są ograniczone do typów wartości dopuszczających wartość null. Można również użyć tych wzorców do sprawdzenia, czy zmienna typu referencyjnego ma wartość lub jest `null`.

Powyższy przykład pokazuje również, jak używać wyrażenia `is` pasującego do wzorca w instrukcji `switch`, gdzie zmienna może być jednym z wielu różnych typów.

Jeśli chcesz sprawdzić, czy zmienna jest danym typem, ale nie jest przypisana do nowej zmiennej, można użyć operatorów `is` i `as` dla typów referencyjnych i typów dopuszczających wartość null. Poniższy kod pokazuje, jak używać instrukcji `is` i `as`, które były częścią C# języka przed wprowadzeniem dopasowania do wzorca w celu przetestowania, jeśli zmienna ma dany typ:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak widać, porównując ten kod z kodem dopasowania wzorca, Składnia dopasowania wzorca zapewnia bardziej niezawodne funkcje, łącząc test i przypisanie w pojedynczej instrukcji. Jeśli to możliwe, użyj składni dopasowania wzorca.

Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
