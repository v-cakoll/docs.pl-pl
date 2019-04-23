---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory elementu (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: 49a2665240f5f35e0d4937e55c39eccf04b1444d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157251"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="07d59-102">Przykłady składni zapytania oparte na metodzie: Operatory elementu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="07d59-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="07d59-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.First%2A> i <xref:System.Linq.Enumerable.ElementAt%2A> metody w celu uzyskania <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="07d59-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="07d59-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="07d59-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="07d59-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="07d59-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="07d59-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="07d59-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]   
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]     

 <span data-ttu-id="07d59-107">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu LINQ to DataSet w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="07d59-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="07d59-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="07d59-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="07d59-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="07d59-109">Example</span></span>  
 <span data-ttu-id="07d59-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.ElementAt%2A> metodę, aby pobrać adres piąty gdzie `PostalCode` == "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="07d59-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]   
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]     
  
## <a name="first"></a><span data-ttu-id="07d59-111">pierwszy</span><span class="sxs-lookup"><span data-stu-id="07d59-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="07d59-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="07d59-112">Example</span></span>  
 <span data-ttu-id="07d59-113">W tym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> metodę, aby zwrócić których typu imię pierwszy kontakt jest "Brooke".</span><span class="sxs-lookup"><span data-stu-id="07d59-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]   
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)] 
  
## <a name="see-also"></a><span data-ttu-id="07d59-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07d59-114">See also</span></span>

- [<span data-ttu-id="07d59-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="07d59-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="07d59-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="07d59-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="07d59-117">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="07d59-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="07d59-118">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07d59-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
