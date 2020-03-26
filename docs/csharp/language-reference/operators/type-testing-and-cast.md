---
title: Operatory testowania i rzutowanie typu — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, których można użyć do sprawdzenia typu wyniku wyrażenia i przekonwertowania go na inny typ, jeśli to konieczne.
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
ms.openlocfilehash: 2dc215a91c55be15e8eee488f0030f41e3492af5
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507090"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Operatory testowania i rzutowanie typu (odwołanie do języka C#)

Do sprawdzania typu lub konwersji typu można użyć następujących operatorów:

- [operator :](#is-operator)aby sprawdzić, czy typ środowiska wykonawczego wyrażenia jest zgodny z danym typem
- [jako operator](#as-operator): jawnie przekonwertować wyrażenie na dany typ, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem
- [operator cast ()](#cast-operator-): w celu przeprowadzenia jawnej konwersji
- [typeof operator](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> aby uzyskać wystąpienie dla typu

## <a name="is-operator"></a>jest operatorem

Operator `is` sprawdza, czy typ środowiska wykonawczego wyniku wyrażenia jest zgodny z danym typem. Począwszy od języka C# 7.0, `is` operator testuje również wynik wyrażenia względem wzorca.

Wyrażenie z operatorem `is` testowania typu ma następujący formularz

```csharp
E is T
```

gdzie `E` jest wyrażeniem, które `T` zwraca wartość i jest nazwą typu lub parametru typu. `E`nie może być metodą anonimową ani wyrażeniem lambda.

Wyrażenie `E is T` zwraca, `true` jeśli `E` wynik jest null i mogą być `T` konwertowane na typ przez konwersję odwołania, konwersji bokserskiej lub konwersji rozpakowywania; w przeciwnym `false`razie zwraca . Operator `is` nie bierze pod uwagę konwersji zdefiniowanych przez użytkownika.

Poniższy przykład pokazuje, `is` że `true` operator zwraca, jeśli typ środowiska uruchomieniowego wyniku wyrażenia pochodzi od danego typu, oznacza to, że istnieje konwersja odwołania między typami:

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

W następnym przykładzie `is` pokazano, że operator bierze pod uwagę konwersje bokserskie i rozpakowywanie, ale nie bierze pod uwagę [konwersji liczbowych:](../builtin-types/numeric-conversions.md)

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

Aby uzyskać informacje o konwersjach w języku C#, zobacz rozdział [Konwersje](~/_csharplang/spec/conversions.md) [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

### <a name="type-testing-with-pattern-matching"></a>Testowanie typów z dopasowaniem wzorca

Począwszy od języka C# 7.0, `is` operator testuje również wynik wyrażenia względem wzorca. W szczególności obsługuje wzorzec typu w następującej formie:

```csharp
E is T v
```

gdzie `E` jest wyrażeniem, które `T` zwraca wartość, jest nazwą typu `v` lub parametru typu `T`i jest nową zmienną lokalną typu . Jeśli wynik `E` jest nie-null i mogą `T` być konwertowane przez odwołanie, boks, lub unboxing konwersji, `E is T v` wyrażenie `true` zwraca `v`i przekonwertowana wartość wyniku jest przypisany do zmiennej `E` .

Poniższy przykład pokazuje użycie `is` operatora z wzorcem typu:

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Aby uzyskać więcej informacji na temat wzorca typu i innych obsługiwanych wzorców, zobacz [Dopasowywanie wzorca z jest](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>jako operator

Operator `as` jawnie konwertuje wynik wyrażenia na dane odwołanie lub typ wartości nullable. Jeśli konwersja nie jest `as` możliwa, operator zwraca . `null` W przeciwieństwie do operatora `as` [rzutowego (),](#cast-operator-)operator nigdy nie zgłasza wyjątku.

Wyrażenie formularza

```csharp
E as T
```

gdzie `E` jest wyrażeniem, które `T` zwraca wartość i jest nazwą typu lub parametru typu, daje taki sam wynik jak

```csharp
E is T ? (T)(E) : (T)null
```

z `E` tą różnicą, że jest oceniana tylko raz.

Operator `as` bierze pod uwagę tylko odwołania, nullable, boks i unboxing konwersji. Nie można `as` użyć operatora do wykonania konwersji zdefiniowanej przez użytkownika. Aby to zrobić, należy użyć [operatora rzutu ()](#cast-operator-).

Poniższy przykład pokazuje użycie `as` operatora:

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak pokazano w poprzednim przykładzie, należy porównać wynik `as` wyrażenia z, `null` aby sprawdzić, czy konwersja zakończy się pomyślnie. Począwszy od języka C# 7.0, można użyć [is operatora](#type-testing-with-pattern-matching) zarówno do testowania, jeśli konwersja powiedzie się i, jeśli zakończy się pomyślnie, przypisać jej wynik do nowej zmiennej.

## <a name="cast-operator-"></a>Operator odlewu ()

Wyrażenie rzutowania formularza `(T)E` wykonuje jawną konwersję wyniku `E` wyrażenia `T`na typ . Jeśli nie istnieje jawna konwersja od typu `E` do typu, `T`występuje błąd w czasie kompilacji. W czasie wykonywania jawne konwersji może nie zakończyć się pomyślnie i wyrażenie rzutu może zgłosić wyjątek.

Poniższy przykład pokazuje jawne konwersje liczbowe i referencyjne:

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

Aby uzyskać informacje na temat obsługiwanych konwersji jawnych, zobacz sekcję [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions) [w specyfikacji języka C#.](~/_csharplang/spec/introduction.md) Aby uzyskać informacje dotyczące definiowania niestandardowej konwersji typu jawnego lub niejawnego, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Inne zastosowania ()

Nawiasy są również używane do [wywoływania metody lub wywoływania pełnomocnika](member-access-operators.md#invocation-expression-).

Inne użycie nawiasów jest dostosowanie kolejności, w jakiej do oceny operacji w wyrażeniu. Aby uzyskać więcej informacji, zobacz [operatory języka C#.](index.md)

## <a name="typeof-operator"></a>typeof — Operator

Operator `typeof` uzyskuje <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu. Argumentem `typeof` operatora musi być nazwa typu lub parametru typu, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

Można również użyć `typeof` operatora z niezwiązane typy ogólne. Nazwa niezwiązanego typu ogólnego musi zawierać odpowiednią liczbę przecinków, która jest mniejsza niż liczba parametrów typu. W poniższym przykładzie `typeof` przedstawiono użycie operatora z niezwiązanym typem ogólnym:

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Wyrażenie nie może być `typeof` argumentem operatora. Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu środowiska wykonawczego wyniku <xref:System.Object.GetType%2A?displayProperty=nameWithType> wyrażenia, należy użyć metody.

### <a name="type-testing-with-the-typeof-operator"></a>Badanie typu `typeof` z operatorem

`typeof` Operator służy do sprawdzania, czy typ środowiska wykonawczego wyniku wyrażenia dokładnie odpowiada danego typu. Poniższy przykład pokazuje różnicę między sprawdzaniem `typeof` typu wykonywanym za pomocą operatora is a [operatorem is:](#is-operator)

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Przeciążenie operatora

`is`Operatory `as`i `typeof` operatory nie mogą być przeciążone.

Typ zdefiniowany przez użytkownika `()` nie może przeciążać operatora, ale może definiować niestandardowe konwersje typu, które mogą być wykonywane przez wyrażenie rzutowane. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Operator is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Jako operator](~/_csharplang/spec/expressions.md#the-as-operator)
- [Wyrażenia rzutowe](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operator typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Jak bezpiecznie rzucać za pomocą dopasowywania wzorców i jest i jako operatorzy](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
