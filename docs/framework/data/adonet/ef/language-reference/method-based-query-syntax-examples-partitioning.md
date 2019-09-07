---
title: 'Przykłady składni zapytania oparte na metodzie: Partycjonowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 168fea5ffe6b8fbb4c08b95578beebbdee171c9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398491"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="d5fe9-102">Przykłady składni zapytania oparte na metodzie: Partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="d5fe9-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="d5fe9-103">W przykładach w tym temacie pokazano <xref:System.Linq.Enumerable.Skip%2A>, jak użyć metod, i <xref:System.Linq.Enumerable.Take%2A> zbadać [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="d5fe9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="d5fe9-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d5fe9-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d5fe9-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="d5fe9-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="d5fe9-106">Skip</span><span class="sxs-lookup"><span data-stu-id="d5fe9-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5fe9-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5fe9-107">Example</span></span>  
 <span data-ttu-id="d5fe9-108">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie pierwsze kontakty z tabeli kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="d5fe9-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="d5fe9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5fe9-109">Example</span></span>  
 <span data-ttu-id="d5fe9-110">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie pierwsze dwa adresy z Seattle.</span><span class="sxs-lookup"><span data-stu-id="d5fe9-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="d5fe9-111">Take</span><span class="sxs-lookup"><span data-stu-id="d5fe9-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5fe9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5fe9-112">Example</span></span>  
 <span data-ttu-id="d5fe9-113">Poniższy przykład używa metody, <xref:System.Linq.Enumerable.Take%2A> Aby uzyskać tylko pięć pierwszych kontaktów z tabeli kontaktów.</span><span class="sxs-lookup"><span data-stu-id="d5fe9-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="d5fe9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5fe9-114">Example</span></span>  
 <span data-ttu-id="d5fe9-115">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Take%2A> metodę, aby pobrać pierwsze trzy adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="d5fe9-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="d5fe9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5fe9-116">See also</span></span>

- [<span data-ttu-id="d5fe9-117">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d5fe9-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
