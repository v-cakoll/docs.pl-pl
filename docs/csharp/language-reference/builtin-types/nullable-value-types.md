---
title: Typy wartości możliwe do wartości null — odwołanie do języka C#
description: Dowiedz się więcej o typach wartości nullable języka C# i o tym, jak z nich korzystać
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: fcd49d7d25b0ad23363db8cb61596004b2e87a8d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738997"
---
# <a name="nullable-value-types-c-reference"></a>Typy wartości możliwe do wartości null (odwołanie do języka C#)

`T?` *Typ wartości możliwej do wartości null* reprezentuje wszystkie wartości jego typ `T` [wartości](value-types.md) podstawowej i dodatkową wartość [null.](../keywords/null.md) Na przykład `bool?` do zmiennej można przypisać dowolną z `true` `false`następujących `null`trzech wartości: , , lub . Typ `T` wartości podstawowej nie może być typem wartości możliwej do wartości null.

> [!NOTE]
> C# 8.0 wprowadza funkcję typów odwołań nullable. Aby uzyskać więcej informacji, zobacz [Typy odwołań do wartości null.](nullable-reference-types.md) Typy wartości możliwe do wartości null są dostępne począwszy od języka C# 2.

Każdy typ wartości nullable jest <xref:System.Nullable%601?displayProperty=nameWithType> wystąpieniem struktury ogólnej. Można odwołać się do typu wartości `T` nullable z typem bazowym w dowolnej z następujących wymiennych formularzy: `Nullable<T>` lub `T?`.

Typ wartości z możliwością wartości nullable jest zazwyczaj używany, gdy należy przedstawić niezdefiniowana wartość typu wartości podstawowej. Na przykład wartość logiczna `bool`lub zmienna może `true` `false`być tylko jedną lub . Jednak w niektórych aplikacjach wartość zmiennej może być niezdefiniowana lub brakuje. Na przykład pole bazy `true` danych `false`może zawierać lub , lub może `NULL`zawierać żadną wartość, to znaczy . Można użyć `bool?` typu w tym scenariuszu.

## <a name="declaration-and-assignment"></a>Deklaracja i przydział

Jako typ wartości jest niejawnie konwertowane do odpowiedniego typu wartości nullable, można przypisać wartość do zmiennej typu wartości nullable, jak to zrobić dla jego typ wartości podstawowej. Można również przypisać `null` wartość. Przykład:

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

Wartość domyślna typu wartości możliwej do wartości null reprezentuje `null` <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> , `false`to znaczy, że jest to wystąpienie, którego właściwość zwraca .

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Badanie wystąpienia typu wartości możliwej domina

Począwszy od języka C# 7.0, można użyć [ `is` operatora z wzorcem typu,](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) aby zarówno zbadać wystąpienie typu wartości możliwej do wartości null dla `null` i pobrać wartość typu bazowego:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Zawsze można użyć następujących właściwości tylko do odczytu, aby zbadać i uzyskać wartość zmiennej typu wartości nullable:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>wskazuje, czy wystąpienie typu wartości możliwej do wartości null ma wartość jego typu bazowego.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>pobiera wartość typu bazowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`. Jeśli <xref:System.Nullable%601.HasValue%2A> `false`tak, <xref:System.Nullable%601.Value%2A> właściwość <xref:System.InvalidOperationException>rzuca .

Poniższy przykład używa `HasValue` właściwości, aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem go:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Można również porównać zmienną typu wartości `null` nullable z `HasValue` zamiast używać właściwości, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Konwersja z typu wartości możliwej do wartości null do typu bazowego

Jeśli chcesz przypisać wartość typu wartości możliwej do wartości null do zmiennej typu wartości nienastępującej wartość `null`null, może być konieczne określenie wartości, która ma być przypisana zamiast pliku . Użyj [operatora `??` scalania null,](../operators/null-coalescing-operator.md) aby to zrobić (można również użyć metody w <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> tym samym celu):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Jeśli chcesz użyć wartości [domyślnej](default-values.md) typu wartości podstawowej `null`zamiast <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , użyj metody.

Można również jawnie rzutować typ wartości nullable do typu niedopuszczalnyego do wartości null, jak pokazano w poniższym przykładzie:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

W czasie wykonywania, jeśli wartość typu wartości `null`możliwej do wartości <xref:System.InvalidOperationException>nullable jest , jawne rzut rzutnie zgłasza .

Typ `T` wartości nienastępnej wartości jest niejawnie konwertowany na odpowiedni typ `T?`wartości null.

## <a name="lifted-operators"></a>Operatorzy podnoszony

