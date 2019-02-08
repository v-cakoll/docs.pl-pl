---
title: 'Przykłady składni zapytania oparte na metodzie: Partycjonowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 181564de997e9a799aafa660a16b32a6ceb91d4a
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827157"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="80c5a-102">Przykłady składni zapytania oparte na metodzie: Partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="80c5a-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="80c5a-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Take%2A> metod do wykonywania zapytań [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="80c5a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="80c5a-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="80c5a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="80c5a-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="80c5a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="80c5a-106">Skip</span><span class="sxs-lookup"><span data-stu-id="80c5a-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="80c5a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c5a-107">Example</span></span>  
 <span data-ttu-id="80c5a-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby uzyskać wszystkie, ale pięciu pierwszych kontakty tabeli Kontakt.</span><span class="sxs-lookup"><span data-stu-id="80c5a-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="80c5a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c5a-109">Example</span></span>  
 <span data-ttu-id="80c5a-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby uzyskać wszystkie, ale pierwsze dwa adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="80c5a-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="80c5a-111">Take</span><span class="sxs-lookup"><span data-stu-id="80c5a-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="80c5a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c5a-112">Example</span></span>  
 <span data-ttu-id="80c5a-113">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metodę, aby uzyskać tylko pięć pierwszych kontakty z tabeli Kontakt.</span><span class="sxs-lookup"><span data-stu-id="80c5a-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="80c5a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c5a-114">Example</span></span>  
 <span data-ttu-id="80c5a-115">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metodę, aby uzyskać pierwszych trzech adresów w Seattle.</span><span class="sxs-lookup"><span data-stu-id="80c5a-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="80c5a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80c5a-116">See also</span></span>
- [<span data-ttu-id="80c5a-117">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="80c5a-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
