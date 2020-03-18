---
title: Typy wartości null - odwołanie do języka C#
description: Dowiedz się więcej o typach wartości null z wartościami języka C# i sposobie ich używania
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: a84b3d60269491846b783e5046a84a1d14e258a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399589"
---
# <a name="nullable-value-types-c-reference"></a>Typy wartości null (odwołanie do języka C#)

*Typ* `T?` wartości nullable reprezentuje wszystkie wartości jego podstawowego typu `T` [wartości](value-types.md) i dodatkowej wartości [null.](../keywords/null.md) Na przykład do `bool?` zmiennej można przypisać dowolną z `true` `false`następujących `null`trzech wartości: , , lub . Typ wartości podstawowej `T` nie może być typem wartości null.

> [!NOTE]
> C# 8.0 wprowadza funkcję typów odwołań nullable. Aby uzyskać więcej informacji, zobacz [Typy odwołań nullable](../../nullable-references.md). Typy wartości nullable są dostępne począwszy od Języka C# 2.

Każdy typ wartości nullable jest <xref:System.Nullable%601?displayProperty=nameWithType> wystąpieniem struktury ogólnej. Można odwołać się do typu wartości null `T` z typem bazowym `Nullable<T>` w `T?`dowolnej z następujących form wymiennych: lub .

Zazwyczaj należy użyć typu wartości null, gdy trzeba reprezentować niezdefiniowaną wartość podstawowego typu wartości. Na przykład wartość logiczna `bool`lub zmienna `true` może `false`być tylko jedną lub zmienną. Jednak w niektórych aplikacjach wartość zmiennej może być niezdefiniowana lub brakuje. Na przykład pole bazy `true` danych `false`może zawierać lub , lub może `NULL`zawierać żadnej wartości w ogóle, to znaczy . Można użyć `bool?` tego typu w tym scenariuszu.

## <a name="declaration-and-assignment"></a>Deklaracja i przypisanie

Jako typ wartości jest niejawnie konwertowalne do odpowiedniego typu wartości nullable, można przypisać wartość do zmiennej typu wartości null, jak to zrobić dla jego podstawowego typu wartości. Można również przypisać `null` wartość. Przykład:

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

Wartość domyślna typu wartości nullable `null`reprezentuje , oznacza to, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> że `false`jest to wystąpienie, którego właściwość zwraca .

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Badanie wystąpienia typu wartości podleganej null

Począwszy od Języka C# 7.0, można użyć [ `is` operatora z wzorcem typu](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) zarówno `null` zbadać wystąpienie typu wartości nullable dla i pobrać wartość typu źródłowego:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Zawsze można użyć następujących właściwości tylko do odczytu, aby sprawdzić i uzyskać wartość zmiennej typu wartości nullable:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>wskazuje, czy wystąpienie typu wartości nullable ma wartość jego typu bazowego.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>pobiera wartość typu bazowego, <xref:System.Nullable%601.HasValue%2A> `true`jeśli jest . Jeśli <xref:System.Nullable%601.HasValue%2A> `false`jest <xref:System.Nullable%601.Value%2A> , właściwość <xref:System.InvalidOperationException>rzuca .

W poniższym `HasValue` przykładzie użyto właściwości, aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem go:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Można również porównać zmienną typu wartości `null` nullable z `HasValue` zamiast przy użyciu właściwości, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Konwersja z typu wartości null do typu bazowego

Jeśli chcesz przypisać wartość typu wartości nullable do zmiennej typu wartości niepodleganej null, może być konieczne określenie `null`wartości, która ma być przypisana w miejsce . Użyj [operatora `??` łączenia wartości null,](../operators/null-coalescing-operator.md) aby to zrobić (można <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> również użyć metody w tym samym celu):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Jeśli chcesz użyć [wartości domyślnej](default-values.md) podstawowego typu wartości `null`w <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> miejsce , należy użyć tej metody.

Można również jawnie rzutować typ wartości nullable do typu niedopuszczającowego, jak pokazano w poniższym przykładzie:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

W czasie wykonywania, jeśli wartość typu `null`wartości nullable jest <xref:System.InvalidOperationException>, jawne rzutnie rzuca .

Typ `T` wartości niepodlegający null jest niejawnie konwertowalny na `T?`odpowiadający mu typ wartości nullable .

## <a name="lifted-operators"></a>Operatorzy podnoszenia

