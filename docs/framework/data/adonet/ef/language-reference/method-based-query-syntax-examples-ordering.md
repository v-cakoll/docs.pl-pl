---
title: 'Przykłady składni zapytania oparte na metodzie: porządkowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: c059bd771667c23bb9aeb78b548e7036e4b8a73a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000820"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="c7ad4-102">Przykłady składni zapytania oparte na metodzie: porządkowanie</span><span class="sxs-lookup"><span data-stu-id="c7ad4-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="c7ad4-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.ThenBy%2A> metody zapytania [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="c7ad4-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="c7ad4-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c7ad4-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c7ad4-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c7ad4-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="c7ad4-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="c7ad4-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="c7ad4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7ad4-107">Example</span></span>  
 <span data-ttu-id="c7ad4-108">W poniższym przykładzie przy użyciu składni zapytania oparte na metodzie <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenBy%2A> aby powrócić do listy kontaktów, uporządkowane według nazwiska, a następnie według imienia.</span><span class="sxs-lookup"><span data-stu-id="c7ad4-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="c7ad4-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="c7ad4-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="c7ad4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7ad4-110">Example</span></span>  
 <span data-ttu-id="c7ad4-111">W poniższym przykładzie użyto <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenByDescending%2A> metody uprzedniego sortować według ceny, a następnie wykonaj, malejąco swoistego nazw produktów.</span><span class="sxs-lookup"><span data-stu-id="c7ad4-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c7ad4-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7ad4-112">See Also</span></span>  
 [<span data-ttu-id="c7ad4-113">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c7ad4-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
