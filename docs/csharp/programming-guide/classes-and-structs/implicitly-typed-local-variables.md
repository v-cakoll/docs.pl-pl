---
title: "Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="2da66-102">Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2da66-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="2da66-103">Zmienne lokalne mogą być deklarowane bez jawnego typu.</span><span class="sxs-lookup"><span data-stu-id="2da66-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="2da66-104">`var` — Słowo kluczowe nakazuje kompilatorowi do wywnioskowania typu zmienną z wyrażenie po prawej stronie instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="2da66-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="2da66-105">Wnioskowany typ może być typem wbudowanym, typu anonimowego, typu zdefiniowanego przez użytkownika lub typ zdefiniowany w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2da66-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="2da66-106">Aby uzyskać więcej informacji dotyczących sposobu inicjowania tablic o `var`, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="2da66-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="2da66-107">W poniższych przykładach pokazano różne sposoby, w których zmienne lokalne mogą być deklarowane z `var`:</span><span class="sxs-lookup"><span data-stu-id="2da66-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="2da66-108">Należy pamiętać, że `var` — słowo kluczowe nie oznacza "variant" i nie wskazuje, że zmienna jest luźno wpisana lub późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="2da66-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="2da66-109">Po prostu oznacza, że kompilator określa i przypisuje najbardziej odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="2da66-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="2da66-110">`var` — Słowo kluczowe może być używany w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="2da66-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="2da66-111">Zmienne lokalne (zmiennych zadeklarowanych w zakresie metody) jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2da66-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="2da66-112">W [dla](../../../csharp/language-reference/keywords/for.md) instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="2da66-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="2da66-113">W [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="2da66-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="2da66-114">W [przy użyciu](../../../csharp/language-reference/keywords/using-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2da66-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="2da66-115">Aby uzyskać więcej informacji, zobacz [porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="2da66-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="2da66-116">var i typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2da66-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="2da66-117">W wielu przypadkach użycia `var` jest opcjonalna i składni udogodnienie.</span><span class="sxs-lookup"><span data-stu-id="2da66-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="2da66-118">Jednak gdy zmienna jest zainicjowana z typu anonimowego należy zadeklarować zmienną jako `var` Jeśli musisz mieć dostęp do właściwości obiektu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="2da66-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="2da66-119">Jest to częsty przypadek w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań.</span><span class="sxs-lookup"><span data-stu-id="2da66-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="2da66-120">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="2da66-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="2da66-121">Z perspektywy kod źródłowy typ anonimowy nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="2da66-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="2da66-122">W związku z tym Jeśli zmienną zapytania został zainicjowany z `var`, a następnie jedynym sposobem, aby uzyskać dostęp do właściwości w sekwencji zwróconych obiektów jest użycie `var` jako typ zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2da66-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="2da66-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2da66-123">Remarks</span></span>  
 <span data-ttu-id="2da66-124">W typie określonym niejawnie deklaracjach zmiennych, obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="2da66-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="2da66-125">`var`można użyć tylko, gdy zmienna lokalna jest zadeklarowany i zainicjowane w tej samej instrukcji; Nie można zainicjować zmiennej, null, lub do grupy metod lub funkcji anonimowej.</span><span class="sxs-lookup"><span data-stu-id="2da66-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="2da66-126">`var`Nie można używać pól w zakresie klasy.</span><span class="sxs-lookup"><span data-stu-id="2da66-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="2da66-127">Zmienne zadeklarowane za pomocą `var` nie można użyć w wyrażeniu inicjowania.</span><span class="sxs-lookup"><span data-stu-id="2da66-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="2da66-128">Innymi słowy, to wyrażenie jest dozwolony`: int i = (i = 20);` to wyrażenie powoduje błąd kompilacji:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="2da66-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="2da66-129">W tej samej instrukcji nie można zainicjować wielu zmienne o typie określonym niejawnie.</span><span class="sxs-lookup"><span data-stu-id="2da66-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="2da66-130">Jeśli typ o nazwie `var` znajduje się w zakresie, a następnie `var` — słowo kluczowe rozwiąże tej nazwy typu i nie będzie traktowane jako część niejawnie wpisane deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="2da66-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="2da66-131">Może się okazać, że `var` mogą być przydatne w przypadku wyrażenia zapytań, w których jest trudne do ustalenia dokładnego skonstruowanego typu zmienną zapytania.</span><span class="sxs-lookup"><span data-stu-id="2da66-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="2da66-132">Taka sytuacja może wystąpić z grupowanie i kolejność operacji.</span><span class="sxs-lookup"><span data-stu-id="2da66-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="2da66-133">`var` — Słowo kluczowe może również być przydatne określonego typu zmienną jest niewygodne wpisz na klawiaturze lub jest jasne lub nie dodaje do czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="2da66-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="2da66-134">Przykładem gdzie `var` jest przydatne w tym sposób się zagnieżdżonych typów ogólnych, takich jak używana z operacjami grupy.</span><span class="sxs-lookup"><span data-stu-id="2da66-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="2da66-135">W następującym zapytaniu jest typu zmienną zapytania `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="2da66-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="2da66-136">Tak długo, jak to zrozumieć użytkowników muszą zachować swój kod, brak problemy z przy użyciu niejawnego wpisując dla wygody i skrócenia.</span><span class="sxs-lookup"><span data-stu-id="2da66-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="2da66-137">Jednak użycie `var` mieć co najmniej może utrudnić kodu zrozumiały dla innych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="2da66-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="2da66-138">Z tego powodu używa ogólnie dokumentacji C# `var` tylko gdy jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="2da66-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da66-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2da66-139">See Also</span></span>  
 [<span data-ttu-id="2da66-140">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2da66-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2da66-141">Niejawnie wpisane tablice</span><span class="sxs-lookup"><span data-stu-id="2da66-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="2da66-142">Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu kwerendy</span><span class="sxs-lookup"><span data-stu-id="2da66-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="2da66-143">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2da66-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="2da66-144">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2da66-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="2da66-145">var</span><span class="sxs-lookup"><span data-stu-id="2da66-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="2da66-146">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="2da66-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="2da66-147">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="2da66-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="2da66-148">dla</span><span class="sxs-lookup"><span data-stu-id="2da66-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="2da66-149">Instrukcja foreach w</span><span class="sxs-lookup"><span data-stu-id="2da66-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="2da66-150">Using — instrukcja</span><span class="sxs-lookup"><span data-stu-id="2da66-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
