---
title: Jak bezpiecznie oddać za pomocą dopasowania wzorców i jest i jako operatorzy
description: Naucz się używać technik dopasowywania wzorców, aby bezpiecznie rzutować zmienne na inny typ. Można użyć dopasowania wzorca, jak również jest i jako operatory do bezpiecznej konwersji typów.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 762f8135063f7256ce7a167c65013703d9249039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973092"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpiecznie oddać za pomocą dopasowania wzorców i jest i jako operatorzy

Ponieważ obiekty są polimorficzne, zmienna typu klasy podstawowej może posiadać [typ](../programming-guide/types/index.md)pochodny . Aby uzyskać dostęp do elementów członkowskich instancji typu pochodnego, należy [rzutować](../programming-guide/types/casting-and-type-conversions.md) wartość z powrotem do typu pochodnego. Jednak oddanych stwarza ryzyko rzucania <xref:System.InvalidCastException>. C# zawiera instrukcje [dopasowania wzorca,](../pattern-matching.md) które wykonują rzutowanie warunkowo tylko wtedy, gdy zakończy się pomyślnie. C# zapewnia również [is](../language-reference/operators/type-testing-and-cast.md#is-operator) i [jako](../language-reference/operators/type-testing-and-cast.md#as-operator) operatory do testowania, czy wartość jest określonego typu.

Poniższy kod demonstruje `is` instrukcję dopasowywania wzorców. Zawiera metody, które testują argument metody, aby ustalić, czy jest to jeden z możliwych zestaw typów pochodnych:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

W poprzednim przykładzie przedstawiono kilka funkcji składni dopasowania wzorca. I `if (a is Mammal m)` `if (o is Mammal m)` instrukcje łączą test z przypisaniem inicjowania. Przypisanie występuje tylko wtedy, gdy test zakończy się pomyślnie. Zmienna `m` jest tylko w `if` zakresie osadzonej instrukcji, gdzie został przypisany. Nie można `m` uzyskać dostępu później w tej samej metodzie. Wypróbuj w interaktywnym oknie.

Tej samej składni można również użyć do testowania, jeśli [typ wartości nullable](../language-reference/builtin-types/nullable-value-types.md) ma wartość, jak pokazano w poniższym przykładowym kodzie:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

W poprzednim przykładzie przedstawiono inne funkcje dopasowania wzorca do użycia z konwersjami. Zmienną dla wzorca zerowego można przetestować, sprawdzając specjalnie `null` wartość. Gdy wartość czasu wykonywania `null`zmiennej `is` jest , instrukcja `false`sprawdzanie typu zawsze zwraca . Instrukcja `is` dopasowania wzorca nie zezwala na typ `int?` wartości `Nullable<int>`z wartością null, na przykład lub , ale można przetestować dla dowolnego innego typu wartości. Wzorce `is` z poprzedniego przykładu nie są ograniczone do typów wartości nullable. Można również użyć tych wzorców, aby sprawdzić, czy zmienna `null`typu odwołania ma wartość lub jest .

W poprzednim przykładzie pokazano również, `is` jak używać `switch` wyrażenia dopasowania wzorca w instrukcji, gdzie zmienna może być jednym z wielu różnych typów.

Jeśli chcesz sprawdzić, czy zmienna jest danym typem, ale nie przypisać go `is` `as` do nowej zmiennej, można użyć i operatorów dla typów odwołań i typów nullable. Poniższy kod pokazuje, jak `is` `as` używać i instrukcje, które były częścią języka C# przed dopasowywanie wzorca został wprowadzony do testowania, jeśli zmienna jest danego typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak widać, porównując ten kod z kodem dopasowywania wzorców, składnia dopasowania wzorca zapewnia bardziej niezawodne funkcje, łącząc test i przypisanie w jednej instrukcji. W miarę możliwości należy używać składni dopasowywania wzorców.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Możesz też pobrać próbki [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
