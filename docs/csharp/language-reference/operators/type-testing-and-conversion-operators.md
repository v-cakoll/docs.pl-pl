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
ms.openlocfilehash: a9e5139e6d650aa6935bff934ca25502fdc14775
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744071"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a><span data-ttu-id="2952e-103">Operatory badania typu i konwersji (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="2952e-103">Type-testing and conversion operators (C# reference)</span></span>

<span data-ttu-id="2952e-104">Następujące operatory służy do sprawdzania typu lub konwersja typu:</span><span class="sxs-lookup"><span data-stu-id="2952e-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="2952e-105">[is — operator](#is-operator): do sprawdzania, czy typ środowiska uruchomieniowego wyrażenia jest niezgodny z danym typem</span><span class="sxs-lookup"><span data-stu-id="2952e-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="2952e-106">[operator](#as-operator): umożliwia jawne konwertowanie wyrażenia do danego typu, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem</span><span class="sxs-lookup"><span data-stu-id="2952e-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="2952e-107">[Rzutowanie — operator ()](#cast-operator-): do wykonania jawnej konwersji</span><span class="sxs-lookup"><span data-stu-id="2952e-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="2952e-108">[TypeOf operator](#typeof-operator): uzyskanie <xref:System.Type?displayProperty=nameWithType> wystąpienia typu</span><span class="sxs-lookup"><span data-stu-id="2952e-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="2952e-109">is — operator</span><span class="sxs-lookup"><span data-stu-id="2952e-109">is operator</span></span>

<span data-ttu-id="2952e-110">`is` Operator sprawdza, czy typ środowiska uruchomieniowego, wynikiem wyrażenia jest zgodne z danym typem.</span><span class="sxs-lookup"><span data-stu-id="2952e-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="2952e-111">Począwszy od C# 7.0, `is` operator sprawdza również, wynik wyrażenia do wzorca.</span><span class="sxs-lookup"><span data-stu-id="2952e-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="2952e-112">Wyrażenie z badania typu `is` operator ma następującą postać</span><span class="sxs-lookup"><span data-stu-id="2952e-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="2952e-113">gdzie `E` to wyrażenie zwracające wartość i `T` jest nazwa typu lub parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="2952e-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="2952e-114">`E` nie może być metody anonimowej lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="2952e-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="2952e-115">`E is T` Zwraca wyrażenie `true` Jeśli wynikiem `E` jest różna od null i można przekonwertować na typ `T` konwersji odwołania, konwersji pakującej lub konwersji rozpakowującej; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="2952e-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="2952e-116">`is` Operator nie bierze pod uwagę konwersje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2952e-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="2952e-117">Poniższy przykład pokazuje, że `is` operator zwraca `true` Jeśli typ środowiska uruchomieniowego, wynikiem wyrażenia jest pochodną od danego typu, oznacza to, że istnieje odwołanie do konwersji pomiędzy typami całkowitymi:</span><span class="sxs-lookup"><span data-stu-id="2952e-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="2952e-118">Następny przykład pokazuje, że `is` operator uwzględnia, opakowywanie i rozpakowywanie konwersji, ale nie bierze pod uwagę konwersje liczbowe:</span><span class="sxs-lookup"><span data-stu-id="2952e-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="2952e-119">Aby uzyskać informacje o C# konwersji, zobacz [konwersje](~/_csharplang/spec/conversions.md) rozdziału [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2952e-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="2952e-120">Typ, testowanie za pomocą dopasowywania do wzorca</span><span class="sxs-lookup"><span data-stu-id="2952e-120">Type testing with pattern matching</span></span>

<span data-ttu-id="2952e-121">Począwszy od C# 7.0, `is` operator sprawdza również, wynik wyrażenia do wzorca.</span><span class="sxs-lookup"><span data-stu-id="2952e-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="2952e-122">W szczególności obsługuje wpisz wzór w następującej postaci:</span><span class="sxs-lookup"><span data-stu-id="2952e-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="2952e-123">gdzie `E` to wyrażenie zwracające wartość `T` jest nazwa typu lub parametrem typu i `v` jest zmienną lokalną nowego typu `T`.</span><span class="sxs-lookup"><span data-stu-id="2952e-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="2952e-124">Jeśli wynik `E` jest różna od null i mogą być konwertowane na `T` przez odwołanie, pakowanie i rozpakowywanie konwersji, `E is T v` zwraca wyrażenie `true` i przekonwertowana wartości wyniku `E` jest przypisany do Zmienna `v`.</span><span class="sxs-lookup"><span data-stu-id="2952e-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="2952e-125">W poniższym przykładzie pokazano użycie `is` operator ze wzorcem typu:</span><span class="sxs-lookup"><span data-stu-id="2952e-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="2952e-126">Aby uzyskać więcej informacji na temat wpisz wzór i inne obsługiwane wzorce zobacz [za pomocą dopasowywania do wzorca jest](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="2952e-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="2952e-127">operator</span><span class="sxs-lookup"><span data-stu-id="2952e-127">as operator</span></span>

<span data-ttu-id="2952e-128">`as` Operator jawnie konwertuje wynik wyrażenia dla danego odwołania lub typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="2952e-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="2952e-129">Jeśli konwersja nie jest to możliwe, `as` operator zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="2952e-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="2952e-130">W odróżnieniu od [rzutowania (operatora)](#cast-operator-), `as` operator nigdy nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2952e-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="2952e-131">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="2952e-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="2952e-132">gdzie `E` to wyrażenie zwracające wartość i `T` Nazwa typu lub parametrem typu, daje ten sam wynik jako</span><span class="sxs-lookup"><span data-stu-id="2952e-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="2952e-133">z tą różnicą, że `E` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="2952e-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="2952e-134">`as` Operator uwzględnia tylko konwersje odwołań, dopuszczającego wartość null, pakowania i rozpakowania.</span><span class="sxs-lookup"><span data-stu-id="2952e-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="2952e-135">Nie można użyć `as` operatora do wykonywania konwersji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2952e-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="2952e-136">Aby to zrobić, należy użyć [rzutowania (operatora)](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="2952e-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="2952e-137">W poniższym przykładzie pokazano użycie `as` operator:</span><span class="sxs-lookup"><span data-stu-id="2952e-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="2952e-138">Jak pokazano na poprzednim przykładzie, należy porównać wynik `as` wyrażenie `null` do sprawdzenia, jeśli konwersja zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2952e-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="2952e-139">Począwszy od C# 7.0, można użyć [jest operatorem](#type-testing-with-pattern-matching) zarówno do testowania, jeśli konwersja powiedzie się i, jeśli się powiedzie, przypisz wynik do nowej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2952e-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="2952e-140">CAST — operator)</span><span class="sxs-lookup"><span data-stu-id="2952e-140">Cast operator ()</span></span>

<span data-ttu-id="2952e-141">Wyrażenie cast w postaci `(T)E` wykonuje jawnej konwersji wynik wyrażenia `E` na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="2952e-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="2952e-142">Jeśli istnieje nie jawna konwersja z typu `E` na typ `T`, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2952e-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="2952e-143">W czasie wykonywania jawna konwersja może się nie powieść i wyrażenia rzutowania może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2952e-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="2952e-144">W poniższym przykładzie pokazano jawnych konwersji liczbowych i odwołania:</span><span class="sxs-lookup"><span data-stu-id="2952e-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="2952e-145">Aby uzyskać informacji na temat obsługiwanych jawnych konwersji, zobacz [jawne konwersje](~/_csharplang/spec/conversions.md#explicit-conversions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2952e-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="2952e-146">Aby uzyskać informacje o definiowaniu typu niestandardowego jawnych lub niejawnych konwersji, zobacz [konwersja zdefiniowana przez użytkownika operatory](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2952e-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="2952e-147">Inne sposoby użycia)</span><span class="sxs-lookup"><span data-stu-id="2952e-147">Other usages of ()</span></span>

<span data-ttu-id="2952e-148">Możesz również użyć nawiasów, aby [wywołania metody lub delegata wywołania](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="2952e-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="2952e-149">Inne użycie nawiasów jest określić kolejność, w którym ma być operacji w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="2952e-149">Other use of parentheses is to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="2952e-150">Aby uzyskać więcej informacji, zobacz [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) części [operatory](../../programming-guide/statements-expressions-operators/operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="2952e-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="2952e-151">Listy uporządkowane według poziomu pierwszeństwo operatorów, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="2952e-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="2952e-152">typeof — Operator</span><span class="sxs-lookup"><span data-stu-id="2952e-152">typeof operator</span></span>

<span data-ttu-id="2952e-153">`typeof` Uzyskuje operator <xref:System.Type?displayProperty=nameWithType> wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="2952e-153">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="2952e-154">Argument `typeof` operatora musi być nazwą typu lub parametrem typu, jak w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="2952e-154">An argument of the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="2952e-155">Możesz również użyć `typeof` operatora z niepowiązanych typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="2952e-155">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="2952e-156">Nazwa typu ogólnego niezwiązanego musi zawierać odpowiednią liczbę przecinkami, które jest mniejsza niż liczba parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="2952e-156">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="2952e-157">W poniższym przykładzie pokazano użycie `typeof` operatora typu niepowiązanego dla ogólnych:</span><span class="sxs-lookup"><span data-stu-id="2952e-157">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="2952e-158">Wyrażenie nie może być argumentem `typeof` operatora.</span><span class="sxs-lookup"><span data-stu-id="2952e-158">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="2952e-159">Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienia typu środowiska uruchomieniowego wyniku wyrażenia, użyj <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2952e-159">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="2952e-160">Testowanie za pomocą typu `typeof` — operator</span><span class="sxs-lookup"><span data-stu-id="2952e-160">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="2952e-161">Użyj `typeof` operatora, aby sprawdzić, czy typ środowiska uruchomieniowego, wynikiem wyrażenia dokładnie odpowiada danego typu.</span><span class="sxs-lookup"><span data-stu-id="2952e-161">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="2952e-162">W poniższym przykładzie pokazano różnicę między sprawdzania typu przeprowadzane przy użyciu `typeof` operatora i [jest operatorem](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="2952e-162">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="2952e-163">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="2952e-163">Operator overloadability</span></span>

<span data-ttu-id="2952e-164">`is`, `as`, I `typeof` operatory nie są z możliwością przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="2952e-164">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="2952e-165">Typ zdefiniowany przez użytkownika nie mogą przeciążać `()` operatora, ale można zdefiniować konwersje typów niestandardowych, które mogą być wykonywane przez wyrażenie rzutowania.</span><span class="sxs-lookup"><span data-stu-id="2952e-165">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="2952e-166">Aby uzyskać więcej informacji, zobacz [konwersja zdefiniowana przez użytkownika operatory](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2952e-166">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2952e-167">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2952e-167">C# language specification</span></span>

<span data-ttu-id="2952e-168">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="2952e-168">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2952e-169">Is — operator</span><span class="sxs-lookup"><span data-stu-id="2952e-169">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="2952e-170">Operator as</span><span class="sxs-lookup"><span data-stu-id="2952e-170">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="2952e-171">Wyrażenia CAST</span><span class="sxs-lookup"><span data-stu-id="2952e-171">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="2952e-172">Typeof — operator</span><span class="sxs-lookup"><span data-stu-id="2952e-172">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="2952e-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2952e-173">See also</span></span>

- [<span data-ttu-id="2952e-174">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="2952e-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2952e-175">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2952e-175">C# operators</span></span>](index.md)
- [<span data-ttu-id="2952e-176">Porady: bezpieczne multiemisji za pomocą dopasowywania do wzorca i jest i operatory</span><span class="sxs-lookup"><span data-stu-id="2952e-176">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
