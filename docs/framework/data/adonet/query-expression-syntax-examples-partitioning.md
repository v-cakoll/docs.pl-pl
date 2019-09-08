---
title: 'Przykłady składni wyrażeń zapytania: Partycjonowanie (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 6a00c5d49acc02c476895c999687aa944ba26aff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795101"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="6f65d-102">Przykłady składni wyrażeń zapytania: Partycjonowanie (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6f65d-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="6f65d-103">W przykładach w tym temacie pokazano, jak używać <xref:System.Linq.Enumerable.Skip%2A> metod <xref:System.Linq.Enumerable.Take%2A> i do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="6f65d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="6f65d-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="6f65d-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6f65d-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6f65d-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6f65d-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="6f65d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="6f65d-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6f65d-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="6f65d-108">Skip</span><span class="sxs-lookup"><span data-stu-id="6f65d-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f65d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f65d-109">Example</span></span>  
 <span data-ttu-id="6f65d-110">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Skip%2A> aby pobrać wszystkie pierwsze dwa adresy z Seattle.</span><span class="sxs-lookup"><span data-stu-id="6f65d-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="6f65d-111">Take</span><span class="sxs-lookup"><span data-stu-id="6f65d-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f65d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f65d-112">Example</span></span>  
 <span data-ttu-id="6f65d-113">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Take%2A> aby pobrać pierwsze trzy adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="6f65d-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="6f65d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f65d-114">See also</span></span>

- [<span data-ttu-id="6f65d-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6f65d-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="6f65d-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6f65d-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="6f65d-117">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="6f65d-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6f65d-118">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f65d-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
