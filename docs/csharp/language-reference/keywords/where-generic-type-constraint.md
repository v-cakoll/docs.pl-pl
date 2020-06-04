---
title: WHERE (ograniczenie typu ogólnego) — odwołanie w C#
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 406c710cd884363c32b98336717732a09b3d1fc1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401878"
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)

`where`Klauzula w definicji ogólnej określa ograniczenia dotyczące typów, które są używane jako argumenty parametrów typu w typie ogólnym, metodzie, delegatze lub funkcji lokalnej. Ograniczenia mogą określać interfejsy, klasy bazowe lub wymagać typu ogólnego, aby być odwołaniem, wartością lub typem niezarządzanym. Deklarują możliwości, że argument typu musi mieć wartość.

Na przykład można zadeklarować klasę generyczną, `MyGenericClass` w taki sposób, aby parametr typu `T` implementuje <xref:System.IComparable%601> Interfejs:

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat klauzuli WHERE w wyrażeniu zapytania, zobacz [klauzula WHERE](where-clause.md).

`where`Klauzula może również zawierać ograniczenie klasy bazowej. Ograniczenie klasy bazowej określa, że typ, który ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę bazową, lub jest tą klasą bazową. Jeśli jest używane ograniczenie klasy bazowej, musi ono znajdować się przed innymi ograniczeniami tego parametru typu. Niektóre typy są niedozwolone jako ograniczenie klasy bazowej: <xref:System.Object> , <xref:System.Array> , i <xref:System.ValueType> . Przed C# 7,3, <xref:System.Enum> , <xref:System.Delegate> i <xref:System.MulticastDelegate> były również niedozwolone jako ograniczenia klas podstawowych. W poniższym przykładzie przedstawiono typy, które można teraz określić jako klasę bazową:

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#2)]

W kontekście dopuszczającym wartość null w języku C# 8,0 i nowszych wartości null typu klasy bazowej są wymuszane. Jeśli klasa bazowa nie dopuszcza wartości null (na przykład `Base` ), argument typu nie może dopuszczać wartości null. Jeśli klasa bazowa nie dopuszcza wartości null (na przykład `Base?` ), argument typu może być typem referencyjnym nullable lub niedopuszczający wartości null. Kompilator generuje ostrzeżenie, jeśli argument typu jest typem referencyjnym dopuszczającym wartość null, jeśli klasa bazowa nie dopuszcza wartości null.

`where`Klauzula może określać, że typem jest `class` lub `struct` . `struct`Ograniczenie eliminuje konieczność określenia ograniczenia klasy bazowej `System.ValueType` . `System.ValueType`Typ nie może być używany jako ograniczenie klasy bazowej. W poniższym przykładzie przedstawiono zarówno `class` warunek, jak i `struct` :

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#3)]

W kontekście dopuszczającym wartość null w języku C# 8,0 i nowszych, `class` ograniczenie wymaga typu jako typu referencyjnego, który nie dopuszcza wartości null. Aby zezwolić na typy referencyjne dopuszczające wartość null, użyj `class?` ograniczenia, które zezwala na typ referencyjny dopuszczający wartości null i niedopuszczający wartości null.

`where`Klauzula może zawierać `notnull` ograniczenie. `notnull`Ograniczenie ogranicza parametr typu do typu niedopuszczający wartości null. Ten typ może być typem [wartości](../builtin-types/value-types.md) lub typem referencyjnym, który nie dopuszcza wartości null. To `notnull` ograniczenie jest dostępne począwszy od języka C# 8,0 dla kodu skompilowanego w [ `nullable enable` kontekście](../../nullable-references.md#nullable-contexts). W przeciwieństwie do innych ograniczeń, jeśli argument typu narusza `notnull` ograniczenie, kompilator generuje ostrzeżenie zamiast błędu. Ostrzeżenia są generowane tylko w `nullable enable` kontekście.

> [!IMPORTANT]
> Deklaracje ogólne zawierające `notnull` ograniczenie mogą być używane w kontekście wartości null Oblivious, ale kompilator nie wymusza ograniczenia.

[!code-csharp[using the nonnull constraint](snippets/GenericWhereConstraints.cs#NotNull)]

`where`Klauzula może również zawierać `unmanaged` ograniczenie. `unmanaged`Ograniczenie ogranicza parametr typu do typów znanych jako [typy niezarządzane](../builtin-types/unmanaged-types.md). To `unmanaged` ograniczenie ułatwia zapisanie kodu międzyoperacyjności niskiego poziomu w języku C#. To ograniczenie umożliwia wykonywanie procedur wielokrotnego użytku we wszystkich typach niezarządzanych. `unmanaged`Nie można połączyć ograniczenia z `class` `struct` ograniczeniem or. `unmanaged`Ograniczenie wymusza, że typ musi być `struct` :

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#4)]

`where`Klauzula może również zawierać ograniczenie konstruktora `new()` . To ograniczenie umożliwia utworzenie wystąpienia parametru typu za pomocą `new` operatora. To [ograniczenie New ()](new-constraint.md) umożliwia kompilatorowi, że każdy dostarczony argument typu musi mieć dostępny Konstruktor bez parametrów. Przykład:

[!code-csharp[using the new constraint](snippets/GenericWhereConstraints.cs#5)]

`new()`Ograniczenie jest wyświetlane jako ostatnie w `where` klauzuli. `new()`Nie można połączyć ograniczenia z `struct` `unmanaged` ograniczeniami lub. Wszystkie typy spełniające te ograniczenia muszą mieć dostępny Konstruktor bez parametrów, co sprawia, że `new()` ograniczenie jest nadmiarowe.

W przypadku wielu parametrów typu należy użyć jednej `where` klauzuli dla każdego parametru typu, na przykład:

[!code-csharp[using multiple where constraints](snippets/GenericWhereConstraints.cs#6)]

Można również dołączyć ograniczenia do parametrów typu metod ogólnych, jak pokazano w następującym przykładzie:

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#7)]

Zauważ, że składnia opisująca ograniczenia parametru typu dla delegatów jest taka sama jak w przypadku metod:

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#8)]

Aby uzyskać informacje na temat delegatów ogólnych, zobacz [Delegaty ogólne](../../programming-guide/generics/generic-delegates.md).

Aby uzyskać szczegółowe informacje na temat składni i użycia ograniczeń, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../programming-guide/generics/index.md)
- [nowe ograniczenie](./new-constraint.md)
- [Ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md)
