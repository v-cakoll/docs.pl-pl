---
title: Wydajność zapytań łańcuchowych (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 15cb9f94a49600c221b0cbb246743a79e9a5297b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353121"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="25512-102">Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25512-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="25512-103">Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że kwerendy łańcuchowe mogą wykonywać, a także pojedyncze, bardziej skomplikowane zapytania.</span><span class="sxs-lookup"><span data-stu-id="25512-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="25512-104">Zapytanie łańcuchowe jest kwerendą, która używa innego zapytania jako źródła.</span><span class="sxs-lookup"><span data-stu-id="25512-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="25512-105">Na przykład w poniższym prostym kodzie `query2` ma `query1` jako Źródło:</span><span class="sxs-lookup"><span data-stu-id="25512-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="25512-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="25512-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="25512-107">To zapytanie łańcuchowe zapewnia ten sam profil wydajności co iteracja w połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="25512-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="25512-108">Oś <xref:System.Xml.Linq.XContainer.Elements%2A> ma zasadniczo taką samą wydajność jak iteracja w połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="25512-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="25512-109"><xref:System.Xml.Linq.XContainer.Elements%2A> jest zaimplementowany jako iterator z odroczonym wykonywaniem.</span><span class="sxs-lookup"><span data-stu-id="25512-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="25512-110">Oznacza to, że wykonuje kilka zadań oprócz iteracji przez połączoną listę, na przykład przydzielanie obiektu iteratora i śledzenie stanu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="25512-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="25512-111">Ta czynność może zostać podzielona na dwie kategorie: pracy, która jest wykonywana w chwili, gdy iterator jest skonfigurowany, i pracy, która jest wykonywana podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="25512-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="25512-112">Konfiguracja pracy jest małą, stałą ilością pracy i pracy wykonywanej podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="25512-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="25512-113">W `query1`, klauzula `Where` powoduje wywołanie metody <xref:System.Linq.Enumerable.Where%2A> przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="25512-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="25512-114">Ta metoda jest również zaimplementowana jako iterator.</span><span class="sxs-lookup"><span data-stu-id="25512-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="25512-115">Konfiguracja zadań składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz normalnej konfiguracji iteratora.</span><span class="sxs-lookup"><span data-stu-id="25512-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="25512-116">Dla każdej iteracji delegat jest wywoływany, aby wykonać predykat.</span><span class="sxs-lookup"><span data-stu-id="25512-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="25512-117">Konfiguracja pracy i pracy wykonanej podczas każdej iteracji jest podobna do wykonanej pracy podczas iteracji na osi.</span><span class="sxs-lookup"><span data-stu-id="25512-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="25512-118">W `query1`, klauzula SELECT powoduje wywołanie metody <xref:System.Linq.Enumerable.Select%2A> przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="25512-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="25512-119">Ta metoda ma ten sam profil wydajności co Metoda <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="25512-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="25512-120">W `query2`zarówno klauzula `Where`, jak i klauzula `Select` mają taki sam profil wydajności jak w `query1`.</span><span class="sxs-lookup"><span data-stu-id="25512-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="25512-121">Iteracja przez `query2` jest więc bezpośrednio proporcjonalna do liczby elementów w źródle pierwszego zapytania, czyli czasu liniowego.</span><span class="sxs-lookup"><span data-stu-id="25512-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="25512-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25512-122">See also</span></span>

- [<span data-ttu-id="25512-123">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25512-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
