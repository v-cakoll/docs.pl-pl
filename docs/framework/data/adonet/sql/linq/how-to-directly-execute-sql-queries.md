---
title: "Porady: bezpośrednie wykonywanie zapytań SQL"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ccc47a1ea740c5106517f6f53620ddc8097c531
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="47dd4-102">Porady: bezpośrednie wykonywanie zapytań SQL</span><span class="sxs-lookup"><span data-stu-id="47dd4-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="47dd4-103">tłumaczy zapytania zostanie zapisany w sparametryzowane zapytania SQL (w postaci tekstu) i wysyła je do serwera SQL w celu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="47dd4-103"> translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="47dd4-104">SQL nie można wykonać różnych metod, które mogą być dostępne lokalnie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47dd4-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="47dd4-105">podejmuje próbę przekonwertowania te metody lokalne na równoważne operacji i funkcje, które są dostępne w środowisku SQL.</span><span class="sxs-lookup"><span data-stu-id="47dd4-105"> tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="47dd4-106">Większość metod i operatory w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wbudowanych typów ma bezpośredni tłumaczenia poleceń SQL.</span><span class="sxs-lookup"><span data-stu-id="47dd4-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="47dd4-107">Niektóre można wyprodukować z funkcji, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="47dd4-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="47dd4-108">Te, które nie mogą być tworzone Generowanie wyjątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="47dd4-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="47dd4-109">Aby uzyskać więcej informacji, zobacz [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="47dd4-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="47dd4-110">W przypadkach, gdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania jest niewystarczający dla specjalnych zadań, możesz użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodę, aby wykonać zapytania SQL, a następnie wykonać konwersję wyników kwerendy bezpośrednio do obiektów.</span><span class="sxs-lookup"><span data-stu-id="47dd4-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47dd4-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="47dd4-111">Example</span></span>  
 <span data-ttu-id="47dd4-112">W poniższym przykładzie przyjęto założenie, że dane dla `Customer` klasy jest rozkładu ponad dwie tabele (customer1 i customer2).</span><span class="sxs-lookup"><span data-stu-id="47dd4-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="47dd4-113">Zapytanie zwraca sekwencji `Customer` obiektów.</span><span class="sxs-lookup"><span data-stu-id="47dd4-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="47dd4-114">Tak długo, jak nazwy kolumn w wynikach tabelarycznym odpowiada właściwości kolumny klasy jednostki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty poza każde zapytanie SQL.</span><span class="sxs-lookup"><span data-stu-id="47dd4-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47dd4-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="47dd4-115">Example</span></span>  
 <span data-ttu-id="47dd4-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metody umożliwia także dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="47dd4-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="47dd4-117">Użyj kodu podobne do poniższych można wykonać zapytania parametrycznego.</span><span class="sxs-lookup"><span data-stu-id="47dd4-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="47dd4-118">Parametry są wyrażane w tekst zapytania przy użyciu tego samego notacji klamrowych używanych przez `Console.WriteLine()` i `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="47dd4-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="47dd4-119">W rzeczywistości `String.Format()` faktycznie jest wywoływana w ciągu kwerendy podasz, zastępując nawiasy nawiasach klamrowych parametrów z wygenerowany takich jak nazwy parametrów @p0, @p1 ..., @p(n).</span><span class="sxs-lookup"><span data-stu-id="47dd4-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47dd4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47dd4-120">See Also</span></span>  
 [<span data-ttu-id="47dd4-121">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="47dd4-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="47dd4-122">Zapytanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="47dd4-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
