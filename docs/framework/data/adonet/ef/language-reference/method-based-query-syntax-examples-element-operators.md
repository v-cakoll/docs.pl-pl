---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 89cbda4d049b30ee50accf94d5b7ec172bc25ae2
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826502"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="05a61-102">Przykłady składni zapytania oparte na metodzie: Operatory elementu</span><span class="sxs-lookup"><span data-stu-id="05a61-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="05a61-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.First%2A> metody zapytania [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="05a61-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="05a61-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="05a61-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="05a61-105">W przykładzie w tym temacie użyto następujących `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="05a61-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="05a61-106">pierwszy</span><span class="sxs-lookup"><span data-stu-id="05a61-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="05a61-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="05a61-107">Example</span></span>  
 <span data-ttu-id="05a61-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> metody do znalezienia pierwszy adres e-mail, który rozpoczyna się za pomocą "caroline".</span><span class="sxs-lookup"><span data-stu-id="05a61-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="05a61-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05a61-109">See also</span></span>
- [<span data-ttu-id="05a61-110">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="05a61-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
