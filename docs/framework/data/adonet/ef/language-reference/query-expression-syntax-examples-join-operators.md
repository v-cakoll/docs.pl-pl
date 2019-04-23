---
title: 'Przykłady składni wyrażeń zapytania: Operatory sprzęgania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: da583ed207a8c4fc9e061d517895ca0f2fea2f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168821"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="51808-102">Przykłady składni wyrażeń zapytania: Operatory sprzęgania</span><span class="sxs-lookup"><span data-stu-id="51808-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="51808-103">Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, które mają żadnych relacji można nawigować do siebie nawzajem, takich jak tabel relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="51808-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="51808-104">Przyłączenia dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych przy użyciu obiektów mających wspólny atrybut w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="51808-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="51808-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="51808-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="51808-106">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.GroupJoin%2A> i <xref:System.Linq.Enumerable.Join%2A> metod do wykonywania zapytań [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="51808-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="51808-107">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="51808-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="51808-108">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="51808-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="51808-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="51808-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="51808-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="51808-110">Example</span></span>  
 <span data-ttu-id="51808-111">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem tabeli SalesOrderHeader i szczegóły zamówienia sprzedaży, aby znaleźć numer zamówienia na klienta.</span><span class="sxs-lookup"><span data-stu-id="51808-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="51808-112">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet jeśli żadne elementy skorelowane znajdują się w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="51808-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="51808-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="51808-113">Example</span></span>  
 <span data-ttu-id="51808-114">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem tabele kontaktu i SalesOrderHeader, aby znaleźć numer zamówienia na kontakt.</span><span class="sxs-lookup"><span data-stu-id="51808-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="51808-115">Liczba zamówień i identyfikatory dla każdego kontaktu są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="51808-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="51808-116">Łączenie</span><span class="sxs-lookup"><span data-stu-id="51808-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="51808-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="51808-117">Example</span></span>  
 <span data-ttu-id="51808-118">Poniższy przykład wykonuje sprzężenie tabel SalesOrderHeader i szczegóły zamówienia sprzedaży, które można pobrać zamówień online z sierpień.</span><span class="sxs-lookup"><span data-stu-id="51808-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="51808-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51808-119">See also</span></span>

- [<span data-ttu-id="51808-120">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="51808-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
