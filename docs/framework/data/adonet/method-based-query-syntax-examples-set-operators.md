---
title: 'Przykłady składni zapytania oparte na metodzie: Ustaw operatory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783578"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="2c469-102">Przykłady składni zapytania oparte na metodzie: Ustaw operatory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2c469-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="2c469-103">W przykładach w <xref:System.Linq.Enumerable.Distinct%2A>tym temacie pokazano, jak używać operatorów, <xref:System.Linq.Enumerable.Intersect%2A> <xref:System.Linq.Enumerable.Except%2A>, i <xref:System.Linq.Enumerable.Union%2A> do wykonywania operacji porównania na podstawie wartości na zestawach wierszy danych.[ Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md) zobacz [porównywanie wierszy DataRows](comparing-datarows-linq-to-dataset.md) , aby <xref:System.Data.DataRowComparer>uzyskać więcej informacji na temat.</span><span class="sxs-lookup"><span data-stu-id="2c469-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="2c469-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="2c469-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2c469-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2c469-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2c469-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="2c469-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="2c469-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2c469-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="2c469-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="2c469-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c469-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c469-109">Example</span></span>  
 <span data-ttu-id="2c469-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Distinct%2A> metody, aby usunąć zduplikowane elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="2c469-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="2c469-111">Ale</span><span class="sxs-lookup"><span data-stu-id="2c469-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c469-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c469-112">Example</span></span>  
 <span data-ttu-id="2c469-113">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Except%2A> metodę, aby zwrócić kontakty, które pojawiają się w pierwszej tabeli, ale nie w drugim.</span><span class="sxs-lookup"><span data-stu-id="2c469-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="2c469-114">Wspólnej</span><span class="sxs-lookup"><span data-stu-id="2c469-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c469-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c469-115">Example</span></span>  
 <span data-ttu-id="2c469-116">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Intersect%2A> metodę, aby zwrócić kontakty, które są wyświetlane w obu tabelach.</span><span class="sxs-lookup"><span data-stu-id="2c469-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="2c469-117">Union</span><span class="sxs-lookup"><span data-stu-id="2c469-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c469-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c469-118">Example</span></span>  
 <span data-ttu-id="2c469-119">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Union%2A> metodę w celu zwrócenia unikatowych kontaktów z jednej z dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="2c469-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="2c469-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c469-120">See also</span></span>

- [<span data-ttu-id="2c469-121">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2c469-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="2c469-122">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="2c469-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="2c469-123">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="2c469-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="2c469-124">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c469-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
