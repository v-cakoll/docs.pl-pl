---
title: Wydajność kwerend łańcuchowa (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="4a857-102">Wydajność kwerend łańcuchowa (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4a857-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4a857-103">Jest jedną z najważniejszych zalet LINQ (i LINQ do XML), czy łańcuchowa zapytania można wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="4a857-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="4a857-104">Łańcuchowa zapytanie jest kwerenda, która używa innego zapytania jako źródło.</span><span class="sxs-lookup"><span data-stu-id="4a857-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="4a857-105">Na przykład w poniższym kodzie proste `query2` ma `query1` jako źródło:</span><span class="sxs-lookup"><span data-stu-id="4a857-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
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
  
 <span data-ttu-id="4a857-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4a857-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="4a857-107">To zapytanie łańcuchowa zawiera ten sam profil wydajności jako iteracja listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="4a857-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="4a857-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracja listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="4a857-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="4a857-109"><xref:System.Xml.Linq.XContainer.Elements%2A> jest implementowany jako iteratora o wykonanie odroczone.</span><span class="sxs-lookup"><span data-stu-id="4a857-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="4a857-110">Oznacza to, że go działa niektórych dodatkowo iteracja listy połączonej, takich jak przydzielanie obiektu iteratora i rejestrowanie informacji o stanie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="4a857-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="4a857-111">Tę pracę można podzielić na dwie kategorie: pracy, którą można wykonać w czasie, o których skonfigurowano iteratora i pracy, który jest wykonywane podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="4a857-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="4a857-112">Praca Instalatora jest mały, stały ilość pracy oraz pracy wykonanej w każdej iteracji jest proporcjonalny do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="4a857-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="4a857-113">W `query1`, `where` klauzuli powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4a857-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="4a857-114">Ta metoda również jest implementowany jako iteratora.</span><span class="sxs-lookup"><span data-stu-id="4a857-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="4a857-115">Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda, a także normalnej konfiguracji dla iteratora.</span><span class="sxs-lookup"><span data-stu-id="4a857-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="4a857-116">A każda iteracja delegat nazywa się do wykonywania predykatu.</span><span class="sxs-lookup"><span data-stu-id="4a857-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="4a857-117">Praca Instalatora i pracy w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.</span><span class="sxs-lookup"><span data-stu-id="4a857-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="4a857-118">W `query1`, klauzula select powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4a857-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="4a857-119">Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4a857-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="4a857-120">W `query2`, oba `where` klauzuli i `select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.</span><span class="sxs-lookup"><span data-stu-id="4a857-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="4a857-121">Iteracja przez `query2` jest bezpośrednio proporcjonalne do liczby elementów w źródle pierwszy, innymi słowy, liniowego czas kwerendy.</span><span class="sxs-lookup"><span data-stu-id="4a857-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="4a857-122">Odpowiedni przykład Visual Basic będzie mieć ten sam profil wydajności.</span><span class="sxs-lookup"><span data-stu-id="4a857-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="4a857-123">Aby uzyskać więcej informacji dotyczących Iteratory, zobacz [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="4a857-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="4a857-124">Bardziej szczegółowy samouczek dotyczący razem łańcucha zapytań, zobacz [samouczek: tworzenie łańcuchów zapytań razem](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span><span class="sxs-lookup"><span data-stu-id="4a857-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a857-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a857-125">See Also</span></span>  
 [<span data-ttu-id="4a857-126">Wydajność (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4a857-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
