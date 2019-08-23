---
title: 'Instrukcje: Wywoływanie funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: dd440be3f73eb2f02a269a8cad29f0fe30920836
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936026"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="66647-102">Instrukcje: Wywoływanie funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="66647-102">How to: Call Database Functions</span></span>
<span data-ttu-id="66647-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Klasa zawiera metody, które uwidaczniają SQL Server funkcje używane w zapytaniach LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="66647-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="66647-104">W przypadku używania <xref:System.Data.Objects.SqlClient.SqlFunctions> metod w LINQ to Entities zapytaniach odpowiednie funkcje bazy danych są wykonywane w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="66647-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66647-105">Funkcje bazy danych, które wykonują obliczenia na zestawie wartości i zwracają pojedynczą wartość (znaną również jako zagregowane funkcje bazy danych), mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="66647-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="66647-106">Inne funkcje kanoniczne można wywołać tylko jako część zapytania LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="66647-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="66647-107">Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji.</span><span class="sxs-lookup"><span data-stu-id="66647-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="66647-108">Aby uzyskać więcej informacji, zobacz drugi przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="66647-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66647-109">Metody w <xref:System.Data.Objects.SqlClient.SqlFunctions> klasie są specyficzne dla SQL Server funkcji.</span><span class="sxs-lookup"><span data-stu-id="66647-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="66647-110">Podobne klasy, które uwidaczniają funkcje bazy danych, mogą być dostępne przez innych dostawców.</span><span class="sxs-lookup"><span data-stu-id="66647-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66647-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="66647-111">Example</span></span>  
 <span data-ttu-id="66647-112">W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="66647-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="66647-113">Przykład wykonuje kwerendę LINQ to Entities, która używa <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metody do zwracania wszystkich kontaktów, których nazwisko zaczyna się od "si":</span><span class="sxs-lookup"><span data-stu-id="66647-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="66647-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="66647-114">Example</span></span>  
 <span data-ttu-id="66647-115">W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="66647-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="66647-116">Przykład wywołuje metodę Aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="66647-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="66647-117">Należy zauważyć, <xref:System.Data.Objects.ObjectQuery%601> że do funkcji jest przenoszona funkcja, która umożliwia jej wywoływanie bez części zapytania LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="66647-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="66647-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66647-118">See also</span></span>

- [<span data-ttu-id="66647-119">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="66647-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="66647-120">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="66647-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