Wstępnie zdefiniowane [operatory](../operators/index.md) jednoarbyowe i binarne lub wszelkie przeciążone operatory obsługiwane przez `T` typ `T?`wartości są również obsługiwane przez odpowiedni typ wartości nullable . Operatorzy ci, znani również jako `null` *operatorzy podniesiony,* produkują, jeśli jeden lub oba argumenty są; `null` w przeciwnym razie operator używa zawartych wartości swoich argumentów do obliczania wyniku. Przykład:

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Dla `bool?` typu wstępnie zdefiniowane `&` i `|` operatory nie są zgodne z regułami opisanymi w tej sekcji: wynik oceny operatora może `null`być nie-null, nawet jeśli jeden z argumentów jest . Aby uzyskać więcej informacji, zobacz [nullable logiczne operatory logiczne](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logiczne logiczne](../operators/boolean-logical-operators.md) logiczne artykułu.

Dla [operatorów](../operators/comparison-operators.md) `<` `>`porównania `<=`, `>=`, , i , `null`jeśli jeden `false`lub oba argumenty są , wynik jest; w przeciwnym razie porównywane są zawarte wartości operandów. Nie należy zakładać, że ponieważ `<=`określone `false`porównanie (na`>`przykład) `true`zwraca , zwraca porównanie przeciwne ( ) zwraca . Poniższy przykład pokazuje, że 10 jest

- ani większe niż lub równe`null`
- ani mniej niż`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Dla [operatora](../operators/equality-operators.md#equality-operator-) `==`równości , jeśli oba `null`argumenty są `true`, wynik jest, jeśli `null`tylko jeden `false`z argumentów jest , wynik jest ; w przeciwnym razie porównywane są zawarte wartości operandów.

Dla [operatora](../operators/equality-operators.md#inequality-operator-) `!=`nierówności , jeśli oba `null`argumenty są `false`, wynik jest, jeśli tylko `null`jeden z `true`argumentów jest , wynik jest ; w przeciwnym razie porównywane są zawarte wartości operandów.

Jeśli istnieje [konwersja zdefiniowana przez użytkownika](../operators/user-defined-conversion-operators.md) między dwoma typami wartości, ta sama konwersja może być również używana między odpowiednimi typami wartości nullable.

## <a name="boxing-and-unboxing"></a>Boks i rozpakowywanie

Wystąpienie typu `T?` wartości możliwej do wartości null jest [zapakowane w](../../programming-guide/types/boxing-and-unboxing.md) następujący sposób:

- Jeśli <xref:System.Nullable%601.HasValue%2A> `false`zwraca , wywoływane jest odwołanie null.
- Jeśli <xref:System.Nullable%601.HasValue%2A> `true`zwraca , odpowiednia wartość `T` typu wartości podstawowej jest <xref:System.Nullable%601>zapakowana, a nie wystąpienie .

Można rozpakować wartość pudełkową typu `T` wartości do odpowiedniego `T?`typu wartości nullable , jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Jak zidentyfikować typ wartości z do wartości możliwej do wartości null

Poniższy przykład pokazuje, jak <xref:System.Type?displayProperty=nameWithType> ustalić, czy wystąpienie reprezentuje skonstruowany <xref:System.Nullable%601?displayProperty=nameWithType> typ wartości nullable, czyli typ z określonym parametrem `T`typu:

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Jak pokazano w przykładzie, operator [typeof](../operators/type-testing-and-cast.md#typeof-operator) służy do tworzenia <xref:System.Type?displayProperty=nameWithType> wystąpienia.

Jeśli chcesz ustalić, czy wystąpienie ma typ wartości powodującej <xref:System.Object.GetType%2A?displayProperty=nameWithType> wartość null, <xref:System.Type> nie używaj metody, aby uzyskać wystąpienie do przetestowania z poprzednim kodem. Po wywołaniu <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu wartości możliwej do <xref:System.Object>wartości null, wystąpienie jest [zapakowane](#boxing-and-unboxing) do . Jako boks wystąpienia nie null typu wartości nullable jest odpowiednikiem boksu <xref:System.Object.GetType%2A> wartości <xref:System.Type> typu bazowego, zwraca wystąpienie, które reprezentuje podstawowy typ typu wartości nullable:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

Ponadto nie należy używać operatora [is,](../operators/type-testing-and-cast.md#is-operator) aby ustalić, czy wystąpienie ma typ wartości nullable. Jak pokazano w poniższym przykładzie, nie można odróżnić typów wystąpienia `is` typu nullable i jego wystąpienia typu bazowego za pomocą operatora:

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Można użyć kodu przedstawionego w poniższym przykładzie, aby ustalić, czy wystąpienie ma typ wartości nullable:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Metody opisane w tej sekcji nie mają zastosowania w przypadku [typów odwołań, których można unieważnić.](nullable-reference-types.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Typy nullowalne](~/_csharplang/spec/types.md#nullable-types)
- [Operatorzy podnoszony](~/_csharplang/spec/expressions.md#lifted-operators)
- [Niejawne konwersje możliwe do unieważnienia](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Jawne konwersje możliwe do unieważnienia](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Udźwignięty operator konwersji](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Co dokładnie oznacza "podniesiony"?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Typy referencyjne dopuszczające wartość null](nullable-reference-types.md)
