---
title: 'Przykłady składni wyrażeń zapytania: Dołącz do operatorów (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: c0bc66bfe78a52fe092890c070c339df1a89199d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088811"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="420b9-102">Przykłady składni wyrażeń zapytania: Dołącz do operatorów (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="420b9-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="420b9-103">Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, które mają żadnych relacji można nawigować do siebie nawzajem, takich jak tabel relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="420b9-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="420b9-104">Przyłączenia dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych przy użyciu obiektów mających wspólny atrybut w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="420b9-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="420b9-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) lub [standardowe operatory zapytań — Przegląd (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="420b9-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="420b9-106">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.GroupJoin%2A> i <xref:System.Linq.Enumerable.Join%2A> metod do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="420b9-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="420b9-107">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="420b9-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="420b9-108">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="420b9-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="420b9-109">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="420b9-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="420b9-110">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu LINQ to DataSet w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="420b9-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="420b9-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="420b9-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="420b9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="420b9-112">Example</span></span>  
 <span data-ttu-id="420b9-113">W tym przykładzie wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem `SalesOrderHeader` i `SalesOrderDetail` tabele, aby znaleźć numer zamówienia na klienta.</span><span class="sxs-lookup"><span data-stu-id="420b9-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="420b9-114">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet jeśli żadne elementy skorelowane znajdują się w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="420b9-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="420b9-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="420b9-115">Example</span></span>  
 <span data-ttu-id="420b9-116">W tym przykładzie wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem `Contact` i `SalesOrderHeader` tabel.</span><span class="sxs-lookup"><span data-stu-id="420b9-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="420b9-117">Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet jeśli żadne elementy skorelowane znajdują się w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="420b9-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="420b9-118">Łączenie</span><span class="sxs-lookup"><span data-stu-id="420b9-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="420b9-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="420b9-119">Example</span></span>  
 <span data-ttu-id="420b9-120">W tym przykładzie wykonuje sprzężenie `SalesOrderHeader` i `SalesOrderDetail` tabele, aby uzyskać zamówienia online z sierpień.</span><span class="sxs-lookup"><span data-stu-id="420b9-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="420b9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="420b9-121">See also</span></span>

- [<span data-ttu-id="420b9-122">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="420b9-122">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="420b9-123">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="420b9-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="420b9-124">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="420b9-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="420b9-125">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="420b9-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
