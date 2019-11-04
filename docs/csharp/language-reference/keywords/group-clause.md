---
title: Klauzula grupy — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 806bc3de138ebae682d2e248593230c753eb7ba2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422765"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="a5378-102">group — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a5378-102">group clause (C# Reference)</span></span>

<span data-ttu-id="a5378-103">Klauzula `group` zwraca sekwencję obiektów <xref:System.Linq.IGrouping%602>, które zawierają zero lub więcej elementów, które pasują do wartości klucza dla grupy.</span><span class="sxs-lookup"><span data-stu-id="a5378-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="a5378-104">Na przykład można grupować sekwencję ciągów zgodnie z pierwszą literą w każdym ciągu.</span><span class="sxs-lookup"><span data-stu-id="a5378-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="a5378-105">W tym przypadku pierwsza litera jest kluczem i ma typ [char](char.md)i jest przechowywana we właściwości `Key` każdego <xref:System.Linq.IGrouping%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5378-105">In this case, the first letter is the key and has a type [char](char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="a5378-106">Kompilator wnioskuje typ klucza.</span><span class="sxs-lookup"><span data-stu-id="a5378-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="a5378-107">Możesz zakończyć wyrażenie zapytania z klauzulą `group`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a5378-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="a5378-108">Jeśli chcesz wykonać dodatkowe operacje zapytań dla każdej grupy, możesz określić tymczasowy identyfikator przy użyciu słowa kluczowego [into](into.md) .</span><span class="sxs-lookup"><span data-stu-id="a5378-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="a5378-109">Gdy używasz `into`, musisz kontynuować zapytania i ostatecznie zakończyć je za pomocą instrukcji `select` lub innej klauzuli `group`, jak pokazano na poniższym fragmencie fragmentu:</span><span class="sxs-lookup"><span data-stu-id="a5378-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="a5378-110">Dokładniejsze przykłady użycia `group` z i bez `into` są podane w przykładowej sekcji tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="a5378-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="a5378-111">Wyliczanie wyników zapytania grupy</span><span class="sxs-lookup"><span data-stu-id="a5378-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="a5378-112">Ponieważ obiekty <xref:System.Linq.IGrouping%602> utworzone przez zapytanie `group` są zasadniczo listą list, należy użyć zagnieżdżonej pętli [foreach](foreach-in.md) , aby uzyskać dostęp do elementów w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="a5378-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="a5378-113">Pętla zewnętrzna wykonuje iterację na klucze grupy, a pętla wewnętrzna wykonuje iterację nad każdym elementem w samej grupie.</span><span class="sxs-lookup"><span data-stu-id="a5378-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="a5378-114">Grupa może mieć klucz, ale nie elementy.</span><span class="sxs-lookup"><span data-stu-id="a5378-114">A group may have a key but no elements.</span></span> <span data-ttu-id="a5378-115">Poniżej znajduje się pętla `foreach`, która wykonuje zapytanie w poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="a5378-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="a5378-116">Typy kluczy</span><span class="sxs-lookup"><span data-stu-id="a5378-116">Key types</span></span>

<span data-ttu-id="a5378-117">Klucze grup mogą być dowolnego typu, takich jak ciąg, wbudowany typ liczbowy lub zdefiniowany przez użytkownika typ nazwany lub typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="a5378-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="a5378-118">Grupowanie według ciągu</span><span class="sxs-lookup"><span data-stu-id="a5378-118">Grouping by string</span></span>

<span data-ttu-id="a5378-119">W poprzednich przykładach kodu użyto `char`.</span><span class="sxs-lookup"><span data-stu-id="a5378-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="a5378-120">Zamiast tego można określić klucz ciągu, na przykład pełną nazwę:</span><span class="sxs-lookup"><span data-stu-id="a5378-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="a5378-121">Grupowanie według wartości logicznej</span><span class="sxs-lookup"><span data-stu-id="a5378-121">Grouping by bool</span></span>

<span data-ttu-id="a5378-122">W poniższym przykładzie pokazano użycie wartości logicznej dla klucza w celu podzielenia wyników na dwie grupy.</span><span class="sxs-lookup"><span data-stu-id="a5378-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="a5378-123">Należy zauważyć, że wartość jest generowana przez Podwyrażenie w klauzuli `group`.</span><span class="sxs-lookup"><span data-stu-id="a5378-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="a5378-124">Grupowanie według zakresu liczbowego</span><span class="sxs-lookup"><span data-stu-id="a5378-124">Grouping by numeric range</span></span>

<span data-ttu-id="a5378-125">W następnym przykładzie używane jest wyrażenie do tworzenia liczbowych kluczy grup reprezentujących zakres percentylu.</span><span class="sxs-lookup"><span data-stu-id="a5378-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="a5378-126">Zwróć uwagę na użycie metody [Let](let-clause.md) jako wygodnej lokalizacji do przechowywania wyniku wywołania metody, tak aby nie trzeba było wywoływać metodę dwa razy w klauzuli `group`.</span><span class="sxs-lookup"><span data-stu-id="a5378-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="a5378-127">Aby uzyskać więcej informacji o sposobie bezpiecznego używania metod w wyrażeniach zapytań, zobacz [How to: Handle Exceptions in Expressions](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a5378-127">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="a5378-128">Grupowanie według kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="a5378-128">Grouping by composite keys</span></span>

<span data-ttu-id="a5378-129">Użyj klucza złożonego, gdy chcesz grupować elementy zgodnie z więcej niż jednym kluczem.</span><span class="sxs-lookup"><span data-stu-id="a5378-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="a5378-130">Można utworzyć klucz złożony przy użyciu typu anonimowego lub nazwanego typu w celu przechowywania elementu klucza.</span><span class="sxs-lookup"><span data-stu-id="a5378-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="a5378-131">W poniższym przykładzie Załóżmy, że Klasa `Person` została zadeklarowana z elementami członkowskimi o nazwie `surname` i `city`.</span><span class="sxs-lookup"><span data-stu-id="a5378-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="a5378-132">Klauzula `group` powoduje utworzenie oddzielnej grupy dla każdego zestawu osób o tej samej nazwie i o tej samej miejscowości.</span><span class="sxs-lookup"><span data-stu-id="a5378-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="a5378-133">Użyj nazwanego typu, jeśli musisz przekazać zmienną zapytania do innej metody.</span><span class="sxs-lookup"><span data-stu-id="a5378-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="a5378-134">Utwórz specjalną klasę przy użyciu wstępnie wdrożonych właściwości kluczy, a następnie zastąp metody <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5378-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="a5378-135">Można również użyć struktury, w tym przypadku nie trzeba przesłonić tych metod.</span><span class="sxs-lookup"><span data-stu-id="a5378-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="a5378-136">Aby uzyskać więcej informacji, zobacz [instrukcje: implementowanie klasy lekkiej przy użyciu właściwości](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) , które są implementowane, i [instrukcje: zapytanie o zduplikowane pliki w drzewie katalogów](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="a5378-136">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="a5378-137">Ten ostatni artykuł zawiera przykład kodu, który demonstruje sposób użycia klucza złożonego z nazwanym typem.</span><span class="sxs-lookup"><span data-stu-id="a5378-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="a5378-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5378-138">Example</span></span>

<span data-ttu-id="a5378-139">Poniższy przykład pokazuje standardowy wzorzec służący do porządkowania danych źródłowych do grup, gdy żadna dodatkowa logika kwerendy nie zostanie zastosowana do grup.</span><span class="sxs-lookup"><span data-stu-id="a5378-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="a5378-140">Jest to nazywane grupowaniem bez kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="a5378-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="a5378-141">Elementy w tablicy ciągów są pogrupowane według ich pierwszej litery.</span><span class="sxs-lookup"><span data-stu-id="a5378-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="a5378-142">Wynikiem zapytania jest typ <xref:System.Linq.IGrouping%602>, który zawiera publiczną właściwość `Key` typu `char` oraz kolekcję <xref:System.Collections.Generic.IEnumerable%601>, która zawiera wszystkie elementy w grupowaniu.</span><span class="sxs-lookup"><span data-stu-id="a5378-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="a5378-143">Wynikiem klauzuli `group` jest sekwencja sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a5378-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="a5378-144">W związku z tym, aby uzyskać dostęp do poszczególnych elementów w każdej zwróconej grupie, Użyj zagnieżdżonej pętli `foreach` wewnątrz pętli, która iteruje klucze grupy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5378-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="a5378-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5378-145">Example</span></span>

<span data-ttu-id="a5378-146">Ten przykład pokazuje, jak wykonać dodatkową logikę dla grup po ich utworzeniu przy użyciu *kontynuacji* `into`.</span><span class="sxs-lookup"><span data-stu-id="a5378-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="a5378-147">Aby uzyskać więcej informacji, zobacz [do](into.md).</span><span class="sxs-lookup"><span data-stu-id="a5378-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="a5378-148">Poniższy przykład wysyła zapytanie do każdej grupy, aby wybrać tylko te, których wartość klucza jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="a5378-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="a5378-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5378-149">Remarks</span></span>

<span data-ttu-id="a5378-150">W czasie kompilacji klauzule `group` są tłumaczone na wywołania metody <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5378-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5378-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5378-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="a5378-152">Słowa kluczowe zapytania</span><span class="sxs-lookup"><span data-stu-id="a5378-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="a5378-153">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a5378-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="a5378-154">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="a5378-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="a5378-155">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="a5378-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="a5378-156">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="a5378-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
