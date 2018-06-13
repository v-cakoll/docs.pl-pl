---
title: Wydajność kwerend łańcuchowa (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: d390fc0e45967cd98697320eb6f61a51cb1c19da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645710"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="7ed66-102">Wydajność kwerend łańcuchowa (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ed66-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7ed66-103">Jest jedną z najważniejszych zalet LINQ (i LINQ do XML), czy łańcuchowa zapytania można wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="7ed66-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="7ed66-104">Łańcuchowa zapytanie jest kwerenda, która używa innego zapytania jako źródło.</span><span class="sxs-lookup"><span data-stu-id="7ed66-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="7ed66-105">Na przykład w poniższym kodzie proste `query2` ma `query1` jako źródło:</span><span class="sxs-lookup"><span data-stu-id="7ed66-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 <span data-ttu-id="7ed66-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7ed66-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="7ed66-107">To zapytanie łańcuchowa zawiera ten sam profil wydajności jako iteracja listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="7ed66-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="7ed66-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracja listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="7ed66-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="7ed66-109"><xref:System.Xml.Linq.XContainer.Elements%2A> jest implementowany jako iteratora o wykonanie odroczone.</span><span class="sxs-lookup"><span data-stu-id="7ed66-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="7ed66-110">Oznacza to, że go działa niektórych dodatkowo iteracja listy połączonej, takich jak przydzielanie obiektu iteratora i rejestrowanie informacji o stanie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="7ed66-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="7ed66-111">Tę pracę można podzielić na dwie kategorie: pracy, którą można wykonać w czasie, o których skonfigurowano iteratora i pracy, który jest wykonywane podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="7ed66-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="7ed66-112">Praca Instalatora jest mały, stały ilość pracy oraz pracy wykonanej w każdej iteracji jest proporcjonalny do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="7ed66-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="7ed66-113">W `query1`, `Where` klauzuli powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7ed66-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="7ed66-114">Ta metoda również jest implementowany jako iteratora.</span><span class="sxs-lookup"><span data-stu-id="7ed66-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="7ed66-115">Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda, a także normalnej konfiguracji dla iteratora.</span><span class="sxs-lookup"><span data-stu-id="7ed66-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="7ed66-116">A każda iteracja delegat nazywa się do wykonywania predykatu.</span><span class="sxs-lookup"><span data-stu-id="7ed66-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="7ed66-117">Praca Instalatora i pracy w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.</span><span class="sxs-lookup"><span data-stu-id="7ed66-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="7ed66-118">W `query1`, klauzula select powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7ed66-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="7ed66-119">Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7ed66-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="7ed66-120">W `query2`, oba `Where` klauzuli i `Select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.</span><span class="sxs-lookup"><span data-stu-id="7ed66-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="7ed66-121">Iteracja przez `query2` jest bezpośrednio proporcjonalne do liczby elementów w źródle pierwszy, innymi słowy, liniowego czas kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7ed66-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed66-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ed66-122">See Also</span></span>  
 [<span data-ttu-id="7ed66-123">Wydajność (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ed66-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
