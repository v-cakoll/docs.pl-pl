---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory elementów (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: 7ef2e2328ed69edea8cbb29942fe665a905e6a03
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794901"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="918ee-102">Przykłady składni zapytania oparte na metodzie: Operatory elementów (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="918ee-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="918ee-103">W przykładach w tym temacie pokazano, jak używać <xref:System.Linq.Enumerable.First%2A> metod <xref:System.Linq.Enumerable.ElementAt%2A> i <xref:System.Data.DataSet> do pobierania <xref:System.Data.DataRow> elementów z przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="918ee-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="918ee-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="918ee-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="918ee-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="918ee-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="918ee-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="918ee-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]   
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]     

 <span data-ttu-id="918ee-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="918ee-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="918ee-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="918ee-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="918ee-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="918ee-109">Example</span></span>  
 <span data-ttu-id="918ee-110">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.ElementAt%2A> aby pobrać piąty adres, gdzie `PostalCode` = = "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="918ee-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]   
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]     
  
## <a name="first"></a><span data-ttu-id="918ee-111">Pierwszego</span><span class="sxs-lookup"><span data-stu-id="918ee-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="918ee-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="918ee-112">Example</span></span>  
 <span data-ttu-id="918ee-113">W tym przykładzie używa <xref:System.Linq.Enumerable.First%2A> metody do zwrócenia pierwszego kontaktu, którego imię to "Brooke".</span><span class="sxs-lookup"><span data-stu-id="918ee-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]   
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)] 
  
## <a name="see-also"></a><span data-ttu-id="918ee-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="918ee-114">See also</span></span>

- [<span data-ttu-id="918ee-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="918ee-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="918ee-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="918ee-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="918ee-117">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="918ee-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="918ee-118">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918ee-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
