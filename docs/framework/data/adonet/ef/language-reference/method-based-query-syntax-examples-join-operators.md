---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory sprzęgania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 2f26f937901debd27cb936d1f642e0a5149b167a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250132"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="ab698-102">Przykłady składni zapytania oparte na metodzie: Operatory sprzęgania</span><span class="sxs-lookup"><span data-stu-id="ab698-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="ab698-103">W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.Join%2A> jak za pomocą metod i <xref:System.Linq.Enumerable.GroupJoin%2A> zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni zapytania opartego na metodzie.</span><span class="sxs-lookup"><span data-stu-id="ab698-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="ab698-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ab698-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ab698-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="ab698-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="ab698-106">GroupJoin —</span><span class="sxs-lookup"><span data-stu-id="ab698-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="ab698-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab698-107">Example</span></span>  
 <span data-ttu-id="ab698-108">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> przekroczenie tabeli SalesOrderHeader i SalesOrderDetail, aby znaleźć liczbę zamówień na klienta.</span><span class="sxs-lookup"><span data-stu-id="ab698-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="ab698-109">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, które zwraca każdy element pierwszego (lewego) źródła danych, nawet jeśli żadne skorelowane elementy nie znajdują się w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ab698-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="ab698-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab698-110">Example</span></span>  
 <span data-ttu-id="ab698-111">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> przekroczenie w tabelach Contact i SalesOrderHeader, aby znaleźć liczbę zamówień na kontakt.</span><span class="sxs-lookup"><span data-stu-id="ab698-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="ab698-112">Zostanie wyświetlona liczba i identyfikatory zamówień dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ab698-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="ab698-113">Łączenie</span><span class="sxs-lookup"><span data-stu-id="ab698-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="ab698-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab698-114">Example</span></span>  
 <span data-ttu-id="ab698-115">Poniższy przykład wykonuje sprzężenie w tabelach Contact i SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="ab698-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="ab698-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab698-116">Example</span></span>  
 <span data-ttu-id="ab698-117">Poniższy przykład wykonuje sprzężenie w tabelach Contact i SalesOrderHeader, grupując wyniki według identyfikatora kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ab698-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ab698-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab698-118">See also</span></span>

- [<span data-ttu-id="ab698-119">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ab698-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
