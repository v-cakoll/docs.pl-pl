---
title: 'Przykłady składni wyrażeń zapytania: Szeregowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: e7591e68490bf1ac35b56d5f483d1838a0a7d0c2
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826320"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="2b1a7-102">Przykłady składni wyrażeń zapytania: Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="2b1a7-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="2b1a7-103">Przykłady w tym temacie prezentują sposób użycia `OrderBy` i `OrderByDescending` metod do wykonywania zapytań [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="2b1a7-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2b1a7-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="2b1a7-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="2b1a7-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="2b1a7-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="2b1a7-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b1a7-107">Example</span></span>  
 <span data-ttu-id="2b1a7-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> aby powrócić do listy kontaktów, uporządkowane według nazwiska.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="2b1a7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b1a7-109">Example</span></span>  
 <span data-ttu-id="2b1a7-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> Aby posortować listę kontaktów według długości nazwisko.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="2b1a7-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="2b1a7-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="2b1a7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b1a7-112">Example</span></span>  
 <span data-ttu-id="2b1a7-113">W poniższym przykładzie użyto `orderby… descending` (`Order By … Descending` w języku Visual Basic), który jest odpowiednikiem <xref:System.Linq.Enumerable.OrderByDescending%2A> metody sortowania w cenniku, od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="2b1a7-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="2b1a7-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="2b1a7-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b1a7-115">Example</span></span>  
 <span data-ttu-id="2b1a7-116">W poniższym przykładzie użyto <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenBy%2A> aby powrócić do listy kontaktów, uporządkowane według nazwiska, a następnie według imienia.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="2b1a7-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="2b1a7-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="2b1a7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b1a7-118">Example</span></span>  
 <span data-ttu-id="2b1a7-119">W poniższym przykładzie użyto `OrderBy… Descending`, który jest odpowiednikiem <xref:System.Linq.Enumerable.ThenByDescending%2A> metody, aby sortować listę produktów, najpierw według nazwy, a następnie według ceny od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="2b1a7-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="2b1a7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b1a7-120">See also</span></span>
- [<span data-ttu-id="2b1a7-121">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2b1a7-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
