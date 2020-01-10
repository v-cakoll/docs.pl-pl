---
title: WHERE (ograniczenie typu ogólnego) — C# odwołanie
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 19bf7682916336173ed93619fb6f0ff1242a1b30
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712809"
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)

Klauzula `where` w definicji ogólnej określa ograniczenia dotyczące typów, które są używane jako argumenty parametrów typu w typie ogólnym, metodzie, delegatze lub funkcji lokalnej. Ograniczenia mogą określać interfejsy, klasy bazowe lub wymagać typu ogólnego, aby być odwołaniem, wartością lub typem niezarządzanym. Deklarują możliwości, że argument typu musi mieć wartość.

Na przykład można zadeklarować klasę generyczną `MyGenericClass`, tak aby parametr typu `T` implementował interfejs <xref:System.IComparable%601>:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat klauzuli WHERE w wyrażeniu zapytania, zobacz [klauzula WHERE](where-clause.md).

Klauzula `where` może również zawierać ograniczenie klasy bazowej. Ograniczenie klasy bazowej określa, że typ, który ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę bazową (lub jest tą klasą bazową), która ma być używana jako argument typu dla tego typu ogólnego. Jeśli jest używane ograniczenie klasy bazowej, musi ono znajdować się przed innymi ograniczeniami tego parametru typu. Niektóre typy są niedozwolone jako ograniczenie klasy bazowej: <xref:System.Object>, <xref:System.Array>i <xref:System.ValueType>. Przed C# 7,3, <xref:System.Enum>, <xref:System.Delegate>i <xref:System.MulticastDelegate> były również niedozwolone jako ograniczenia klas podstawowych. W poniższym przykładzie przedstawiono typy, które można teraz określić jako klasę bazową:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Klauzula `where` może określać, że typ jest `class` lub `struct`. Ograniczenie `struct` eliminuje konieczność określenia ograniczenia klasy bazowej `System.ValueType`. Typ `System.ValueType` nie może być używany jako ograniczenie klasy bazowej. W poniższym przykładzie przedstawiono zarówno ograniczenia `class`, jak i `struct`:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

Klauzula `where` może zawierać ograniczenie `notnull`. Ograniczenie `notnull` ogranicza parametr typu do typów niedopuszczających wartości null. Ten typ może być typem [wartości](struct.md) lub typem referencyjnym, który nie dopuszcza wartości null. Ograniczenie `notnull` jest dostępne począwszy od C# 8,0 dla kodu skompilowanego w [kontekście`nullable enable`](../../nullable-references.md#nullable-contexts). W przeciwieństwie do innych ograniczeń, jeśli argument typu narusza ograniczenie `notnull`, kompilator generuje ostrzeżenie, a nie błąd. Ostrzeżenia są generowane tylko w kontekście `nullable enable`. 

> [!IMPORTANT]
> Deklaracje ogólne zawierające ograniczenie `notnull` mogą być używane w kontekście dopuszczającym wartość null, ale kompilator nie wymusza ograniczenia.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Klauzula `where` może również zawierać ograniczenie `unmanaged`. Ograniczenie `unmanaged` ogranicza parametr typu do typów znanych jako [typy niezarządzane](../builtin-types/unmanaged-types.md). Ograniczenie `unmanaged` ułatwia pisanie kodu międzyoperacyjności niskiego poziomu w programie C#. To ograniczenie umożliwia wykonywanie procedur wielokrotnego użytku we wszystkich typach niezarządzanych. Nie można połączyć ograniczenia `unmanaged` z ograniczeniem `class` lub `struct`. Ograniczenie `unmanaged` wymusza, że typ musi być `struct`:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Klauzula `where` może również zawierać ograniczenie konstruktora, `new()`. To ograniczenie umożliwia utworzenie wystąpienia parametru typu za pomocą operatora `new`. To [ograniczenie New ()](new-constraint.md) umożliwia kompilatorowi, że każdy dostarczony argument typu musi mieć dostępny Konstruktor bez parametrów. Na przykład:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Ograniczenie `new()` pojawia się jako ostatni w klauzuli `where`. Nie można łączyć ograniczenia `new()` z ograniczeniami `struct` lub `unmanaged`. Wszystkie typy spełniające te ograniczenia muszą mieć dostępny Konstruktor bez parametrów, co sprawia, że ograniczenie `new()` nadmiarowe.

W przypadku wielu parametrów typu należy użyć jednej `where` klauzul dla każdego parametru typu, na przykład:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Można również dołączyć ograniczenia do parametrów typu metod ogólnych, jak pokazano w następującym przykładzie:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Zauważ, że składnia opisująca ograniczenia parametru typu dla delegatów jest taka sama jak w przypadku metod:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Aby uzyskać informacje na temat delegatów ogólnych, zobacz [Delegaty ogólne](../../programming-guide/generics/generic-delegates.md).

Aby uzyskać szczegółowe informacje na temat składni i użycia ograniczeń, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../programming-guide/generics/index.md)
- [new, ograniczenie](./new-constraint.md)
- [Ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md)
