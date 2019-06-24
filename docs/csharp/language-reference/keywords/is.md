---
title: jest - C# odwołania
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306591"
---
# <a name="is-c-reference"></a><span data-ttu-id="bd831-102">is (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bd831-102">is (C# Reference)</span></span>

<span data-ttu-id="bd831-103">`is` Operator sprawdza, czy wynikiem wyrażenia jest zgodne z danym typem lub (począwszy od C# 7.0) sprawdza wyrażenie do wzorca.</span><span class="sxs-lookup"><span data-stu-id="bd831-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="bd831-104">Aby uzyskać informacje na temat typu testowania `is` Zobacz operator [jest operatorem](../operators/type-testing-and-conversion-operators.md#is-operator) części [operatory badania typu i konwersji](../operators/type-testing-and-conversion-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="bd831-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-conversion-operators.md#is-operator) section of the [Type-testing and conversion operators](../operators/type-testing-and-conversion-operators.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="bd831-105">Dopasowywanie wzorca z `is`</span><span class="sxs-lookup"><span data-stu-id="bd831-105">Pattern matching with `is`</span></span>

<span data-ttu-id="bd831-106">Począwszy od C# 7.0, `is` i [Przełącz](switch.md) instrukcje obsługują dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="bd831-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="bd831-107">`is` — Słowo kluczowe obsługuje następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="bd831-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="bd831-108">[Wpisz wzór](#type-pattern), który sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="bd831-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="bd831-109">[Wzór stałej](#constant-pattern), która sprawdza, czy wyrażenie ma określoną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="bd831-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="bd831-110">[wzorzec var](#var-pattern), dopasowania zawsze zakończy się pomyślnie i Nowa zmienna lokalna jest powiązana wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bd831-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="bd831-111">Wpisz wzór</span><span class="sxs-lookup"><span data-stu-id="bd831-111">Type pattern</span></span>

<span data-ttu-id="bd831-112">W przypadku używania wzorca typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="bd831-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="bd831-113">To proste rozszerzenie `is` instrukcję, która umożliwia ocenę zwięzły typ i konwersji.</span><span class="sxs-lookup"><span data-stu-id="bd831-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="bd831-114">Ogólna postać `is` typu wzorzec jest:</span><span class="sxs-lookup"><span data-stu-id="bd831-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="bd831-115">gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu *typu* nazwę typu, do którego jest wynikiem *wyrażenie* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr* jest konwertowany, jeśli `is` test jest `true`.</span><span class="sxs-lookup"><span data-stu-id="bd831-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="bd831-116">`is` Wyrażenie jest `true` Jeśli *expr* nie jest `null`, i jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bd831-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="bd831-117">*wyrażenie* to wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd831-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="bd831-118">*wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd831-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="bd831-119">Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd831-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="bd831-120">*wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd831-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="bd831-121">*Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="bd831-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="bd831-122">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bd831-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="bd831-123">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bd831-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="bd831-124">Począwszy od C# 7.1, *expr* może mieć typ kompilacji, zdefiniowane przez parametr typu ogólnego i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bd831-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="bd831-125">Jeśli *expr* jest `true` i `is` jest używana z `if` instrukcji *nazwa_zmiennej* jest przypisywane w ramach `if` tylko instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd831-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="bd831-126">Zakres *nazwa_zmiennej* pochodzi z `is` wyrażenia na końcu otaczający blok `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd831-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="bd831-127">Za pomocą *nazwa_zmiennej* w dowolnej innej lokalizacji generuje błąd w czasie kompilacji do użytku w zmiennej, która nie została przypisana.</span><span class="sxs-lookup"><span data-stu-id="bd831-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="bd831-128">W poniższym przykładzie użyto `is` wpisz wzór do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bd831-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="bd831-129">Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="bd831-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="bd831-130">Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="bd831-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="bd831-131">`is` Wpisz wzór również generuje kod bardziej zwarty podczas określania typu o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="bd831-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="bd831-132">W poniższym przykładzie użyto `is` wpisz wzór, aby ustalić, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="bd831-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="bd831-133">Równoważny kod bez dopasowywania do wzorca wymaga oddzielnych przypisania, które obejmuje jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bd831-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="bd831-134">Wzór stałej</span><span class="sxs-lookup"><span data-stu-id="bd831-134">Constant pattern</span></span>

<span data-ttu-id="bd831-135">Podczas przeprowadzania dopasowywanie wzorca za wzór stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="bd831-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="bd831-136">W języku C# 6 i starszych wersji wzór stałej jest obsługiwana przez [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd831-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="bd831-137">Począwszy od C# 7.0, nie jest obsługiwany przez `is` także instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd831-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="bd831-138">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bd831-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="bd831-139">gdzie *expr* jest wyrażenie do oceny, i *stałej* jest wartością do testowania.</span><span class="sxs-lookup"><span data-stu-id="bd831-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="bd831-140">*Stała* może być dowolną z następujących stałych wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="bd831-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="bd831-141">Wartość literału.</span><span class="sxs-lookup"><span data-stu-id="bd831-141">A literal value.</span></span>

- <span data-ttu-id="bd831-142">Nazwa deklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bd831-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="bd831-143">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bd831-143">An enumeration constant.</span></span>

<span data-ttu-id="bd831-144">Stałe wyrażenie jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bd831-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="bd831-145">Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="bd831-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="bd831-146">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="bd831-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="bd831-147">Poniższy przykład łączy wzorców typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość skumulowane dice to 6.</span><span class="sxs-lookup"><span data-stu-id="bd831-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="bd831-148">Sprawdzanie `null` mogą być wykonywane przy użyciu wzorca stałej.</span><span class="sxs-lookup"><span data-stu-id="bd831-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="bd831-149">`null` — Słowo kluczowe jest obsługiwana przez `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bd831-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="bd831-150">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bd831-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="bd831-151">W poniższym przykładzie przedstawiono porównanie `null` sprawdza, czy:</span><span class="sxs-lookup"><span data-stu-id="bd831-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="bd831-152">wzorzec var</span><span class="sxs-lookup"><span data-stu-id="bd831-152">var pattern</span></span>

<span data-ttu-id="bd831-153">`var` Wzorzec jest wychwytywania dla dowolnego typu lub wartości.</span><span class="sxs-lookup"><span data-stu-id="bd831-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="bd831-154">Wartość *expr* jest zawsze przypisywana do zmiennej lokalnej taki sam typ co typ czasu kompilacji *expr*.</span><span class="sxs-lookup"><span data-stu-id="bd831-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="bd831-155">Wynik `is` wyrażenie ma zawsze wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="bd831-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="bd831-156">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bd831-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="bd831-157">W poniższym przykładzie użyto wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`.</span><span class="sxs-lookup"><span data-stu-id="bd831-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="bd831-158">Następnie wyświetla wartość i typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="bd831-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="bd831-159">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bd831-159">C# language specification</span></span>
  
<span data-ttu-id="bd831-160">Aby uzyskać więcej informacji, zobacz [jest operatorem](~/_csharplang/spec/expressions.md#the-is-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md) następujący kod C# propozycji języka:</span><span class="sxs-lookup"><span data-stu-id="bd831-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="bd831-161">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="bd831-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="bd831-162">Dopasowywanie wzorca do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="bd831-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="bd831-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd831-163">See also</span></span>

- [<span data-ttu-id="bd831-164">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="bd831-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bd831-165">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="bd831-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="bd831-166">Operatory badania typu i konwersji</span><span class="sxs-lookup"><span data-stu-id="bd831-166">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
