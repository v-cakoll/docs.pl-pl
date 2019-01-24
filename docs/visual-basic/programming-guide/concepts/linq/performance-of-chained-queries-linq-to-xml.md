---
title: Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8a4893a000bc80fa703e7d47aa5d73f02b95a8ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601873"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="6cb14-102">Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cb14-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6cb14-103">Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że zapytań łańcuchowych może wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="6cb14-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="6cb14-104">Łańcuchowe zapytań jest zapytanie, które używa innego zapytania jako źródło.</span><span class="sxs-lookup"><span data-stu-id="6cb14-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="6cb14-105">Na przykład w poniższym kodzie prosty `query2` ma `query1` jako źródło:</span><span class="sxs-lookup"><span data-stu-id="6cb14-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 <span data-ttu-id="6cb14-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6cb14-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="6cb14-107">To zapytanie łańcuchowych zawiera ten sam profil wydajności jako iteracji przez listę połączoną.</span><span class="sxs-lookup"><span data-stu-id="6cb14-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="6cb14-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracji przez listę połączoną.</span><span class="sxs-lookup"><span data-stu-id="6cb14-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="6cb14-109"><xref:System.Xml.Linq.XContainer.Elements%2A> jest implementowany jako iterator za pomocą odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="6cb14-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="6cb14-110">Oznacza to, że robi jakąś pracę dodatkowo do iteracji w połączonej listy, takich jak obiekt iteratora do przydzielania i śledzeniu stanu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6cb14-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="6cb14-111">Tę pracę można podzielić na dwie kategorie: prac, które odbywa się w czasie, o których iterator który jest skonfigurowany i czynności, które odbywa się podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="6cb14-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="6cb14-112">Praca Instalatora jest mały, stały ilość pracy i Praca wykonana podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="6cb14-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="6cb14-113">W `query1`, `Where` klauzuli powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6cb14-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="6cb14-114">Ta metoda jest również implementowana jako iterator.</span><span class="sxs-lookup"><span data-stu-id="6cb14-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="6cb14-115">Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz zwykłej instalacji dla iteratora.</span><span class="sxs-lookup"><span data-stu-id="6cb14-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="6cb14-116">Z każdą iteracją delegat jest wywoływana, aby wykonać predykat.</span><span class="sxs-lookup"><span data-stu-id="6cb14-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="6cb14-117">Praca Instalatora i pracy wykonanej w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.</span><span class="sxs-lookup"><span data-stu-id="6cb14-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="6cb14-118">W `query1`, klauzula select powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6cb14-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="6cb14-119">Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6cb14-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="6cb14-120">W `query2`, zarówno `Where` klauzuli i `Select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.</span><span class="sxs-lookup"><span data-stu-id="6cb14-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="6cb14-121">Iteracja przez `query2` jest zatem bezpośrednio proporcjonalnie do liczby elementów w źródle pierwsze zapytanie, innymi słowy, liniowo.</span><span class="sxs-lookup"><span data-stu-id="6cb14-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb14-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cb14-122">See also</span></span>
- [<span data-ttu-id="6cb14-123">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cb14-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
