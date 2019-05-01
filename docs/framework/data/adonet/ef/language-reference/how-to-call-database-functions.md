---
title: 'Instrukcje: Wywoływanie funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 5990e9f4c08eafeae6bed18d3d8af0617b84ff54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774598"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="4e234-102">Instrukcje: Wywoływanie funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="4e234-102">How to: Call Database Functions</span></span>
<span data-ttu-id="4e234-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Klasa zawiera metody, które udostępniają funkcje programu SQL Server do użycia w składniku LINQ do zapytań jednostki.</span><span class="sxs-lookup"><span data-stu-id="4e234-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="4e234-104">Kiedy używasz <xref:System.Data.Objects.SqlClient.SqlFunctions> metody w składniku LINQ do kwerendy jednostek, z odpowiednimi funkcjami bazy danych są wykonywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4e234-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e234-105">Funkcje bazy danych, wykonywania obliczeń na zbiór wartości, które zwraca pojedynczą wartość (znany także jako funkcje agregujące bazy danych), może być wywoływany bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="4e234-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="4e234-106">Inne funkcje canonical można wywołać tylko jako część zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4e234-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="4e234-107">Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji.</span><span class="sxs-lookup"><span data-stu-id="4e234-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="4e234-108">Aby uzyskać więcej informacji zobacz drugi przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="4e234-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e234-109">Metody w <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy są specyficzne dla funkcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4e234-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="4e234-110">Podobne klas, które udostępniają funkcje bazy danych mogą być dostępne za pośrednictwem innych dostawców.</span><span class="sxs-lookup"><span data-stu-id="4e234-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e234-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e234-111">Example</span></span>  
 <span data-ttu-id="4e234-112">W poniższym przykładzie użyto [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="4e234-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="4e234-113">Kod w przykładzie wykonuje zapytaniu składnika LINQ to Entities używającej <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metodę, aby zwrócić wszystkie kontakty, których nazwisko zaczyna się od "Si":</span><span class="sxs-lookup"><span data-stu-id="4e234-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="4e234-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e234-114">Example</span></span>  
 <span data-ttu-id="4e234-115">W poniższym przykładzie użyto [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="4e234-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="4e234-116">Przykład wywołuje agregacji <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> bezpośrednio metodę.</span><span class="sxs-lookup"><span data-stu-id="4e234-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="4e234-117">Należy pamiętać, że <xref:System.Data.Objects.ObjectQuery%601> jest przekazywany do funkcji, co pozwala na można wywołać bez bycie częścią zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4e234-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4e234-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e234-118">See also</span></span>

- [<span data-ttu-id="4e234-119">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4e234-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="4e234-120">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4e234-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
