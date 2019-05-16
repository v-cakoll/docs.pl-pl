---
title: Niejawnie wpisane zmienne lokalne - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 8c09ddc5a9db71a4e0bef0434d2fc14a4c088352
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635550"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="6a123-102">Niejawnie wpisane zmienne lokalne (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="6a123-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="6a123-103">Zmienne lokalne, może być zadeklarowana bez jawnego typu.</span><span class="sxs-lookup"><span data-stu-id="6a123-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="6a123-104">`var` — Słowo kluczowe nakazuje kompilatorowi wywnioskowania typu zmiennej z wyrażenie po prawej stronie instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6a123-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="6a123-105">Wnioskowany typ może być wbudowany typ, typ anonimowy, typ zdefiniowany przez użytkownika lub typ zdefiniowany w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a123-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="6a123-106">Aby uzyskać więcej informacji o tym, jak zainicjować tablic z `var`, zobacz [niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="6a123-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="6a123-107">W poniższych przykładach pokazano różne sposoby, w których zmienne lokalne mogą być deklarowane przy użyciu `var`:</span><span class="sxs-lookup"><span data-stu-id="6a123-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="6a123-108">Należy pamiętać, że `var` — słowo kluczowe nie oznaczać "variant" i nie wskazuje, że zmienna jest luźno wpisane lub z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="6a123-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="6a123-109">Po prostu oznacza to, że kompilator określa i przypisuje najbardziej odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="6a123-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="6a123-110">`var` — Słowo kluczowe może być używana w kontekstach następujące:</span><span class="sxs-lookup"><span data-stu-id="6a123-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="6a123-111">W zmiennych lokalnych (zmiennych zadeklarowanych w zakresie metoda) jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6a123-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="6a123-112">W [dla](../../language-reference/keywords/for.md) instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6a123-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for(var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="6a123-113">W [foreach](../../language-reference/keywords/foreach-in.md) instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6a123-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach(var item in list){...}
    ```

- <span data-ttu-id="6a123-114">W [przy użyciu](../../language-reference/keywords/using-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6a123-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="6a123-115">Aby uzyskać więcej informacji, zobacz [jak: Użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="6a123-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="6a123-116">var i typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="6a123-116">var and anonymous types</span></span>

<span data-ttu-id="6a123-117">W wielu przypadkach użycia `var` jest opcjonalny, a to udogodnienie składni.</span><span class="sxs-lookup"><span data-stu-id="6a123-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="6a123-118">Jednak gdy zmienna jest inicjowana za pomocą typu anonimowego należy zadeklarować zmienną jako `var` Jeśli chcesz uzyskać dostęp do właściwości obiektu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="6a123-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="6a123-119">Jest to typowy scenariusz w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="6a123-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="6a123-120">Aby uzyskać więcej informacji, zobacz [typy anonimowe](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="6a123-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="6a123-121">Z punktu widzenia kodu źródłowego typ anonimowy nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="6a123-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="6a123-122">W związku z tym jeśli zmienna zapytania została zainicjowana przy użyciu `var`, a następnie jedynym sposobem, aby uzyskać dostęp do właściwości w zwracanej sekwencji obiektów jest użycie `var` jako typ zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6a123-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="6a123-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a123-123">Remarks</span></span>

<span data-ttu-id="6a123-124">Poniższe ograniczenia mają zastosowanie do deklaracji zmiennych wpisanych niejawnie:</span><span class="sxs-lookup"><span data-stu-id="6a123-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="6a123-125">`var` można używać tylko w przypadku zmiennej lokalnej jest deklarowane i inicjowane w tej samej instrukcji; Nie można zainicjować zmiennej, na wartość null lub do grupy metoda lub funkcja anonimowa.</span><span class="sxs-lookup"><span data-stu-id="6a123-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="6a123-126">`var` Nie można używać w polach w zakresie klasy.</span><span class="sxs-lookup"><span data-stu-id="6a123-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="6a123-127">Zmienne zadeklarowane za pomocą `var` nie można używać w wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6a123-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="6a123-128">Innymi słowy, to wyrażenie jest legalna`: int i = (i = 20);` to wyrażenie powoduje błąd w czasie kompilacji: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="6a123-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="6a123-129">Nie można zainicjować wiele zmiennych wpisanych niejawnie w tej samej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6a123-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="6a123-130">Jeśli typ o nazwie `var` znajduje się w zakresie, a następnie `var` — słowo kluczowe zostanie rozwiązany w tej nazwy typu i nie będzie traktowane jako część niejawnie wpisane deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6a123-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="6a123-131">Niejawnego wpisywania z `var` — słowo kluczowe można stosować tylko do zmiennych w zakresie metody lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6a123-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="6a123-132">Niejawnego wpisywania nie jest dostępna dla pola klasy jako C# kompilator napotyka logiczne paradox przetworzeniu kod: kompilator musi znać typ pola, ale nie można określić typu, dopóki nie zostanie przeanalizowany wyrażenia przypisania, i Nie można obliczyć wyrażenia, nie wiedząc o tym typie.</span><span class="sxs-lookup"><span data-stu-id="6a123-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="6a123-133">Rozważmy poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="6a123-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="6a123-134">`bookTitles` To pole klasy dla danego typu `var`.</span><span class="sxs-lookup"><span data-stu-id="6a123-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="6a123-135">Ponieważ pole zawiera Brak wyrażenia do obliczenia, nie ma możliwości aby kompilator wywnioskuje typ `bookTitles` powinien być.</span><span class="sxs-lookup"><span data-stu-id="6a123-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="6a123-136">Ponadto dodanie wyrażenie do pola (tak jak w przypadku dla zmiennej lokalnej) jest również niewystarczające:</span><span class="sxs-lookup"><span data-stu-id="6a123-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="6a123-137">Gdy kompilator napotka pól podczas kompilacji kodu, rejestruje typ każdego pola przed przetworzeniem wszystkie wyrażenia skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="6a123-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="6a123-138">Kompilator napotka na tym samym paradox, próby przeprowadzenia analizy `bookTitles`: musi wiedzieć typu pola, ale kompilator będzie zazwyczaj określić `var`tego typu, analizując wyrażenie, które nie jest możliwe, nie wiedząc o tym typie wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6a123-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="6a123-139">Może się okazać, że `var` może być również przydatne w przypadku wyrażeń zapytania, w których jest trudny do określenia dokładnego skonstruowanego typu zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="6a123-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="6a123-140">Może to być spowodowane grupowania i kolejność operacji.</span><span class="sxs-lookup"><span data-stu-id="6a123-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="6a123-141">`var` — Słowo kluczowe może być także przydatny podczas określonego typu zmiennej jest niewygodna do typu na klawiaturze, jest oczywiste lub nie zwiększa czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="6a123-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="6a123-142">Jednym z przykładów gdzie `var` przydaje się w tym sposób jest zagnieżdżonych typów rodzajowych, takich jak używane z operacjami grupy.</span><span class="sxs-lookup"><span data-stu-id="6a123-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="6a123-143">W następującym zapytaniu typ zmiennej zapytania jest `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="6a123-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="6a123-144">Tak długo, jak Ty i inni, którzy muszą utrzymywać kod to zrozumieć, tam nie ma problemu przy użyciu niejawnego wpisywania dla wygody i skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="6a123-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="6a123-145">Jednak użycie `var` mieć co najmniej mogą sprawić, że kod jest trudniejszy do zrozumienia innym deweloperom.</span><span class="sxs-lookup"><span data-stu-id="6a123-145">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="6a123-146">Z tego powodu, dokumentacja języka C# zazwyczaj używa `var` tylko jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="6a123-146">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a123-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a123-147">See also</span></span>

- [<span data-ttu-id="6a123-148">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a123-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="6a123-149">Niejawnie wpisane tablice</span><span class="sxs-lookup"><span data-stu-id="6a123-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="6a123-150">Instrukcje: Użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="6a123-150">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="6a123-151">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="6a123-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="6a123-152">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="6a123-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="6a123-153">var</span><span class="sxs-lookup"><span data-stu-id="6a123-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="6a123-154">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="6a123-154">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
- [<span data-ttu-id="6a123-155">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6a123-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="6a123-156">for</span><span class="sxs-lookup"><span data-stu-id="6a123-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="6a123-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="6a123-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="6a123-158">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a123-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
