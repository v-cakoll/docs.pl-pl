---
title: Przykłady składni zapytania oparte na metodzie, operatory elementu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 4215dcddf44647d98ee70c6f2d06345737cba5de
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384593"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="318b1-102">Przykłady składni zapytania oparte na metodzie, operatory elementu</span><span class="sxs-lookup"><span data-stu-id="318b1-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="318b1-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.First%2A> metody zapytania [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="318b1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="318b1-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="318b1-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="318b1-105">W przykładzie w tym temacie użyto następujących `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="318b1-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="318b1-106">pierwszy</span><span class="sxs-lookup"><span data-stu-id="318b1-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="318b1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="318b1-107">Example</span></span>  
 <span data-ttu-id="318b1-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> metody do znalezienia pierwszy adres e-mail, który rozpoczyna się za pomocą "caroline".</span><span class="sxs-lookup"><span data-stu-id="318b1-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="318b1-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="318b1-109">See Also</span></span>  
 [<span data-ttu-id="318b1-110">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="318b1-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
