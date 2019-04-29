---
title: 'Przykłady składni wyrażeń zapytania: Operatory elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 1b73e22e79c665763390561a1e48b2583ec6cd27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614443"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="c5b83-102">Przykłady składni wyrażeń zapytania: Operatory elementu</span><span class="sxs-lookup"><span data-stu-id="c5b83-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="c5b83-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.First%2A> metody zapytania [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="c5b83-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using the query expression syntax.</span></span> <span data-ttu-id="c5b83-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c5b83-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c5b83-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c5b83-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="c5b83-106">pierwszy</span><span class="sxs-lookup"><span data-stu-id="c5b83-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="c5b83-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5b83-107">Example</span></span>  
 <span data-ttu-id="c5b83-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> metodę, aby zwrócić których typu imię pierwszy kontakt jest "Brooke".</span><span class="sxs-lookup"><span data-stu-id="c5b83-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="c5b83-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5b83-109">See also</span></span>

- [<span data-ttu-id="c5b83-110">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c5b83-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
