---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory konwersji (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 4828aafc4e19b9a9d1c74a215dc255caa2dae01d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518773"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="7d5e7-102">Przykłady składni zapytania oparte na metodzie: Operatory konwersji (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7d5e7-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="7d5e7-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, i <xref:System.Linq.Enumerable.ToList%2A> metody, aby natychmiast wykonać wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="7d5e7-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7d5e7-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7d5e7-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7d5e7-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="7d5e7-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7d5e7-107">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7d5e7-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="7d5e7-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="7d5e7-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="7d5e7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d5e7-109">Example</span></span>  
 <span data-ttu-id="7d5e7-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby od razu oceny sekwencji do tablicy.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="7d5e7-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="7d5e7-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="7d5e7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d5e7-112">Example</span></span>  
 <span data-ttu-id="7d5e7-113">W tym przykładzie użyto <xref:System.Linq.Enumerable.ToDictionary%2A> metodę, aby od razu ocenić sekwencji i powiązane wyrażenia klucza do słownika.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="7d5e7-114">Tolist —</span><span class="sxs-lookup"><span data-stu-id="7d5e7-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="7d5e7-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d5e7-115">Example</span></span>  
 <span data-ttu-id="7d5e7-116">W tym przykładzie użyto <xref:System.Linq.Enumerable.ToList%2A> metodę, aby od razu oceny sekwencji do <xref:System.Collections.Generic.List%601>, gdzie `T` typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="7d5e7-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="7d5e7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d5e7-117">See Also</span></span>  
 [<span data-ttu-id="7d5e7-118">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7d5e7-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="7d5e7-119">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7d5e7-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="7d5e7-120">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="7d5e7-120">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
