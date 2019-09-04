---
title: 'Przykłady składni wyrażeń zapytania: Partycjonowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 034cca65f92f1fd8bd64d540de0cf1470a16c9e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249359"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="ebc3b-102">Przykłady składni wyrażeń zapytania: Partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="ebc3b-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="ebc3b-103">W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.Skip%2A> jak za pomocą metod i <xref:System.Linq.Enumerable.Take%2A> zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="ebc3b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="ebc3b-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ebc3b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ebc3b-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="ebc3b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="ebc3b-106">Skip</span><span class="sxs-lookup"><span data-stu-id="ebc3b-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="ebc3b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebc3b-107">Example</span></span>  
 <span data-ttu-id="ebc3b-108">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie pierwsze dwa adresy z Seattle.</span><span class="sxs-lookup"><span data-stu-id="ebc3b-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="ebc3b-109">Take</span><span class="sxs-lookup"><span data-stu-id="ebc3b-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="ebc3b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebc3b-110">Example</span></span>  
 <span data-ttu-id="ebc3b-111">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Take%2A> metodę, aby pobrać pierwsze trzy adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="ebc3b-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="ebc3b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebc3b-112">See also</span></span>

- [<span data-ttu-id="ebc3b-113">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ebc3b-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
