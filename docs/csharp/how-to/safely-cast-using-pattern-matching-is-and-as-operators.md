---
title: Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów is i AS
description: Dowiedz się, jak używać technik dopasowywania wzorców, aby bezpiecznie rzutować zmienne na inny typ. Możesz użyć dopasowania wzorca oraz operatorów is i AS, aby bezpiecznie skonwertować typy.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: f10ce837057cc61b84130f237a13af708849dfc5
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662969"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów is i AS

Ponieważ obiekty są polimorficzne, istnieje możliwość, aby zmienna typu klasy bazowej była przechowywana [typu](../programming-guide/types/index.md)pochodnego. Aby uzyskać dostęp do elementów członkowskich wystąpienia typu pochodnego, konieczne jest [rzutowanie](../programming-guide/types/casting-and-type-conversions.md) wartości z powrotem na typ pochodny. Jednak rzutowanie tworzy ryzyko wyrzucania <xref:System.InvalidCastException> . Język C# zawiera instrukcje [dopasowania wzorca](../pattern-matching.md) , które wykonują rzutowanie warunkowo tylko wtedy, gdy powiedzie się. Język C# zawiera również operatory [is](../language-reference/operators/type-testing-and-cast.md#is-operator) i [as](../language-reference/operators/type-testing-and-cast.md#as-operator) do sprawdzenia, czy wartość jest określonego typu.

Poniższy przykład pokazuje, jak używać instrukcji dopasowania do wzorca `is` :

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs" id="PatternMatchingIs":::

Powyższy przykład ilustruje kilka cech składni dopasowania do wzorca. `if (a is Mammal m)`Instrukcja łączy test z przypisaniem inicjalizacji. Przypisanie występuje tylko wtedy, gdy test zakończy się pomyślnie. Zmienna `m` jest tylko w zakresie w osadzonej instrukcji, w `if` której został przypisany. Nie można uzyskać dostępu `m` dalej w tej samej metodzie. W poprzednim przykładzie pokazano również, jak użyć [ `as` operatora](../language-reference/operators/type-testing-and-cast.md#as-operator) , aby przekonwertować obiekt na określony typ.

Można także użyć tej samej składni do testowania, jeśli [Typ wartości null](../language-reference/builtin-types/nullable-value-types.md) ma wartość, jak pokazano w następującym przykładzie:

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs" id="PatternMatchingNullable":::

Powyższy przykład ilustruje inne funkcje dopasowania do wzorca do użycia z konwersjemi. Można testować zmienną dla wzorca o wartości null, sprawdzając odpowiednie `null` wartości. Gdy wartość środowiska uruchomieniowego zmiennej to `null` , `is` Sprawdzanie instrukcji dla typu zawsze zwraca wartość `false` . Instrukcja dopasowania wzorca `is` nie zezwala na typ wartości null, np `int?` `Nullable<int>` . lub, ale można testować dla dowolnego innego typu wartości. `is`Wzorce z poprzedniego przykładu nie są ograniczone do typów wartości dopuszczających wartość null. Można również użyć tych wzorców do sprawdzenia, czy zmienna typu referencyjnego ma wartość lub `null` .

Powyższy przykład pokazuje również, jak używać wzorca typu w instrukcji, `switch` gdzie zmienna może być jednym z wielu różnych typów.

Jeśli chcesz sprawdzić, czy zmienna jest danym typem, ale nie jest przypisana do nowej zmiennej, można użyć `is` `as` operatorów i dla typów referencyjnych i wartości null. Poniższy kod pokazuje, jak używać `is` `as` instrukcji i, które były częścią języka C# przed dopasowaniem do wzorca, aby sprawdzić, czy zmienna ma dany typ:

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs" id="IsAndAs":::

Jak widać, porównując ten kod z kodem dopasowania wzorca, Składnia dopasowania wzorca zapewnia bardziej niezawodne funkcje, łącząc test i przypisanie w pojedynczej instrukcji. Jeśli to możliwe, użyj składni dopasowania wzorca.
