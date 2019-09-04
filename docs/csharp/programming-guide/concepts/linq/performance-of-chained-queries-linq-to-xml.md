---
title: Wydajność zapytań łańcuchowych (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253122"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="81e9c-102">Wydajność zapytań łańcuchowych (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="81e9c-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="81e9c-103">Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że kwerendy łańcuchowe mogą wykonywać, a także pojedyncze, bardziej skomplikowane zapytania.</span><span class="sxs-lookup"><span data-stu-id="81e9c-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="81e9c-104">Zapytanie łańcuchowe jest kwerendą, która używa innego zapytania jako źródła.</span><span class="sxs-lookup"><span data-stu-id="81e9c-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="81e9c-105">Na przykład, w poniższym prostym kodzie, `query2` ma `query1` jako Źródło:</span><span class="sxs-lookup"><span data-stu-id="81e9c-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="81e9c-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="81e9c-106">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="81e9c-107">To zapytanie łańcuchowe zapewnia ten sam profil wydajności co iteracja w połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="81e9c-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="81e9c-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Oś ma zasadniczo taką samą wydajność jak iteracja w połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="81e9c-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="81e9c-109"><xref:System.Xml.Linq.XContainer.Elements%2A>jest zaimplementowany jako iterator z odroczonym wykonaniem.</span><span class="sxs-lookup"><span data-stu-id="81e9c-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="81e9c-110">Oznacza to, że wykonuje kilka zadań oprócz iteracji przez połączoną listę, na przykład przydzielanie obiektu iteratora i śledzenie stanu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="81e9c-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="81e9c-111">Ta czynność może zostać podzielona na dwie kategorie: pracy, która jest wykonywana w chwili, gdy iterator jest skonfigurowany, i pracy, która jest wykonywana podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="81e9c-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="81e9c-112">Konfiguracja pracy jest małą, stałą ilością pracy i pracy wykonywanej podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="81e9c-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="81e9c-113">W programie `query1` <xref:System.Linq.Enumerable.Where%2A> klauzula powoduje wywołanie metody. `where`</span><span class="sxs-lookup"><span data-stu-id="81e9c-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="81e9c-114">Ta metoda jest również zaimplementowana jako iterator.</span><span class="sxs-lookup"><span data-stu-id="81e9c-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="81e9c-115">Konfiguracja zadań składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz normalnej konfiguracji iteratora.</span><span class="sxs-lookup"><span data-stu-id="81e9c-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="81e9c-116">Dla każdej iteracji delegat jest wywoływany, aby wykonać predykat.</span><span class="sxs-lookup"><span data-stu-id="81e9c-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="81e9c-117">Konfiguracja pracy i pracy wykonanej podczas każdej iteracji jest podobna do wykonanej pracy podczas iteracji na osi.</span><span class="sxs-lookup"><span data-stu-id="81e9c-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="81e9c-118">W `query1`programie klauzula SELECT powoduje, że zapytanie <xref:System.Linq.Enumerable.Select%2A> wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="81e9c-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="81e9c-119">Ta metoda ma ten sam profil wydajności co <xref:System.Linq.Enumerable.Where%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="81e9c-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="81e9c-120">W `query2`programie `select` obie klauzule i klauzula mają taki sam profil wydajności jak w `query1`. `where`</span><span class="sxs-lookup"><span data-stu-id="81e9c-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="81e9c-121">Iteracja w programie `query2` jest w związku z tym bezpośrednio proporcjonalna do liczby elementów w źródle pierwszego zapytania, czyli czasu liniowego.</span><span class="sxs-lookup"><span data-stu-id="81e9c-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="81e9c-122">Odpowiadający przykład Visual Basic będzie miał ten sam profil wydajności.</span><span class="sxs-lookup"><span data-stu-id="81e9c-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="81e9c-123">Aby uzyskać więcej informacji na temat iteratorów, zobacz [Yield](../../../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="81e9c-123">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="81e9c-124">Aby zapoznać się z bardziej szczegółowym samouczkiem dotyczącym łączenia [zapytań, zobacz Samouczek: Łączenie łańcuchowe zapytań](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="81e9c-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
