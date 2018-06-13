---
title: where — Ograniczenie typu ogólnego (odwołanie w C#)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 94db10c81af55030dfcf6e210a86658c84868e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288323"
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)

`where` w ogólną definicję klauzuli określa ograniczenia dotyczące typów, które są używane jako argumenty dla parametrów typu w typu ogólnego, metody, delegat lub funkcji lokalnej. Ograniczenia można określić interfejsów, klas podstawowych lub wymagają ogólnego typu odwołania, wartości ani typu niezarządzanego. Zadeklarować ich możliwości, które musi posiadać argumentów typu.

Na przykład można zadeklarować klasy ogólnej, `MyGenericClass`, że parametr typu `T` implementuje <xref:System.IComparable%601> interfejsu:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Aby uzyskać więcej informacji o tym, gdzie klauzula w wyrażeniu zapytania, zobacz [gdzie klauzuli](where-clause.md).

`where` Klauzuli mogą również obejmować ograniczenia klasy podstawowej. Ograniczenie klasy podstawowej stwierdza, że typ ma być używany jako typ argumentu dla tego typu ogólnego ma określonej klasy jako klasę podstawową (lub jest to, że klasa podstawowa) ma być używany jako typ argumentu dla tego typu ogólnego. Jeśli używane jest ograniczenie klasy podstawowej, musi występować przed wszystkimi innymi ograniczeniami dla tego parametru typu. Niektóre typy są niedozwolone jako ograniczenie klasy podstawowej: <xref:System.Object>, <xref:System.Array>, i <xref:System.ValueType>. Przed C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, i <xref:System.MulticastDelegate> zostały również zgłoszenia ograniczenia klasy podstawowej. W poniższym przykładzie przedstawiono typy, które teraz mogą być określone jako klasy podstawowej:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` Klauzuli można określić, czy ten typ jest `class` lub `struct`. `struct` Ograniczenia usuwa konieczności określania z ograniczeniem klasy podstawowej `System.ValueType`. `System.ValueType` Typu nie może być używany jako ograniczenie klasy podstawowej. W poniższym przykładzie przedstawiono oba `class` i `struct` ograniczenia:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Klauzuli mogą również obejmować `unmanaged` ograniczenia. `unmanaged` Ograniczenia ogranicza parametr typu do typów znany jako **niezarządzanych typy**. **Niezarządzany typ** jest typ, który nie jest typem referencyjnym i nie zawiera odwołanie do pola typu na dowolnym poziomie zagnieżdżenia. `unmanaged` Ograniczenia ułatwia pisanie niskiego poziomu międzyoperacyjnego kodu w języku C#. To ograniczenie umożliwia wielokrotnego użytku procedury wszystkich typów niezarządzane. `unmanaged` Ograniczenia nie można połączyć z `class` lub `struct` ograniczenia. `unmanaged` Ograniczenie wymusza musi być typu `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` Klauzuli mogą również obejmować ograniczenie konstruktora `new()`. Czy ograniczenia umożliwia utworzenie wystąpienia parametru typu przy użyciu `new` operatora. [Ograniczenia new()](new-constraint.md) umożliwia kompilatora wiedzieć, że wszelkie argumentu typu dostarczonego musi mieć dostęp bez parametrów--lub konstruktora domyślnego —. Na przykład:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Ograniczenia pojawia się w ostatniej `where` klauzuli. `new()` Ograniczenia nie można połączyć z `struct` lub `unmanaged` ograniczenia. Wszystkie typy spełniające te ograniczenia musi mieć konstruktora bez parametrów dostępny, przez co `new()` nadmiarowe ograniczenia.

Wiele parametrów typu, za pomocą jednego `where` klauzula dla każdego parametru typu, na przykład:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Można również dołączyć ograniczenia na parametry metody ogólne typu, jak pokazano w poniższym przykładzie:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Zauważ, że opis ograniczenia parametru typu delegatów składni jest takie samo jak w przypadku metod:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Informacje ogólne delegatów, zobacz [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).

Aby uzyskać więcej informacji o składni i użycia ograniczenia, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [new, ograniczenie](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
