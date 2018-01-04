---
title: Tabeli zapytania (LINQ do DataSet)
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
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 059dd39f3583c3b8fcf6736e514b9cc4870d3ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="da952-102">Tabeli zapytania (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="da952-102">Cross-Table Queries (LINQ to DataSet)</span></span>
<span data-ttu-id="da952-103">Oprócz wykonywania zapytania w jednej tabeli, można również wykonywać zapytania między tabelami w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da952-103">In addition to querying a single table, you can also perform cross-table queries in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="da952-104">Jest to zrobić za pomocą *sprzężenia*.</span><span class="sxs-lookup"><span data-stu-id="da952-104">This is done by using a *join*.</span></span> <span data-ttu-id="da952-105">Sprzężenia jest skojarzenie obiektów w jedno źródło danych z obiektów, które udostępnianie wspólny atrybut w inne źródło danych, takich jak produkt, lub skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="da952-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="da952-106">W programowanie zorientowane obiektowo relacje między obiektami są stosunkowo łatwa do nawigować, ponieważ każdy obiekt ma elementu członkowskiego, który odwołuje się do innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="da952-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="da952-107">W przypadku tabel zewnętrznych baz danych jednak nawigowanie po relacjach nie jest równie proste.</span><span class="sxs-lookup"><span data-stu-id="da952-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="da952-108">Tabele bazy danych nie zawierają wbudowanych relacji.</span><span class="sxs-lookup"><span data-stu-id="da952-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="da952-109">W takich przypadkach można operacji tworzenia sprzężenia zgodne elementy z każdego źródła.</span><span class="sxs-lookup"><span data-stu-id="da952-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="da952-110">Przykładowo podana dwóch tabel, które zawierają informacje o produkcie i informacji o sprzedaży, można operacji tworzenia sprzężenia do dopasowania informacji o sprzedaży i produkty do tej samej kolejności sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="da952-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="da952-111">[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework zapewnia dołączyć dwa operatory, <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="da952-111">The [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="da952-112">Wykonaj te operatory *sprzężeniami*: oznacza to, sprzężenia, które pasują dwóch danych źródła tylko wtedy, gdy ich kluczy są takie same.</span><span class="sxs-lookup"><span data-stu-id="da952-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="da952-113">(Natomiast [!INCLUDE[tsql](../../../../includes/tsql-md.md)] obsługuje dołączenia innych niż operatory `equals`, takich jak `less than` operatora.)</span><span class="sxs-lookup"><span data-stu-id="da952-113">(By contrast, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="da952-114">W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenia wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="da952-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="da952-115">Typ sprzężenia jest sprzężenie wewnętrzne w zwracane są tylko te obiekty, które mają odpowiednika w przeciwną zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="da952-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="da952-116"><xref:System.Linq.Enumerable.GroupJoin%2A> Operatory nie mają bezpośredniego odpowiednika w warunkach relacyjnej bazy danych; wdrażają podzbiorem sprzężenia wewnętrzne i lewe sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="da952-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="da952-117">Lewe sprzężenie zewnętrzne jest sprzężenia, które zwraca każdy element pierwszej kolekcji (po lewej), nawet jeśli go nie ma żadnych elementów skorelowane w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="da952-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="da952-118">Aby uzyskać więcej informacji na temat sprzężeń, zobacz [operacji Join](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span><span class="sxs-lookup"><span data-stu-id="da952-118">For more information about joins, see [Join Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da952-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="da952-119">Example</span></span>  
 <span data-ttu-id="da952-120">Poniższy przykład wykonuje tradycyjnych przyłączenia `SalesOrderHeader` i `SalesOrderDetail` tabel z przykładowej bazy danych AdventureWorks uzyskanie zamówień online w ciągu miesiąca sierpnia.</span><span class="sxs-lookup"><span data-stu-id="da952-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="da952-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da952-121">See Also</span></span>  
 [<span data-ttu-id="da952-122">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="da952-122">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="da952-123">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="da952-123">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="da952-124">Wykonywanie zapytania do typizowanych zestawów danych</span><span class="sxs-lookup"><span data-stu-id="da952-124">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="da952-125">Operacje połączone</span><span class="sxs-lookup"><span data-stu-id="da952-125">Join Operations</span></span>](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [<span data-ttu-id="da952-126">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="da952-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
