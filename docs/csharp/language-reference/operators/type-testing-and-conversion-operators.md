---
title: Operatorzy badania typu i konwersji — C# odwołania
description: Dowiedz się więcej o C# operatorów, które służy do Sprawdź typ wyniku wyrażenia i przekonwertować go na inny typ, jeśli to konieczne.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 4468bc86634ad97f2dfbdb5f842eb5206f957a79
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307509"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a>Operatory badania typu i konwersji (C# odwołania)

Następujące operatory służy do sprawdzania typu lub konwersja typu:

- [is — operator](#is-operator): do sprawdzania, czy typ środowiska uruchomieniowego wyrażenia jest niezgodny z danym typem
- [operator](#as-operator): umożliwia jawne konwertowanie wyrażenia do danego typu, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem
- [Rzutowanie — operator ()](#cast-operator-): do wykonania jawnej konwersji
- [TypeOf operator](#typeof-operator): uzyskanie <xref:System.Type?displayProperty=nameWithType> wystąpienia typu

## <a name="is-operator"></a>is — operator

`is` Operator sprawdza, czy typ środowiska uruchomieniowego, wynikiem wyrażenia jest zgodne z danym typem. Począwszy od C# 7.0, `is` operator sprawdza również, wynik wyrażenia do wzorca.

Wyrażenie z badania typu `is` operator ma następującą postać

```csharp
E is T
```

gdzie `E` to wyrażenie zwracające wartość i `T` jest nazwa typu lub parametrem typu. `E` nie może być metody anonimowej lub wyrażenia lambda.

`E is T` Zwraca wyrażenie `true` Jeśli wynikiem `E` jest różna od null i można przekonwertować na typ `T` konwersji odwołania, konwersji pakującej lub konwersji rozpakowującej; w przeciwnym razie zwraca `false`. `is` Operator nie bierze pod uwagę konwersje zdefiniowane przez użytkownika.

Poniższy przykład pokazuje, że `is` operator zwraca `true` Jeśli typ środowiska uruchomieniowego, wynikiem wyrażenia jest pochodną od danego typu, oznacza to, że istnieje odwołanie do konwersji pomiędzy typami całkowitymi:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Następny przykład pokazuje, że `is` operator uwzględnia, opakowywanie i rozpakowywanie konwersji, ale nie bierze pod uwagę konwersje liczbowe:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Aby uzyskać informacje o C# konwersji, zobacz [konwersje](~/_csharplang/spec/conversions.md) rozdziału [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Typ, testowanie za pomocą dopasowywania do wzorca

Począwszy od C# 7.0, `is` operator sprawdza również, wynik wyrażenia do wzorca. W szczególności obsługuje wpisz wzór w następującej postaci:

```csharp
E is T v
```

gdzie `E` to wyrażenie zwracające wartość `T` jest nazwa typu lub parametrem typu i `v` jest zmienną lokalną nowego typu `T`. Jeśli wynik `E` jest różna od null i mogą być konwertowane na `T` przez odwołanie, pakowanie i rozpakowywanie konwersji, `E is T v` zwraca wyrażenie `true` i przekonwertowana wartości wyniku `E` jest przypisany do Zmienna `v`.

W poniższym przykładzie pokazano użycie `is` operator ze wzorcem typu:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Aby uzyskać więcej informacji na temat wpisz wzór i inne obsługiwane wzorce zobacz [za pomocą dopasowywania do wzorca jest](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>operator

`as` Operator jawnie konwertuje wynik wyrażenia dla danego odwołania lub typu wartości null. Jeśli konwersja nie jest to możliwe, `as` operator zwraca `null`. W odróżnieniu od [rzutowania (operatora)](#cast-operator-), `as` operator nigdy nie zgłasza wyjątku.

Wyrażenie formularza

```csharp
E as T
```

gdzie `E` to wyrażenie zwracające wartość i `T` Nazwa typu lub parametrem typu, daje ten sam wynik jako

```csharp
E is T ? (T)(E) : (T)null
```

z tą różnicą, że `E` jest obliczany tylko raz.

`as` Operator uwzględnia tylko konwersje odwołań, dopuszczającego wartość null, pakowania i rozpakowania. Nie można użyć `as` operatora do wykonywania konwersji zdefiniowanej przez użytkownika. Aby to zrobić, należy użyć [rzutowania (operatora)](#cast-operator-).

W poniższym przykładzie pokazano użycie `as` operator:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak pokazano na poprzednim przykładzie, należy porównać wynik `as` wyrażenie `null` do sprawdzenia, jeśli konwersja zakończy się pomyślnie. Począwszy od C# 7.0, można użyć [jest operatorem](#type-testing-with-pattern-matching) zarówno do testowania, jeśli konwersja powiedzie się i, jeśli się powiedzie, przypisz wynik do nowej zmiennej.

## <a name="cast-operator-"></a>CAST — operator)

Wyrażenie cast w postaci `(T)E` wykonuje jawnej konwersji wynik wyrażenia `E` na typ `T`. Jeśli istnieje nie jawna konwersja z typu `E` na typ `T`, wystąpi błąd kompilacji. W czasie wykonywania jawna konwersja może się nie powieść i wyrażenia rzutowania może zgłosić wyjątek.

W poniższym przykładzie pokazano jawnych konwersji liczbowych i odwołania:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Aby uzyskać informacji na temat obsługiwanych jawnych konwersji, zobacz [jawne konwersje](~/_csharplang/spec/conversions.md#explicit-conversions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md). Uzyskać informacji o definiowaniu typu niestandardowego jawnych lub niejawnych konwersji, zobacz [jawne](../keywords/explicit.md) lub [niejawne](../keywords/implicit.md) artykuł — słowo kluczowe, odpowiednio.

### <a name="other-usages-of-"></a>Inne sposoby użycia)

Możesz również użyć nawiasów, aby [wywołania metody lub delegata wywołania](member-access-operators.md#invocation-operator-).

Inne użycie nawiasów jest określić kolejność, w którym ma być operacji w wyrażeniu. Aby uzyskać więcej informacji, zobacz [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) części [operatory](../../programming-guide/statements-expressions-operators/operators.md) artykułu. Listy uporządkowane według poziomu pierwszeństwo operatorów, zobacz [ C# operatory](index.md).

## <a name="typeof-operator"></a>typeof — Operator

`typeof` Uzyskuje operator <xref:System.Type?displayProperty=nameWithType> wystąpienie typu. Argument `typeof` operatora musi być nazwą typu lub parametrem typu, jak w poniższym przykładzie pokazano:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Możesz również użyć `typeof` operatora z niepowiązanych typów ogólnych. Nazwa typu ogólnego niezwiązanego musi zawierać odpowiednią liczbę przecinkami, które jest mniejsza niż liczba parametrów typu. W poniższym przykładzie pokazano użycie `typeof` operatora typu niepowiązanego dla ogólnych:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Wyrażenie nie może być argumentem `typeof` operatora. Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienia typu środowiska uruchomieniowego wyniku wyrażenia, użyj <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody.

### <a name="type-testing-with-the-typeof-operator"></a>Testowanie za pomocą typu `typeof` — operator

Użyj `typeof` operatora, aby sprawdzić, czy typ środowiska uruchomieniowego, wynikiem wyrażenia dokładnie odpowiada danego typu. W poniższym przykładzie pokazano różnicę między sprawdzania typu przeprowadzane przy użyciu `typeof` operatora i [jest operatorem](#is-operator):

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Overloadability — operator

`is`, `as`, I `typeof` operatory nie są z możliwością przeciążenia.

Typ zdefiniowany przez użytkownika nie mogą przeciążać `()` operatora, ale można zdefiniować konwersje typów niestandardowych, które mogą być wykonywane przez wyrażenie rzutowania. Aby uzyskać więcej informacji, zobacz [jawne](../keywords/explicit.md) i [niejawne](../keywords/implicit.md) artykuły — słowo kluczowe.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Is — operator](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operator as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Wyrażenia CAST](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typeof — operator](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Porady: bezpieczne multiemisji za pomocą dopasowywania do wzorca i jest i operatory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
