---
title: 'Przykłady składni wyrażeń zapytania: Porządkowanie (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 932f5e4f6073844a951d06dabec45e5ff3e743bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782997"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="094ed-102">Przykłady składni wyrażeń zapytania: Porządkowanie (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="094ed-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="094ed-103">W przykładach w <xref:System.Linq.Enumerable.OrderBy%2A>tym temacie pokazano, jak używać metod, <xref:System.Linq.Enumerable.Reverse%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A>,, <xref:System.Linq.Enumerable.ThenByDescending%2A> i do wykonywania zapytań <xref:System.Data.DataSet> i kolejności wyników przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="094ed-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="094ed-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="094ed-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="094ed-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="094ed-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="094ed-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="094ed-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="094ed-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="094ed-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="094ed-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="094ed-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="094ed-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="094ed-109">Example</span></span>  
 <span data-ttu-id="094ed-110">Ten przykład używa <xref:System.Linq.Enumerable.OrderBy%2A> do zwracania listy kontaktów uporządkowanych według nazwiska.</span><span class="sxs-lookup"><span data-stu-id="094ed-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="094ed-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="094ed-111">Example</span></span>  
 <span data-ttu-id="094ed-112">Ten przykład używa <xref:System.Linq.Enumerable.OrderBy%2A> do sortowania listy kontaktów według długości nazwiska.</span><span class="sxs-lookup"><span data-stu-id="094ed-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="094ed-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="094ed-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="094ed-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="094ed-114">Example</span></span>  
 <span data-ttu-id="094ed-115">Ten przykład używa `orderby… descending` (`Order By … Descending`), <xref:System.Linq.Enumerable.OrderByDescending%2A> który jest odpowiednikiem metody, do sortowania cennika od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="094ed-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="094ed-116">Cofnięci</span><span class="sxs-lookup"><span data-stu-id="094ed-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="094ed-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="094ed-117">Example</span></span>  
 <span data-ttu-id="094ed-118">Ten przykład używa <xref:System.Linq.Enumerable.Reverse%2A> do tworzenia listy zamówień, których `OrderDate` wartość jest wcześniejsza niż 20 lutego 2002.</span><span class="sxs-lookup"><span data-stu-id="094ed-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="094ed-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="094ed-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="094ed-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="094ed-120">Example</span></span>  
 <span data-ttu-id="094ed-121">Ten przykład używa `OrderBy… Descending` , który jest odpowiednikiem <xref:System.Linq.Enumerable.ThenByDescending%2A> metody, do sortowania listy produktów, najpierw według nazwy, a następnie według cennika, od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="094ed-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="094ed-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="094ed-122">See also</span></span>

- [<span data-ttu-id="094ed-123">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="094ed-123">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="094ed-124">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="094ed-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="094ed-125">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="094ed-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="094ed-126">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="094ed-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
