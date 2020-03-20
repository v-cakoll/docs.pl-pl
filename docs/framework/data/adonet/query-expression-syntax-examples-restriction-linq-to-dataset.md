---
title: 'Przykłady składni wyrażenia kwerendy: ograniczenie (LINQ do dataset)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 6ec4eac6c0fb2d044e429e88d50c619aa38de4b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149196"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="37dac-102">Przykłady składni wyrażenia kwerendy: ograniczenie (LINQ do dataset)</span><span class="sxs-lookup"><span data-stu-id="37dac-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="37dac-103">Przykłady w tym temacie pokazują, <xref:System.Linq.Enumerable.Where%2A> jak użyć <xref:System.Data.DataSet> metody do kwerendy przy użyciu składni wyrażenia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="37dac-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="37dac-104">Metoda `FillDataSet` używana w tych przykładach jest określona w [loading data into a DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="37dac-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="37dac-105">Przykłady w tym temacie używają kontaktów, adres, produkt, SalesOrderHeader i SalesOrderDetail tabel w adventureworks przykładowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="37dac-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="37dac-106">Przykłady w tym temacie `using` / `Imports` używają następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="37dac-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="37dac-107">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie projektu LINQ do zestawu danych w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="37dac-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="37dac-108">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="37dac-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="37dac-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="37dac-109">Example</span></span>  
 <span data-ttu-id="37dac-110">W tym przykładzie zwraca wszystkie zamówienia online.</span><span class="sxs-lookup"><span data-stu-id="37dac-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="37dac-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="37dac-111">Example</span></span>  
 <span data-ttu-id="37dac-112">W tym przykładzie zwraca zamówienia, w których ilość zamówienia jest większa niż 2 i mniejsza niż 6.</span><span class="sxs-lookup"><span data-stu-id="37dac-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="37dac-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="37dac-113">Example</span></span>  
 <span data-ttu-id="37dac-114">W tym przykładzie zwraca wszystkie produkty w kolorze czerwonym.</span><span class="sxs-lookup"><span data-stu-id="37dac-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="37dac-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="37dac-115">Example</span></span>  
 <span data-ttu-id="37dac-116">W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> użyto metody, aby znaleźć zamówienia, które zostały wykonane po <xref:System.Data.DataRow.GetChildRows%2A> 1 grudnia 2002 r., a następnie używa metody, aby uzyskać szczegółowe informacje dla każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="37dac-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="37dac-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37dac-117">See also</span></span>

- [<span data-ttu-id="37dac-118">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="37dac-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="37dac-119">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="37dac-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="37dac-120">Omówienie standardowych operatorów kwerend (C#)</span><span class="sxs-lookup"><span data-stu-id="37dac-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="37dac-121">Omówienie standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37dac-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
