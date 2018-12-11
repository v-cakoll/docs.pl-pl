---
title: 'Porady: bezpieczne multiemisji za pomocą dopasowywania do wzorca i jest i operatory'
description: Dowiedz się użyć metod dopasowania do wzorca można bezpieczne rzutować zmienne do innego typu. Możesz użyć dopasowywania do wzorca, jak również jest oraz jako operatorów można bezpiecznie konwersji typów.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 4e0eb53a44a6348d0f5154a0a08222da90985864
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149318"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-is-and-as-operators"></a>Porady: bezpieczne rzutowanie za pomocą dopasowywania do wzorca jest i operatory

Ponieważ obiekty są polimorficznych, jest możliwe dla zmiennej typu klasy bazowej, aby pomieścić pochodnej [typu](../programming-guide/types/index.md). Aby uzyskać dostęp do składowych wystąpienia typu pochodnego, konieczne jest [rzutowania](../programming-guide/types/casting-and-type-conversions.md) wartość do typu pochodnego. Rzutowanie tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>. C# zawiera [dopasowywania do wzorca](../pattern-matching.md) instrukcji, które wykonują rzutowania warunkowo, tylko wtedy, gdy zakończy się powodzeniem. C# oferuje także [jest](../language-reference/keywords/is.md) i [jako](../language-reference/keywords/as.md) operatory, aby sprawdzić, czy wartość jest określonego typu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy przykład demonstruje wzorzec dopasowywania `is` instrukcji. Zawiera metody testowania argumentu metody, aby ustalić, czy jest jednym z możliwych zestawów typów pochodnych:

[!code-csharp-interactive[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

W poprzednim przykładzie pokazano kilka funkcji Składnia dopasowania do wzorca. `if (a is Mammal m)` i `if (o is Mammal m)` instrukcje łączenia testu z przydziałem inicjowania. Przypisanie odbywa się tylko wtedy gdy test zakończy się pomyślnie. Zmienna `m` jest tylko w zakresie osadzonego `if` instrukcji, w którym został przypisany. Nie można uzyskać dostępu `m` dalej w tej samej metody. Wypróbuj go w oknie interaktywnym.

Można również użyć tej samej składni do badania, jeśli [typu dopuszczającego wartość null](../programming-guide/nullable-types/index.md) ma wartość, jak pokazano w poniższym przykładowym kodzie:

[!code-csharp-interactive[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Poprzedni przykład pokazuje inne funkcje za pomocą konwersji dopasowywania do wzorca. Możesz przetestować zmienną deseń zerowy, sprawdzając specjalnie pod kątem `null` wartość. Gdy wartość zmiennej środowiska uruchomieniowego jest `null`, `is` instrukcji sprawdzania dla typu zawsze zwraca `false`. Dopasowanie wzorca `is` instrukcji nie dopuszcza typem wartościowym, takich jak `int?` lub `Nullable<int>`, ale możesz testować dowolny inny typ wartości.

W poprzednim przykładzie pokazano, jak użyć dopasowania wzorca `is` wyrażenia w `switch` instrukcji, w którym zmienna może być jednym z wielu różnych typów.

Jeśli chcesz sprawdzić, czy zmienna jest danego typu, ale nie przypisać ją do nowej zmiennej, można użyć `is` i `as` operatorów dla typów odwołań i typy dopuszczające wartości null. Poniższy kod przedstawia sposób użycia `is` i `as` instrukcji, które były częścią języka C#, zanim dopasowywania do wzorca została wprowadzona, aby sprawdzić, czy zmienna jest danego typu:

[!code-csharp-interactive[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak widać, porównując ten kod z kodem dopasowania wzorca Składnia dopasowania do wzorca zapewnia bardziej niezawodne funkcje, łącząc testu i przypisania w pojedynczej instrukcji. Użyj wzorca dopasowania składni, jeśli to możliwe.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
