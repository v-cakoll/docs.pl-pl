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
ms.openlocfilehash: 62186409fdc1abb2275af535be3ae939a1e63323
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922281"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="f2534-103">Operatory testowania typu i rzutowania (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="f2534-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="f2534-104">Można użyć następujących operatorów do przeprowadzenia sprawdzania typu lub konwersji typu:</span><span class="sxs-lookup"><span data-stu-id="f2534-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="f2534-105">[is — operator](#is-operator): Aby sprawdzić, czy typ środowiska uruchomieniowego wyrażenia jest zgodny z danym typem</span><span class="sxs-lookup"><span data-stu-id="f2534-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="f2534-106">[operator as](#as-operator): Aby jawnie przekonwertować wyrażenie na dany typ, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem</span><span class="sxs-lookup"><span data-stu-id="f2534-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="f2534-107">[operator rzutowania ()](#cast-operator-): Aby wykonać konwersję jawną</span><span class="sxs-lookup"><span data-stu-id="f2534-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="f2534-108">[operator typeof](#typeof-operator): Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu</span><span class="sxs-lookup"><span data-stu-id="f2534-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="f2534-109">IS — operator</span><span class="sxs-lookup"><span data-stu-id="f2534-109">is operator</span></span>

<span data-ttu-id="f2534-110">`is` Operator sprawdza, czy typ środowiska uruchomieniowego wyniku wyrażenia jest zgodny z danym typem.</span><span class="sxs-lookup"><span data-stu-id="f2534-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="f2534-111">Począwszy od C# 7,0, `is` operator sprawdza także wynik wyrażenia względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="f2534-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="f2534-112">Wyrażenie z operatorem testowania `is` typu ma następującą postać</span><span class="sxs-lookup"><span data-stu-id="f2534-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="f2534-113">gdzie `E` jest wyrażeniem zwracającym wartość i `T` jest nazwą typu lub parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="f2534-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="f2534-114">`E`nie może być metodą anonimową ani wyrażeniem lambda.</span><span class="sxs-lookup"><span data-stu-id="f2534-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="f2534-115">`true` `E` `T` Wyrażenie zwraca wartość, jeśli wynik ma wartość inną niż null i można go przekonwertować na typ za pomocą konwersji odwołania, konwersji pakującej lub konwersji rozpakowywania; w przeciwnym razie zwraca wartość `false`. `E is T`</span><span class="sxs-lookup"><span data-stu-id="f2534-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="f2534-116">`is` Operator nie uwzględnia konwersji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2534-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="f2534-117">Poniższy przykład pokazuje, że `is` operator zwraca `true` , jeśli typ środowiska uruchomieniowego wyniku wyrażenia pochodzi z danego typu, to oznacza, że istnieje konwersja odwołania między typami:</span><span class="sxs-lookup"><span data-stu-id="f2534-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="f2534-118">W następnym przykładzie pokazano, że `is` operator bierze pod uwagę opakowanie i konwersje rozpakowywanie, ale nie uwzględnia konwersji liczbowych:</span><span class="sxs-lookup"><span data-stu-id="f2534-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="f2534-119">Aby uzyskać informacje C# na temat konwersji, zobacz rozdział dotyczący [konwersji](~/_csharplang/spec/conversions.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f2534-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="f2534-120">Testowanie typu z dopasowaniem do wzorca</span><span class="sxs-lookup"><span data-stu-id="f2534-120">Type testing with pattern matching</span></span>

<span data-ttu-id="f2534-121">Począwszy od C# 7,0, `is` operator sprawdza także wynik wyrażenia względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="f2534-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="f2534-122">W szczególności obsługuje wzorzec typu w następującej postaci:</span><span class="sxs-lookup"><span data-stu-id="f2534-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="f2534-123">gdzie `E` jest wyrażeniem zwracającym wartość, `T` jest nazwą typu lub parametrem typu, a `v` to Nowa zmienna lokalna typu `T`.</span><span class="sxs-lookup"><span data-stu-id="f2534-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="f2534-124">Jeśli `E` wynik jest inny niż null i można go przekonwertować na `T` za pomocą konwersji referencyjnej, pakującej lub rozpakowywania, `E is T v` wyrażenie zwraca `true` i przekonwertowaną wartość wyniku `E` jest przypisane do zmienna `v`.</span><span class="sxs-lookup"><span data-stu-id="f2534-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="f2534-125">Poniższy przykład ilustruje użycie `is` operatora z wzorcem typu:</span><span class="sxs-lookup"><span data-stu-id="f2534-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="f2534-126">Aby uzyskać więcej informacji na temat wzorca typu i innych obsługiwanych wzorców, zobacz [Dopasowanie wzorców do](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="f2534-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="f2534-127">AS — operator</span><span class="sxs-lookup"><span data-stu-id="f2534-127">as operator</span></span>

<span data-ttu-id="f2534-128">`as` Operator jawnie konwertuje wynik wyrażenia na daną odwołanie lub typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="f2534-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="f2534-129">Jeśli konwersja nie jest możliwa, `as` operator zwraca. `null`</span><span class="sxs-lookup"><span data-stu-id="f2534-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="f2534-130">W przeciwieństwie do [operatora CAST ()](#cast-operator-) `as` operator nigdy nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f2534-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="f2534-131">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="f2534-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="f2534-132">gdzie `E` jest wyrażeniem zwracającym wartość i `T` jest nazwą typu lub parametrem typu, daje ten sam wynik jako</span><span class="sxs-lookup"><span data-stu-id="f2534-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="f2534-133">z tą różnicą, że `E` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f2534-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="f2534-134">`as` Operator traktuje wyłącznie konwersje odwołania, dopuszczające wartość null, opakowanie i rozpakowywanie.</span><span class="sxs-lookup"><span data-stu-id="f2534-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="f2534-135">Nie można użyć `as` operatora do wykonania konwersji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2534-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="f2534-136">Aby to zrobić, użyj [operatora CAST ()](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="f2534-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="f2534-137">Poniższy przykład ilustruje użycie `as` operatora:</span><span class="sxs-lookup"><span data-stu-id="f2534-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="f2534-138">Jak pokazano na powyższym przykładzie, należy porównać wynik `as` wyrażenia z `null` , aby sprawdzić, czy konwersja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f2534-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="f2534-139">Począwszy od C# 7,0, można użyć [operatora is](#type-testing-with-pattern-matching) , aby sprawdzić, czy konwersja się powiedzie i, jeśli zakończy się pomyślnie, przypisz wynik do nowej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f2534-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="f2534-140">Operator rzutowania ()</span><span class="sxs-lookup"><span data-stu-id="f2534-140">Cast operator ()</span></span>

<span data-ttu-id="f2534-141">Wyrażenie rzutowania formularza `(T)E` wykonuje jawną konwersję wyniku wyrażenia `E` na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="f2534-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="f2534-142">Jeśli nie istnieje jawna konwersja z typu `E` do typu `T`, wystąpi błąd czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f2534-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="f2534-143">W czasie wykonywania jawna konwersja może się nie powieść, a wyrażenie rzutowania może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f2534-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="f2534-144">W poniższym przykładzie zademonstrowano jawne konwersje liczbowe i odwołania:</span><span class="sxs-lookup"><span data-stu-id="f2534-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="f2534-145">Aby uzyskać informacje na temat obsługiwanych konwersji jawnych, zobacz sekcję [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f2534-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="f2534-146">Aby uzyskać informacje dotyczące sposobu definiowania niestandardowej jawnej lub niejawnej konwersji typu, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f2534-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f2534-147">Inne użycie ()</span><span class="sxs-lookup"><span data-stu-id="f2534-147">Other usages of ()</span></span>

<span data-ttu-id="f2534-148">Należy również użyć nawiasów do [wywołania metody lub wywołania delegata](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="f2534-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="f2534-149">Innym zastosowaniem nawiasów jest dostosowanie kolejności, w której mają być oceniane operacje w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f2534-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="f2534-150">Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="f2534-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="f2534-151">typeof — Operator</span><span class="sxs-lookup"><span data-stu-id="f2534-151">typeof operator</span></span>

<span data-ttu-id="f2534-152">Operator uzyskuje <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu. `typeof`</span><span class="sxs-lookup"><span data-stu-id="f2534-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="f2534-153">Argument `typeof` operatora musi być nazwą typu lub parametrem typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f2534-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="f2534-154">Można również użyć `typeof` operatora z niepowiązane typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="f2534-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="f2534-155">Nazwa niepowiązanego typu ogólnego musi zawierać odpowiednią liczbę przecinków, która jest mniejsza niż liczba parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="f2534-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="f2534-156">W poniższym przykładzie pokazano użycie `typeof` operatora z niezwiązanym typem ogólnym:</span><span class="sxs-lookup"><span data-stu-id="f2534-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="f2534-157">Wyrażenie nie może być argumentem `typeof` operatora.</span><span class="sxs-lookup"><span data-stu-id="f2534-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="f2534-158">Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu środowiska uruchomieniowego wyniku wyrażenia, <xref:System.Object.GetType%2A?displayProperty=nameWithType> Użyj metody.</span><span class="sxs-lookup"><span data-stu-id="f2534-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="f2534-159">Testowanie typu za pomocą `typeof` operatora</span><span class="sxs-lookup"><span data-stu-id="f2534-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="f2534-160">Użyj operatora `typeof` , aby sprawdzić, czy typ środowiska uruchomieniowego wyniku wyrażenia dokładnie pasuje do danego typu.</span><span class="sxs-lookup"><span data-stu-id="f2534-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="f2534-161">Poniższy przykład ilustruje różnicę między sprawdzaniem typu wykonane z `typeof` operatorem i operatorem [is](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="f2534-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="f2534-162">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="f2534-162">Operator overloadability</span></span>

<span data-ttu-id="f2534-163">`as`Operatorów `is`, i niemożna`typeof` przeciążać.</span><span class="sxs-lookup"><span data-stu-id="f2534-163">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="f2534-164">Typ zdefiniowany przez użytkownika nie może przeciążać `()` operatora, ale może definiować konwersje typów niestandardowych, które mogą być wykonywane przez wyrażenie rzutowania.</span><span class="sxs-lookup"><span data-stu-id="f2534-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="f2534-165">Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f2534-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2534-166">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f2534-166">C# language specification</span></span>

<span data-ttu-id="f2534-167">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="f2534-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f2534-168">Operator is</span><span class="sxs-lookup"><span data-stu-id="f2534-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="f2534-169">Operator as</span><span class="sxs-lookup"><span data-stu-id="f2534-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="f2534-170">Wyrażenia rzutowania</span><span class="sxs-lookup"><span data-stu-id="f2534-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="f2534-171">Operator typeof</span><span class="sxs-lookup"><span data-stu-id="f2534-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="f2534-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2534-172">See also</span></span>

- [<span data-ttu-id="f2534-173">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="f2534-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f2534-174">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f2534-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="f2534-175">Instrukcje: bezpieczne rzutowanie przy użyciu dopasowania wzorca i operatory is i AS</span><span class="sxs-lookup"><span data-stu-id="f2534-175">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)