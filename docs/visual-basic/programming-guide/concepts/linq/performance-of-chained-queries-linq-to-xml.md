---
title: Wydajność zapytań łańcuchowych (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 6b87f2744f663ebd45dceb036dcaac71b80765fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396392"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="28002-102">Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28002-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="28002-103">Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że kwerendy łańcuchowe mogą wykonywać, a także pojedyncze, bardziej skomplikowane zapytania.</span><span class="sxs-lookup"><span data-stu-id="28002-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="28002-104">Zapytanie łańcuchowe jest kwerendą, która używa innego zapytania jako źródła.</span><span class="sxs-lookup"><span data-stu-id="28002-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="28002-105">Na przykład, w poniższym prostym kodzie, `query2` ma `query1` jako Źródło:</span><span class="sxs-lookup"><span data-stu-id="28002-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="28002-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28002-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="28002-107">To zapytanie łańcuchowe zapewnia ten sam profil wydajności co iteracja w połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="28002-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="28002-108"><xref:System.Xml.Linq.XContainer.Elements%2A>Oś ma zasadniczo taką samą wydajność jak iteracja w połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="28002-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="28002-109"><xref:System.Xml.Linq.XContainer.Elements%2A>jest zaimplementowany jako iterator z odroczonym wykonaniem.</span><span class="sxs-lookup"><span data-stu-id="28002-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="28002-110">Oznacza to, że wykonuje kilka zadań oprócz iteracji przez połączoną listę, na przykład przydzielanie obiektu iteratora i śledzenie stanu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="28002-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="28002-111">Ta czynność może zostać podzielona na dwie kategorie: pracy, która jest wykonywana w chwili, gdy iterator jest skonfigurowany, i pracy, która jest wykonywana podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="28002-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="28002-112">Konfiguracja pracy jest małą, stałą ilością pracy i pracy wykonywanej podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="28002-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="28002-113">W programie `query1` `Where` klauzula powoduje wywołanie <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28002-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="28002-114">Ta metoda jest również zaimplementowana jako iterator.</span><span class="sxs-lookup"><span data-stu-id="28002-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="28002-115">Konfiguracja zadań składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz normalnej konfiguracji iteratora.</span><span class="sxs-lookup"><span data-stu-id="28002-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="28002-116">Dla każdej iteracji delegat jest wywoływany, aby wykonać predykat.</span><span class="sxs-lookup"><span data-stu-id="28002-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="28002-117">Konfiguracja pracy i pracy wykonanej podczas każdej iteracji jest podobna do wykonanej pracy podczas iteracji na osi.</span><span class="sxs-lookup"><span data-stu-id="28002-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="28002-118">W programie `query1` klauzula SELECT powoduje, że zapytanie wywołuje <xref:System.Linq.Enumerable.Select%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="28002-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="28002-119">Ta metoda ma ten sam profil wydajności co <xref:System.Linq.Enumerable.Where%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="28002-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="28002-120">W programie `query2` obie `Where` klauzule i `Select` klauzula mają taki sam profil wydajności jak w `query1` .</span><span class="sxs-lookup"><span data-stu-id="28002-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="28002-121">Iteracja w programie `query2` jest w związku z tym bezpośrednio proporcjonalna do liczby elementów w źródle pierwszego zapytania, czyli czasu liniowego.</span><span class="sxs-lookup"><span data-stu-id="28002-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="28002-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28002-122">See also</span></span>

- [<span data-ttu-id="28002-123">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28002-123">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
