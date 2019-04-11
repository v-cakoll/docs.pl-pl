---
title: jest - C# odwołania
ms.custom: seodec18
ms.date: 04/09/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 83cb308a14a6db99f65b30eded20442d675cbd57
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480836"
---
# <a name="is-c-reference"></a><span data-ttu-id="4c7ff-102">is (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4c7ff-102">is (C# Reference)</span></span>

<span data-ttu-id="4c7ff-103">Sprawdza, czy obiekt jest zgodny z danego typu, lub (rozpoczynający się znakami języka C# 7.0) sprawdza się wyrażenie do wzorca.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="4c7ff-104">Testowanie zgodności typu</span><span class="sxs-lookup"><span data-stu-id="4c7ff-104">Testing for type compatibility</span></span>

<span data-ttu-id="4c7ff-105">`is` — Słowo kluczowe ocenia zgodność z typem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="4c7ff-106">Określa, czy wystąpienie obiektu lub wyniku wyrażenia można przekonwertować na określony typ.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="4c7ff-107">Ma składnię</span><span class="sxs-lookup"><span data-stu-id="4c7ff-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="4c7ff-108">gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu i *typu* jest nazwą typu, do której wynik *expr* do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="4c7ff-109">`is` Instrukcja jest `true` Jeśli *expr* jest inna niż null i wyniki z obliczając wartość wyrażenia można przekonwertować na obiekt *typu*; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="4c7ff-110">Na przykład, poniższy kod określa, czy `obj` mogą być rzutowane na wystąpienie `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="4c7ff-111">`is` Instrukcja jest wartość true, jeśli:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="4c7ff-112">*wyrażenie* to wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="4c7ff-113">*wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="4c7ff-114">Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="4c7ff-115">*wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="4c7ff-116">*Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="4c7ff-117">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="4c7ff-118">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="4c7ff-119">Poniższy przykład pokazuje, że `is` wyrażenie daje w wyniku `true` dla każdej takiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="4c7ff-120">`is` — Słowo kluczowe generuje ostrzeżenie kompilacji, jeśli wiadomo, że wyrażenie zawsze być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="4c7ff-121">Analizuje ona tylko konwersje odwołań, konwersje boxing i konwersji unboxing; nie traktuje konwersje zdefiniowane przez użytkownika lub konwersje zdefiniowane przez typ [niejawne](implicit.md) i [jawne](explicit.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="4c7ff-122">Poniższy przykład generuje ostrzeżenia, ponieważ wynik konwersji jest znany w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-122">The following example generates warnings because the result of the conversion is known at compile time.</span></span> <span data-ttu-id="4c7ff-123">`is` Wyrażenia w przypadku konwersji z typu `int` do `long` i `double` zwraca wartość FAŁSZ, ponieważ te konwersje są obsługiwane przez [niejawne](implicit.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-123">The `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` <span data-ttu-id="4c7ff-124">nie może być anonimowa metoda lub wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-124">cannot be an anonymous method or lambda expression.</span></span> <span data-ttu-id="4c7ff-125">Może być dowolne wyrażenie zwracające wartość.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-125">It can be any other expression that returns a value.</span></span> <span data-ttu-id="4c7ff-126">W poniższym przykładzie użyto `is` można obliczyć wartość zwracaną przez wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="4c7ff-127">Począwszy od języka C# 7.0, można użyć dopasowywania do wzorca z [wpisz wzór](#type) napisać bardziej zwięzły widok kodu, który używa `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-127">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="4c7ff-128">Dopasowywanie wzorca z `is`</span><span class="sxs-lookup"><span data-stu-id="4c7ff-128">Pattern matching with `is`</span></span>

<span data-ttu-id="4c7ff-129">Począwszy od C# 7.0, `is` i [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcje obsługują dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-129">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="4c7ff-130">`is` — Słowo kluczowe obsługuje następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="4c7ff-131">[Wpisz wzór](#type), który sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="4c7ff-132">[Wzór stałej](#constant), która sprawdza, czy wyrażenie ma określoną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="4c7ff-133">[wzorzec var](#var), dopasowania zawsze zakończy się pomyślnie i Nowa zmienna lokalna jest powiązana wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <a name="a-nametype-type-pattern"></a><span data-ttu-id="4c7ff-134"><a name="type" />Wpisz wzór</span><span class="sxs-lookup"><span data-stu-id="4c7ff-134"><a name="type" />Type pattern</span></span>

<span data-ttu-id="4c7ff-135">W przypadku używania wzorca typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="4c7ff-136">To proste rozszerzenie `is` instrukcję, która umożliwia ocenę zwięzły typ i konwersji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-136">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="4c7ff-137">Ogólna postać `is` typu wzorzec jest:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="4c7ff-138">gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu *typu* nazwę typu, do którego jest wynikiem *wyrażenie* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr* jest konwertowany, jeśli `is` test jest `true`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="4c7ff-139">`is` Wyrażenie jest `true` Jeśli *expr* nie jest `null`, i jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-139">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="4c7ff-140">*wyrażenie* to wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="4c7ff-141">*wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="4c7ff-142">Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="4c7ff-143">*wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="4c7ff-144">*Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="4c7ff-145">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="4c7ff-146">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="4c7ff-147">Począwszy od C# 7.1, *expr* może mieć typ kompilacji, zdefiniowane przez parametr typu ogólnego i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-147">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span> 

<span data-ttu-id="4c7ff-148">Jeśli *expr* jest `true` i `is` jest używana z `if` instrukcji, *nazwa_zmiennej* przypisano i ma zakres lokalny w ramach `if` tylko instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-148">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="4c7ff-149">W poniższym przykładzie użyto `is` wpisz wzór do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-149">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="4c7ff-150">Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-150">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="4c7ff-151">Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-151">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="4c7ff-152">`is` Wpisz wzór również generuje kod bardziej zwarty podczas określania typu o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-152">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="4c7ff-153">W poniższym przykładzie użyto `is` wpisz wzór, aby ustalić, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-153">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="4c7ff-154">Równoważny kod bez dopasowywania do wzorca wymaga oddzielnych przypisania, które obejmuje jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-154">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="4c7ff-155"><a name="constant" /> Wzór stałej</span><span class="sxs-lookup"><span data-stu-id="4c7ff-155"><a name="constant" /> Constant pattern</span></span>

<span data-ttu-id="4c7ff-156">Podczas przeprowadzania dopasowywanie wzorca za wzór stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-156">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="4c7ff-157">W języku C# 6 i starszych wersji wzór stałej jest obsługiwana przez [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-157">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="4c7ff-158">Począwszy od C# 7.0, nie jest obsługiwany przez `is` także instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-158">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="4c7ff-159">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-159">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="4c7ff-160">gdzie *expr* jest wyrażenie do oceny, i *stałej* jest wartością do testowania.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-160">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="4c7ff-161">*Stała* może być dowolną z następujących stałych wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-161">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="4c7ff-162">Wartość literału.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-162">A literal value.</span></span>

- <span data-ttu-id="4c7ff-163">Nazwa deklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-163">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="4c7ff-164">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-164">An enumeration constant.</span></span>

<span data-ttu-id="4c7ff-165">Stałe wyrażenie jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-165">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="4c7ff-166">Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="4c7ff-166">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="4c7ff-167">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-167">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="4c7ff-168">Poniższy przykład łączy wzorców typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość skumulowane dice to 6.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-168">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="4c7ff-169">Sprawdzanie `null` mogą być wykonywane przy użyciu wzorca stałej.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-169">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="4c7ff-170">`null` — Słowo kluczowe jest obsługiwana przez `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-170">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="4c7ff-171">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-171">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="4c7ff-172">W poniższym przykładzie przedstawiono porównanie `null` sprawdza, czy:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-172">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="4c7ff-173"><a name="var" /> wzorzec var </a></span><span class="sxs-lookup"><span data-stu-id="4c7ff-173"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="4c7ff-174">Dopasowanie do wzorca za pomocą wzorca var zawsze kończy się powodzeniem dla wyrażeń inną niż null; Jeśli *expr* jest `null`, `is` wyrażenie jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-174">A pattern match with the var pattern always succeeds for non-null expressions; if *expr* is `null`, the `is` expression is `false`.</span></span> <span data-ttu-id="4c7ff-175">Wartość inną niż null *expr* jest zawsze przypisywana do zmiennej lokalnej taki sam typ co typ czasu środowiska uruchomieniowego *expr*.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-175">The non-null value of *expr* is always assigned to a local variable the same type as the runtime time type of *expr*.</span></span>  <span data-ttu-id="4c7ff-176">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="4c7ff-176">Its syntax is:</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="4c7ff-177">W poniższym przykładzie użyto wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-177">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="4c7ff-178">Następnie wyświetla wartość i typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="4c7ff-178">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="4c7ff-179">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4c7ff-179">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c7ff-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c7ff-180">See also</span></span>

- [<span data-ttu-id="4c7ff-181">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4c7ff-181">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4c7ff-182">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4c7ff-182">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="4c7ff-183">typeof</span><span class="sxs-lookup"><span data-stu-id="4c7ff-183">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
- [<span data-ttu-id="4c7ff-184">as</span><span class="sxs-lookup"><span data-stu-id="4c7ff-184">as</span></span>](../../../csharp/language-reference/keywords/as.md)
- [<span data-ttu-id="4c7ff-185">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="4c7ff-185">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
