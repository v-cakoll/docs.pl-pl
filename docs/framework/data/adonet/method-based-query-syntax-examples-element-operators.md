---
title: 'Przykłady składni kwerend opartych na metodzie: Operatory elementów (LINQ do DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149510"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="a41f8-102">Przykłady składni kwerend opartych na metodzie: Operatory elementów (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="a41f8-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="a41f8-103">Przykłady w tym temacie pokazano, <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.ElementAt%2A> jak używać <xref:System.Data.DataRow> i <xref:System.Data.DataSet> metody, aby uzyskać elementy z przy użyciu składni wyrażenia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a41f8-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="a41f8-104">Metoda `FillDataSet` używana w tych przykładach jest określona w [loading data into a DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="a41f8-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="a41f8-105">Przykłady w tym temacie używają kontaktów, adres, produkt, SalesOrderHeader i SalesOrderDetail tabel w adventureworks przykładowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a41f8-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a41f8-106">Przykłady w tym temacie `using` / `Imports` używają następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="a41f8-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="a41f8-107">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie projektu LINQ do zestawu danych w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a41f8-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="a41f8-108">Elementat</span><span class="sxs-lookup"><span data-stu-id="a41f8-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="a41f8-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a41f8-109">Example</span></span>  
 <span data-ttu-id="a41f8-110">W tym przykładzie <xref:System.Linq.Enumerable.ElementAt%2A> użyto metody do `PostalCode` pobrania piątego adresu, gdzie == "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="a41f8-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="a41f8-111">First</span><span class="sxs-lookup"><span data-stu-id="a41f8-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="a41f8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a41f8-112">Example</span></span>  
 <span data-ttu-id="a41f8-113">W tym przykładzie <xref:System.Linq.Enumerable.First%2A> użyto metody do zwrócenia pierwszego kontaktu, którego imię to "Brooke".</span><span class="sxs-lookup"><span data-stu-id="a41f8-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="a41f8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a41f8-114">See also</span></span>

- [<span data-ttu-id="a41f8-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a41f8-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="a41f8-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a41f8-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="a41f8-117">Omówienie standardowych operatorów kwerend (C#)</span><span class="sxs-lookup"><span data-stu-id="a41f8-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a41f8-118">Omówienie standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a41f8-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
