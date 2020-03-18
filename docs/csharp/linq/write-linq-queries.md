---
title: Zapisywanie zapytań LINQ w C#
description: Dowiedz się, jak pisać zapytania LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632876"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="7ad07-103">Napisz zapytania LINQ w C\#</span><span class="sxs-lookup"><span data-stu-id="7ad07-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="7ad07-104">W tym artykule przedstawiono trzy sposoby, w których można napisać kwerendę LINQ w języku C#:</span><span class="sxs-lookup"><span data-stu-id="7ad07-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="7ad07-105">Użyj składni kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7ad07-105">Use query syntax.</span></span>

2. <span data-ttu-id="7ad07-106">Użyj składni metody.</span><span class="sxs-lookup"><span data-stu-id="7ad07-106">Use method syntax.</span></span>

3. <span data-ttu-id="7ad07-107">Użyj kombinacji składni kwerendy i składni metody.</span><span class="sxs-lookup"><span data-stu-id="7ad07-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="7ad07-108">W poniższych przykładach przedstawiono kilka prostych zapytań LINQ przy użyciu każdego podejścia wymienione wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7ad07-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="7ad07-109">Ogólnie rzecz biorąc, regułą jest stosowanie (1) w miarę możliwości i stosowanie (2) i (3) w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="7ad07-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="7ad07-110">Te zapytania działają na prostych kolekcji w pamięci; Jednak podstawowa składnia jest taka sama jak w LINQ do jednostek i LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="7ad07-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="7ad07-111">Przykład — składnia kwerendy</span><span class="sxs-lookup"><span data-stu-id="7ad07-111">Example - Query syntax</span></span>

<span data-ttu-id="7ad07-112">Zalecanym sposobem pisania większości kwerend jest użycie *składni kwerendy* do tworzenia *wyrażeń kwerend .*</span><span class="sxs-lookup"><span data-stu-id="7ad07-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="7ad07-113">W poniższym przykładzie przedstawiono trzy wyrażenia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7ad07-113">The following example shows three query expressions.</span></span> <span data-ttu-id="7ad07-114">Pierwsze wyrażenie kwerendy pokazuje, jak filtrować lub `where` ograniczać wyniki, stosując warunki z klauzulą.</span><span class="sxs-lookup"><span data-stu-id="7ad07-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="7ad07-115">Zwraca wszystkie elementy w sekwencji źródłowej, których wartości są większe niż 7 lub mniej niż 3.</span><span class="sxs-lookup"><span data-stu-id="7ad07-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="7ad07-116">Drugie wyrażenie pokazuje, jak uporządkować zwrócone wyniki.</span><span class="sxs-lookup"><span data-stu-id="7ad07-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="7ad07-117">Trzecie wyrażenie pokazuje, jak grupować wyniki zgodnie z kluczem.</span><span class="sxs-lookup"><span data-stu-id="7ad07-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="7ad07-118">Ta kwerenda zwraca dwie grupy na podstawie pierwszej litery wyrazu.</span><span class="sxs-lookup"><span data-stu-id="7ad07-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="7ad07-119">Należy zauważyć, że typ <xref:System.Collections.Generic.IEnumerable%601>kwerend jest .</span><span class="sxs-lookup"><span data-stu-id="7ad07-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="7ad07-120">Wszystkie te zapytania mogą `var` być zapisywane przy użyciu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7ad07-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="7ad07-121">W każdym poprzednim przykładzie kwerendy faktycznie nie są wykonywane, dopóki `foreach` nie iterate nad zmienną kwerendy w instrukcji lub innej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7ad07-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="7ad07-122">Aby uzyskać więcej informacji, zobacz [Wprowadzenie do linq zapytania](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="7ad07-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="7ad07-123">Przykład — składnia metody</span><span class="sxs-lookup"><span data-stu-id="7ad07-123">Example - Method syntax</span></span>

<span data-ttu-id="7ad07-124">Niektóre operacje kwerendy muszą być wyrażone jako wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="7ad07-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="7ad07-125">Najczęstsze takie metody to te, które zwracają pojedyncze <xref:System.Linq.Enumerable.Sum%2A>wartości <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A>liczbowe, takie jak , , , <xref:System.Linq.Enumerable.Average%2A>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7ad07-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="7ad07-126">Te metody muszą być zawsze wywoływane jako ostatnie w dowolnej kwerendzie, ponieważ reprezentują tylko jedną wartość i nie mogą służyć jako źródło dodatkowej operacji kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7ad07-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="7ad07-127">W poniższym przykładzie przedstawiono wywołanie metody w wyrażeniu kwerendy:</span><span class="sxs-lookup"><span data-stu-id="7ad07-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="7ad07-128">Jeśli metoda ma Action lub Func parametry, są one dostarczane w postaci wyrażenia [lambda,](../programming-guide/statements-expressions-operators/lambda-expressions.md) jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7ad07-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="7ad07-129">W poprzednich kwerendach tylko kwerenda #4 jest wykonywana natychmiast.</span><span class="sxs-lookup"><span data-stu-id="7ad07-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="7ad07-130">Jest to spowodowane zwraca pojedynczą wartość, <xref:System.Collections.Generic.IEnumerable%601> a nie kolekcji ogólnej.</span><span class="sxs-lookup"><span data-stu-id="7ad07-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="7ad07-131">Sama metoda musi `foreach` użyć w celu obliczenia jej wartości.</span><span class="sxs-lookup"><span data-stu-id="7ad07-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="7ad07-132">Każde z poprzednich zapytań można zapisać przy użyciu niejawnego wpisywania z [var](../language-reference/keywords/var.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7ad07-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="7ad07-133">Przykład — składnia kwerendmieszanych i metod</span><span class="sxs-lookup"><span data-stu-id="7ad07-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="7ad07-134">W tym przykładzie pokazano, jak używać składni metody na wynikach klauzuli kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7ad07-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="7ad07-135">Wystarczy ująć wyrażenie kwerendy w nawiasy, a następnie zastosować operator kropki i wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="7ad07-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="7ad07-136">W poniższym przykładzie kwerenda #7 zwraca liczbę liczb, których wartość wynosi od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="7ad07-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="7ad07-137">Ogólnie rzecz biorąc jednak lepiej jest użyć drugiej zmiennej do przechowywania wyniku wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="7ad07-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="7ad07-138">W ten sposób kwerenda jest mniej prawdopodobne, aby być mylone z wynikami kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7ad07-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="7ad07-139">Ponieważ #7 kwerendy zwraca pojedynczą wartość, a nie kolekcję, kwerenda jest wykonywana natychmiast.</span><span class="sxs-lookup"><span data-stu-id="7ad07-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="7ad07-140">Poprzednie zapytanie można zapisać przy użyciu `var`niejawnego wpisywania z , w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ad07-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="7ad07-141">Może być napisany w składni metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ad07-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="7ad07-142">Można go zapisać przy użyciu jawnego wpisywania, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ad07-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="7ad07-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ad07-143">See also</span></span>

- [<span data-ttu-id="7ad07-144">Instruktaż: Pisanie zapytań w C #</span><span class="sxs-lookup"><span data-stu-id="7ad07-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="7ad07-145">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7ad07-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="7ad07-146">gdzie klauzula</span><span class="sxs-lookup"><span data-stu-id="7ad07-146">where clause</span></span>](../language-reference/keywords/where-clause.md)
