---
title: Niejawnie wpisane zmienne lokalne C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: dab708bfbc33458bc2664c0d04757f0badcc2575
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141599"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="5abf2-102">Niejawnie wpisane zmienne lokalneC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="5abf2-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="5abf2-103">Zmienne lokalne można deklarować bez udzielania jawnego typu.</span><span class="sxs-lookup"><span data-stu-id="5abf2-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="5abf2-104">Słowo kluczowe `var` instruuje kompilator do wywnioskowania typu zmiennej z wyrażenia po prawej stronie instrukcji inicjującej.</span><span class="sxs-lookup"><span data-stu-id="5abf2-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="5abf2-105">Typ wnioskowany może być typem wbudowanym, typem anonimowym, typem zdefiniowanym przez użytkownika lub typem zdefiniowanym w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5abf2-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="5abf2-106">Aby uzyskać więcej informacji na temat inicjowania tablic z `var`, zobacz [niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5abf2-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="5abf2-107">W poniższych przykładach pokazano różne sposoby deklarowania zmiennych lokalnych przy użyciu `var`:</span><span class="sxs-lookup"><span data-stu-id="5abf2-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="5abf2-108">Ważne jest, aby zrozumieć, że słowo kluczowe `var` nie ma znaczenia "Variant" i nie wskazuje, że zmienna jest luźno wpisana lub późna.</span><span class="sxs-lookup"><span data-stu-id="5abf2-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="5abf2-109">Oznacza to, że kompilator określa i przypisuje najbardziej odpowiedni typ.</span><span class="sxs-lookup"><span data-stu-id="5abf2-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="5abf2-110">Słowo kluczowe `var` może być używane w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="5abf2-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="5abf2-111">W przypadku zmiennych lokalnych (zmienne zadeklarowane w zakresie metody), jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5abf2-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="5abf2-112">W instrukcji [for](../../language-reference/keywords/for.md) inicjującej.</span><span class="sxs-lookup"><span data-stu-id="5abf2-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="5abf2-113">W instrukcji inicjującej [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="5abf2-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="5abf2-114">W instrukcji [using](../../language-reference/keywords/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="5abf2-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="5abf2-115">Aby uzyskać więcej informacji, zobacz [jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="5abf2-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="5abf2-116">typy var i Anonymous</span><span class="sxs-lookup"><span data-stu-id="5abf2-116">var and anonymous types</span></span>

<span data-ttu-id="5abf2-117">W wielu przypadkach użycie `var` jest opcjonalne i jest tylko wygodą składni.</span><span class="sxs-lookup"><span data-stu-id="5abf2-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="5abf2-118">Jeśli jednak zmienna jest inicjowana z typem anonimowym, należy zadeklarować zmienną jako `var`, jeśli chcesz uzyskać dostęp do właściwości obiektu w późniejszym momencie.</span><span class="sxs-lookup"><span data-stu-id="5abf2-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="5abf2-119">Jest to typowy scenariusz w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="5abf2-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5abf2-120">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="5abf2-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="5abf2-121">Z perspektywy kodu źródłowego typ anonimowy nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="5abf2-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="5abf2-122">W związku z tym, jeśli zmienna zapytania została zainicjowana przy użyciu `var`, jedynym sposobem uzyskania dostępu do właściwości w zwracanej sekwencji obiektów jest użycie `var` jako typu zmiennej iteracji w instrukcji `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5abf2-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="5abf2-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5abf2-123">Remarks</span></span>

<span data-ttu-id="5abf2-124">Następujące ograniczenia dotyczą deklaracji zmiennej o typie określonym niejawnie:</span><span class="sxs-lookup"><span data-stu-id="5abf2-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="5abf2-125">`var` można używać tylko wtedy, gdy zmienna lokalna jest zadeklarowana i zainicjowana w tej samej instrukcji; nie można zainicjować zmiennej do wartości null lub do grupy metod lub funkcji anonimowej.</span><span class="sxs-lookup"><span data-stu-id="5abf2-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="5abf2-126">nie można używać `var` dla pól w zakresie klasy.</span><span class="sxs-lookup"><span data-stu-id="5abf2-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="5abf2-127">Zmienne zadeklarowane za pomocą `var` nie mogą być używane w wyrażeniu inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="5abf2-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="5abf2-128">Innymi słowy, to wyrażenie jest dozwolone: `int i = (i = 20);` ale to wyrażenie powoduje błąd czasu kompilacji: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="5abf2-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="5abf2-129">W tej samej instrukcji nie można zainicjować wielu niejawnie wpisanych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="5abf2-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="5abf2-130">Jeśli typ o nazwie `var` znajduje się w zakresie, wówczas słowo kluczowe `var` zostanie rozpoznane jako nazwa tego typu i nie będzie traktowane jako część niejawnie wpisanej deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5abf2-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="5abf2-131">Niejawne wpisywanie za pomocą słowa kluczowego `var` może być stosowane tylko do zmiennych w zakresie metody lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5abf2-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="5abf2-132">Niejawne wpisywanie nie jest dostępne dla pól C# klas, ponieważ kompilator napotyka logiczną Paradox w trakcie przetwarzania kodu: kompilator musi znać typ pola, ale nie może ustalić typu do momentu przeanalizowania wyrażenia przypisania i nie można oszacować wyrażenia bez znajomości typu.</span><span class="sxs-lookup"><span data-stu-id="5abf2-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="5abf2-133">Rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5abf2-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="5abf2-134">`bookTitles` to pole klasy, którego typ to `var`.</span><span class="sxs-lookup"><span data-stu-id="5abf2-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="5abf2-135">Ponieważ pole nie ma wyrażenia do obliczenia, nie jest możliwe, aby kompilator mógł wnioskować, jakiego typu `bookTitles` ma być.</span><span class="sxs-lookup"><span data-stu-id="5abf2-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="5abf2-136">Ponadto dodanie wyrażenia do pola (na przykład dla zmiennej lokalnej) jest również niewystarczające:</span><span class="sxs-lookup"><span data-stu-id="5abf2-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="5abf2-137">Gdy kompilator napotyka pola podczas kompilacji kodu, rejestruje każdy typ pola przed przetworzeniem skojarzonych z nim wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="5abf2-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="5abf2-138">Kompilator napotyka ten sam program Paradox, próbując przeanalizować `bookTitles`: musi znać typ pola, ale kompilator zwykle określa typ `var`, analizując wyrażenie, które nie jest możliwe bez uprzedniego poznania typu.</span><span class="sxs-lookup"><span data-stu-id="5abf2-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="5abf2-139">Może się okazać, że `var` może być również przydatne w przypadku wyrażeń zapytania, w których dokładny, skonstruowany typ zmiennej zapytania jest trudny do określenia.</span><span class="sxs-lookup"><span data-stu-id="5abf2-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="5abf2-140">Może się to zdarzyć w przypadku operacji grupowania i porządkowania.</span><span class="sxs-lookup"><span data-stu-id="5abf2-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="5abf2-141">Słowo kluczowe `var` może być również przydatne, gdy określony typ zmiennej jest żmudnym do wpisywania na klawiaturze lub jest oczywiste lub nie dodaje do czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="5abf2-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="5abf2-142">Przykład, w którym `var` jest pomocne w ten sposób, to z zagnieżdżonych typów ogólnych, takich jak te używane w przypadku operacji grupowych.</span><span class="sxs-lookup"><span data-stu-id="5abf2-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="5abf2-143">W poniższym zapytaniu typ zmiennej zapytania jest `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="5abf2-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="5abf2-144">Tak długo, jak ty i inne osoby, które muszą zachować ten kod, nie występują problemy z użyciem niejawnego wpisywania dla wygody i zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="5abf2-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="5abf2-145">Jednak użycie `var` ma co najmniej potencjał, aby kod był trudniejszy do zrozumienia dla innych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="5abf2-145">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="5abf2-146">Z tego powodu dokumentacja zazwyczaj C# używa `var` tylko wtedy, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="5abf2-146">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="5abf2-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5abf2-147">See also</span></span>

- [<span data-ttu-id="5abf2-148">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="5abf2-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="5abf2-149">Niejawnie wpisane tablice</span><span class="sxs-lookup"><span data-stu-id="5abf2-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="5abf2-150">Jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="5abf2-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="5abf2-151">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5abf2-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="5abf2-152">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="5abf2-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="5abf2-153">var</span><span class="sxs-lookup"><span data-stu-id="5abf2-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="5abf2-154">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="5abf2-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="5abf2-155">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="5abf2-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="5abf2-156">for</span><span class="sxs-lookup"><span data-stu-id="5abf2-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="5abf2-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="5abf2-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="5abf2-158">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5abf2-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
