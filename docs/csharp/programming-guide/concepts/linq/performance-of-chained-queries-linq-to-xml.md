---
title: Wydajność zapytań łańcuchowych (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253122"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="7198d-102">Wydajność zapytań łańcuchowych (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7198d-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="7198d-103">Jedną z najważniejszych zalet LINQ (i LINQ do XML) jest to, że zapytania łańcuchowe mogą wykonywać, a także pojedyncze większe, bardziej skomplikowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="7198d-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="7198d-104">Kwerenda łańcuchowa to kwerenda, która używa innej kwerendy jako źródła.</span><span class="sxs-lookup"><span data-stu-id="7198d-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="7198d-105">Na przykład w następującym `query2` prostym `query1` kodzie ma jako źródło:</span><span class="sxs-lookup"><span data-stu-id="7198d-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

<span data-ttu-id="7198d-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7198d-106">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="7198d-107">Ta kwerenda łańcuchowa zapewnia ten sam profil wydajności, co iteracji za pośrednictwem listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="7198d-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="7198d-108">Oś <xref:System.Xml.Linq.XContainer.Elements%2A> ma zasadniczo taką samą wydajność jak iteracji za pośrednictwem listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="7198d-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="7198d-109"><xref:System.Xml.Linq.XContainer.Elements%2A>jest implementowana jako iterator z odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="7198d-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="7198d-110">Oznacza to, że wykonuje pewną pracę oprócz iteracji za pośrednictwem listy połączonej, takich jak przydzielanie obiektu iteratora i śledzenie stanu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7198d-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="7198d-111">Tę pracę można podzielić na dwie kategorie: pracę wykonywaną w momencie skonfigurowania iterator i pracę wykonywaną podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="7198d-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="7198d-112">Praca konfiguratowana jest niewielką, stałą ilością pracy, a praca wykonywana podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="7198d-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="7198d-113">W `query1`klauzuli `where` powoduje, że <xref:System.Linq.Enumerable.Where%2A> kwerenda do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="7198d-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="7198d-114">Ta metoda jest również implementowana jako iterator.</span><span class="sxs-lookup"><span data-stu-id="7198d-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="7198d-115">Praca konfiguratorna polega na uprzedzeniu delegata, który będzie odwoływał się do wyrażenia lambda, a także normalnej konfiguracji sterująca.</span><span class="sxs-lookup"><span data-stu-id="7198d-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="7198d-116">Z każdą iteracją pełnomocnik jest wywoływany do wykonania predykatu.</span><span class="sxs-lookup"><span data-stu-id="7198d-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="7198d-117">Praca konfiguratora i praca wykonywana podczas każdej iteracji jest podobna do pracy wykonanej podczas iteracji przez oś.</span><span class="sxs-lookup"><span data-stu-id="7198d-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="7198d-118">W `query1`programie select klauzula powoduje, <xref:System.Linq.Enumerable.Select%2A> że kwerenda wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="7198d-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="7198d-119">Ta metoda ma ten sam <xref:System.Linq.Enumerable.Where%2A> profil wydajności co metoda.</span><span class="sxs-lookup"><span data-stu-id="7198d-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="7198d-120">W `query2`, `where` zarówno klauzula, jak i klauzula `select` mają taki sam profil wydajności jak w `query1`.</span><span class="sxs-lookup"><span data-stu-id="7198d-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="7198d-121">Iteracja jest `query2` zatem bezpośrednio proporcjonalna do liczby elementów w źródle pierwszego zapytania, innymi słowy, czas liniowy.</span><span class="sxs-lookup"><span data-stu-id="7198d-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="7198d-122">Odpowiedni przykład języka Visual Basic będzie miał ten sam profil wydajności.</span><span class="sxs-lookup"><span data-stu-id="7198d-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="7198d-123">Aby uzyskać więcej informacji na temat iteratorów, zobacz [wydajność](../../../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="7198d-123">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="7198d-124">Aby uzyskać bardziej szczegółowy samouczek dotyczący łączenia zapytań, zobacz [Samouczek: Łączenie zapytań razem](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7198d-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
