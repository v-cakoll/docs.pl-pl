---
title: Operatory testowania typu i rzutowania — C# odwołanie
description: Dowiedz C# się więcej na temat operatorów, których można użyć do sprawdzenia typu wyniku wyrażenia i przekonwertowania go na inny typ w razie potrzeby.
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
ms.openlocfilehash: c29833ece83e386446aaf0a5d242bda366cbfbb0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239043"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Operatory testowania typu i rzutowania (C# odwołanie)

Można użyć następujących operatorów do przeprowadzenia sprawdzania typu lub konwersji typu:

- [is — operator](#is-operator): Aby sprawdzić, czy typ środowiska uruchomieniowego wyrażenia jest zgodny z danym typem
- [operator as](#as-operator): Aby jawnie przekonwertować wyrażenie na dany typ, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem
- [operator rzutowania ()](#cast-operator-): Aby wykonać konwersję jawną
- [operator typeof](#typeof-operator): Aby uzyskać wystąpienie <xref:System.Type?displayProperty=nameWithType> dla typu

## <a name="is-operator"></a>IS — operator

Operator `is` sprawdza, czy typ środowiska uruchomieniowego wyniku wyrażenia jest zgodny z danym typem. Począwszy od C# 7,0, operator `is` również testuje wynik wyrażenia w stosunku do wzorca.

Wyrażenie z operatorem `is` testowania typu ma następującą postać

```csharp
E is T
```

gdzie `E` jest wyrażeniem zwracającym wartość i `T` jest nazwą typu lub parametrem typu. `E` nie może być metodą anonimową ani wyrażeniem lambda.

Wyrażenie `E is T` zwraca `true`, jeśli wynik `E` ma wartość różną od null i można go przekonwertować na typ `T` przez konwersję odwołania, konwersję z opakowaniem lub konwersję rozpakowywanie. w przeciwnym razie zwraca `false`. Operator `is` nie uwzględnia konwersji zdefiniowanych przez użytkownika.

Poniższy przykład pokazuje, że operator `is` zwraca `true`, jeśli typ środowiska uruchomieniowego wynik wyrażenia pochodzi z danego typu, to oznacza, że istnieje konwersja odwołania między typami:

[!code-csharp[is with reference conversion](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

W następnym przykładzie pokazano, że operator `is` uwzględnia konwersje pakowania i rozpakowywania, ale nie uwzględnia [konwersji liczbowych](../builtin-types/numeric-conversions.md):

[!code-csharp-interactive[is with int](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Aby uzyskać informacje C# na temat konwersji, zobacz rozdział dotyczący [konwersji](~/_csharplang/spec/conversions.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Testowanie typu z dopasowaniem do wzorca

Począwszy od C# 7,0, operator `is` również testuje wynik wyrażenia w stosunku do wzorca. W szczególności obsługuje wzorzec typu w następującej postaci:

```csharp
E is T v
```

gdzie `E` jest wyrażeniem zwracającym wartość, `T` jest nazwą typu lub parametrem typu, a `v` jest nową zmienną lokalną typu `T`. Jeśli wynik `E` ma wartość różną od null i można go przekonwertować na `T` przez konwersję, opakowanie lub odpakowywanie, wyrażenie `E is T v` zwraca `true`, a przekonwertowana wartość wyniku `E` zostanie przypisana do zmiennej `v`.

Poniższy przykład ilustruje użycie operatora `is` ze wzorcem typu:

[!code-csharp-interactive[is with type pattern](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Aby uzyskać więcej informacji na temat wzorca typu i innych obsługiwanych wzorców, zobacz [Dopasowanie wzorców do](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>AS — operator

Operator `as` jawnie konwertuje wynik wyrażenia na daną odwołanie lub typ wartości null. Jeśli konwersja nie jest możliwa, operator `as` zwraca `null`. W przeciwieństwie do [operatora CAST ()](#cast-operator-)operator `as` nigdy nie zgłasza wyjątku.

Wyrażenie formularza

```csharp
E as T
```

gdzie `E` jest wyrażeniem zwracającym wartość i `T` jest nazwą typu lub parametrem typu, daje ten sam wynik jako

```csharp
E is T ? (T)(E) : (T)null
```

z tą różnicą, że `E` są oceniane tylko raz.

Operator `as` uwzględnia tylko konwersje odwołania, dopuszczające wartość null, opakowanie i rozpakowywanie. Nie można użyć operatora `as` do wykonania konwersji zdefiniowanej przez użytkownika. Aby to zrobić, użyj [operatora CAST ()](#cast-operator-).

Poniższy przykład ilustruje użycie operatora `as`:

[!code-csharp-interactive[as operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak pokazano w powyższym przykładzie, należy porównać wynik wyrażenia `as` z `null`, aby sprawdzić, czy konwersja zakończyła się pomyślnie. Począwszy od C# 7,0, można użyć [operatora is](#type-testing-with-pattern-matching) , aby sprawdzić, czy konwersja się powiedzie i, jeśli zakończy się pomyślnie, przypisz wynik do nowej zmiennej.

## <a name="cast-operator-"></a>Operator rzutowania ()

Wyrażenie rzutowania formularza `(T)E` wykonuje jawną konwersję wyniku `E` wyrażenia, aby wpisać `T`. Jeśli nie ma żadnej jawnej konwersji z typu `E` do typu `T`, wystąpi błąd w czasie kompilacji. W czasie wykonywania jawna konwersja może się nie powieść, a wyrażenie rzutowania może zgłosić wyjątek.

W poniższym przykładzie zademonstrowano jawne konwersje liczbowe i odwołania:

[!code-csharp-interactive[cast expression](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Aby uzyskać informacje na temat obsługiwanych konwersji jawnych, zobacz sekcję [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md). Aby uzyskać informacje dotyczące sposobu definiowania niestandardowej jawnej lub niejawnej konwersji typu, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Inne użycie ()

Należy również użyć nawiasów do [wywołania metody lub wywołania delegata](member-access-operators.md#invocation-operator-).

Innym zastosowaniem nawiasów jest dostosowanie kolejności, w której mają być oceniane operacje w wyrażeniu. Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).

## <a name="typeof-operator"></a>typeof — Operator

Operator `typeof` uzyskuje <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu. Argument operatora `typeof` musi być nazwą typu lub parametrem typu, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[typeof operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Można również użyć operatora `typeof` z niepowiązane typy ogólne. Nazwa niepowiązanego typu ogólnego musi zawierać odpowiednią liczbę przecinków, która jest mniejsza niż liczba parametrów typu. W poniższym przykładzie pokazano użycie operatora `typeof` z niezwiązanym typem ogólnym:

[!code-csharp-interactive[typeof unbound generic](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Wyrażenie nie może być argumentem operatora `typeof`. Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienia dla typu wyniku w czasie wykonywania wyrażenia, użyj metody <xref:System.Object.GetType%2A?displayProperty=nameWithType>.

### <a name="type-testing-with-the-typeof-operator"></a>Testowanie typu za pomocą operatora `typeof`

Użyj operatora `typeof`, aby sprawdzić, czy typ środowiska uruchomieniowego wynik wyrażenia jest dokładnie zgodny z danym typem. Poniższy przykład ilustruje różnicę między sprawdzaniem typu wykonanego za pomocą operatora `typeof` i [operatorem is](#is-operator):

[!code-csharp[typeof vs is](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatory `is`, `as`i `typeof` nie mogą być przeciążone.

Typ zdefiniowany przez użytkownika nie może przeciążać operatora `()`, ale może definiować konwersje typów niestandardowych, które mogą być wykonywane przez wyrażenie rzutowania. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operator is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operator as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Wyrażenia rzutowania](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operator typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów is i AS](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
