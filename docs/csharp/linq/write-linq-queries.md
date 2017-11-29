---
title: "Pisanie zapytań LINQ w C#"
description: "Jak pisać zapytania."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: f3efbfd232bd7e19d3db56289f57724c71dca064
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="ae408-104">Pisanie zapytań LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="ae408-104">Write LINQ queries in C#</span></span>

<span data-ttu-id="ae408-105">W tym temacie przedstawiono trzy sposoby, w których można napisać zapytanie LINQ w C#:</span><span class="sxs-lookup"><span data-stu-id="ae408-105">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="ae408-106">Należy użyć składni zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae408-106">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="ae408-107">Należy użyć składni metody.</span><span class="sxs-lookup"><span data-stu-id="ae408-107">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="ae408-108">Użyj kombinacji składnia zapytania a składnia metody.</span><span class="sxs-lookup"><span data-stu-id="ae408-108">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="ae408-109">W poniższych przykładach pokazano kilka prostych zapytań LINQ za pomocą każdego z podejść wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="ae408-109">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="ae408-110">Ogólnie rzecz biorąc reguła jest używana (1), jeśli to możliwe i (2) i (3), jeśli zajdzie potrzeba.</span><span class="sxs-lookup"><span data-stu-id="ae408-110">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae408-111">Kwerendy te działają na prosty kolekcje w pamięci; Podstawowa składnia jest jednak używaną w składniku LINQ to Entities i LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="ae408-111">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae408-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae408-112">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="ae408-113">Składnia zapytania</span><span class="sxs-lookup"><span data-stu-id="ae408-113">Query syntax</span></span>  
 <span data-ttu-id="ae408-114">Zalecanym sposobem zapisu większości kwerend jest użycie *Składnia kwerendy* utworzyć *wyrażenia zapytań*.</span><span class="sxs-lookup"><span data-stu-id="ae408-114">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="ae408-115">W poniższym przykładzie przedstawiono trzy wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae408-115">The following example shows three query expressions.</span></span> <span data-ttu-id="ae408-116">Pierwsze wyrażenie zapytanie pokazuje, jak filtrowanie lub ograniczanie wyników, stosując warunków z `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ae408-116">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="ae408-117">Zwraca wszystkie elementy w sekwencji źródłowej, w których wartości są większe niż 7 lub mniej niż 3.</span><span class="sxs-lookup"><span data-stu-id="ae408-117">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="ae408-118">Drugie wyrażenie pokazano, jak kolejność zwracanych wyników.</span><span class="sxs-lookup"><span data-stu-id="ae408-118">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="ae408-119">Trzeci wyrażenie pokazano, jak grupowanie wyników według klucza.</span><span class="sxs-lookup"><span data-stu-id="ae408-119">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="ae408-120">Ta kwerenda zwraca dwie grupy oparte na pierwszą literę słowa.</span><span class="sxs-lookup"><span data-stu-id="ae408-120">This query returns two groups based on the first letter of the word.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 <span data-ttu-id="ae408-121">Należy zauważyć, że typ zapytania <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ae408-121">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="ae408-122">Wszystkie te zapytania można można pisać przy użyciu `var` jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ae408-122">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="ae408-123">W poprzednim przykładzie zapytania nie faktycznie wykonuj dopóki iteracja zmienną zapytania w `foreach` lub innych instrukcję.</span><span class="sxs-lookup"><span data-stu-id="ae408-123">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="ae408-124">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="ae408-124">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae408-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae408-125">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="ae408-126">Składnia metody</span><span class="sxs-lookup"><span data-stu-id="ae408-126">Method syntax</span></span>  
 <span data-ttu-id="ae408-127">Niektóre operacje kwerend muszą być wyrażone jako wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="ae408-127">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="ae408-128">Najbardziej typowe metody te są tymi, które zwraca pojedyncze wartości liczbowe, takie jak <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ae408-128">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="ae408-129">Te metody zawsze należy wywołać ostatniego w każde zapytanie operacji ponieważ reprezentuje pojedynczą wartość i nie może służyć jako źródło dla operacji zapytania dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="ae408-129">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="ae408-130">W poniższym przykładzie pokazano wywołanie metody w wyrażeniu zapytania:</span><span class="sxs-lookup"><span data-stu-id="ae408-130">The following example shows a method call in a query expression:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="ae408-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae408-131">Example</span></span>  
 <span data-ttu-id="ae408-132">Jeśli metoda ma parametry akcji lub Func, te są udostępniane w formie [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) wyrażenia, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ae408-132">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 <span data-ttu-id="ae408-133">W poprzednich zapytań tylko zapytania #4 wykonuje natychmiast.</span><span class="sxs-lookup"><span data-stu-id="ae408-133">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="ae408-134">Jest to spowodowane zwraca pojedynczą wartość, a nie ogólnego <xref:System.Collections.Generic.IEnumerable%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ae408-134">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="ae408-135">Tej metody ma używać `foreach` Aby obliczyć wartość.</span><span class="sxs-lookup"><span data-stu-id="ae408-135">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="ae408-136">Każdy z poprzednich zapytań można pisać przy użyciu niejawnego wpisaniu [var](../language-reference/keywords/var.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ae408-136">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="ae408-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae408-137">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="ae408-138">Mieszane składnia zapytania i metody</span><span class="sxs-lookup"><span data-stu-id="ae408-138">Mixed query and method syntax</span></span>  
 <span data-ttu-id="ae408-139">W tym przykładzie pokazano, jak używać składni metody wyników klauzuli zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae408-139">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="ae408-140">Tylko ujmij wyrażenie kwerendy w nawiasy, a następnie zastosować operator kropki i wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="ae408-140">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="ae408-141">W poniższym przykładzie zapytanie #7 zwraca liczbę cyfr, którego wartość wynosi od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="ae408-141">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="ae408-142">Ogólnie rzecz biorąc jednak warto użyć zmiennej drugi do przechowywania wyniku wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="ae408-142">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="ae408-143">W ten sposób zapytanie jest mniej prawdopodobne różni się od wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae408-143">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 <span data-ttu-id="ae408-144">Ponieważ zapytania #7 zwraca pojedynczą wartość i nie jest kolekcją, natychmiast wykonuje zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae408-144">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="ae408-145">Poprzednie zapytanie można pisać przy użyciu niejawnego wpisaniu `var`w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ae408-145">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="ae408-146">Go może być zapisany w składni metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ae408-146">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="ae408-147">Może być zapisany przy użyciu wpisywać jawne, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ae408-147">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae408-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae408-148">See Also</span></span>  
  <span data-ttu-id="ae408-149">[Wskazówki: Pisanie zapytań w języku C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="ae408-149">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 [<span data-ttu-id="ae408-150">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="ae408-150">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="ae408-151">gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="ae408-151">where clause</span></span>](../language-reference/keywords/where-clause.md)
