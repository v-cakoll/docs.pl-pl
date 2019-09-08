---
title: 'Przykłady składni wyrażeń zapytania: Ograniczenie (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 04a7b2027ac956d14086f94527b10d253749949d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794664"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="d8135-102">Przykłady składni wyrażeń zapytania: Ograniczenie (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d8135-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="d8135-103">W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.Where%2A> jak używać metody do <xref:System.Data.DataSet> wykonywania zapytań przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="d8135-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="d8135-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="d8135-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d8135-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d8135-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d8135-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="d8135-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]        
  
 <span data-ttu-id="d8135-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d8135-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="d8135-108">Gdzie</span><span class="sxs-lookup"><span data-stu-id="d8135-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="d8135-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8135-109">Example</span></span>  
 <span data-ttu-id="d8135-110">Ten przykład zwraca wszystkie zamówienia online.</span><span class="sxs-lookup"><span data-stu-id="d8135-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]     
  
### <a name="example"></a><span data-ttu-id="d8135-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8135-111">Example</span></span>  
 <span data-ttu-id="d8135-112">Ten przykład zwraca zamówienia, w których ilość zamówienia jest większa niż 2 i mniejsza niż 6.</span><span class="sxs-lookup"><span data-stu-id="d8135-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]     
  
### <a name="example"></a><span data-ttu-id="d8135-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8135-113">Example</span></span>  
 <span data-ttu-id="d8135-114">Ten przykład zwraca wszystkie kolorowe produkty.</span><span class="sxs-lookup"><span data-stu-id="d8135-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]     
  
### <a name="example"></a><span data-ttu-id="d8135-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8135-115">Example</span></span>  
 <span data-ttu-id="d8135-116">W <xref:System.Linq.Enumerable.Where%2A> tym przykładzie użyto metody, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2002, a następnie <xref:System.Data.DataRow.GetChildRows%2A> używa metody, aby uzyskać szczegółowe informacje dla poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="d8135-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]       
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="d8135-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8135-117">See also</span></span>

- [<span data-ttu-id="d8135-118">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d8135-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="d8135-119">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d8135-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="d8135-120">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="d8135-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d8135-121">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8135-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