Wstępnie zdefiniowane [operatory](../operators/index.md) nieoparte i binarne lub wszelkie przeciążone operatory, które są obsługiwane przez typ `T` wartości, są również obsługiwane przez odpowiedni typ `T?`wartości nullable . Podmioty te, znane również jako `null` *operatorzy podnoszenia,* `null`produkują, jeśli jeden lub oba operandy są; w przeciwnym razie operator używa zawartych wartości swoich operandów do obliczenia wyniku. Przykład:

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Dla `bool?` typu wstępnie zdefiniowane `&` i `|` operatory nie są zgodne z regułami opisanymi w tej sekcji: wynik oceny operatora może `null`być non-null, nawet jeśli jeden z operands jest . Aby uzyskać więcej informacji, zobacz [nullable logicznych operatorów logicznych](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logicznych operatorów logicznych.](../operators/boolean-logical-operators.md)

Dla [operatorów](../operators/comparison-operators.md) `<`porównawczych `<=`, `>=` `>`, i , jeśli `null`jeden lub `false`oba argumenty są , wynik jest; w przeciwnym razie porównywane są zawarte wartości argumentów. Nie zakładaj, że ponieważ określone `<=`porównanie `false`(na przykład)`>`zwraca, odwrotne porównanie ( ) zwraca `true`. W poniższym przykładzie pokazano, że 10

- ani większe niż równe`null`
- ani mniej niż`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Dla [operatora](../operators/equality-operators.md#equality-operator-) `==`równości , jeśli oba `null`operandy `true`są , wynik jest , `null`jeśli tylko `false`jeden z argumentów jest , wynik jest; w przeciwnym razie porównywane są zawarte wartości argumentów.

Dla [operatora](../operators/equality-operators.md#inequality-operator-) `!=`nierówności , jeśli oba `null`argumenty `false`są , wynik jest , `null`jeśli tylko `true`jeden z argumentów jest , wynik jest; w przeciwnym razie porównywane są zawarte wartości argumentów.

Jeśli istnieje [konwersja zdefiniowana przez użytkownika](../operators/user-defined-conversion-operators.md) między dwoma typami wartości, ta sama konwersja może być również używana między odpowiadającymi typami wartości nullable.

## <a name="boxing-and-unboxing"></a>Boks i rozpakowywanie

Wystąpienie typu `T?` wartości nullable jest [zapakowane w](../../programming-guide/types/boxing-and-unboxing.md) następujący sposób:

- Jeśli <xref:System.Nullable%601.HasValue%2A> `false`zwraca, odwołanie null jest tworzony.
- Jeśli <xref:System.Nullable%601.HasValue%2A> `true`zwraca, odpowiednia wartość podstawowego `T` typu wartości jest zapakowana, a nie wystąpienie <xref:System.Nullable%601>.

Można rozpakować zakrojoną `T` wartość typu wartości do `T?`odpowiedniego typu wartości nullable , jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Jak zidentyfikować typ wartości z wartością nullable

W poniższym przykładzie pokazano, jak określić, czy <xref:System.Type?displayProperty=nameWithType> wystąpienie reprezentuje skonstruowany typ wartości nullable, czyli <xref:System.Nullable%601?displayProperty=nameWithType> typ z parametrem `T`określonego typu:

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Jak pokazano w przykładzie, należy użyć <xref:System.Type?displayProperty=nameWithType> [operatora typeof](../operators/type-testing-and-cast.md#typeof-operator) do utworzenia wystąpienia.

Jeśli chcesz ustalić, czy wystąpienie ma wartość nullable, nie <xref:System.Object.GetType%2A?displayProperty=nameWithType> należy używać <xref:System.Type> metody, aby uzyskać wystąpienie do przetestowania z poprzednim kodem. Podczas wywoływania <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu wartości nullable, wystąpienie <xref:System.Object>jest [zapakowane](#boxing-and-unboxing) w . Jako boks wystąpienia non-null typu wartości nulljest odpowiednik bokserskiej wartości typu podstawowego, <xref:System.Type> zwraca wystąpienie, <xref:System.Object.GetType%2A> które reprezentuje typ wartości o wartości null:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

Ponadto nie należy używać [is](../operators/type-testing-and-cast.md#is-operator) operator, aby ustalić, czy wystąpienie jest typu wartości null. Jak pokazano w poniższym przykładzie, nie można odróżnić typów wystąpienia typu `is` wartości nulli z jego wystąpieniem typu źródłowego z operatorem:

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Kod przedstawiony w poniższym przykładzie, aby ustalić, czy wystąpienie ma wartość nullable:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Metody opisane w tej sekcji nie mają zastosowania w przypadku [typów odwołań podlegających wartości null.](../../nullable-references.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Typy z możliwością null](~/_csharplang/spec/types.md#nullable-types)
- [Operatorzy podnoszenia](~/_csharplang/spec/expressions.md#lifted-operators)
- [Niejawne konwersje nullable](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Jawne konwersje nullable](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Operatorzy konwersji podniesionej](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Co dokładnie oznacza "zniesione"?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Typy referencyjne dopuszczające wartość null](../../nullable-references.md)
