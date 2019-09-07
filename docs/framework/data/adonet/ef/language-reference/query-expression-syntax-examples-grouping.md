---
title: 'Przykłady składni wyrażeń zapytania: Grupowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: c9876c72a03f7827ec4b28d78f06ed372460caff
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398464"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="0525b-102">Przykłady składni wyrażeń zapytania: Grupowanie</span><span class="sxs-lookup"><span data-stu-id="0525b-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="0525b-103">W przykładach w tym temacie pokazano, `GroupBy` jak używać metody do wykonywania zapytań względem [modelu sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="0525b-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="0525b-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0525b-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0525b-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="0525b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="0525b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0525b-106">Example</span></span>  
 <span data-ttu-id="0525b-107">Poniższy przykład zwraca `Address` obiekty pogrupowane według kodu pocztowego.</span><span class="sxs-lookup"><span data-stu-id="0525b-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="0525b-108">Wyniki są rzutowane na typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="0525b-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="0525b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0525b-109">Example</span></span>  
 <span data-ttu-id="0525b-110">Poniższy przykład zwraca `Contact` obiekty pogrupowane według pierwszej litery nazwiska kontaktu.</span><span class="sxs-lookup"><span data-stu-id="0525b-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="0525b-111">Wyniki są również sortowane według pierwszej litery ostatniej nazwy i są rzutowane na typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="0525b-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="0525b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0525b-112">Example</span></span>  
 <span data-ttu-id="0525b-113">Poniższy przykład zwraca `SalesOrderHeader` obiekty pogrupowane według identyfikatora klienta.</span><span class="sxs-lookup"><span data-stu-id="0525b-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="0525b-114">Zwracana jest również liczba sprzedaży dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="0525b-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="0525b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0525b-115">See also</span></span>

- [<span data-ttu-id="0525b-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0525b-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
