---
title: Operatory testowania typu i rzutów — odwołanie do języka C#
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
ms.openlocfilehash: 037ddc8eeda418b2e4858ab98be6cd362ca0e1e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399470"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Operatory testowania typu i rzutów (odwołanie do języka C#)

Za pomocą następujących operatorów można przeprowadzać sprawdzanie typów lub konwersję typów:

- [jest operatorem:](#is-operator)aby sprawdzić, czy typ środowiska uruchomieniowego wyrażenia jest zgodny z danym typem
- [jako operator](#as-operator): jawnie przekonwertować wyrażenie na dany typ, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem
- [operator odlewu ()](#cast-operator-): do przeprowadzenia jawnej konwersji
- [operator typeof](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> w celu uzyskania instancji dla typu

## <a name="is-operator"></a>jest operatorem

Operator `is` sprawdza, czy typ środowiska uruchomieniowego wyniku wyrażenia jest zgodny z danym typem. Począwszy od Języka C# `is` 7.0, operator testuje również wynik wyrażenia względem wzorca.

Wyrażenie z operatorem `is` testowania typu ma następujący formularz

```csharp
E is T
```

gdzie `E` jest wyrażenie, które `T` zwraca wartość i jest nazwą typu lub parametru typu. `E`nie może być metodą anonimową ani wyrażeniem lambda.

Wyrażenie `E is T` zwraca, `true` jeśli `E` wynik jest non-null i mogą `T` być konwertowane na typ przez konwersję odwołania, konwersji bokserskiej lub konwersji rozpakowywania; w przeciwnym `false`razie zwraca . Operator `is` nie bierze pod uwagę konwersji zdefiniowanych przez użytkownika.

W poniższym przykładzie `is` pokazano, że operator zwraca, `true` jeśli typ czasu wykonywania wyniku wyrażenia pochodzi od danego typu, oznacza to, że istnieje konwersja odwołania między typami:

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Następny przykład pokazuje, `is` że operator bierze pod uwagę boks i unboxing konwersji, ale nie bierze pod uwagę [konwersje liczbowe:](../builtin-types/numeric-conversions.md)

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

Aby uzyskać informacje na temat konwersji języka C#, zobacz rozdział [Konwersje](~/_csharplang/spec/conversions.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

### <a name="type-testing-with-pattern-matching"></a>Testowanie typów z dopasowaniem wzorców

Począwszy od Języka C# `is` 7.0, operator testuje również wynik wyrażenia względem wzorca. W szczególności obsługuje wzorzec typu w następującej formie:

```csharp
E is T v
```

gdzie `E` jest wyrażeniem, które `T` zwraca wartość, jest nazwą typu `v` lub parametru typu `T`i jest nową zmienną lokalną typu . Jeśli wynik `E` nie jest null i mogą `T` być konwertowane przez odwołanie, boks `E is T v` lub `true` unboxing konwersji, wyrażenie zwraca `E` i przekonwertowana wartość wyniku jest przypisany do zmiennej `v`.

W poniższym przykładzie przedstawiono `is` użycie operatora ze wzorcem typu:

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Aby uzyskać więcej informacji na temat wzorca typu i innych obsługiwanych wzorców, zobacz [Dopasowanie wzorca z is](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>jako operator

Operator `as` jawnie konwertuje wynik wyrażenia na dany typ wartości odniesienia lub wartości null. Jeśli konwersja nie jest `as` możliwa, operator zwraca `null`. W przeciwieństwie do operatora `as` [rzutowania ()](#cast-operator-)operator nigdy nie zgłasza wyjątek.

Wyrażenie formularza

```csharp
E as T
```

gdzie `E` jest wyrażenie, które `T` zwraca wartość i jest nazwą typu lub parametru typu, daje taki sam wynik jak

```csharp
E is T ? (T)(E) : (T)null
```

chyba `E` że jest oceniana tylko raz.

Operator `as` uwzględnia tylko odwołania, nullable, boks i unboxing konwersji. Nie można `as` użyć operatora do wykonania konwersji zdefiniowanej przez użytkownika. Aby to zrobić, należy użyć [operatora rzutowania ()](#cast-operator-).

W poniższym przykładzie przedstawiono `as` użycie operatora:

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak pokazano w poprzednim przykładzie, należy porównać `as` wynik `null` wyrażenia z, aby sprawdzić, czy konwersja zakończyła się pomyślnie. Począwszy od Języka C# 7.0, można użyć [is operator](#type-testing-with-pattern-matching) zarówno do testowania, jeśli konwersja zakończy się pomyślnie, a jeśli zakończy się pomyślnie, przypisać jego wynik do nowej zmiennej.

## <a name="cast-operator-"></a>Operator rzutowania ()

Wyrażenie rzutowania formularza `(T)E` wykonuje jawną konwersję wyniku `E` wyrażenia `T`do typu . Jeśli nie istnieje jawna `E` konwersja `T`z typu typu typu, występuje błąd w czasie kompilacji. W czasie wykonywania jawne konwersji może się nie powieść i wyrażenie rzutowania może zgłosić wyjątek.

W poniższym przykładzie przedstawiono jawne konwersje liczbowe i referencyjne:

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

Aby uzyskać informacje o obsługiwanych jawnych konwersjach, zobacz [jawne konwersje](~/_csharplang/spec/conversions.md#explicit-conversions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md) Aby uzyskać informacje dotyczące definiowania niestandardowej konwersji typu jawnego lub niejawnego, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Inne zastosowania ()

Nawiasy można również użyć do [wywołania metody lub wywołania delegata](member-access-operators.md#invocation-operator-).

Inne użycie nawiasów jest dostosowanie kolejności, w jakiej do oceny operacji w wyrażeniu. Aby uzyskać więcej informacji, zobacz [Operatory języka C#.](index.md)

## <a name="typeof-operator"></a>typeof — Operator

Operator `typeof` uzyskuje <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu. Argument `typeof` do operatora musi być nazwa typu lub parametrtypu, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

Można również użyć `typeof` operatora z niepowiązanych typów ogólnych. Nazwa niezwiązanego typu ogólnego musi zawierać odpowiednią liczbę przecinków, która jest mniejsza niż liczba parametrów typu. W poniższym przykładzie przedstawiono `typeof` użycie operatora z niepowiązanym typem ogólnym:

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Wyrażenie nie może być `typeof` argumentem operatora. Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu czasu wykonywania wyniku <xref:System.Object.GetType%2A?displayProperty=nameWithType> wyrażenia, należy użyć metody.

### <a name="type-testing-with-the-typeof-operator"></a>Testowanie typu `typeof` z operatorem

Użyj `typeof` operatora, aby sprawdzić, czy typ czasu wykonywania wyniku wyrażenia dokładnie pasuje do danego typu. Poniższy przykład pokazuje różnicę między sprawdzanietypu `typeof` wykonywane z operatorem i [jest operator:](#is-operator)

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Przeciążenie operatora

`is`Program `as`, `typeof` i operatory nie mogą być przeciążone.

Typ zdefiniowany przez użytkownika `()` nie może przeciążać operatora, ale można zdefiniować konwersje typu niestandardowego, które mogą być wykonywane przez wyrażenie rzutowania. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Operator jest](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operator jako](~/_csharplang/spec/expressions.md#the-as-operator)
- [Rzutacja wyrażeń](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operator typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Jak bezpiecznie oddać za pomocą dopasowania wzorców i jest i jako operatorzy](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
