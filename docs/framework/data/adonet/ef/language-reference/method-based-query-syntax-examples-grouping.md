---
title: "Przykłady składni zapytania oparte na metodzie: grupowanie"
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
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b2001c76cac2c09159508d2d13da451c81b4cf1a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="aab0a-102">Przykłady składni zapytania oparte na metodzie: grupowanie</span><span class="sxs-lookup"><span data-stu-id="aab0a-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="aab0a-103">Przykłady w tym temacie opisano, jak używać `GroupBy` metody query [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="aab0a-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="aab0a-104">Model sprzedaży AdventureWorks używanego w tych przykładach składa się z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aab0a-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aab0a-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="aab0a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="aab0a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="aab0a-106">Example</span></span>  
 <span data-ttu-id="aab0a-107">W poniższym przykładzie użyto `GroupBy` metodę, aby zwrócić `Address` obiektów, które są pogrupowane według kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="aab0a-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="aab0a-108">Wyniki są przedstawione jako typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="aab0a-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="aab0a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="aab0a-109">Example</span></span>  
 <span data-ttu-id="aab0a-110">W poniższym przykładzie użyto `GroupBy` metodę, aby zwrócić `Contact` obiektów, które są pogrupowane według pierwszą literę nazwisko osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="aab0a-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="aab0a-111">Wyniki są również sortowane według pierwszą literę nazwisko i przedstawione jako typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="aab0a-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="aab0a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="aab0a-112">Example</span></span>  
 <span data-ttu-id="aab0a-113">W poniższym przykładzie użyto `GroupBy` metodę, aby zwrócić `SalesOrderHeader` obiektów, które są pogrupowane według identyfikatora klienta.</span><span class="sxs-lookup"><span data-stu-id="aab0a-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="aab0a-114">Jest także zwracany liczbę transakcji dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="aab0a-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="aab0a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aab0a-115">See Also</span></span>  
 [<span data-ttu-id="aab0a-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="aab0a-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
