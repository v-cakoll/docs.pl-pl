---
title: Operatory testowania typów i wyrażenie rzutowanie — odwołanie do języka C#
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
ms.openlocfilehash: bc293c359af5744eebc63c0d0f94b4cebe3d450a
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021241"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="dc3ea-103">Operatory testowania typów i wyrażenie rzutowanie (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="dc3ea-104">Do sprawdzania typu lub konwersji typu można użyć następujących operatorów i wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="dc3ea-105">[operator :](#is-operator)aby sprawdzić, czy typ środowiska wykonawczego wyrażenia jest zgodny z danym typem</span><span class="sxs-lookup"><span data-stu-id="dc3ea-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="dc3ea-106">[jako operator](#as-operator): jawnie przekonwertować wyrażenie na dany typ, jeśli jego typ środowiska uruchomieniowego jest zgodny z tym typem</span><span class="sxs-lookup"><span data-stu-id="dc3ea-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="dc3ea-107">[wyrażenie rzutowe](#cast-expression): aby wykonać jawną konwersję</span><span class="sxs-lookup"><span data-stu-id="dc3ea-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="dc3ea-108">[typeof operator](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> aby uzyskać wystąpienie dla typu</span><span class="sxs-lookup"><span data-stu-id="dc3ea-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="dc3ea-109">jest operatorem</span><span class="sxs-lookup"><span data-stu-id="dc3ea-109">is operator</span></span>

<span data-ttu-id="dc3ea-110">Operator `is` sprawdza, czy typ środowiska wykonawczego wyniku wyrażenia jest zgodny z danym typem.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="dc3ea-111">Począwszy od języka C# 7.0, `is` operator testuje również wynik wyrażenia względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="dc3ea-112">Wyrażenie z operatorem `is` testowania typu ma następujący formularz</span><span class="sxs-lookup"><span data-stu-id="dc3ea-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="dc3ea-113">gdzie `E` jest wyrażeniem, które `T` zwraca wartość i jest nazwą typu lub parametru typu.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="dc3ea-114">`E`nie może być metodą anonimową ani wyrażeniem lambda.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="dc3ea-115">Wyrażenie `E is T` zwraca, `true` jeśli `E` wynik jest null i mogą być `T` konwertowane na typ przez konwersję odwołania, konwersji bokserskiej lub konwersji rozpakowywania; w przeciwnym `false`razie zwraca .</span><span class="sxs-lookup"><span data-stu-id="dc3ea-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="dc3ea-116">Operator `is` nie bierze pod uwagę konwersji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="dc3ea-117">Poniższy przykład pokazuje, `is` że `true` operator zwraca, jeśli typ środowiska uruchomieniowego wyniku wyrażenia pochodzi od danego typu, oznacza to, że istnieje konwersja odwołania między typami:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="dc3ea-118">W następnym przykładzie `is` pokazano, że operator bierze pod uwagę konwersje bokserskie i rozpakowywanie, ale nie bierze pod uwagę [konwersji liczbowych:](../builtin-types/numeric-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="dc3ea-119">Aby uzyskać informacje o konwersjach w języku C#, zobacz rozdział [Konwersje](~/_csharplang/spec/conversions.md) [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="dc3ea-120">Testowanie typów z dopasowaniem wzorca</span><span class="sxs-lookup"><span data-stu-id="dc3ea-120">Type testing with pattern matching</span></span>

<span data-ttu-id="dc3ea-121">Począwszy od języka C# 7.0, `is` operator testuje również wynik wyrażenia względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="dc3ea-122">W szczególności obsługuje wzorzec typu w następującej formie:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="dc3ea-123">gdzie `E` jest wyrażeniem, które `T` zwraca wartość, jest nazwą typu `v` lub parametru typu `T`i jest nową zmienną lokalną typu .</span><span class="sxs-lookup"><span data-stu-id="dc3ea-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="dc3ea-124">Jeśli wynik `E` jest nie-null i mogą `T` być konwertowane przez odwołanie, boks, lub unboxing konwersji, `E is T v` wyrażenie `true` zwraca `v`i przekonwertowana wartość wyniku jest przypisany do zmiennej `E` .</span><span class="sxs-lookup"><span data-stu-id="dc3ea-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="dc3ea-125">Poniższy przykład pokazuje użycie `is` operatora z wzorcem typu:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="dc3ea-126">Aby uzyskać więcej informacji na temat wzorca typu i innych obsługiwanych wzorców, zobacz [Dopasowywanie wzorca z jest](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="dc3ea-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="dc3ea-127">operator as</span><span class="sxs-lookup"><span data-stu-id="dc3ea-127">as operator</span></span>

<span data-ttu-id="dc3ea-128">Operator `as` jawnie konwertuje wynik wyrażenia na dane odwołanie lub typ wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="dc3ea-129">Jeśli konwersja nie jest `as` możliwa, operator zwraca . `null`</span><span class="sxs-lookup"><span data-stu-id="dc3ea-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="dc3ea-130">W przeciwieństwie do `as` [wyrażenia rzutowego](#cast-expression)operator nigdy nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-130">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="dc3ea-131">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="dc3ea-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="dc3ea-132">gdzie `E` jest wyrażeniem, które `T` zwraca wartość i jest nazwą typu lub parametru typu, daje taki sam wynik jak</span><span class="sxs-lookup"><span data-stu-id="dc3ea-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="dc3ea-133">z `E` tą różnicą, że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="dc3ea-134">Operator `as` bierze pod uwagę tylko odwołania, nullable, boks i unboxing konwersji.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="dc3ea-135">Nie można `as` użyć operatora do wykonania konwersji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="dc3ea-136">Aby to zrobić, należy użyć [wyrażenia rzutowego](#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="dc3ea-136">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="dc3ea-137">Poniższy przykład pokazuje użycie `as` operatora:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="dc3ea-138">Jak pokazano w poprzednim przykładzie, należy porównać wynik `as` wyrażenia z, `null` aby sprawdzić, czy konwersja zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="dc3ea-139">Począwszy od języka C# 7.0, można użyć [is operatora](#type-testing-with-pattern-matching) zarówno do testowania, jeśli konwersja powiedzie się i, jeśli zakończy się pomyślnie, przypisać jej wynik do nowej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="dc3ea-140">Wyrażenie rzutowe</span><span class="sxs-lookup"><span data-stu-id="dc3ea-140">Cast expression</span></span>

<span data-ttu-id="dc3ea-141">Wyrażenie rzutowania formularza `(T)E` wykonuje jawną konwersję wyniku `E` wyrażenia `T`na typ .</span><span class="sxs-lookup"><span data-stu-id="dc3ea-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="dc3ea-142">Jeśli nie istnieje jawna konwersja od typu `E` do typu, `T`występuje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="dc3ea-143">W czasie wykonywania jawne konwersji może nie zakończyć się pomyślnie i wyrażenie rzutu może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="dc3ea-144">Poniższy przykład pokazuje jawne konwersje liczbowe i referencyjne:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="dc3ea-145">Aby uzyskać informacje na temat obsługiwanych konwersji jawnych, zobacz sekcję [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions) [w specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="dc3ea-146">Aby uzyskać informacje dotyczące definiowania niestandardowej konwersji typu jawnego lub niejawnego, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc3ea-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="dc3ea-147">Inne zastosowania ()</span><span class="sxs-lookup"><span data-stu-id="dc3ea-147">Other usages of ()</span></span>

<span data-ttu-id="dc3ea-148">Nawiasy są również używane do [wywoływania metody lub wywoływania pełnomocnika](member-access-operators.md#invocation-expression-).</span><span class="sxs-lookup"><span data-stu-id="dc3ea-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="dc3ea-149">Inne użycie nawiasów jest dostosowanie kolejności, w jakiej do oceny operacji w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="dc3ea-150">Aby uzyskać więcej informacji, zobacz [operatory języka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="dc3ea-151">typeof — Operator</span><span class="sxs-lookup"><span data-stu-id="dc3ea-151">typeof operator</span></span>

<span data-ttu-id="dc3ea-152">Operator `typeof` uzyskuje <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="dc3ea-153">Argumentem `typeof` operatora musi być nazwa typu lub parametru typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="dc3ea-154">Można również użyć `typeof` operatora z niezwiązane typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-154">You can also use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="dc3ea-155">Nazwa niezwiązanego typu ogólnego musi zawierać odpowiednią liczbę przecinków, która jest mniejsza niż liczba parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="dc3ea-156">W poniższym przykładzie `typeof` przedstawiono użycie operatora z niezwiązanym typem ogólnym:</span><span class="sxs-lookup"><span data-stu-id="dc3ea-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="dc3ea-157">Wyrażenie nie może być `typeof` argumentem operatora.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="dc3ea-158">Aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie dla typu środowiska wykonawczego wyniku <xref:System.Object.GetType%2A?displayProperty=nameWithType> wyrażenia, należy użyć metody.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="dc3ea-159">Badanie typu `typeof` z operatorem</span><span class="sxs-lookup"><span data-stu-id="dc3ea-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="dc3ea-160">`typeof` Operator służy do sprawdzania, czy typ środowiska wykonawczego wyniku wyrażenia dokładnie odpowiada danego typu.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="dc3ea-161">Poniższy przykład pokazuje różnicę między sprawdzaniem `typeof` typu wykonywanym za pomocą operatora is a [operatorem is:](#is-operator)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="dc3ea-162">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="dc3ea-162">Operator overloadability</span></span>

<span data-ttu-id="dc3ea-163">`is`Operatory `as`i `typeof` operatory nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="dc3ea-164">Typ zdefiniowany przez użytkownika `()` nie może przeciążać operatora, ale może definiować niestandardowe konwersje typu, które mogą być wykonywane przez wyrażenie rzutowane.</span><span class="sxs-lookup"><span data-stu-id="dc3ea-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="dc3ea-165">Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc3ea-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dc3ea-166">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dc3ea-166">C# language specification</span></span>

<span data-ttu-id="dc3ea-167">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dc3ea-168">Operator is</span><span class="sxs-lookup"><span data-stu-id="dc3ea-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="dc3ea-169">Jako operator</span><span class="sxs-lookup"><span data-stu-id="dc3ea-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="dc3ea-170">Wyrażenia rzutowe</span><span class="sxs-lookup"><span data-stu-id="dc3ea-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="dc3ea-171">Operator typeof</span><span class="sxs-lookup"><span data-stu-id="dc3ea-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="dc3ea-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc3ea-172">See also</span></span>

- [<span data-ttu-id="dc3ea-173">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dc3ea-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dc3ea-174">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="dc3ea-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="dc3ea-175">Jak bezpiecznie rzucać za pomocą dopasowywania wzorców i jest i jako operatorzy</span><span class="sxs-lookup"><span data-stu-id="dc3ea-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="dc3ea-176">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="dc3ea-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
