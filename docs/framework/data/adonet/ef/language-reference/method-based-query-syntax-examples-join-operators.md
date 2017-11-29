---
title: "Przykłady składni zapytania oparte na metodzie: Operatorów sprzężenia"
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
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 79946dc2724e292c90949597d3c2ca8ee7d2ae08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="5160c-102">Przykłady składni zapytania oparte na metodzie: Operatorów sprzężenia</span><span class="sxs-lookup"><span data-stu-id="5160c-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="5160c-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A> metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="5160c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="5160c-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5160c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5160c-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="5160c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="5160c-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="5160c-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="5160c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5160c-107">Example</span></span>  
 <span data-ttu-id="5160c-108">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem SalesOrderHeader i szczegóły zamówienia sprzedaży tabele, aby znaleźć numer zamówienia na klienta.</span><span class="sxs-lookup"><span data-stu-id="5160c-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="5160c-109">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej), nawet jeśli skorelowane elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="5160c-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="5160c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5160c-110">Example</span></span>  
 <span data-ttu-id="5160c-111">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem kontaktów i SalesOrderHeader tabele, aby znaleźć numer zamówienia na kontakt.</span><span class="sxs-lookup"><span data-stu-id="5160c-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="5160c-112">Liczba kolejności i identyfikatory dla każdego kontakt są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="5160c-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="5160c-113">Łączenie</span><span class="sxs-lookup"><span data-stu-id="5160c-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="5160c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="5160c-114">Example</span></span>  
 <span data-ttu-id="5160c-115">Poniższy przykład wykonuje sprzężenie za pośrednictwem kontaktów i SalesOrderHeader tabel.</span><span class="sxs-lookup"><span data-stu-id="5160c-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="5160c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5160c-116">Example</span></span>  
 <span data-ttu-id="5160c-117">Sprzężenia w poniższym przykładzie jest wykonywane za pośrednictwem kontaktu i tabele SalesOrderHeader, grupowanie wyników według identyfikatora. Skontaktuj się z</span><span class="sxs-lookup"><span data-stu-id="5160c-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="5160c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5160c-118">See Also</span></span>  
 [<span data-ttu-id="5160c-119">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5160c-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
