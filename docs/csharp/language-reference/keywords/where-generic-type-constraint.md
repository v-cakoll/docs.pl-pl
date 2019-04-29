---
title: gdzie (ograniczenie typu ogólnego) - C# odwołania
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 094358dea9054bf198ded77736dc45af1a436787
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660232"
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)

`where` Klauzula w ogólne definicji określa ograniczenia na typy, które są używane jako argumenty dla parametrów typu w typ ogólny, metoda, delegata lub funkcja lokalna. Ograniczenia można określić interfejsy, klasy bazowe lub wymaga użycia typu ogólnego być odwołaniem, wartością lub typu niezarządzanego. Które deklarują funkcje, które musi posiadać argument typu.

Na przykład, można zadeklarować klasy ogólnej `MyGenericClass`, w taki sposób, że parametr typu `T` implementuje <xref:System.IComparable%601> interfejsu:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Aby uzyskać więcej informacji o tym, gdzie klauzula w wyrażeniu zapytania, zobacz [gdzie klauzula](where-clause.md).

`where` Klauzuli mogą również zawierać ograniczenia klasy bazowej. Ograniczenie klasy bazowej stwierdzający, że typ ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę bazową (lub jest to, że klasa bazowa) ma być używany jako argument typu dla tego typu ogólnego. Jeśli jest używany do ograniczenia klasy bazowej, musi znajdować się przed wszystkimi innymi ograniczeniami dla tego parametru typu. Niektóre typy są niedozwolone jako ograniczenie klasy bazowej: <xref:System.Object>, <xref:System.Array>, i <xref:System.ValueType>. Przed C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, i <xref:System.MulticastDelegate> zostały również niedozwolone jako warunki ograniczające klasy bazowej. Poniższy przykład przedstawia typy, które można teraz określić jako klasa bazowa:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` Klauzuli można określić, czy typ jest `class` lub `struct`. `struct` Ograniczenie usuwa potrzebę określenia ograniczenie klasy bazowej `System.ValueType`. `System.ValueType` Typ nie może być używany jako ograniczenie klasy bazowej. W poniższym przykładzie pokazano oba `class` i `struct` ograniczenia:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Klauzuli mogą również obejmować `unmanaged` ograniczenia. `unmanaged` Ograniczenie ogranicza parametr typu dla typów znane jako **niezarządzanych typów**. **Niezarządzany typ** to typ, który nie jest typem odwołania i nie zawiera pola typu odwołania na każdym poziomie zagnieżdżania. `unmanaged` Ograniczenie ułatwia pisanie niskiego poziomu międzyoperacyjnego kodu w języku C#. Pozwala to uzyskać wielokrotnego użytku procedury dla wszystkich typów niezarządzanych. `unmanaged` Ograniczenia nie można łączyć z `class` lub `struct` ograniczenia. `unmanaged` Ograniczenie wymusza na to, że typ musi być `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` Klauzuli mogą również obejmować ograniczenie konstruktora `new()`. Czy ograniczenie sprawia, że można utworzyć wystąpienia typu parametru przy użyciu `new` operatora. [Ograniczenia new()](new-constraint.md) informuje kompilator, wiedzieć, że wszelkie podany argument typu musi mieć dostępne bez parametrów — lub konstruktora domyślnego —. Na przykład:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Ograniczenia pojawia się ostatni w `where` klauzuli. `new()` Ograniczenia nie można łączyć z `struct` lub `unmanaged` ograniczenia. Wszystkie typy spełniającej te ograniczenia musi być dostępny konstruktora bez parametrów, dzięki czemu `new()` ograniczenie nadmiarowe.

Z wieloma parametrami typu, użyj jednej `where` klauzulę dla każdego parametru typu, na przykład:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Można również dołączyć ograniczenia na parametry metod rodzajowych typu, jak pokazano w poniższym przykładzie:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Zauważ, że opis ograniczenia parametru typu delegatów składni takie same jak w przypadku metod:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Aby uzyskać informacji na temat delegatów, zobacz [delegatów ogólnych](../../../csharp/programming-guide/generics/generic-delegates.md).

Aby uzyskać szczegółowe informacje o składni i użycia ograniczeń, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [new, ograniczenie](../../../csharp/language-reference/keywords/new-constraint.md)
- [Ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)