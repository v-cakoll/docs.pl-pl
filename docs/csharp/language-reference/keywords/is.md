---
title: '\- C# odwołanie'
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a04105137fad7cd3a25b869c3aa7fcbe91ed20ab
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566308"
---
# <a name="is-c-reference"></a><span data-ttu-id="42936-102">is (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="42936-102">is (C# Reference)</span></span>

<span data-ttu-id="42936-103">Operator sprawdza, czy wynik wyrażenia jest zgodny z danym typem, lub (Zaczynając od C# 7,0) testuje wyrażenie względem wzorca. `is`</span><span class="sxs-lookup"><span data-stu-id="42936-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="42936-104">Aby uzyskać informacje o operatorze testowania `is` typu, zobacz sekcję [operator is](../operators/type-testing-and-cast.md#is-operator) w artykule operatorion [-Test and Cast](../operators/type-testing-and-cast.md) .</span><span class="sxs-lookup"><span data-stu-id="42936-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="42936-105">Dopasowanie wzorca z`is`</span><span class="sxs-lookup"><span data-stu-id="42936-105">Pattern matching with `is`</span></span>

<span data-ttu-id="42936-106">Począwszy od C# 7,0, `is` instrukcje i [przełącznik](switch.md) obsługują Dopasowywanie wzorców.</span><span class="sxs-lookup"><span data-stu-id="42936-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="42936-107">`is` Słowo kluczowe obsługuje następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="42936-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="42936-108">[Wzorzec typu](#type-pattern), który sprawdza, czy wyrażenie może być konwertowane do określonego typu i, jeśli może, przerzutuje go do zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="42936-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="42936-109">[Wzorzec stałej](#constant-pattern), który sprawdza, czy wyrażenie daje w wyniku określoną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="42936-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="42936-110">[wzorzec var](#var-pattern), dopasowanie, które zawsze powiedzie się i wiąże wartość wyrażenia z nową zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="42936-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="42936-111">Wzorzec typu</span><span class="sxs-lookup"><span data-stu-id="42936-111">Type pattern</span></span>

<span data-ttu-id="42936-112">W przypadku używania wzorca typu do dopasowania do wzorca, `is` sprawdza, czy wyrażenie może być konwertowane do określonego typu i, jeśli może, rzutowania go na zmienną tego typu.</span><span class="sxs-lookup"><span data-stu-id="42936-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="42936-113">Jest to proste rozszerzenie `is` instrukcji, która umożliwia obliczanie i konwersję typu zwięzłego.</span><span class="sxs-lookup"><span data-stu-id="42936-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="42936-114">Ogólna forma `is` wzorca typu jest:</span><span class="sxs-lookup"><span data-stu-id="42936-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="42936-115">gdzie *Expr* jest wyrażeniem, którego wynikiem jest wystąpienie pewnego typu, *Type* jest nazwą typu, do którego zostanie przekonwertowany wynik *wyrażenia* , a *nazwa_zmiennej* jest obiektem, do którego jest konwertowany wynik *wyrażenia* , jeśli `is` test jest `true`.</span><span class="sxs-lookup"><span data-stu-id="42936-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="42936-116">Wyrażenie jest Jeśli `true` *wyrażenie* jest nieobsługiwane `null`, a którykolwiek z następujących warunków jest spełniony: `is`</span><span class="sxs-lookup"><span data-stu-id="42936-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="42936-117">*wyrażenie* jest wystąpieniem tego samego typu co *Typ*.</span><span class="sxs-lookup"><span data-stu-id="42936-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="42936-118">*wyrażenie* jest wystąpieniem typu, który pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="42936-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="42936-119">Innymi słowy, wynik *wyrażenia* może być rzutowany na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="42936-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="42936-120">*wyrażenie* ma typ czasu kompilacji, który jest klasą bazową *typu*, a *wyrażenie* ma typ środowiska uruchomieniowego, który jest *typem* lub pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="42936-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="42936-121">*Typ czasu kompilacji* zmiennej to typ zmiennej, zgodnie z definicją w swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="42936-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="42936-122">*Typ środowiska uruchomieniowego* zmiennej to typ wystąpienia, które jest przypisane do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42936-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="42936-123">*wyrażenie* jest wystąpieniem typu, który implementuje interfejs *typu* .</span><span class="sxs-lookup"><span data-stu-id="42936-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="42936-124">Począwszy od C# 7,1, *wyrażenie* może mieć typ czasu kompilacji zdefiniowany przez parametr typu ogólnego i jego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="42936-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="42936-125">Jeśli *wyrażenie* jest `true` i `is` jest używane z `if` instrukcją, *nazwa_zmiennej* jest przypisywana tylko `if` wewnątrz instrukcji.</span><span class="sxs-lookup"><span data-stu-id="42936-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="42936-126">Zakres elementu *nazwa_zmiennej* pochodzi z `is` wyrażenia na końcu `if` bloku otaczającego instrukcję.</span><span class="sxs-lookup"><span data-stu-id="42936-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="42936-127">Użycie elementu *nazwa_zmiennej* w dowolnej innej lokalizacji generuje błąd czasu kompilacji do użycia zmiennej, która nie została przypisana.</span><span class="sxs-lookup"><span data-stu-id="42936-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="42936-128">Poniższy przykład używa wzorca typu `is` , aby zapewnić implementację <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.</span><span class="sxs-lookup"><span data-stu-id="42936-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="42936-129">Bez dopasowania do wzorca ten kod może być zapisany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="42936-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="42936-130">Użycie dopasowania wzorca typu daje bardziej zwarty, czytelny kod, eliminując konieczność sprawdzenia, czy wynik konwersji to `null`.</span><span class="sxs-lookup"><span data-stu-id="42936-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="42936-131">Wzorzec `is` typu generuje również bardziej zwarty kod podczas określania typu wartości.</span><span class="sxs-lookup"><span data-stu-id="42936-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="42936-132">W poniższym przykładzie używa się `is` wzorca typu, aby określić, czy obiekt `Person` jest `Dog` wystąpieniem, czy przed wyświetleniem wartości odpowiedniej właściwości.</span><span class="sxs-lookup"><span data-stu-id="42936-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="42936-133">Odpowiedni kod bez dopasowania do wzorca wymaga oddzielnego przypisania zawierającego jawne rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="42936-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="42936-134">Wzorzec stałej</span><span class="sxs-lookup"><span data-stu-id="42936-134">Constant pattern</span></span>

<span data-ttu-id="42936-135">Podczas wykonywania dopasowania wzorca ze wzorcem stałej, `is` sprawdza, czy wyrażenie jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="42936-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="42936-136">W C# 6 i wcześniejszych wersjach wzorzec stałej jest obsługiwany przez instrukcję [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="42936-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="42936-137">Począwszy od C# 7,0, jest to również obsługiwane przez `is` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="42936-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="42936-138">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="42936-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="42936-139">gdzie *Expr* jest wyrażeniem, które ma zostać obliczone, a *stała* jest wartością do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="42936-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="42936-140">*stała* może być dowolnym z następujących wyrażeń stałych:</span><span class="sxs-lookup"><span data-stu-id="42936-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="42936-141">Wartość literału.</span><span class="sxs-lookup"><span data-stu-id="42936-141">A literal value.</span></span>

- <span data-ttu-id="42936-142">Nazwa zadeklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42936-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="42936-143">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="42936-143">An enumeration constant.</span></span>

<span data-ttu-id="42936-144">Wyrażenie stałe jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="42936-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="42936-145">Jeśli *wyrażenie* i *stała* są typami całkowitymi, C# operator równości określa, czy wyrażenie zwróci `true` wartość (to znaczy czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="42936-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="42936-146">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody static [obiektu. Equals (wyrażenie, stała)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="42936-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="42936-147">Poniższy przykład łączy typ i wzorce stałe, aby sprawdzić, czy obiekt jest `Dice` wystąpieniem i, jeśli to jest, aby określić, czy wartość rzutowania indeksu to 6.</span><span class="sxs-lookup"><span data-stu-id="42936-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="42936-148">Sprawdzanie dla `null` można wykonać przy użyciu wzorca stałego.</span><span class="sxs-lookup"><span data-stu-id="42936-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="42936-149">Słowo kluczowe jest obsługiwane `is` przez instrukcję. `null`</span><span class="sxs-lookup"><span data-stu-id="42936-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="42936-150">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="42936-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="42936-151">W poniższym przykładzie przedstawiono porównanie `null` kontroli:</span><span class="sxs-lookup"><span data-stu-id="42936-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="42936-152">wzorzec wariancji</span><span class="sxs-lookup"><span data-stu-id="42936-152">var pattern</span></span>

<span data-ttu-id="42936-153">`var` Wzorzec jest wartością przechwycenia dla dowolnego typu lub wartości.</span><span class="sxs-lookup"><span data-stu-id="42936-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="42936-154">Wartość *wyrażenia* jest zawsze przypisywana do zmiennej lokalnej tego samego typu co typ czasu kompilacji *wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="42936-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="42936-155">Wynik `is` wyrażenia jest zawsze `true`.</span><span class="sxs-lookup"><span data-stu-id="42936-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="42936-156">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="42936-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="42936-157">Poniższy przykład używa wzorca wariancji do przypisania wyrażenia do zmiennej o nazwie `obj`.</span><span class="sxs-lookup"><span data-stu-id="42936-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="42936-158">Następnie zostanie wyświetlona wartość i typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="42936-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="42936-159">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="42936-159">C# language specification</span></span>
  
<span data-ttu-id="42936-160">Aby uzyskać więcej informacji, zapoznaj się z sekcją [operatora is](~/_csharplang/spec/expressions.md#the-is-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md) i następujących C# propozycjach języka:</span><span class="sxs-lookup"><span data-stu-id="42936-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="42936-161">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="42936-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="42936-162">Dopasowywanie wzorca do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="42936-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="42936-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42936-163">See also</span></span>

- [<span data-ttu-id="42936-164">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="42936-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="42936-165">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="42936-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="42936-166">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="42936-166">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
