---
title: 'Przykłady składni wyrażeń zapytania: Grupowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: 0a4aa57ba709852c30223598b9d1af146eaf6013
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212001"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="fe5dd-102">Przykłady składni wyrażeń zapytania: Grupowanie</span><span class="sxs-lookup"><span data-stu-id="fe5dd-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="fe5dd-103">Przykłady w tym temacie prezentują sposób użycia `GroupBy` metody zapytania [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="fe5dd-104">Model sprzedaży AdventureWorks używanego w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fe5dd-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="fe5dd-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="fe5dd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe5dd-106">Example</span></span>  
 <span data-ttu-id="fe5dd-107">Poniższy przykład zwraca `Address` obiekty pogrupowane według kodu pocztowego.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="fe5dd-108">Wyniki są przedstawione typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="fe5dd-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe5dd-109">Example</span></span>  
 <span data-ttu-id="fe5dd-110">Poniższy przykład zwraca `Contact` obiekty pogrupowane według pierwszej litery nazwiska osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="fe5dd-111">Wyniki są również sortowane według pierwszej litery nazwiska i przekazana do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="fe5dd-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe5dd-112">Example</span></span>  
 <span data-ttu-id="fe5dd-113">Poniższy przykład zwraca `SalesOrderHeader` obiekty pogrupowane według identyfikatora klienta.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="fe5dd-114">Liczba sprzedaży dla każdego klienta jest także zwracany.</span><span class="sxs-lookup"><span data-stu-id="fe5dd-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="fe5dd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe5dd-115">See also</span></span>

- [<span data-ttu-id="fe5dd-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="fe5dd-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
