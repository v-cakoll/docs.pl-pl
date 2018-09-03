---
title: Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 91020886e381d8410358cae9511107e28c51452a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464911"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="9b19b-102">Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9b19b-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="9b19b-103">Zmienne lokalne, może być zadeklarowana bez jawnego typu.</span><span class="sxs-lookup"><span data-stu-id="9b19b-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="9b19b-104">`var` — Słowo kluczowe nakazuje kompilatorowi wywnioskowania typu zmiennej z wyrażenie po prawej stronie instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9b19b-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="9b19b-105">Wnioskowany typ może być wbudowany typ, typ anonimowy, typ zdefiniowany przez użytkownika lub typ zdefiniowany w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b19b-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="9b19b-106">Aby uzyskać więcej informacji o tym, jak zainicjować tablic z `var`, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="9b19b-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="9b19b-107">W poniższych przykładach pokazano różne sposoby, w których zmienne lokalne mogą być deklarowane przy użyciu `var`:</span><span class="sxs-lookup"><span data-stu-id="9b19b-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="9b19b-108">Należy pamiętać, że `var` — słowo kluczowe nie oznaczać "variant" i nie wskazuje, że zmienna jest luźno wpisane lub z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="9b19b-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="9b19b-109">Po prostu oznacza to, że kompilator określa i przypisuje najbardziej odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="9b19b-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="9b19b-110">`var` — Słowo kluczowe może być używana w kontekstach następujące:</span><span class="sxs-lookup"><span data-stu-id="9b19b-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="9b19b-111">W zmiennych lokalnych (zmiennych zadeklarowanych w zakresie metoda) jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b19b-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="9b19b-112">W [dla](../../../csharp/language-reference/keywords/for.md) instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9b19b-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="9b19b-113">W [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9b19b-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="9b19b-114">W [przy użyciu](../../../csharp/language-reference/keywords/using-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9b19b-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="9b19b-115">Aby uzyskać więcej informacji, zobacz [porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="9b19b-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="9b19b-116">var i typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9b19b-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="9b19b-117">W wielu przypadkach użycia `var` jest opcjonalny, a to udogodnienie składni.</span><span class="sxs-lookup"><span data-stu-id="9b19b-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="9b19b-118">Jednak gdy zmienna jest inicjowana za pomocą typu anonimowego należy zadeklarować zmienną jako `var` Jeśli chcesz uzyskać dostęp do właściwości obiektu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="9b19b-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="9b19b-119">Jest to typowy scenariusz w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="9b19b-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="9b19b-120">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9b19b-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="9b19b-121">Z punktu widzenia kodu źródłowego typ anonimowy nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="9b19b-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="9b19b-122">W związku z tym jeśli zmienna zapytania została zainicjowana przy użyciu `var`, a następnie jedynym sposobem, aby uzyskać dostęp do właściwości w zwracanej sekwencji obiektów jest użycie `var` jako typ zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9b19b-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="9b19b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b19b-123">Remarks</span></span>  
 <span data-ttu-id="9b19b-124">Poniższe ograniczenia mają zastosowanie do deklaracji zmiennych wpisanych niejawnie:</span><span class="sxs-lookup"><span data-stu-id="9b19b-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="9b19b-125">`var` można używać tylko w przypadku zmiennej lokalnej jest deklarowane i inicjowane w tej samej instrukcji; Nie można zainicjować zmiennej, na wartość null lub do grupy metoda lub funkcja anonimowa.</span><span class="sxs-lookup"><span data-stu-id="9b19b-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="9b19b-126">`var` Nie można używać w polach w zakresie klasy.</span><span class="sxs-lookup"><span data-stu-id="9b19b-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="9b19b-127">Zmienne zadeklarowane za pomocą `var` nie można używać w wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9b19b-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="9b19b-128">Innymi słowy, to wyrażenie jest legalna`: int i = (i = 20);` to wyrażenie powoduje błąd w czasie kompilacji: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="9b19b-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="9b19b-129">Nie można zainicjować wiele zmiennych wpisanych niejawnie w tej samej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9b19b-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="9b19b-130">Jeśli typ o nazwie `var` znajduje się w zakresie, a następnie `var` — słowo kluczowe zostanie rozwiązany w tej nazwy typu i nie będzie traktowane jako część niejawnie wpisane deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="9b19b-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="9b19b-131">Może się okazać, że `var` może być również przydatne w przypadku wyrażeń zapytania, w których jest trudny do określenia dokładnego skonstruowanego typu zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="9b19b-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="9b19b-132">Może to być spowodowane grupowania i kolejność operacji.</span><span class="sxs-lookup"><span data-stu-id="9b19b-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="9b19b-133">`var` — Słowo kluczowe może być także przydatny podczas określonego typu zmiennej jest niewygodna do typu na klawiaturze, jest oczywiste lub nie zwiększa czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="9b19b-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="9b19b-134">Jednym z przykładów gdzie `var` przydaje się w tym sposób jest zagnieżdżonych typów rodzajowych, takich jak używane z operacjami grupy.</span><span class="sxs-lookup"><span data-stu-id="9b19b-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="9b19b-135">W następującym zapytaniu typ zmiennej zapytania jest `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="9b19b-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="9b19b-136">Tak długo, jak Ty i inni, którzy muszą utrzymywać kod to zrozumieć, tam nie ma problemu przy użyciu niejawnego wpisywania dla wygody i skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="9b19b-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="9b19b-137">Jednak użycie `var` mieć co najmniej mogą sprawić, że kod jest trudniejszy do zrozumienia innym deweloperom.</span><span class="sxs-lookup"><span data-stu-id="9b19b-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="9b19b-138">Z tego powodu, dokumentacja języka C# zazwyczaj używa `var` tylko jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="9b19b-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b19b-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b19b-139">See Also</span></span>  
 [<span data-ttu-id="9b19b-140">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9b19b-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9b19b-141">Niejawnie wpisane tablice</span><span class="sxs-lookup"><span data-stu-id="9b19b-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="9b19b-142">Instrukcje: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="9b19b-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="9b19b-143">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9b19b-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="9b19b-144">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="9b19b-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="9b19b-145">var</span><span class="sxs-lookup"><span data-stu-id="9b19b-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="9b19b-146">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="9b19b-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="9b19b-147">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="9b19b-147">LINQ (Language-Integrated Query)</span></span>](../../../csharp/linq/index.md)  
 [<span data-ttu-id="9b19b-148">for</span><span class="sxs-lookup"><span data-stu-id="9b19b-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="9b19b-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="9b19b-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="9b19b-150">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9b19b-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
