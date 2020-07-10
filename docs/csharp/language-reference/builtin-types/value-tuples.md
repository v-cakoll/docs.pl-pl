---
title: Typy krotek — odwołanie w C#
description: 'Dowiedz się więcej o kolekcjach języka C#: lekkie struktury danych, których można użyć do grupowania luźno powiązanych elementów danych'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174992"
---
# <a name="tuple-types-c-reference"></a>Typy krotek (odwołanie w C#)

Dostępna w języku C# 7,0 i nowszych funkcja *kroteks* oferuje zwięzłą składnię do grupowania wielu elementów danych w lekkiej strukturze danych. Poniższy przykład pokazuje, jak można zadeklarować zmienną krotki, zainicjować ją i uzyskać dostęp do jej członków danych:

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

Jak pokazano w powyższym przykładzie, aby zdefiniować typ krotki, należy określić typy wszystkich elementów członkowskich danych i, opcjonalnie, [nazwy pól](#tuple-field-names). Nie można definiować metod w typie krotki, ale można użyć metod dostarczonych przez platformę .NET, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

Począwszy od języka C# 7,3, typy krotek obsługują [Operatory równości](../operators/equality-operators.md) `==` i `!=` . Aby uzyskać więcej informacji, zobacz sekcję [równość krotki](#tuple-equality) .

Typy krotek to [typy wartości](value-types.md); elementy krotki są polami publicznymi. Sprawia, że typy wartości *modyfikowalnych* krotek.

> [!NOTE]
> Funkcja krotek wymaga <xref:System.ValueTuple?displayProperty=nameWithType> typu i pokrewnych typów ogólnych (na przykład <xref:System.ValueTuple%602?displayProperty=nameWithType> ), które są dostępne w oprogramowaniu .NET Core i .NET Framework 4,7 i nowszych. Aby używać krotek w projekcie, który jest celem .NET Framework 4.6.2 lub wcześniejszym, Dodaj pakiet NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) do projektu.

Można definiować krotki z dowolną dużą liczbą elementów:

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a>Przypadki użycia krotek

Jednym z najczęstszych przypadków użycia krotek jest jako zwracany typ metody. Oznacza to, że zamiast definiować [ `out` Parametry metody](../keywords/out-parameter-modifier.md), można grupować wyniki metody w typie zwracanym spójnej kolekcji, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

