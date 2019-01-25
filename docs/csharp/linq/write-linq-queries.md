---
title: Zapisywanie zapytań LINQ w C#
description: Dowiedz się, jak pisać zapytania LINQ w C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 0837ebc6ebb2282ea26fad29ac1c31c87a0627ce
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857817"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="2de2b-103">Zapisywanie zapytań LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="2de2b-103">Write LINQ queries in C#</span></span> #

<span data-ttu-id="2de2b-104">W tym artykule przedstawiono trzy sposoby, w których można napisać zapytanie LINQ w C#:</span><span class="sxs-lookup"><span data-stu-id="2de2b-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="2de2b-105">Za pomocą składni zapytania.</span><span class="sxs-lookup"><span data-stu-id="2de2b-105">Use query syntax.</span></span>

2. <span data-ttu-id="2de2b-106">Za pomocą składni metody.</span><span class="sxs-lookup"><span data-stu-id="2de2b-106">Use method syntax.</span></span>

3. <span data-ttu-id="2de2b-107">Użyj kombinacji składnia zapytania a składnia metody.</span><span class="sxs-lookup"><span data-stu-id="2de2b-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="2de2b-108">W poniższych przykładach pokazano pewnych prostych zapytań LINQ, za pomocą danej metody wymienione wcześniej.</span><span class="sxs-lookup"><span data-stu-id="2de2b-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="2de2b-109">Ogólnie rzecz biorąc reguła jest użycie (1), jeśli to możliwe, a (2) i (3), jeśli zajdzie taka potrzeba.</span><span class="sxs-lookup"><span data-stu-id="2de2b-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="2de2b-110">Te zapytania działają na prostych kolekcji w pamięci; Podstawowa składnia jest jednak używaną w składniku LINQ to Entities i LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2de2b-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="2de2b-111">Przykład — składnia zapytań</span><span class="sxs-lookup"><span data-stu-id="2de2b-111">Example - Query syntax</span></span>

<span data-ttu-id="2de2b-112">Zalecanym sposobem pisania zapytań większości jest użycie *składni zapytania* utworzyć *wyrażeniach zapytań*.</span><span class="sxs-lookup"><span data-stu-id="2de2b-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="2de2b-113">Poniższy przykład przedstawia trzy wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="2de2b-113">The following example shows three query expressions.</span></span> <span data-ttu-id="2de2b-114">Pierwsze wyrażenie zapytanie pokazuje, jak filtrowanie lub ograniczanie wyników, stosując warunki z `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2de2b-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="2de2b-115">Zwraca wszystkie elementy w sekwencji źródłowej, w których wartości są większe niż 7 lub mniej niż 3.</span><span class="sxs-lookup"><span data-stu-id="2de2b-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="2de2b-116">Drugie wyrażenie pokazuje, jak kolejność zwróconych wyników.</span><span class="sxs-lookup"><span data-stu-id="2de2b-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="2de2b-117">Trzeci wyrażenie pokazuje, jak grupowanie wyników według klucza.</span><span class="sxs-lookup"><span data-stu-id="2de2b-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="2de2b-118">Ta kwerenda zwraca dwie grupy, w oparciu o pierwszą literę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="2de2b-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="2de2b-119">Należy zauważyć, że typ zapytania <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="2de2b-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2de2b-120">Wszystkie te zapytania można napisane przy użyciu `var` jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2de2b-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="2de2b-121">W poprzednim przykładzie zapytania nie są faktycznie wykonywane do czasu iteracji nad zmienną kwerendy w `foreach` instrukcji lub innych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2de2b-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="2de2b-122">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="2de2b-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="2de2b-123">Przykład — składnia metody</span><span class="sxs-lookup"><span data-stu-id="2de2b-123">Example - Method syntax</span></span>

<span data-ttu-id="2de2b-124">Niektóre operacje zapytania musi być wyrażona jako wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="2de2b-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="2de2b-125">Najczęściej są to te, które zwracają pojedyncze wartości liczbowe, takie jak <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2de2b-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="2de2b-126">Te metody zawsze należy wywołać ostatnia w każdym zapytaniu ponieważ reprezentuje pojedynczą wartość i nie może służyć jako źródło dla operacji zapytania dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="2de2b-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="2de2b-127">Poniższy przykład przedstawia wywołania metody w wyrażeniu zapytania:</span><span class="sxs-lookup"><span data-stu-id="2de2b-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="2de2b-128">Jeśli metoda ma parametry akcji lub Func, są one udostępniane w formie [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) wyrażenia, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2de2b-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="2de2b-129">W poprzednich zapytań tylko zapytania nr 4 wykonuje natychmiast.</span><span class="sxs-lookup"><span data-stu-id="2de2b-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="2de2b-130">Jest to spowodowane zwraca pojedynczą wartość, a nie ogólny <xref:System.Collections.Generic.IEnumerable%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2de2b-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="2de2b-131">Sama metoda ma używać `foreach` celu obliczenia jego wartość.</span><span class="sxs-lookup"><span data-stu-id="2de2b-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="2de2b-132">Każdy z poprzednich zapytań mogą być zapisywane przy użyciu niejawnego wpisywania z [var](../language-reference/keywords/var.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2de2b-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="2de2b-133">Przykład — mieszane składnia zapytania i metody</span><span class="sxs-lookup"><span data-stu-id="2de2b-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="2de2b-134">W tym przykładzie pokazano, jak używać składni metody na wynikach klauzuli kwerendy.</span><span class="sxs-lookup"><span data-stu-id="2de2b-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="2de2b-135">Po prostu należy umieścić w wyrażeniu zapytania w nawiasach, a następnie zastosowanie operatora kropki i wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="2de2b-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="2de2b-136">W poniższym przykładzie zapytanie #7 zwraca liczbę liczb, którego wartością jest od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="2de2b-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="2de2b-137">Ogólnie rzecz biorąc, lepiej jest używać drugiej zmiennej do przechowywania wynik wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="2de2b-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="2de2b-138">W ten sposób zapytanie jest mniej prawdopodobne, należy go mylić z wynikami zapytania.</span><span class="sxs-lookup"><span data-stu-id="2de2b-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="2de2b-139">Ponieważ 7 zapytanie zwraca pojedynczą wartość i nie jest kolekcją, natychmiast wykonuje zapytanie.</span><span class="sxs-lookup"><span data-stu-id="2de2b-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="2de2b-140">Poprzednie zapytanie mogą być zapisywane przy użyciu niejawnego wpisywania z `var`, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2de2b-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="2de2b-141">Może być zapisana w składni metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2de2b-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="2de2b-142">Mogą być zapisywane za pomocą jawnego wpisywania, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2de2b-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="2de2b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2de2b-143">See also</span></span>

- [<span data-ttu-id="2de2b-144">Przewodnik: Pisanie zapytań wC#</span><span class="sxs-lookup"><span data-stu-id="2de2b-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="2de2b-145">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2de2b-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="2de2b-146">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="2de2b-146">where clause</span></span>](../language-reference/keywords/where-clause.md)