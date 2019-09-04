---
title: 'Przykłady składni wyrażeń zapytania: Operatory sprzęgania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: e80c50daeb0de7f4a8477786f28441d1495033ea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249487"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="5d81a-102">Przykłady składni wyrażeń zapytania: Operatory sprzęgania</span><span class="sxs-lookup"><span data-stu-id="5d81a-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="5d81a-103">Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, które nie mają relacji nawigacji ze sobą, takich jak tabele relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5d81a-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="5d81a-104">Sprzężenie dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="5d81a-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="5d81a-105">Aby uzyskać więcej informacji, zobacz [Omówienie standardowych operatorów zapytań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="5d81a-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="5d81a-106">W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.GroupJoin%2A> jak za pomocą metod i <xref:System.Linq.Enumerable.Join%2A> zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="5d81a-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="5d81a-107">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5d81a-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5d81a-108">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="5d81a-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="5d81a-109">GroupJoin —</span><span class="sxs-lookup"><span data-stu-id="5d81a-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="5d81a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d81a-110">Example</span></span>  
 <span data-ttu-id="5d81a-111">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> przekroczenie tabeli SalesOrderHeader i SalesOrderDetail, aby znaleźć liczbę zamówień na klienta.</span><span class="sxs-lookup"><span data-stu-id="5d81a-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="5d81a-112">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, które zwraca każdy element pierwszego (lewego) źródła danych, nawet jeśli żadne skorelowane elementy nie znajdują się w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="5d81a-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="5d81a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d81a-113">Example</span></span>  
 <span data-ttu-id="5d81a-114">Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> przekroczenie w tabelach Contact i SalesOrderHeader, aby znaleźć liczbę zamówień na kontakt.</span><span class="sxs-lookup"><span data-stu-id="5d81a-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="5d81a-115">Zostanie wyświetlona liczba i identyfikatory zamówień dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="5d81a-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="5d81a-116">Łączenie</span><span class="sxs-lookup"><span data-stu-id="5d81a-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="5d81a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d81a-117">Example</span></span>  
 <span data-ttu-id="5d81a-118">Poniższy przykład wykonuje sprzężenie w tabelach SalesOrderHeader i SalesOrderDetail w celu uzyskania zamówień online od miesiąca sierpnia.</span><span class="sxs-lookup"><span data-stu-id="5d81a-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="5d81a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d81a-119">See also</span></span>

- [<span data-ttu-id="5d81a-120">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5d81a-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
