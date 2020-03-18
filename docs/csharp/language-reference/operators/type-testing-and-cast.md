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
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="a45f9-103">Operatory testowania typu i rzutów (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="a45f9-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="a45f9-104">Za pomocą następujących operatorów można przeprowadzać sprawdzanie typów lub konwersję typów:</span><span class="sxs-lookup"><span data-stu-id="a45f9-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="a45f9-105">[jest operatorem:](#is-operator)aby sprawdzić, czy typ środowiska uruchomieniowego wyrażenia jest zgodny z danym typem</span><span class="sxs-lookup"><span data-stu-id="a45f9-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="a45f9-106">[jako operator](#as-operator): jawnie przekonwertować wyrażenie na dany typ, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem</span><span class="sxs-lookup"><span data-stu-id="a45f9-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="a45f9-107">[operator odlewu ()](#cast-operator-): do przeprowadzenia jawnej konwersji</span><span class="sxs-lookup"><span data-stu-id="a45f9-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="a45f9-108">[operator typeof](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> w celu uzyskania instancji dla typu</span><span class="sxs-lookup"><span data-stu-id="a45f9-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="a45f9-109">jest operatorem</span><span class="sxs-lookup"><span data-stu-id="a45f9-109">is operator</span></span>

<span data-ttu-id="a45f9-110">Operator `is` sprawdza, czy typ środowiska uruchomieniowego wyniku wyrażenia jest zgodny z danym typem.</span><span class="sxs-lookup"><span data-stu-id="a45f9-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="a45f9-111">Począwszy od Języka C# `is` 7.0, operator testuje również wynik wyrażenia względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="a45f9-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="a45f9-112">Wyrażenie z operatorem `is` testowania typu ma następujący formularz</span><span class="sxs-lookup"><span data-stu-id="a45f9-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="a45f9-113">gdzie `E` jest wyrażenie, które `T` zwraca wartość i jest nazwą typu lub parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a45f9-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="a45f9-114">`E`nie może być metodą anonimową ani wyrażeniem lambda.</span><span class="sxs-lookup"><span data-stu-id="a45f9-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="a45f9-115">Wyrażenie `E is T` zwraca, `true` jeśli `E` wynik jest non-null i mogą `T` być konwertowane na typ przez konwersję odwołania, konwersji bokserskiej lub konwersji rozpakowywania; w przeciwnym `false`razie zwraca .</span><span class="sxs-lookup"><span data-stu-id="a45f9-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="a45f9-116">Operator `is` nie bierze pod uwagę konwersji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a45f9-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="a45f9-117">W poniższym przykładzie `is` pokazano, że operator zwraca, `true` jeśli typ czasu wykonywania wyniku wyrażenia pochodzi od danego typu, oznacza to, że istnieje konwersja odwołania między typami:</span><span class="sxs-lookup"><span data-stu-id="a45f9-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="a45f9-118">Następny przykład pokazuje, `is` że operator bierze pod uwagę boks i unboxing konwersji, ale nie bierze pod uwagę [konwersje liczbowe:](../builtin-types/numeric-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="a45f9-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="a45f9-119">Aby uzyskać informacje na temat konwersji języka C#, zobacz rozdział [Konwersje](~/_csharplang/spec/conversions.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a45f9-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="a45f9-120">Testowanie typów z dopasowaniem wzorców</span><span class="sxs-lookup"><span data-stu-id="a45f9-120">Type testing with pattern matching</span></span>

<span data-ttu-id="a45f9-121">Począwszy od Języka C# `is` 7.0, operator testuje również wynik wyrażenia względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="a45f9-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="a45f9-122">W szczególności obsługuje wzorzec typu w następującej formie:</span><span class="sxs-lookup"><span data-stu-id="a45f9-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="a45f9-123">gdzie `E` jest wyrażeniem, które `T` zwraca wartość, jest nazwą typu `v` lub parametru typu `T`i jest nową zmienną lokalną typu .</span><span class="sxs-lookup"><span data-stu-id="a45f9-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="a45f9-124">Jeśli wynik `E` nie jest null i mogą `T` być konwertowane przez odwołanie, boks `E is T v` lub `true` unboxing konwersji, wyrażenie zwraca `E` i przekonwertowana wartość wyniku jest przypisany do zmiennej `v`.</span><span class="sxs-lookup"><span data-stu-id="a45f9-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="a45f9-125">W poniższym przykładzie przedstawiono `is` użycie operatora ze wzorcem typu:</span><span class="sxs-lookup"><span data-stu-id="a45f9-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="a45f9-126">Aby uzyskać więcej informacji na temat wzorca typu i innych obsługiwanych wzorców, zobacz [Dopasowanie wzorca z is](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="a45f9-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="a45f9-127">jako operator</span><span class="sxs-lookup"><span data-stu-id="a45f9-127">as operator</span></span>

<span data-ttu-id="a45f9-128">Operator `as` jawnie konwertuje wynik wyrażenia na dany typ wartości odniesienia lub wartości null.</span><span class="sxs-lookup"><span data-stu-id="a45f9-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="a45f9-129">Jeśli konwersja nie jest `as` możliwa, operator zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="a45f9-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="a45f9-130">W przeciwieństwie do operatora `as` [rzutowania ()](#cast-operator-)operator nigdy nie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a45f9-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="a45f9-131">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="a45f9-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="a45f9-132">gdzie `E` jest wyrażenie, które `T` zwraca wartość i jest nazwą typu lub parametru typu, daje taki sam wynik jak</span><span class="sxs-lookup"><span data-stu-id="a45f9-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="a45f9-133">chyba `E` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="a45f9-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="a45f9-134">Operator `as` uwzględnia tylko odwołania, nullable, boks i unboxing konwersji.</span><span class="sxs-lookup"><span data-stu-id="a45f9-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="a45f9-135">Nie można `as` użyć operatora do wykonania konwersji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a45f9-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="a45f9-136">Aby to zrobić, należy użyć [operatora rzutowania ()](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="a45f9-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="a45f9-137">W poniższym przykładzie przedstawiono `as` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="a45f9-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="a45f9-138">Jak pokazano w poprzednim przykładzie, należy porównać `as` wynik `null` wyrażenia z, aby sprawdzić, czy konwersja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a45f9-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="a45f9-139">Począwszy od Języka C# 7.0, można użyć [is operator](#type-testing-with-pattern-matching) zarówno do testowania, jeśli konwersja zakończy się pomyślnie, a jeśli zakończy się pomyślnie, przypisać jego wynik do nowej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a45f9-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="a45f9-140">Operator rzutowania ()</span><span class="sxs-lookup"><span data-stu-id="a45f9-140">Cast operator ()</span></span>

<span data-ttu-id="a45f9-141">Wyrażenie rzutowania formularza `(T)E` wykonuje jawną konwersję wyniku `E` wyrażenia `T`do typu .</span><span class="sxs-lookup"><span data-stu-id="a45f9-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="a45f9-142">Jeśli nie istnieje jawna `E` konwersja `T`z typu typu typu, występuje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a45f9-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="a45f9-143">W czasie wykonywania jawne konwersji może się nie powieść i wyrażenie rzutowania może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a45f9-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="a45f9-144">W poniższym przykładzie przedstawiono jawne konwersje liczbowe i referencyjne:</span><span class="sxs-lookup"><span data-stu-id="a45f9-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="a45f9-145">Aby uzyskać informacje o obsługiwanych jawnych konwersjach, zobacz [jawne konwersje](~/_csharplang/spec/conversions.md#explicit-conversions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a45f9-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="a45f9-146">Aby uzyskać informacje dotyczące definiowania niestandardowej konwersji typu jawnego lub niejawnego, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a45f9-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="a45f9-147">Inne zastosowania ()</span><span class="sxs-lookup"><span data-stu-id="a45f9-147">Other usages of ()</span></span>

<span data-ttu-id="a45f9-148">Nawiasy można również użyć do [wywołania metody lub wywołania delegata](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="a45f9-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="a45f9-149">Inne użycie nawiasów jest dostosowanie kolejności, w jakiej do oceny operacji w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a45f9-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="a45f9-150">Aby uzyskać więcej informacji, zobacz [Operatory języka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="a45f9-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="a45f9-151">typeof — Operator</span><span class="sxs-lookup"><span data-stu-id="a45f9-151">typeof operator</span></span>

<span data-ttu-id="a45f9-152">Operator `typeof` uzyskuje <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu.</span><span class="sxs-lookup"><span data-stu-id="a45f9-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="a45f9-153">Argument `typeof` do operatora musi być nazwa typu lub parametrtypu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a45f9-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="a45f9-154">Można również użyć `typeof` operatora z niepowiązanych typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="a45f9-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="a45f9-155">Nazwa niezwiązanego typu ogólnego musi zawierać odpowiednią liczbę przecinków, która jest mniejsza niż liczba parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="a45f9-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="a45f9-156">W poniższym przykładzie przedstawiono `typeof` użycie operatora z niepowiązanym typem ogólnym:</span><span class="sxs-lookup"><span data-stu-id="a45f9-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="a45f9-157">Wyrażenie nie może być `typeof` argumentem operatora.</span><span class="sxs-lookup"><span data-stu-id="a45f9-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="a45f9-158">Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu czasu wykonywania wyniku <xref:System.Object.GetType%2A?displayProperty=nameWithType> wyrażenia, należy użyć metody.</span><span class="sxs-lookup"><span data-stu-id="a45f9-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="a45f9-159">Testowanie typu `typeof` z operatorem</span><span class="sxs-lookup"><span data-stu-id="a45f9-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="a45f9-160">Użyj `typeof` operatora, aby sprawdzić, czy typ czasu wykonywania wyniku wyrażenia dokładnie pasuje do danego typu.</span><span class="sxs-lookup"><span data-stu-id="a45f9-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="a45f9-161">Poniższy przykład pokazuje różnicę między sprawdzanietypu `typeof` wykonywane z operatorem i [jest operator:](#is-operator)</span><span class="sxs-lookup"><span data-stu-id="a45f9-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="a45f9-162">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="a45f9-162">Operator overloadability</span></span>

<span data-ttu-id="a45f9-163">`is`Program `as`, `typeof` i operatory nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="a45f9-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="a45f9-164">Typ zdefiniowany przez użytkownika `()` nie może przeciążać operatora, ale można zdefiniować konwersje typu niestandardowego, które mogą być wykonywane przez wyrażenie rzutowania.</span><span class="sxs-lookup"><span data-stu-id="a45f9-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="a45f9-165">Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a45f9-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a45f9-166">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a45f9-166">C# language specification</span></span>

<span data-ttu-id="a45f9-167">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a45f9-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a45f9-168">Operator jest</span><span class="sxs-lookup"><span data-stu-id="a45f9-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="a45f9-169">Operator jako</span><span class="sxs-lookup"><span data-stu-id="a45f9-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="a45f9-170">Rzutacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a45f9-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="a45f9-171">Operator typeof</span><span class="sxs-lookup"><span data-stu-id="a45f9-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="a45f9-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a45f9-172">See also</span></span>

- [<span data-ttu-id="a45f9-173">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a45f9-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a45f9-174">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a45f9-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="a45f9-175">Jak bezpiecznie oddać za pomocą dopasowania wzorców i jest i jako operatorzy</span><span class="sxs-lookup"><span data-stu-id="a45f9-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="a45f9-176">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="a45f9-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
