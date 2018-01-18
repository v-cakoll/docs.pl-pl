---
title: "Przykłady składni wyrażeń zapytania: grupowanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4d9351cd5978632b83f54ef1247a7a5679030c69
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="712a9-102">Przykłady składni wyrażeń zapytania: grupowanie</span><span class="sxs-lookup"><span data-stu-id="712a9-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="712a9-103">Przykłady w tym temacie przedstawiają sposób użycia `GroupBy` metody query [AdventureWorks sprzedaży modelu](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="712a9-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="712a9-104">Model sprzedaży AdventureWorks używany w tym przykładzie składa się z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="712a9-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="712a9-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="712a9-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="712a9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="712a9-106">Example</span></span>  
 <span data-ttu-id="712a9-107">Poniższy przykład zwraca `Address` obiekty pogrupowane według kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="712a9-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="712a9-108">Wyniki są przedstawione jako typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="712a9-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="712a9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="712a9-109">Example</span></span>  
 <span data-ttu-id="712a9-110">Poniższy przykład zwraca `Contact` obiekty pogrupowane według pierwszą literę nazwisko osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="712a9-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="712a9-111">Wyniki są również sortowane według pierwszą literę nazwisko i przedstawione jako typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="712a9-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="712a9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="712a9-112">Example</span></span>  
 <span data-ttu-id="712a9-113">Poniższy przykład zwraca `SalesOrderHeader` obiekty pogrupowane według identyfikatora klienta.</span><span class="sxs-lookup"><span data-stu-id="712a9-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="712a9-114">Jest także zwracany liczbę transakcji dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="712a9-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="712a9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="712a9-115">See Also</span></span>  
 [<span data-ttu-id="712a9-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="712a9-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
