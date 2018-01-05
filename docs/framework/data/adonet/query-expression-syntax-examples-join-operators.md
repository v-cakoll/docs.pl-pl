---
title: "Przykłady składni wyrażeń zapytania: Operatorów sprzężenia (LINQ do DataSet)"
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
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: db777e6ce332313206b0dcce4c692bcb3e3eacae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="11869-102">Przykłady składni wyrażeń zapytania: Operatorów sprzężenia (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="11869-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="11869-103">Sprzęganie jest ważne operacji w zapytaniach, które odnoszą się do źródła danych, których nie można nawigować relacje między, takich jak tabele relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="11869-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="11869-104">Sprzężenia dwóch źródeł danych jest skojarzenie obiektów w jedno źródło danych z obiektami, które mają wspólny atrybut w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="11869-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="11869-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="11869-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="11869-106">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.GroupJoin%2A> i <xref:System.Linq.Enumerable.Join%2A> metod do badania <xref:System.Data.DataSet> przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="11869-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="11869-107">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="11869-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="11869-108">Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="11869-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="11869-109">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="11869-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="11869-110">Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="11869-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="11869-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="11869-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="11869-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="11869-112">Example</span></span>  
 <span data-ttu-id="11869-113">W tym przykładzie przeprowadza <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem `SalesOrderHeader` i `SalesOrderDetail` tabele, aby znaleźć numer zamówienia na klienta.</span><span class="sxs-lookup"><span data-stu-id="11869-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="11869-114">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej), nawet jeśli skorelowane elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="11869-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="11869-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="11869-115">Example</span></span>  
 <span data-ttu-id="11869-116">W tym przykładzie przeprowadza <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem `Contact` i `SalesOrderHeader` tabel.</span><span class="sxs-lookup"><span data-stu-id="11869-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="11869-117">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej), nawet jeśli skorelowane elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="11869-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="11869-118">Łączenie</span><span class="sxs-lookup"><span data-stu-id="11869-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="11869-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="11869-119">Example</span></span>  
 <span data-ttu-id="11869-120">W tym przykładzie wykonuje sprzężenie za pośrednictwem `SalesOrderHeader` i `SalesOrderDetail` tabele, aby pobrać zamówień online w ciągu miesiąca sierpnia.</span><span class="sxs-lookup"><span data-stu-id="11869-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="11869-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11869-121">See Also</span></span>  
 [<span data-ttu-id="11869-122">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="11869-122">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="11869-123">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="11869-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="11869-124">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="11869-124">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
