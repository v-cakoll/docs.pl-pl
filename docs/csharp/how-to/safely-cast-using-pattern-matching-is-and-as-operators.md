---
title: Jak bezpiecznie rzucać za pomocą dopasowywania wzorców i jest i jako operatorzy
description: Dowiedz się, jak używać technik dopasowywania wzorców, aby bezpiecznie rzutować zmienne na inny typ. Można użyć dopasowywania wzorców, jak również is i operatorów do bezpiecznego konwertowania typów.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 9f5690e6840098f94360dba89f09fb23b258b782
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739047"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpiecznie rzucać za pomocą dopasowywania wzorców i jest i jako operatorzy

Ponieważ obiekty są polimorficzne, zmienna typu klasy podstawowej może zawierać [typ](../programming-guide/types/index.md)pochodny . Aby uzyskać dostęp do elementów członkowskich wystąpienia typu pochodnego, konieczne jest [rzutanie](../programming-guide/types/casting-and-type-conversions.md) wartości z powrotem do typu pochodnego. Jednak obsada stwarza ryzyko rzucania <xref:System.InvalidCastException>. C# zawiera [instrukcje dopasowania wzorca,](../pattern-matching.md) które wykonują rzutowanie warunkowo tylko wtedy, gdy zakończy się pomyślnie. C# zapewnia również [is](../language-reference/operators/type-testing-and-cast.md#is-operator) i [jako](../language-reference/operators/type-testing-and-cast.md#as-operator) operatorów, aby przetestować, jeśli wartość jest pewnego typu.

W poniższym przykładzie pokazano, `is` jak używać instrukcji dopasowywania wzorców:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

W poprzednim przykładzie przedstawiono kilka funkcji składni dopasowania wzorca. Instrukcja `if (a is Mammal m)` łączy test z przypisaniem inicjowania. Przypisanie występuje tylko wtedy, gdy test zakończy się pomyślnie. Zmienna `m` jest tylko w zakresie `if` w osadzonej instrukcji, gdzie została przypisana. Nie można `m` uzyskać dostępu później w tej samej metodzie. W poprzednim przykładzie pokazano również, jak użyć [ `as` operatora](../language-reference/operators/type-testing-and-cast.md#as-operator) do konwersji obiektu na określony typ.

Można również użyć tej samej składni do testowania, jeśli [typ wartości nullable](../language-reference/builtin-types/nullable-value-types.md) ma wartość, jak pokazano w poniższym przykładzie:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

W poprzednim przykładzie przedstawiono inne funkcje dopasowania wzorca do użycia z konwersjami. Można przetestować zmienną dla wzorca null, `null` sprawdzając specjalnie dla wartości. Gdy wartość środowiska uruchomieniowego `null`zmiennej jest , `is` instrukcja `false`sprawdzania typu zawsze zwraca . Instrukcja `is` dopasowywania wzorców nie zezwala na `int?` typ `Nullable<int>`wartości nullable, takich jak lub , ale można przetestować dla dowolnego innego typu wartości. Wzorce `is` z poprzedniego przykładu nie są ograniczone do typów wartości nullable. Można również użyć tych wzorców, aby sprawdzić, czy zmienna typu `null`odwołania ma wartość lub jest .

W poprzednim przykładzie pokazano również, jak `switch` używać wzorca typu w instrukcji, gdzie zmienna może być jednym z wielu różnych typów.

Jeśli chcesz przetestować, czy zmienna jest danym typem, ale nie przypisać `is` `as` go do nowej zmiennej, można użyć i operatorów dla typów odwołań i nullable typów wartości. Poniższy kod pokazuje, `is` jak `as` używać i instrukcji, które były częścią języka C# przed dopasowaniem wzorca został wprowadzony do testowania, jeśli zmienna jest danego typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak widać, porównując ten kod z kodem dopasowania wzorca, składnia pasująca do wzorca zapewnia bardziej niezawodne funkcje, łącząc test i przypisanie w jednej instrukcji. W miarę możliwości należy używać składni dopasowywania wzorca.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/safelycast). Możesz też pobrać próbki [jako plik zip](../../../samples/snippets/csharp/how-to/safelycast.zip).
