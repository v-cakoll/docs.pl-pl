---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory zestawów (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: d7b5729c8213a0d6c38dedb8244faee60e4f8587
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538651"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="c10fe-102">Przykłady składni zapytania oparte na metodzie: Operatory zestawów (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c10fe-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="c10fe-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, i <xref:System.Linq.Enumerable.Union%2A> operatory do wykonywania operacji na podstawie wartości porównania na zestawy wierszy danych.[ Trwa ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) zobacz [porównywanie wierszy danych](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) więcej informacji na temat <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="c10fe-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="c10fe-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="c10fe-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="c10fe-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c10fe-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c10fe-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c10fe-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="c10fe-107">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu LINQ to DataSet w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c10fe-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="c10fe-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="c10fe-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="c10fe-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c10fe-109">Example</span></span>  
 <span data-ttu-id="c10fe-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Distinct%2A> metodę, aby usunąć zduplikowane elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c10fe-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="c10fe-111">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="c10fe-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="c10fe-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c10fe-112">Example</span></span>  
 <span data-ttu-id="c10fe-113">W tym przykładzie użyto <xref:System.Linq.Enumerable.Except%2A> metodę, aby zwrócić kontakty, które pojawiają się w pierwszej tabeli, ale nie w ciągu sekundy.</span><span class="sxs-lookup"><span data-stu-id="c10fe-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="c10fe-114">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="c10fe-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="c10fe-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c10fe-115">Example</span></span>  
 <span data-ttu-id="c10fe-116">W tym przykładzie użyto <xref:System.Linq.Enumerable.Intersect%2A> metodę, aby zwrócić kontakty, które pojawiają się w obu tabelach.</span><span class="sxs-lookup"><span data-stu-id="c10fe-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="c10fe-117">Union</span><span class="sxs-lookup"><span data-stu-id="c10fe-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="c10fe-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c10fe-118">Example</span></span>  
 <span data-ttu-id="c10fe-119">W tym przykładzie użyto <xref:System.Linq.Enumerable.Union%2A> metodę, aby zwrócić unikatowy kontakty z jednej z dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="c10fe-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="c10fe-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c10fe-120">See also</span></span>
- [<span data-ttu-id="c10fe-121">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c10fe-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="c10fe-122">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c10fe-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="c10fe-123">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="c10fe-123">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
