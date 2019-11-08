---
title: Typy wartości null — C# odwołanie
description: Dowiedz C# się więcej o typach wartości null i sposobach ich użycia
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: b9400cd76eb0430dbe9c278e835a3cec7f9f131e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741166"
---
# <a name="nullable-value-types-c-reference"></a>Typy wartości null (C# odwołanie)

Typ wartości null `T?` reprezentuje wszystkie wartości jego bazowego [typu wartości](../keywords/value-types.md) `T` i dodatkową wartość [null](../keywords/null.md) . Na przykład można przypisać jedną z następujących trzech wartości do zmiennej `bool?`: `true`, `false`lub `null`. Podstawowy typ wartości `T` nie może być samym typem wartości null.

> [!NOTE]
> C#8,0 wprowadza funkcję typów odwołań do wartości null. Aby uzyskać więcej informacji, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md). Typy wartości null są dostępne od C# 2.

Każdy typ wartości null jest wystąpieniem ogólnej struktury <xref:System.Nullable%601?displayProperty=nameWithType>. Można odwołać się do typu wartości null z typem podstawowym `T` w dowolnej z następujących formularzy, które można zmieniać: `Nullable<T>` lub `T?`.

Typ wartości null jest zazwyczaj używany, gdy trzeba reprezentować niezdefiniowaną wartość bazowego typu wartości. Na przykład wartość logiczna lub `bool`zmienna może być tylko `true` lub `false`. Jednak w niektórych aplikacjach wartość zmiennej może być niezdefiniowana lub brakująca. Na przykład pole bazy danych może zawierać `true` lub `false`lub nie może zawierać żadnej wartości, czyli `NULL`. W tym scenariuszu można użyć typu `bool?`.

## <a name="declaration-and-assignment"></a>Deklaracja i przypisanie

Ponieważ typ wartości jest niejawnie konwertowany do odpowiadającego typu wartości null, można przypisać wartość do zmiennej typu wartości null, tak jak w przypadku jego bazowego typu wartości. Możesz również przypisać wartość `null`. Na przykład:

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

Wartość domyślna typu wartości null reprezentuje `null`, czyli jest to wystąpienie, którego właściwość <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> zwraca `false`.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Badanie wystąpienia typu wartości null

Począwszy od C# 7,0, można użyć [operatora`is` ze wzorcem typu](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) do obu badań wystąpienie typu wartości null dla `null` i pobrać wartość typu podstawowego:

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

Aby sprawdzać i pobierać wartość zmiennej typu wartości null, zawsze można użyć następujących właściwości tylko do odczytu:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> wskazuje, czy wystąpienie typu wartości null ma wartość jego typu podstawowego.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, właściwość <xref:System.Nullable%601.Value%2A> zgłasza <xref:System.InvalidOperationException>.

W poniższym przykładzie zastosowano Właściwość `HasValue`, aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem:

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

Można także porównać zmienną typu wartości null z `null` zamiast korzystać z właściwości `HasValue`, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Konwersja z typu wartości null na typ podstawowy

Jeśli chcesz przypisać wartość typu wartości null do zmiennej typu wartości, która nie dopuszcza wartości null, może być konieczne określenie wartości, która ma zostać przypisana zamiast `null`. Użyj [`??`operatora łączenia wartości null](../operators/null-coalescing-operator.md) , aby to zrobić (można również użyć metody <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> do tego samego celu):

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

Jeśli chcesz użyć [domyślnej](../keywords/default-values-table.md) wartości bazowego typu wartości zamiast `null`, użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>.

Można również jawnie rzutować typ wartości null na typ niedopuszczający wartości null, co ilustruje poniższy przykład:

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

W czasie wykonywania, jeśli wartość typu wartości null jest `null`, jawne rzutowanie zgłosi <xref:System.InvalidOperationException>.

Typ wartości niedopuszczający wartości null `T` jest niejawnie konwertowany na odpowiedni typ wartości null `T?`.

## <a name="lifted-operators"></a>Podniesione operatory

