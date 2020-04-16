---
title: gdzie (ograniczenie typu ogólnego) - Odwołanie C#
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 5a56b8058735d3ca786520a82424c79d1975bfc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463012"
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)

Klauzula `where` w definicji ogólnej określa ograniczenia dotyczące typów, które są używane jako argumenty dla parametrów typu w typie ogólnym, metodzie, delegata lub funkcji lokalnej. Ograniczenia można określić interfejsy, klasy podstawowe lub wymagają typu ogólnego, aby być odwołanie, wartość lub typu niezarządzanego. Deklarują możliwości, które musi mieć argument typu.

Na przykład można zadeklarować klasy `MyGenericClass`ogólnej, tak, `T` że <xref:System.IComparable%601> parametr typu implementuje interfejs:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat klauzuli where w wyrażeniu kwerendy, zobacz [where clause](where-clause.md).

Klauzula `where` może również zawierać ograniczenie klasy podstawowej. Ograniczenie klasy podstawowej stwierdza, że typ, który ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę podstawową lub jest tą klasą podstawową. Jeśli używane jest ograniczenie klasy podstawowej, musi pojawić się przed innymi ograniczeniami dla tego parametru typu. Niektóre typy są niedozwolone <xref:System.Object> <xref:System.Array>jako <xref:System.ValueType>ograniczenie klasy podstawowej: , i . Przed C# 7.3, <xref:System.Enum>, <xref:System.Delegate>i <xref:System.MulticastDelegate> zostały również niedozwolone jako ograniczenia klasy podstawowej. Poniższy przykład przedstawia typy, które można teraz określić jako klasę podstawową:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

W kontekście nullable w języku C# 8.0 i nowszych, nullability typu klasy podstawowej jest wymuszane. Jeśli klasa podstawowa nie może być `Base`nullable (na przykład), argument typu musi być nie można nullable. Jeśli klasa podstawowa jest nullable (na przykład), `Base?`argument typu może być nullable lub non-nullable typu odwołania. Kompilator generuje ostrzeżenie, jeśli argument typu jest typem odwołania z dopuszczalną wartością null, gdy klasa podstawowa nie może być nullowa.

Klauzula `where` może określać, `class` że `struct`typ jest lub . Ograniczenie `struct` eliminuje konieczność określania ograniczenia klasy `System.ValueType`podstawowej . Typ `System.ValueType` nie może być używany jako ograniczenie klasy podstawowej. Poniższy przykład przedstawia `class` `struct` zarówno ograniczenia, jak i ograniczenia:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

W kontekście nullable w języku C# 8.0 i `class` nowszych, ograniczenie wymaga typu, który ma być typem odwołania niepodjętego do null. Aby zezwolić na typy `class?` odwołań nullable, należy użyć ograniczenia, które umożliwia zarówno nullable i non-null typy odwołania.

Klauzula `where` może `notnull` zawierać ograniczenie. Ograniczenie `notnull` ogranicza parametr typu do typów nienastępalnych do wartości null. Ten typ może być [typem wartości](../builtin-types/value-types.md) lub typem odwołania, którego nie można podkreślać. Ograniczenie `notnull` jest dostępne począwszy od języka C# 8.0 dla kodu skompilowanego w [ `nullable enable` kontekście](../../nullable-references.md#nullable-contexts). W przeciwieństwie do innych ograniczeń, jeśli `notnull` argument typu narusza ograniczenie, kompilator generuje ostrzeżenie zamiast błędu. Ostrzeżenia są generowane `nullable enable` tylko w kontekście.

> [!IMPORTANT]
> Ogólne deklaracje, `notnull` które zawierają ograniczenie mogą być używane w kontekście nullable oblivious, ale kompilator nie wymusza ograniczenia.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Klauzula `where` może również `unmanaged` zawierać ograniczenie. Ograniczenie `unmanaged` ogranicza parametr typu do typów nazywany jako [typy niezarządzane](../builtin-types/unmanaged-types.md). Ograniczenie `unmanaged` ułatwia pisanie kodu interop niskiego poziomu w języku C#. To ograniczenie umożliwia procedury wielokrotnegoużynia we wszystkich typach niezarządzanych. Ograniczenia `unmanaged` nie można łączyć `class` z `struct` ograniczeniem lub ograniczeniem. Ograniczenie `unmanaged` wymusza, że typ `struct`musi być:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Klauzula `where` może również zawierać ograniczenie `new()`konstruktora, . To ograniczenie umożliwia utworzenie wystąpienia parametru typu `new` przy użyciu operatora. [Ograniczenie new()](new-constraint.md) informuje kompilatora wiedzieć, że każdy argument typu dostarczone musi mieć dostępne bez parametrów konstruktora. Przykład:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Ograniczenie `new()` pojawia się `where` ostatnio w klauzuli. Ograniczenia `new()` nie można łączyć `struct` z `unmanaged` ograniczeniami lub ograniczeniami. Wszystkie typy spełniające te ograniczenia muszą mieć dostępny `new()` konstruktor bez parametrów, co powoduje, że ograniczenie jest zbędne.

W przypadku wielu parametrów typu należy użyć jednej `where` klauzuli dla każdego parametru typu, na przykład:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Ograniczenia można również dołączyć do parametrów typu metod ogólnych, jak pokazano w poniższym przykładzie:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Należy zauważyć, że składnia opisująca ograniczenia parametrów typu delegatów jest taka sama jak w metodach:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Aby uzyskać informacje na temat delegatów ogólnych, zobacz [Ogólne delegatów](../../programming-guide/generics/generic-delegates.md).

Aby uzyskać szczegółowe informacje na temat składni i stosowania ograniczeń, zobacz [Ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../programming-guide/generics/index.md)
- [nowe ograniczenie](./new-constraint.md)
- [Ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md)
