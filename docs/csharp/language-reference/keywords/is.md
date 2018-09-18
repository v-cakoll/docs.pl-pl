---
title: is (odwołanie w C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 8e4103f8e71858ec74c348ee1f675828e6468eb2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972178"
---
# <a name="is-c-reference"></a><span data-ttu-id="5a561-102">is (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5a561-102">is (C# Reference)</span></span> #

<span data-ttu-id="5a561-103">Sprawdza, czy obiekt jest zgodny z danego typu, lub (rozpoczynający się znakami języka C# 7.0) sprawdza się wyrażenie do wzorca.</span><span class="sxs-lookup"><span data-stu-id="5a561-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="5a561-104">Testowanie zgodności typu</span><span class="sxs-lookup"><span data-stu-id="5a561-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="5a561-105">`is` — Słowo kluczowe ocenia zgodność z typem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5a561-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="5a561-106">Określa, czy wystąpienie obiektu lub wyniku wyrażenia można przekonwertować na określony typ.</span><span class="sxs-lookup"><span data-stu-id="5a561-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="5a561-107">Ma składnię</span><span class="sxs-lookup"><span data-stu-id="5a561-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="5a561-108">gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu i *typu* jest nazwą typu, do której wynik *expr* do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="5a561-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="5a561-109">`is` Instrukcja jest `true` Jeśli *expr* jest inna niż null i wyniki z obliczając wartość wyrażenia można przekonwertować na obiekt *typu*; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="5a561-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="5a561-110">Na przykład, poniższy kod określa, czy `obj` mogą być rzutowane na wystąpienie `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="5a561-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="5a561-111">`is` Instrukcja jest wartość true, jeśli:</span><span class="sxs-lookup"><span data-stu-id="5a561-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="5a561-112">*wyrażenie* to wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="5a561-113">*wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="5a561-114">Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="5a561-115">*wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="5a561-116">*Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5a561-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="5a561-117">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5a561-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="5a561-118">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5a561-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="5a561-119">Poniższy przykład pokazuje, że `is` wyrażenie daje w wyniku `true` dla każdej takiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="5a561-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="5a561-120">`is` — Słowo kluczowe generuje ostrzeżenie kompilacji, jeśli wiadomo, że wyrażenie zawsze być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="5a561-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="5a561-121">Analizuje ona tylko konwersje odwołań, konwersje boxing i konwersji unboxing; nie traktuje konwersje zdefiniowane przez użytkownika lub konwersje zdefiniowane przez typ [niejawne](implicit.md) i [jawne](explicit.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="5a561-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="5a561-122">Poniższy przykład generuje ostrzeżenia, ponieważ wynik konwersji jest znany w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5a561-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="5a561-123">Należy pamiętać, że `is` wyrażenia w przypadku konwersji z typu `int` do `long` i `double` zwraca wartość FAŁSZ, ponieważ te konwersje są obsługiwane przez [niejawne](implicit.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="5a561-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="5a561-124">`expr` może to być wyrażenie zwracające wartość, z wyjątkiem metod anonimowych, jak i o wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="5a561-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="5a561-125">W poniższym przykładzie użyto `is` można obliczyć wartość zwracaną przez wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="5a561-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="5a561-126">Począwszy od języka C# 7.0, można użyć dopasowywania do wzorca z [wpisz wzór](#type) napisać bardziej zwięzły widok kodu, który używa `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5a561-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="5a561-127">Dopasowywanie wzorca z `is`</span><span class="sxs-lookup"><span data-stu-id="5a561-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="5a561-128">Począwszy od C# 7.0, `is` i [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcje obsługują dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="5a561-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="5a561-129">`is` — Słowo kluczowe obsługuje następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="5a561-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="5a561-130">[Wpisz wzór](#type), który sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="5a561-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="5a561-131">[Wzór stałej](#constant), która sprawdza, czy wyrażenie ma określoną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="5a561-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="5a561-132">[wzorzec var](#var), dopasowania zawsze zakończy się pomyślnie i Nowa zmienna lokalna jest powiązana wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5a561-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="5a561-133"><a name="type" /> Wpisz wzór </a></span><span class="sxs-lookup"><span data-stu-id="5a561-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="5a561-134">W przypadku używania wzorca typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="5a561-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="5a561-135">To proste rozszerzenie `is` instrukcję, która umożliwia ocenę zwięzły typ i konwersji.</span><span class="sxs-lookup"><span data-stu-id="5a561-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="5a561-136">Ogólna postać `is` typu wzorzec jest:</span><span class="sxs-lookup"><span data-stu-id="5a561-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="5a561-137">gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu *typu* nazwę typu, do którego jest wynikiem *wyrażenie* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr* jest konwertowany, jeśli `is` test jest `true`.</span><span class="sxs-lookup"><span data-stu-id="5a561-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="5a561-138">`is` Wyrażenie jest `true` Jeśli *expr* nie `null`, i jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5a561-138">The `is` expression is `true` if *expr* is not `null`, and any of the following is true:</span></span>

- <span data-ttu-id="5a561-139">*wyrażenie* to wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="5a561-140">*wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="5a561-141">Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="5a561-142">*wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*.</span><span class="sxs-lookup"><span data-stu-id="5a561-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="5a561-143">*Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5a561-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="5a561-144">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5a561-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="5a561-145">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5a561-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="5a561-146">Jeśli *expr* jest `true` i `is` jest używana z `if` instrukcji, *nazwa_zmiennej* przypisano i ma zakres lokalny w ramach `if` tylko instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5a561-146">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="5a561-147">W poniższym przykładzie użyto `is` wpisz wzór do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5a561-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="5a561-148">Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5a561-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="5a561-149">Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="5a561-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="5a561-150">`is` Wpisz wzór również generuje kod bardziej zwarty podczas określania typu o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="5a561-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="5a561-151">W poniższym przykładzie użyto `is` wpisz wzór, aby ustalić, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a561-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="5a561-152">Równoważny kod bez dopasowywania do wzorca wymaga oddzielnych przypisania, które obejmuje jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="5a561-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="5a561-153"><a name="constant" /> Wzór stałej</span><span class="sxs-lookup"><span data-stu-id="5a561-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="5a561-154">Podczas przeprowadzania dopasowywanie wzorca za wzór stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="5a561-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="5a561-155">W języku C# 6 i starszych wersji wzór stałej jest obsługiwana przez [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5a561-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="5a561-156">Począwszy od języka C# 7.0 nie jest obsługiwany przez `is` także instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5a561-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="5a561-157">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5a561-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="5a561-158">gdzie *expr* jest wyrażenie do oceny, i *stałej* jest wartością do testowania.</span><span class="sxs-lookup"><span data-stu-id="5a561-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="5a561-159">*Stała* może być dowolną z następujących stałych wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="5a561-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="5a561-160">Wartość literału.</span><span class="sxs-lookup"><span data-stu-id="5a561-160">A literal value.</span></span>

- <span data-ttu-id="5a561-161">Nazwa deklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5a561-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="5a561-162">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5a561-162">An enumeration constant.</span></span>

<span data-ttu-id="5a561-163">Stałe wyrażenie jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5a561-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="5a561-164">Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="5a561-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="5a561-165">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="5a561-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="5a561-166">Poniższy przykład łączy wzorców typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość skumulowane dice to 6.</span><span class="sxs-lookup"><span data-stu-id="5a561-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="5a561-167">Sprawdzanie `null` mogą być wykonywane przy użyciu wzorca stałej.</span><span class="sxs-lookup"><span data-stu-id="5a561-167">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="5a561-168">`null` — Słowo kluczowe jest obsługiwana przez `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5a561-168">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="5a561-169">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5a561-169">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="5a561-170">W poniższym przykładzie przedstawiono porównanie `null` sprawdza, czy:</span><span class="sxs-lookup"><span data-stu-id="5a561-170">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="5a561-171"><a name="var" /> wzorzec var </a></span><span class="sxs-lookup"><span data-stu-id="5a561-171"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="5a561-172">Dopasowanie do wzorca za pomocą wzorca var zawsze kończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5a561-172">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="5a561-173">Jest jego składni</span><span class="sxs-lookup"><span data-stu-id="5a561-173">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="5a561-174">gdy wartość *expr* jest zawsze przypisywana do zmiennej lokalnej o nazwie *nazwa_zmiennej*.</span><span class="sxs-lookup"><span data-stu-id="5a561-174">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="5a561-175">*nazwa_zmiennej* jest zmienna statyczna tego samego typu co *expr*.</span><span class="sxs-lookup"><span data-stu-id="5a561-175">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="5a561-176">W poniższym przykładzie użyto wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`.</span><span class="sxs-lookup"><span data-stu-id="5a561-176">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="5a561-177">Następnie wyświetla wartość i typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="5a561-177">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="5a561-178">Należy pamiętać, że jeśli *expr* jest `null`, `is` wyrażenie nadal ma wartość true, przypisuje `null` do *nazwa_zmiennej*.</span><span class="sxs-lookup"><span data-stu-id="5a561-178">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="5a561-179">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a561-179">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a561-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a561-180">See also</span></span>

- [<span data-ttu-id="5a561-181">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a561-181">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5a561-182">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5a561-182">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="5a561-183">typeof</span><span class="sxs-lookup"><span data-stu-id="5a561-183">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
- [<span data-ttu-id="5a561-184">as</span><span class="sxs-lookup"><span data-stu-id="5a561-184">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
- [<span data-ttu-id="5a561-185">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="5a561-185">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