Wstępnie zdefiniowane operatory jednoargumentowe i binarne lub wszelkie przeciążone operatory obsługiwane przez typ wartości `T` są również obsługiwane przez odpowiedni typ wartości null `T?`. Te operatory, znane także jako *zniesione operatory*, tworzą `null`, jeśli jeden lub oba operandy są `null`; w przeciwnym razie operator używa zawartych wartości argumentów operacji, aby obliczyć wynik. Na przykład:

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Dla typu `bool?` wstępnie zdefiniowane operatory `&` i `|` nie są zgodne z regułami opisanymi w tej sekcji: wynik oceny operatora może być inny niż null, nawet jeśli jeden z operandów jest `null`. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../operators/boolean-logical-operators.md) .

Dla [operatorów porównania](../operators/comparison-operators.md) `<`, `>`, `<=`i `>=`, jeśli jeden lub oba operandy są `null`, wynik jest `false`; w przeciwnym razie zawarte wartości argumentów operacji są porównywane. Nie należy zakładać, że ponieważ określone porównanie (na przykład `<=`) zwraca `false`, przeciwieństwo do porównania (`>`) zwraca `true`. Poniższy przykład pokazuje, że 10 jest

- nie większe niż ani równe `null`
- ani nie mniejsze niż `null`

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

W powyższym przykładzie przedstawiono również, że porównanie równości dwóch wystąpień typu wartości null, które są jednocześnie `null` oblicza `true`.

Jeśli istnieje [konwersja zdefiniowana przez użytkownika](../operators/user-defined-conversion-operators.md) między dwoma typami wartości, można także użyć tej samej konwersji między odpowiednimi typami wartości null.

## <a name="boxing-and-unboxing"></a>Pakowanie i rozpakowywanie

Wystąpienie typu wartości null `T?` jest [opakowane](../../programming-guide/types/boxing-and-unboxing.md) w następujący sposób:

- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `false`, zostanie wygenerowane odwołanie o wartości null.
- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`, odpowiadająca wartość bazowego typu wartości `T` jest opakowana, a nie wystąpieniem <xref:System.Nullable%601>.

Można Unbox wartość opakowaną typu wartości `T` do odpowiadającego typu wartości null `T?`, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Jak zidentyfikować typ wartości null

Poniższy przykład pokazuje, jak ustalić, czy wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentuje skonstruowany typ wartości null, czyli typ <xref:System.Nullable%601?displayProperty=nameWithType> z określonym parametrem typu `T`:

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

Jak pokazano w przykładzie, należy użyć operatora [typeof](../operators/type-testing-and-cast.md#typeof-operator) , aby utworzyć wystąpienie <xref:System.Type?displayProperty=nameWithType>.

Aby określić, czy wystąpienie ma typ wartości null, nie należy używać metody <xref:System.Object.GetType%2A?displayProperty=nameWithType>, aby uzyskać <xref:System.Type> wystąpienie do przetestowania przy użyciu poprzedniego kodu. Po wywołaniu metody <xref:System.Object.GetType%2A?displayProperty=nameWithType> w wystąpieniu typu wartości null wystąpienie jest [opakowane](#boxing-and-unboxing) do <xref:System.Object>. Jako opakowanie niezerowego typu wartości null jest równoważne z opakowaniem wartości typu podstawowego, <xref:System.Object.GetType%2A> zwraca wystąpienie <xref:System.Type> reprezentujące typ podstawowy typu wartości null:

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

Ponadto nie należy używać operatora [is](../operators/type-testing-and-cast.md#is-operator) , aby określić, czy wystąpienie ma typ wartości null. Jak pokazano na poniższym przykładzie, nie można rozróżnić typów wystąpienia typu wartości null i jego wystąpienia podstawowego z operatorem `is`:

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

Możesz użyć kodu przedstawionego w poniższym przykładzie, aby określić, czy wystąpienie ma typ wartości null:

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Metody opisane w tej sekcji nie mają zastosowania w przypadku [typów referencyjnych dopuszczających wartość null](../../nullable-references.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Typy dopuszczające wartości null](~/_csharplang/spec/types.md#nullable-types)
- [Podniesione operatory](~/_csharplang/spec/expressions.md#lifted-operators)
- [Niejawne konwersje dopuszczające wartość null](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Jawne konwersje dopuszczające wartość null](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Przenoszone operatory konwersji](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Co dokładnie ma znaczenie "zniesione"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Typy referencyjne dopuszczające wartość null](../../nullable-references.md)
