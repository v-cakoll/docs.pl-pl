---
title: is - C# Odwołanie
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399638"
---
# <a name="is-c-reference"></a><span data-ttu-id="cb751-102">is (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cb751-102">is (C# Reference)</span></span>

<span data-ttu-id="cb751-103">Operator `is` sprawdza, czy wynik wyrażenia jest zgodny z danym typem lub (począwszy od Języka C# 7.0) testuje wyrażenie względem wzorca.</span><span class="sxs-lookup"><span data-stu-id="cb751-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="cb751-104">Aby uzyskać informacje na `is` temat operatora testowania typu zobacz [jest operator](../operators/type-testing-and-cast.md#is-operator) sekcji [typ testowania i odlewane operatorów](../operators/type-testing-and-cast.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="cb751-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="cb751-105">Dopasowanie wzorca z`is`</span><span class="sxs-lookup"><span data-stu-id="cb751-105">Pattern matching with `is`</span></span>

<span data-ttu-id="cb751-106">Począwszy od języka C# `is` 7.0, i [switch](switch.md) instrukcje obsługują dopasowanie wzorca.</span><span class="sxs-lookup"><span data-stu-id="cb751-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="cb751-107">Słowo `is` kluczowe obsługuje następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="cb751-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="cb751-108">[Wzorzec typu](#type-pattern), który sprawdza, czy wyrażenie może być konwertowane na określony typ i, jeśli może być, rzutuje go do zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="cb751-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="cb751-109">[Wzorzec stały](#constant-pattern), który sprawdza, czy wyrażenie oblicza określoną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="cb751-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="cb751-110">[var pattern](#var-pattern), dopasowanie, które zawsze powiedzie się i wiąże wartość wyrażenia z nową zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="cb751-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="cb751-111">Wzorzec tekstu</span><span class="sxs-lookup"><span data-stu-id="cb751-111">Type pattern</span></span>

<span data-ttu-id="cb751-112">Korzystając z wzorca typu do `is` wykonywania dopasowania wzorca, sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może być, rzutuje go do zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="cb751-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="cb751-113">Jest to proste rozszerzenie `is` instrukcji, która umożliwia zwięzłe oceny typu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="cb751-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="cb751-114">Ogólna forma `is` wzorca typu jest:</span><span class="sxs-lookup"><span data-stu-id="cb751-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="cb751-115">W przypadku *gdy expr* jest wyrażeniem, które oblicza wystąpienie pewnego typu, *typ* jest nazwą typu, na który ma zostać przekonwertowany wynik *expr,* `is` a `true` *varname* jest obiektem, na który jest konwertowany wynik *expr,* jeśli test jest .</span><span class="sxs-lookup"><span data-stu-id="cb751-115">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="cb751-116">Wyrażenie `is` jest, `true` jeśli *expr* nie `null`jest , a którykolwiek z następujących jest true:</span><span class="sxs-lookup"><span data-stu-id="cb751-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="cb751-117">*expr* jest wystąpieniem tego samego typu co *typ*.</span><span class="sxs-lookup"><span data-stu-id="cb751-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="cb751-118">*expr* jest wystąpieniem typu, który pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="cb751-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="cb751-119">Innymi słowy wynik *expr* może być rzutnie na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="cb751-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="cb751-120">*expr* ma typ kompilacji w czasie, który jest klasą podstawową *typu*, a *expr* ma typ czasu wykonywania, który jest *typem* lub pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="cb751-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="cb751-121">*Typ czasu kompilacji* zmiennej jest typem zmiennej zdefiniowanym w jej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cb751-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="cb751-122">*Typ czasu wykonywania* zmiennej jest typem wystąpienia przypisanego do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cb751-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="cb751-123">*expr* jest wystąpieniem typu, który implementuje interfejs *typu.*</span><span class="sxs-lookup"><span data-stu-id="cb751-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="cb751-124">Począwszy od języka C# 7.1, *expr* może mieć typ kompilacji zdefiniowany przez parametr typu ogólnego i jego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="cb751-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="cb751-125">Jeśli *expr* `true` jest i `is` `if` jest używany z instrukcją, `if` *varname* jest przypisany tylko w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cb751-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="cb751-126">Zakres *varname* jest od `is` wyrażenia do końca bloku otaczającego `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cb751-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="cb751-127">Użycie *varname* w dowolnej innej lokalizacji generuje błąd czasu kompilacji dla użycia zmiennej, która nie została przypisana.</span><span class="sxs-lookup"><span data-stu-id="cb751-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="cb751-128">W poniższym `is` przykładzie użyto wzorca typu, <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> aby zapewnić implementację metody typu.</span><span class="sxs-lookup"><span data-stu-id="cb751-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="cb751-129">Bez dopasowywania wzorców ten kod może być napisany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cb751-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="cb751-130">Użycie dopasowywania wzorców typów daje bardziej kompaktowy, czytelny kod, eliminując konieczność testowania, czy wynikiem konwersji jest . `null`</span><span class="sxs-lookup"><span data-stu-id="cb751-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="cb751-131">Wzorzec `is` typu tworzy również bardziej kompaktowy kod podczas określania typu typu wartości.</span><span class="sxs-lookup"><span data-stu-id="cb751-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="cb751-132">W poniższym `is` przykładzie użyto wzorca typu, aby określić, czy obiekt jest lub `Person` `Dog` wystąpienie przed wyświetleniem wartości odpowiedniej właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb751-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="cb751-133">Równoważny kod bez dopasowywania wzorców wymaga oddzielnego przypisania, które zawiera jawną rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="cb751-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="cb751-134">Stały wzór</span><span class="sxs-lookup"><span data-stu-id="cb751-134">Constant pattern</span></span>

<span data-ttu-id="cb751-135">Podczas wykonywania wzorca pasującego do wzorca stałego sprawdza, `is` czy wyrażenie jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="cb751-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="cb751-136">W języku C# 6 i wcześniejszych wersjach wzorzec stałej jest obsługiwany przez [switch](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cb751-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="cb751-137">Począwszy od języka C# 7.0, `is` jest również obsługiwana przez instrukcję.</span><span class="sxs-lookup"><span data-stu-id="cb751-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="cb751-138">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="cb751-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="cb751-139">gdzie *expr* jest wyrażeniem do oceny, a *stała* jest wartością do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="cb751-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="cb751-140">*stała* może być dowolne z następujących wyrażeń stałych:</span><span class="sxs-lookup"><span data-stu-id="cb751-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="cb751-141">Wartość dosłowna.</span><span class="sxs-lookup"><span data-stu-id="cb751-141">A literal value.</span></span>

- <span data-ttu-id="cb751-142">Nazwa zadeklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cb751-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="cb751-143">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb751-143">An enumeration constant.</span></span>

<span data-ttu-id="cb751-144">Wyrażenie stałe jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cb751-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="cb751-145">Jeśli *expr* i *stała* są typami integralnymi, operator `true` równości Języka C# określa, czy wyrażenie zwraca (czyli czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="cb751-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="cb751-146">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [Object.Equals(expr, stała)](xref:System.Object.Equals(System.Object,System.Object)) metoda.</span><span class="sxs-lookup"><span data-stu-id="cb751-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="cb751-147">Poniższy przykład łączy typu i stałych wzorców, aby `Dice` sprawdzić, czy obiekt jest wystąpienie i, jeśli jest, aby ustalić, czy wartość rzutu kości jest 6.</span><span class="sxs-lookup"><span data-stu-id="cb751-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="cb751-148">Sprawdzanie `null` można wykonać przy użyciu stałego wzorca.</span><span class="sxs-lookup"><span data-stu-id="cb751-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="cb751-149">Słowo `null` kluczowe jest obsługiwane `is` przez instrukcję.</span><span class="sxs-lookup"><span data-stu-id="cb751-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="cb751-150">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="cb751-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="cb751-151">W poniższym przykładzie `null` przedstawiono porównanie kontroli:</span><span class="sxs-lookup"><span data-stu-id="cb751-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="cb751-152">wzór var</span><span class="sxs-lookup"><span data-stu-id="cb751-152">var pattern</span></span>

<span data-ttu-id="cb751-153">Dopasowanie wzorca `var` do wzorca zawsze kończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cb751-153">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="cb751-154">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="cb751-154">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="cb751-155">Gdzie wartość *expr* jest zawsze przypisana do zmiennej lokalnej o nazwie *varname*.</span><span class="sxs-lookup"><span data-stu-id="cb751-155">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="cb751-156">*varname* jest zmienną tego samego typu co typ *kompie typu expr.*</span><span class="sxs-lookup"><span data-stu-id="cb751-156">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="cb751-157">Jeśli *expr* oblicza `null`, `is` wyrażenie `true` generuje i `null` przypisuje *varname*.</span><span class="sxs-lookup"><span data-stu-id="cb751-157">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="cb751-158">Var wzorzec jest jednym `is` z `true` niewielu `null` zastosowań, które produkuje dla wartości.</span><span class="sxs-lookup"><span data-stu-id="cb751-158">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="cb751-159">`var` Wzorzec służy do tworzenia zmiennej tymczasowej w wyrażenie logiczne, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cb751-159">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="cb751-160">W poprzednim przykładzie zmienna tymczasowa jest używana do przechowywania wyniku kosztownej operacji.</span><span class="sxs-lookup"><span data-stu-id="cb751-160">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="cb751-161">Zmienna może być następnie używana wiele razy.</span><span class="sxs-lookup"><span data-stu-id="cb751-161">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cb751-162">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb751-162">C# language specification</span></span>
  
<span data-ttu-id="cb751-163">Aby uzyskać więcej informacji, zobacz [jest operator](~/_csharplang/spec/expressions.md#the-is-operator) sekcji [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i następujące propozycje języka C#:</span><span class="sxs-lookup"><span data-stu-id="cb751-163">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="cb751-164">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="cb751-164">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="cb751-165">Dopasowywanie wzorca do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="cb751-165">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="cb751-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb751-166">See also</span></span>

- [<span data-ttu-id="cb751-167">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb751-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cb751-168">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cb751-168">C# keywords</span></span>](index.md)
- [<span data-ttu-id="cb751-169">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="cb751-169">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