Jak pokazano w powyższym przykładzie, można współpracować z zwracanym wystąpieniem krotki bezpośrednio lub [dekonstruować](#tuple-assignment-and-deconstruction) go w oddzielnych zmiennych.

Można również użyć typów krotek zamiast [typów anonimowych](../../programming-guide/classes-and-structs/anonymous-types.md); na przykład w zapytaniach LINQ. Aby uzyskać więcej informacji, zobacz [Wybieranie typów anonimowych i krotek](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).

Zwykle można używać krotek do grupowania luźno powiązanych elementów danych. Jest to zazwyczaj przydatne w przypadku prywatnych i wewnętrznych metod narzędziowych. W przypadku publicznego interfejsu API Rozważ zdefiniowanie [klasy](../keywords/class.md) lub typu [struktury](struct.md) .

## <a name="tuple-field-names"></a>Nazwy pól krotki

Można jawnie określić nazwy pól spójnych w wyrażeniu inicjowania krotki lub w definicji typu krotki, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

Począwszy od języka C# 7,1, jeśli nie określisz nazwy pola, można wywnioskować ją z nazwy odpowiadającej zmiennej w wyrażeniu inicjowania kolekcji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

Są to znane jako inicjatory projekcji krotki. Nazwa zmiennej nie jest rzutowana na nazwę pola krotki w następujących przypadkach:

- Nazwa kandydata to nazwa elementu członkowskiego typu krotki, na przykład,, `Item3` `ToString` lub `Rest` .
- Nazwa kandydata jest duplikatem innej nazwy pola krotki, jawnej lub niejawnej.

W takich przypadkach można jawnie określić nazwę pola lub uzyskać dostęp do pola według jego nazwy domyślnej.

Domyślne nazwy pól krotki są `Item1` , `Item2` , `Item3` i tak dalej. Zawsze możesz użyć domyślnej nazwy pola, nawet jeśli nazwa pola jest określona jawnie lub wywnioskowana, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

Porównanie [kolekcji](#tuple-assignment-and-deconstruction) i [równości krotek](#tuple-equality) nie przyjmuje nazw pól w ramach konta.

W czasie kompilacji kompilator zastępuje nazwy pól inne niż domyślne odpowiednimi nazwami domyślnymi. W związku z tym jawnie określone lub wywnioskowane nazwy pól nie są dostępne w czasie wykonywania.

## <a name="tuple-assignment-and-deconstruction"></a>Przypisanie krotki i dekonstrukcja

Język C# obsługuje przypisanie między typami krotek, które spełniają oba z następujących warunków:

- Oba typy krotek mają tę samą liczbę elementów
- dla każdej pozycji krotki typ elementu krotki po prawej stronie jest taki sam jak lub niejawnie konwertowany na typ odpowiadającego elementu krotki po lewej stronie

Wartości elementu krotki są przypisywane po kolejności elementów krotki. Nazwy pól krotek są ignorowane i nie są przypisywane, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

Można również użyć operatora przypisania, `=` Aby wypróbować wystąpienie krotki w oddzielnych zmiennych. *deconstruct* Można to zrobić w jeden z następujących sposobów:

- Jawnie Zadeklaruj typ każdej zmiennej w nawiasach:

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- Użyj `var` słowa kluczowego poza nawiasami, aby zadeklarować zmienne niejawnie wpisane i pozwolić kompilatorowi na wnioskowanie typów:

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- Użyj istniejących zmiennych:

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

Aby uzyskać więcej informacji na temat dekonstrukcji krotek i innych typów, zobacz [dekonstrukcja kroteks i innych typów](../../deconstruct.md).

## <a name="tuple-equality"></a>Równość krotki

Począwszy od języka C# 7,3, typy krotek obsługują `==` `!=` Operatory i. Te operatory porównują elementy członkowskie operandu po lewej stronie z odpowiednimi elementami członkowskimi operandu po prawej stronie po kolejności elementów krotki.

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

Jak pokazano w powyższym przykładzie `==` , `!=` operacje i nie uwzględniają nazw pól krotki.

Dwie krotki są porównywalne, gdy spełnione są oba z następujących warunków:

- Obie krotki mają tę samą liczbę elementów. Na przykład, `t1 != t2` nie kompiluje, jeśli `t1` i `t2` mają różne liczby elementów.
- Dla każdej pozycji krotki odpowiednie elementy z operandów po lewej stronie i po prawej stronie są porównywalne z `==` `!=` operatorami i. Na przykład `(1, (2, 3)) == ((1, 2), 3)` nie kompiluje się, ponieważ `1` nie jest porównywalna z `(1, 2)` .

`==`Operatory i `!=` porównują krotki w sposób skrócony obwodu. Oznacza to, że operacja zostaje zatrzymana, gdy tylko spełni parę elementów nierównych lub osiąga końce krotek. Jednak przed jakimkolwiek porównaniem *wszystkie* elementy krotki są oceniane, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a>Krotki jako parametry out

Zazwyczaj refaktoryzacja jest metoda, która ma [ `out` Parametry](../keywords/out-parameter-modifier.md) w metodzie zwracającej krotkę. Istnieją jednak przypadki, w których `out` parametr może być typu krotki. Poniższy przykład pokazuje, jak używać krotek jako `out` parametrów:

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a>Krotki a`System.Tuple`

Krotki języka C#, które są obsługiwane przez <xref:System.ValueTuple?displayProperty=nameWithType> typy, różnią się od krotek, które są reprezentowane przez <xref:System.Tuple?displayProperty=nameWithType> typy. Główne różnice są następujące:

- `ValueTuple`typy są [typami wartości](value-types.md). `Tuple`typy to [typy odwołań](../keywords/reference-types.md).
- `ValueTuple`typy są modyfikowalne. `Tuple`typy są niezmienne.
- Elementy członkowskie danych `ValueTuple` typów są polami. Elementy członkowskie danych `Tuple` typów są właściwościami.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące uwagi dotyczące propozycji funkcji:

- [Wywnioskowanie nazw krotek (aliasy projekcji w kolekcji.](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [Obsługa `==` typów krotek i dla nich `!=`](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Wybór między typami anonimowymi a kolekcjami](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
