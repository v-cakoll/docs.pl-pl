---
title: Niejawnie wpisane zmienne lokalne — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 842f73b7af9671157495df961f5db22702ae897e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240710"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="6006b-102">Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6006b-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="6006b-103">Zmienne lokalne można deklarować bez udzielania jawnego typu.</span><span class="sxs-lookup"><span data-stu-id="6006b-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="6006b-104">`var`Słowo kluczowe instruuje kompilator do wywnioskowania typu zmiennej z wyrażenia po prawej stronie instrukcji inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="6006b-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="6006b-105">Typ wnioskowany może być typem wbudowanym, typem anonimowym, typem zdefiniowanym przez użytkownika lub typem zdefiniowanym w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="6006b-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET class library.</span></span> <span data-ttu-id="6006b-106">Aby uzyskać więcej informacji o sposobach inicjowania tablic w programie `var` , zobacz [niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="6006b-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="6006b-107">W poniższych przykładach pokazano różne sposoby deklarowania zmiennych lokalnych przy użyciu `var` :</span><span class="sxs-lookup"><span data-stu-id="6006b-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="6006b-108">Ważne jest, aby zrozumieć, że `var` słowo kluczowe nie ma znaczenia "Variant" i nie wskazuje, że zmienna jest luźno wpisana lub późna.</span><span class="sxs-lookup"><span data-stu-id="6006b-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="6006b-109">Oznacza to, że kompilator określa i przypisuje najbardziej odpowiedni typ.</span><span class="sxs-lookup"><span data-stu-id="6006b-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="6006b-110">`var`Słowo kluczowe może być używane w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6006b-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="6006b-111">W przypadku zmiennych lokalnych (zmienne zadeklarowane w zakresie metody), jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6006b-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="6006b-112">W instrukcji [for](../../language-reference/keywords/for.md) inicjującej.</span><span class="sxs-lookup"><span data-stu-id="6006b-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="6006b-113">W instrukcji inicjującej [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="6006b-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="6006b-114">W instrukcji [using](../../language-reference/keywords/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="6006b-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="6006b-115">Aby uzyskać więcej informacji, zobacz [jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="6006b-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="6006b-116">typy var i Anonymous</span><span class="sxs-lookup"><span data-stu-id="6006b-116">var and anonymous types</span></span>

<span data-ttu-id="6006b-117">W wielu przypadkach użycie `var` jest opcjonalne i jest tylko wygodną składnią.</span><span class="sxs-lookup"><span data-stu-id="6006b-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="6006b-118">Jeśli jednak zmienna jest inicjowana z typem anonimowym, należy zadeklarować zmienną tak, jakby `var` trzeba uzyskać dostęp do właściwości obiektu w późniejszym momencie.</span><span class="sxs-lookup"><span data-stu-id="6006b-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="6006b-119">Jest to typowy scenariusz w wyrażeniach zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="6006b-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="6006b-120">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="6006b-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="6006b-121">Z perspektywy kodu źródłowego typ anonimowy nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="6006b-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="6006b-122">W związku z tym, jeśli zmienna zapytania została zainicjowana przy użyciu `var` , jedynym sposobem na uzyskanie dostępu do właściwości w zwracanej sekwencji obiektów jest użycie `var` jako typ zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6006b-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="6006b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6006b-123">Remarks</span></span>

<span data-ttu-id="6006b-124">Następujące ograniczenia dotyczą deklaracji zmiennej o typie określonym niejawnie:</span><span class="sxs-lookup"><span data-stu-id="6006b-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="6006b-125">`var`można go użyć tylko wtedy, gdy zmienna lokalna jest zadeklarowana i zainicjowana w tej samej instrukcji; nie można zainicjować zmiennej do wartości null lub do grupy metod lub funkcji anonimowej.</span><span class="sxs-lookup"><span data-stu-id="6006b-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="6006b-126">`var`nie można użyć dla pól w zakresie klasy.</span><span class="sxs-lookup"><span data-stu-id="6006b-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="6006b-127">Zmienne zadeklarowane za pomocą `var` nie mogą być używane w wyrażeniu inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="6006b-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="6006b-128">Innymi słowy, to wyrażenie jest dozwolone: `int i = (i = 20);` ale to wyrażenie powoduje błąd czasu kompilacji:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="6006b-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="6006b-129">W tej samej instrukcji nie można zainicjować wielu niejawnie wpisanych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="6006b-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="6006b-130">Jeśli typ o nazwie `var` znajduje się w zakresie, `var` słowo kluczowe będzie rozpoznawane jako nazwa tego typu i nie będzie traktowane jako część niejawnie wpisanej deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6006b-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="6006b-131">Niejawne wpisywanie `var` słowa kluczowego może być stosowane tylko do zmiennych w zakresie metody lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6006b-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="6006b-132">Niejawne wpisywanie nie jest dostępne w przypadku pól klas, ponieważ kompilator języka C# napotka logiczną Paradox w trakcie przetwarzania kodu: kompilator musi znać typ pola, ale nie może określić typu, dopóki wyrażenie przypisania nie zostanie przeanalizowane, a wyrażenie nie może być ocenione bez znajomości typu.</span><span class="sxs-lookup"><span data-stu-id="6006b-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="6006b-133">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="6006b-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="6006b-134">`bookTitles`to pole klasy, które ma typ `var` .</span><span class="sxs-lookup"><span data-stu-id="6006b-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="6006b-135">Ponieważ pole nie ma wyrażenia do obliczenia, nie jest możliwe, aby kompilator mógł wnioskować, jaki typ `bookTitles` powinien być.</span><span class="sxs-lookup"><span data-stu-id="6006b-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="6006b-136">Ponadto dodanie wyrażenia do pola (na przykład dla zmiennej lokalnej) jest również niewystarczające:</span><span class="sxs-lookup"><span data-stu-id="6006b-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="6006b-137">Gdy kompilator napotyka pola podczas kompilacji kodu, rejestruje każdy typ pola przed przetworzeniem skojarzonych z nim wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6006b-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="6006b-138">Kompilator napotyka ten sam plik programu Paradox, który próbuje przeanalizować `bookTitles` : musi znać typ pola, ale kompilator zwykle określa `var` Typ, analizując wyrażenie, które nie jest możliwe bez uprzedniego poznania typu.</span><span class="sxs-lookup"><span data-stu-id="6006b-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="6006b-139">Może się okazać, że `var` może być również przydatne w przypadku wyrażeń zapytania, w których dokładny, skonstruowany typ zmiennej zapytania jest trudny do określenia.</span><span class="sxs-lookup"><span data-stu-id="6006b-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="6006b-140">Może się to zdarzyć w przypadku operacji grupowania i porządkowania.</span><span class="sxs-lookup"><span data-stu-id="6006b-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="6006b-141">`var`Słowo kluczowe może być również przydatne, gdy określony typ zmiennej jest żmudnym do wpisywania na klawiaturze lub jest oczywiste lub nie dodaje do czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="6006b-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="6006b-142">Przykładem, gdzie `var` jest przydatny w ten sposób, jest użycie zagnieżdżonych typów ogólnych, takich jak te używane z operacjami grupy.</span><span class="sxs-lookup"><span data-stu-id="6006b-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="6006b-143">W poniższym zapytaniu typem zmiennej zapytania jest `IEnumerable<IGrouping<string, Student>>` .</span><span class="sxs-lookup"><span data-stu-id="6006b-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="6006b-144">Tak długo, jak ty i inne osoby, które muszą zachować ten kod, nie występują problemy z użyciem niejawnego wpisywania dla wygody i zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="6006b-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="6006b-145">Korzystanie z programu `var` ułatwia uproszczenie kodu, ale jego użycie powinno być ograniczone do przypadków, w których jest wymagane, lub gdy ułatwia odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="6006b-145">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="6006b-146">Aby uzyskać więcej informacji o tym, kiedy należy `var` prawidłowo używać, zobacz sekcję [niejawnie wpisane zmienne lokalne](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) w artykule wytyczne dotyczące kodowania w języku C#.</span><span class="sxs-lookup"><span data-stu-id="6006b-146">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="6006b-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6006b-147">See also</span></span>

- [<span data-ttu-id="6006b-148">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6006b-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="6006b-149">Niejawnie wpisane tablice</span><span class="sxs-lookup"><span data-stu-id="6006b-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="6006b-150">Porada: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="6006b-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="6006b-151">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="6006b-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="6006b-152">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="6006b-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="6006b-153">funkcję</span><span class="sxs-lookup"><span data-stu-id="6006b-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="6006b-154">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="6006b-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="6006b-155">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="6006b-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="6006b-156">dla</span><span class="sxs-lookup"><span data-stu-id="6006b-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="6006b-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="6006b-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="6006b-158">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6006b-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
