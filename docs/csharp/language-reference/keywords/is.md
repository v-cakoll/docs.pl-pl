---
title: is (odwołanie w C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 16d318c1c1a5d8e560b97d9e996f1165a4566c6a
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208386"
---
# <a name="is-c-reference"></a><span data-ttu-id="661aa-102">is (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="661aa-102">is (C# Reference)</span></span> #

<span data-ttu-id="661aa-103">Sprawdza, czy obiekt jest zgodny z danego typu, lub (począwszy od wersji 7.0 C#) testów wyrażenia do wzorca.</span><span class="sxs-lookup"><span data-stu-id="661aa-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="661aa-104">Testowanie zgodności typu</span><span class="sxs-lookup"><span data-stu-id="661aa-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="661aa-105">`is` — Słowo kluczowe ocenia zgodność typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="661aa-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="661aa-106">Określa, czy wystąpienie obiektu lub można przekonwertować na określony typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="661aa-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="661aa-107">Ma ona składni</span><span class="sxs-lookup"><span data-stu-id="661aa-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="661aa-108">gdzie *wyrażenie* wyrażenie obliczane do wystąpienia typu, i *typu* jest nazwa typu, do którego wynik *wyrażenie* do konwertowania.</span><span class="sxs-lookup"><span data-stu-id="661aa-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="661aa-109">`is` Instrukcja jest `true` Jeśli *wyrażenie* jest inne niż null i wyniki z obliczenie wyrażenia można przekonwertować na obiekt *typu*; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="661aa-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="661aa-110">Na przykład następujący kod określa, czy `obj` mogą być rzutowane na wystąpienie `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="661aa-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="661aa-111">`is` Instrukcja jest wartość true, jeśli:</span><span class="sxs-lookup"><span data-stu-id="661aa-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="661aa-112">*wyrażenie* jest wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="661aa-113">*wyrażenie* jest wystąpieniem typu pochodzącego od *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="661aa-114">Innymi słowy, wynik *wyrażenie* może być upcast na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="661aa-115">*wyrażenie* zawiera typ kompilacji jest klasą podstawową *typu*, i *wyrażenie* ma typ obsługi, który jest *typu* lub pochodzi z *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="661aa-116">*Typu kompilacji* zmiennej jest typu zmienną, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="661aa-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="661aa-117">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, który jest przypisany do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="661aa-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="661aa-118">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="661aa-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="661aa-119">W poniższym przykładzie pokazano, że `is` wyrażenie ma `true` dla każdego z tych konwersji.</span><span class="sxs-lookup"><span data-stu-id="661aa-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="661aa-120">`is` — Słowo kluczowe generuje ostrzeżenie kompilacji, jeśli wiadomo, że wyrażenie zawsze być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="661aa-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="661aa-121">Traktuje tylko konwersje odwołań, konwersje boxing i konwersji unboxing; nie traktuje konwersje zdefiniowane przez użytkownika lub konwersje zdefiniowane przez określony typ [niejawne](implicit.md) i [jawne](explicit.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="661aa-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="661aa-122">Poniższy przykład generuje ostrzeżenia, ponieważ wynik konwersji jest znany w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="661aa-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="661aa-123">Należy pamiętać, że `is` wyrażenie dla konwersji z `int` do `long` i `double` zwraca wartość false, ponieważ te konwersje są obsługiwane przez [niejawne](implicit.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="661aa-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="661aa-124">`expr` może być dowolnym wyrażenie zwracające wartość, z wyjątkiem metody anonimowe i wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="661aa-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="661aa-125">W poniższym przykładzie użyto `is` do oceny, zwracana wartość wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="661aa-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="661aa-126">Począwszy od wersji 7.0 C#, można użyć dopasowywanie do wzorca za [wzorzec typu](#type) do pisania kodu bardziej zwięzły, który używa `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="661aa-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="661aa-127">Dopasowywanie do wzorca z `is`</span><span class="sxs-lookup"><span data-stu-id="661aa-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="661aa-128">Począwszy od C# 7.0, `is` i [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcje obsługuje dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="661aa-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="661aa-129">`is` — Słowo kluczowe obsługuje następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="661aa-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="661aa-130">[Wzorzec typu](#type), która sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli można ją, rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="661aa-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="661aa-131">[Stałe wzorzec](#constant), która sprawdza, czy wyrażenie ma określoną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="661aa-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="661aa-132">[var — wzorzec](#var), dopasowanie, która zawsze kończy się powodzeniem i wiąże wartość wyrażenia do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="661aa-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="661aa-133"><a name="type" /> Wzorzec typu </a></span><span class="sxs-lookup"><span data-stu-id="661aa-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="661aa-134">Korzystając ze wzorcem typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli można ją, rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="661aa-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="661aa-135">Jest prosta rozszerzenie `is` instrukcji, która umożliwia ocenę zwięzła, typ i konwersji.</span><span class="sxs-lookup"><span data-stu-id="661aa-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="661aa-136">Ogólny kształt `is` typu wzorzec jest:</span><span class="sxs-lookup"><span data-stu-id="661aa-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="661aa-137">gdzie *wyrażenie* wyrażenie obliczane do wystąpienia typu niektórych *typu* jest nazwa typu, do którego wynik *wyrażenie* należy skonwertować i *nazwa_zmiennej* obiektu, do którego wynik *wyrażenie* przekonwertowaniu Jeśli `is` testu jest `true`.</span><span class="sxs-lookup"><span data-stu-id="661aa-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="661aa-138">`is` Wyrażenie jest `true` Jeśli *wyrażenie* nie jest `null`, i jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="661aa-138">The `is` expression is `true` if *expr* is not `null`, and any of the following is true:</span></span>

- <span data-ttu-id="661aa-139">*wyrażenie* jest wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="661aa-140">*wyrażenie* jest wystąpieniem typu pochodzącego od *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="661aa-141">Innymi słowy, wynik *wyrażenie* może być upcast na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="661aa-142">*wyrażenie* zawiera typ kompilacji jest klasą podstawową *typu*, i *wyrażenie* ma typ obsługi, który jest *typu* lub pochodzi z *typu*.</span><span class="sxs-lookup"><span data-stu-id="661aa-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="661aa-143">*Typu kompilacji* zmiennej jest typu zmienną, zgodnie z definicją w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="661aa-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="661aa-144">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, który jest przypisany do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="661aa-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="661aa-145">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="661aa-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="661aa-146">Jeśli *wyrażenie* jest `true` i `is` jest używany z `if` instrukcji, *nazwa_zmiennej* przypisano i ma zasięg lokalny w `if` tylko instrukcji.</span><span class="sxs-lookup"><span data-stu-id="661aa-146">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="661aa-147">W poniższym przykładzie użyto `is` typu wzorzec do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="661aa-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="661aa-148">Bez wzorca dopasowania, ten kod może być zapisana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="661aa-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="661aa-149">Użycie typu dopasowanie wzorca tworzy kodu mniejszych, który może zostać odczytany, eliminując konieczność, aby sprawdzić, czy wynik konwersji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="661aa-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="661aa-150">`is` Wzorzec typu tworzy również mniejszych kodu podczas określania typu typu wartości.</span><span class="sxs-lookup"><span data-stu-id="661aa-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="661aa-151">W poniższym przykładzie użyto `is` typu wzorzec do ustalenia, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="661aa-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="661aa-152">Odpowiednik kodu bez dopasowywania do wzorca wymaga oddzielnych przypisania, która obejmuje jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="661aa-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="661aa-153"><a name="constant" /> Stałe wzorzec</span><span class="sxs-lookup"><span data-stu-id="661aa-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="661aa-154">Podczas wykonywania dopasowywanie do wzorca z wzorcem stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="661aa-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="661aa-155">W języku C# 6 i wcześniejszych wersjach stałe wzorzec jest obsługiwany przez [przełącznika](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="661aa-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="661aa-156">Począwszy od wersji 7.0 C#, nie jest obsługiwany przez `is` również instrukcji.</span><span class="sxs-lookup"><span data-stu-id="661aa-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="661aa-157">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="661aa-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="661aa-158">gdzie *wyrażenie* jest wyrażenie do oceny, i *stałej* jest wartość do testowania.</span><span class="sxs-lookup"><span data-stu-id="661aa-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="661aa-159">*Stała* może być dowolny z następujących wyrażenia stałe:</span><span class="sxs-lookup"><span data-stu-id="661aa-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="661aa-160">Wartość literału.</span><span class="sxs-lookup"><span data-stu-id="661aa-160">A literal value.</span></span>

- <span data-ttu-id="661aa-161">Nazwy deklarowanych `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="661aa-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="661aa-162">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="661aa-162">An enumeration constant.</span></span>

<span data-ttu-id="661aa-163">Stałe wyrażenie jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="661aa-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="661aa-164">Jeśli *wyrażenie* i *stałej* są typy całkowite operator równości C# Określa, czy wyrażenie zwraca `true` (to znaczy czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="661aa-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="661aa-165">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie do statycznego [Object.Equals (wyrażenie stałej)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="661aa-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="661aa-166">Poniższy przykład łączy wzorce typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość zbiorczego selekcji jest 6.</span><span class="sxs-lookup"><span data-stu-id="661aa-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <span data-ttu-id="661aa-167"><a name="var" /> var — wzorzec </a></span><span class="sxs-lookup"><span data-stu-id="661aa-167"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="661aa-168">Wzorzec dopasowania wzorca var zawsze kończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="661aa-168">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="661aa-169">Składnia może się</span><span class="sxs-lookup"><span data-stu-id="661aa-169">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="661aa-170">Jeżeli wartość *wyrażenie* jest zawsze przypisywana do zmiennej lokalnej o nazwie *nazwa_zmiennej*.</span><span class="sxs-lookup"><span data-stu-id="661aa-170">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="661aa-171">*nazwa_zmiennej* jest zmienna statyczna tego samego typu co *wyrażenie*.</span><span class="sxs-lookup"><span data-stu-id="661aa-171">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="661aa-172">Poniższy przykład korzysta ze wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`.</span><span class="sxs-lookup"><span data-stu-id="661aa-172">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="661aa-173">Następnie wyświetla wartości i typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="661aa-173">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="661aa-174">Należy pamiętać, że jeśli *wyrażenie* jest `null`, `is` wyrażenie nadal ma wartość true i przypisuje `null` do *nazwa_zmiennej*.</span><span class="sxs-lookup"><span data-stu-id="661aa-174">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="661aa-175">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="661aa-175">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="661aa-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="661aa-176">See also</span></span>  
 [<span data-ttu-id="661aa-177">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="661aa-177">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="661aa-178">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="661aa-178">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="661aa-179">typeof</span><span class="sxs-lookup"><span data-stu-id="661aa-179">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="661aa-180">as</span><span class="sxs-lookup"><span data-stu-id="661aa-180">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="661aa-181">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="661aa-181">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
