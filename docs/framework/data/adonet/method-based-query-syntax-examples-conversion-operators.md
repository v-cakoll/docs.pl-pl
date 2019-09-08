---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory konwersji (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 3e2a72a2bb0921828bdd90fe437987fddfc995b5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783694"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="1460b-102">Przykłady składni zapytania oparte na metodzie: Operatory konwersji (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1460b-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="1460b-103">W przykładach w tym temacie pokazano <xref:System.Linq.Enumerable.ToArray%2A>, jak za pomocą metod, <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToDictionary%2A>i natychmiast wykonać wyrażenie zapytania.</span><span class="sxs-lookup"><span data-stu-id="1460b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="1460b-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="1460b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="1460b-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1460b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1460b-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="1460b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="1460b-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1460b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="1460b-108">ToArray —</span><span class="sxs-lookup"><span data-stu-id="1460b-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="1460b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1460b-109">Example</span></span>  
 <span data-ttu-id="1460b-110">Ten przykład używa <xref:System.Linq.Enumerable.ToArray%2A> metody do natychmiastowego oszacowania sekwencji do tablicy.</span><span class="sxs-lookup"><span data-stu-id="1460b-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="1460b-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="1460b-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="1460b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1460b-112">Example</span></span>  
 <span data-ttu-id="1460b-113">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.ToDictionary%2A> aby natychmiast oszacować sekwencję i powiązane wyrażenie klucza do słownika.</span><span class="sxs-lookup"><span data-stu-id="1460b-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="1460b-114">ToList —</span><span class="sxs-lookup"><span data-stu-id="1460b-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="1460b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="1460b-115">Example</span></span>  
 <span data-ttu-id="1460b-116">W tym przykładzie używa <xref:System.Linq.Enumerable.ToList%2A> metody do natychmiastowego oszacowania sekwencji <xref:System.Collections.Generic.List%601>do, gdzie `T` jest typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="1460b-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="1460b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1460b-117">See also</span></span>

- [<span data-ttu-id="1460b-118">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1460b-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="1460b-119">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1460b-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="1460b-120">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="1460b-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1460b-121">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1460b-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
