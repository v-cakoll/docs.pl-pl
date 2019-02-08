---
title: 'Przykłady składni zapytania oparte na metodzie: Grupowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: d414218604887fca2d69a02b40dfa87f13961aae
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825384"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="738bb-102">Przykłady składni zapytania oparte na metodzie: Grupowanie</span><span class="sxs-lookup"><span data-stu-id="738bb-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="738bb-103">Przykłady w tym temacie pokazano, jak używać `GroupBy` metody zapytania [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="738bb-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="738bb-104">Model sprzedaży AdventureWorks, który jest używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="738bb-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="738bb-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="738bb-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="738bb-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="738bb-106">Example</span></span>  
 <span data-ttu-id="738bb-107">W poniższym przykładzie użyto `GroupBy` metodę, aby zwrócić `Address` obiektów, które są pogrupowane według kodu pocztowego.</span><span class="sxs-lookup"><span data-stu-id="738bb-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="738bb-108">Wyniki są przedstawione typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="738bb-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="738bb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="738bb-109">Example</span></span>  
 <span data-ttu-id="738bb-110">W poniższym przykładzie użyto `GroupBy` metodę, aby zwrócić `Contact` obiekty, które są grupowane w pierwszej litery nazwiska osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="738bb-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="738bb-111">Wyniki są również sortowane według pierwszej litery nazwiska i przekazana do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="738bb-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="738bb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="738bb-112">Example</span></span>  
 <span data-ttu-id="738bb-113">W poniższym przykładzie użyto `GroupBy` metodę, aby zwrócić `SalesOrderHeader` obiektów, które są grupowane według identyfikatora klienta.</span><span class="sxs-lookup"><span data-stu-id="738bb-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="738bb-114">Liczba sprzedaży dla każdego klienta jest także zwracany.</span><span class="sxs-lookup"><span data-stu-id="738bb-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="738bb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="738bb-115">See also</span></span>
- [<span data-ttu-id="738bb-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="738bb-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
