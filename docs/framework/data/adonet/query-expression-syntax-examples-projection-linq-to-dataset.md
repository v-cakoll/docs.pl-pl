---
title: 'Przykłady składni wyrażeń zapytania: Projekcja (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 9b8e898ce666b8b443521391eda67318bdf23915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783003"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="9cdaa-102">Przykłady składni wyrażeń zapytania: Projekcja (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9cdaa-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="9cdaa-103">W przykładach w tym temacie pokazano, jak używać <xref:System.Linq.Enumerable.Select%2A> metod <xref:System.Linq.Enumerable.SelectMany%2A> i do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="9cdaa-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="9cdaa-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9cdaa-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9cdaa-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="9cdaa-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9cdaa-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9cdaa-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="9cdaa-108">Wybierz</span><span class="sxs-lookup"><span data-stu-id="9cdaa-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="9cdaa-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cdaa-109">Example</span></span>  
 <span data-ttu-id="9cdaa-110">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Select%2A> aby zwrócić wszystkie wiersze `Product` z tabeli i wyświetlić nazwy produktów.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="9cdaa-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cdaa-111">Example</span></span>  
 <span data-ttu-id="9cdaa-112">Ten przykład używa <xref:System.Linq.Enumerable.Select%2A> do zwracania sekwencji tylko nazw produktów.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="9cdaa-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="9cdaa-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="9cdaa-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cdaa-114">Example</span></span>  
 <span data-ttu-id="9cdaa-115">W tym przykładzie `From …, …` zastosowano (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody), aby wybrać wszystkie zamówienia, `TotalDue` których wartość jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="9cdaa-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cdaa-116">Example</span></span>  
 <span data-ttu-id="9cdaa-117">W tym przykładzie `From …, …` użyto (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody), aby wybrać wszystkie zamówienia, w których zamówienie zostało wykonane w dniu 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="9cdaa-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cdaa-118">Example</span></span>  
 <span data-ttu-id="9cdaa-119">W tym przykładzie zastosowano `From …, …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody), aby wybrać wszystkie zamówienia, w których suma zamówienia jest większa niż 10000,00, i `From` używa przypisania, aby uniknąć podania łącznej liczby dwa razy.</span><span class="sxs-lookup"><span data-stu-id="9cdaa-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="9cdaa-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cdaa-120">See also</span></span>

- [<span data-ttu-id="9cdaa-121">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9cdaa-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="9cdaa-122">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9cdaa-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="9cdaa-123">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="9cdaa-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9cdaa-124">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cdaa-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
