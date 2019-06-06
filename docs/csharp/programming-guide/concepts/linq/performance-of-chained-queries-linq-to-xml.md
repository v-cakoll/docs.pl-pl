---
title: Wydajność zapytań łańcuchowych (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 1ccb7dfec57a4aeea8329456084ca99f5ca3124d
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689995"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="67208-102">Wydajność zapytań łańcuchowych (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="67208-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="67208-103">Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że zapytań łańcuchowych może wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="67208-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="67208-104">Łańcuchowe zapytań jest zapytanie, które używa innego zapytania jako źródło.</span><span class="sxs-lookup"><span data-stu-id="67208-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="67208-105">Na przykład w poniższym kodzie prosty `query2` ma `query1` jako źródło:</span><span class="sxs-lookup"><span data-stu-id="67208-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="67208-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="67208-106">This example produces the following output:</span></span>

```
4
```

<span data-ttu-id="67208-107">To zapytanie łańcuchowych zawiera ten sam profil wydajności jako iteracji przez listę połączoną.</span><span class="sxs-lookup"><span data-stu-id="67208-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="67208-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracji przez listę połączoną.</span><span class="sxs-lookup"><span data-stu-id="67208-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="67208-109"><xref:System.Xml.Linq.XContainer.Elements%2A> jest implementowany jako iterator za pomocą odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="67208-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="67208-110">Oznacza to, że robi jakąś pracę dodatkowo do iteracji w połączonej listy, takich jak obiekt iteratora do przydzielania i śledzeniu stanu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="67208-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="67208-111">Tę pracę można podzielić na dwie kategorie: prac, które odbywa się w czasie, o których iterator który jest skonfigurowany i czynności, które odbywa się podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="67208-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="67208-112">Praca Instalatora jest mały, stały ilość pracy i Praca wykonana podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="67208-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="67208-113">W `query1`, `where` klauzuli powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="67208-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="67208-114">Ta metoda jest również implementowana jako iterator.</span><span class="sxs-lookup"><span data-stu-id="67208-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="67208-115">Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz zwykłej instalacji dla iteratora.</span><span class="sxs-lookup"><span data-stu-id="67208-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="67208-116">Z każdą iteracją delegat jest wywoływana, aby wykonać predykat.</span><span class="sxs-lookup"><span data-stu-id="67208-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="67208-117">Praca Instalatora i pracy wykonanej w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.</span><span class="sxs-lookup"><span data-stu-id="67208-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="67208-118">W `query1`, klauzula select powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="67208-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="67208-119">Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="67208-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="67208-120">W `query2`, zarówno `where` klauzuli i `select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.</span><span class="sxs-lookup"><span data-stu-id="67208-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="67208-121">Iteracja przez `query2` jest zatem bezpośrednio proporcjonalnie do liczby elementów w źródle pierwsze zapytanie, innymi słowy, liniowo.</span><span class="sxs-lookup"><span data-stu-id="67208-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="67208-122">Odpowiedni przykład Visual Basic będą mieć ten sam profil wydajności.</span><span class="sxs-lookup"><span data-stu-id="67208-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="67208-123">Aby uzyskać więcej informacji dotyczących iteratorów, zobacz [uzyskanie](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="67208-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="67208-124">Aby uzyskać bardziej szczegółowy samouczek dotyczący Łączenie łańcuchowe zapytań, zobacz [samouczka: Łączenie łańcuchowe zapytań](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="67208-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
