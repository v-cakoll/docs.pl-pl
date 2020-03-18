---
title: gdzie (ograniczenie typu ogólnego) - Odwołanie c#
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: d236420c5019f7529b729155b13df50807dc1dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626714"
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)

Klauzula `where` w definicji ogólnej określa ograniczenia typów, które są używane jako argumenty dla parametrów typu w typie ogólnym, metody, delegowania lub funkcji lokalnej. Ograniczenia mogą określać interfejsy, klasy podstawowe lub wymagać, aby typ ogólny był typem referencyjnym, wartościowym lub niezarządzanym. Deklarują one możliwości, które musi posiadać argument typu.

Na przykład można zadeklarować klasę `MyGenericClass`rodzajową, w `T` taki <xref:System.IComparable%601> sposób, że parametr type implementuje interfejs:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat where klauzuli w wyrażeniu kwerendy, zobacz [gdzie klauzula](where-clause.md).

Klauzula `where` może również zawierać ograniczenie klasy podstawowej. Ograniczenie klasy podstawowej stwierdza, że typ, który ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę podstawową (lub jest tą klasą podstawową), która ma być używana jako argument typu dla tego typu ogólnego. Jeśli używane jest ograniczenie klasy podstawowej, musi pojawić się przed innymi ograniczeniami dla tego parametru typu. Niektóre typy są niedozwolone jako ograniczenie klasy <xref:System.Object> <xref:System.Array>podstawowej: , , i <xref:System.ValueType>. Przed C# 7.3 <xref:System.Enum> <xref:System.Delegate>, <xref:System.MulticastDelegate> , i były również niedozwolone jako ograniczenia klasy podstawowej. W poniższym przykładzie przedstawiono typy, które można teraz określić jako klasę podstawową:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Klauzula `where` może określać, `class` że `struct`typ jest a lub . Ograniczenie `struct` eliminuje konieczność określania ograniczenia klasy podstawowej . `System.ValueType` Typ `System.ValueType` nie może być używany jako ograniczenie klasy podstawowej. W poniższym `class` przykładzie `struct` przedstawiono zarówno i ograniczenia:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

Klauzula `where` może `notnull` zawierać ograniczenie. Ograniczenie `notnull` ogranicza parametr typu do typów niepodlegających zerwaniu. Ten typ może być [typem wartości](../builtin-types/value-types.md) lub typem odwołania niepodlegającym wartości null. Ograniczenie `notnull` jest dostępne począwszy od języka C# 8.0 dla kodu skompilowanego w [ `nullable enable` kontekście](../../nullable-references.md#nullable-contexts). W przeciwieństwie do innych ograniczeń, `notnull` jeśli argument typu narusza ograniczenie, kompilator generuje ostrzeżenie zamiast błędu. Ostrzeżenia są generowane tylko `nullable enable` w kontekście.

> [!IMPORTANT]
> Deklaracje ogólne, `notnull` które zawierają ograniczenie mogą być używane w kontekście nullable nieświadomych, ale kompilator nie wymusza ograniczenia.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Klauzula `where` może również `unmanaged` zawierać ograniczenie. Ograniczenie `unmanaged` ogranicza parametr typu do typów znanych jako [typy niezarządzane](../builtin-types/unmanaged-types.md). Ograniczenie `unmanaged` ułatwia pisanie kodu współdliczbowego niskiego poziomu w języku C#. To ograniczenie umożliwia procedury wielokrotnego użytku we wszystkich typach niezarządzanych. Ograniczenia `unmanaged` nie można łączyć z `class` lub `struct` ograniczenia. `unmanaged` Ograniczenie wymusza, że typ musi być `struct`:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Klauzula `where` może również zawierać ograniczenie konstruktora. `new()` To ograniczenie umożliwia utworzenie wystąpienia parametru typu przy `new` użyciu operatora. [New() Ograniczenie](new-constraint.md) informuje kompilator wiedzieć, że każdy argument typu dostarczone musi mieć dostępny konstruktor bez parametrów. Przykład:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Ograniczenie `new()` pojawia się ostatnio `where` w klauzuli. Ograniczenia `new()` nie można łączyć z ograniczeniami `struct` `unmanaged` lub ograniczeniami. Wszystkie typy spełniające te ograniczenia muszą mieć konstruktora dostępnego bezparametrów, dzięki czemu `new()` ograniczenie jest nadmiarowe.

W przypadku wielu parametrów `where` typu należy użyć jednej klauzuli dla każdego parametru typu, na przykład:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Ograniczenia można również dołączyć do parametrów typu metod ogólnych, jak pokazano w poniższym przykładzie:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Należy zauważyć, że składnia opisująca ograniczenia parametrów typu dla delegatów jest taka sama jak w przypadku metod:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Aby uzyskać informacje na temat delegatów ogólnych, zobacz [Ogólne delegatów](../../programming-guide/generics/generic-delegates.md).

Aby uzyskać szczegółowe informacje na temat składni i użycia ograniczeń, zobacz [Ograniczenia parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../programming-guide/generics/index.md)
- [nowe ograniczenie](./new-constraint.md)
- [Ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md)
