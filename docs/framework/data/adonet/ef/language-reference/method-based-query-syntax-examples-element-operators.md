---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 302530b38e4feb7c34e672fbaa4473044515faf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542863"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="8e27b-102">Przykłady składni zapytania oparte na metodzie: Operatory elementu</span><span class="sxs-lookup"><span data-stu-id="8e27b-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="8e27b-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.First%2A> metody zapytania [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="8e27b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="8e27b-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8e27b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8e27b-105">W przykładzie w tym temacie użyto następujących `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="8e27b-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="8e27b-106">pierwszy</span><span class="sxs-lookup"><span data-stu-id="8e27b-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e27b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e27b-107">Example</span></span>  
 <span data-ttu-id="8e27b-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> metody do znalezienia pierwszy adres e-mail, który rozpoczyna się za pomocą "caroline".</span><span class="sxs-lookup"><span data-stu-id="8e27b-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8e27b-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e27b-109">See also</span></span>
- [<span data-ttu-id="8e27b-110">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8e27b-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
