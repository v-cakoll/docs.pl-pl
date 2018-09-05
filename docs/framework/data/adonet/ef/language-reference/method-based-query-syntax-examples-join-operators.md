---
title: Przykłady składni zapytania oparte na metodzie, operatory sprzężenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: ee753f5101f525fc7d86a91f2aa3545d257a2be5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671354"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="6c33f-102">Przykłady składni zapytania oparte na metodzie, operatory sprzężenia</span><span class="sxs-lookup"><span data-stu-id="6c33f-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="6c33f-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A> metod do wykonywania zapytań [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="6c33f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="6c33f-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6c33f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6c33f-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="6c33f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="6c33f-106">Groupjoin —</span><span class="sxs-lookup"><span data-stu-id="6c33f-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c33f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c33f-107">Example</span></span>  
 <span data-ttu-id="6c33f-108">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem tabeli SalesOrderHeader i szczegóły zamówienia sprzedaży, aby znaleźć numer zamówienia na klienta.</span><span class="sxs-lookup"><span data-stu-id="6c33f-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="6c33f-109">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet jeśli żadne elementy skorelowane znajdują się w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="6c33f-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="6c33f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c33f-110">Example</span></span>  
 <span data-ttu-id="6c33f-111">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem tabele kontaktu i SalesOrderHeader, aby znaleźć numer zamówienia na kontakt.</span><span class="sxs-lookup"><span data-stu-id="6c33f-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="6c33f-112">Liczba zamówień i identyfikatory dla każdego kontaktu są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="6c33f-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="6c33f-113">Łączenie</span><span class="sxs-lookup"><span data-stu-id="6c33f-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c33f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c33f-114">Example</span></span>  
 <span data-ttu-id="6c33f-115">Poniższy przykład wykonuje sprzężenie tabel skontaktuj się z pomocą i SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="6c33f-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="6c33f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c33f-116">Example</span></span>  
 <span data-ttu-id="6c33f-117">Poniższy przykład wykonuje sprzężenie kontaktu i tabele SalesOrderHeader, grupowanie wyników według identyfikatora. Skontaktuj się z</span><span class="sxs-lookup"><span data-stu-id="6c33f-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6c33f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c33f-118">See Also</span></span>  
 [<span data-ttu-id="6c33f-119">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6c33f-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
