---
title: "Porady: Wywołaj funkcje bazy danych"
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
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4395128abc3a8f604eee762479bc1a26bed7f95b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="f0afd-102">Porady: Wywołaj funkcje bazy danych</span><span class="sxs-lookup"><span data-stu-id="f0afd-102">How to: Call Database Functions</span></span>
<span data-ttu-id="f0afd-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Klasa zawiera metody, które udostępniają funkcje programu SQL Server do użycia w składniku LINQ do jednostek zapytań.</span><span class="sxs-lookup"><span data-stu-id="f0afd-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="f0afd-104">Jeśli używasz <xref:System.Data.Objects.SqlClient.SqlFunctions> metody w technologii LINQ do jednostek zapytań, odpowiednie funkcje bazy danych są wykonywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f0afd-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0afd-105">Funkcje bazy danych, wykonywanie obliczeń na zbiór wartości, które zwraca pojedynczą wartość (znanej także jako funkcje agregujące bazy danych), może być wywoływany bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f0afd-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="f0afd-106">Inne funkcje canonical można wywołać tylko w ramach zapytania składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="f0afd-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="f0afd-107">Aby wywołać funkcję agregującą bezpośrednio, należy podać <xref:System.Data.Objects.ObjectQuery%601> funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0afd-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="f0afd-108">Aby uzyskać więcej informacji zobacz drugi przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="f0afd-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0afd-109">Metody w <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy są specyficzne dla funkcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f0afd-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="f0afd-110">Podobne klas, które udostępniają funkcje bazy danych mogą być dostępne za pośrednictwem innych dostawców.</span><span class="sxs-lookup"><span data-stu-id="f0afd-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0afd-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0afd-111">Example</span></span>  
 <span data-ttu-id="f0afd-112">W poniższym przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="f0afd-112">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="f0afd-113">Przykład wykonuje zapytania składnika LINQ to Entities używającej <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metodę, aby zwrócić wszystkie kontakty, których nazwisko zaczyna się od "Si":</span><span class="sxs-lookup"><span data-stu-id="f0afd-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f0afd-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0afd-114">Example</span></span>  
 <span data-ttu-id="f0afd-115">W poniższym przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="f0afd-115">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="f0afd-116">Przykład wywołuje agregacji <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metody bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f0afd-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="f0afd-117">Należy pamiętać, że <xref:System.Data.Objects.ObjectQuery%601> została przekazana do funkcji, co umożliwia można wywołać bez części zapytania składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="f0afd-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f0afd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0afd-118">See Also</span></span>  
 [<span data-ttu-id="f0afd-119">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f0afd-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="f0afd-120">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f0afd-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
