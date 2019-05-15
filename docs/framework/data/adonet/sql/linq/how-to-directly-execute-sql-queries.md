---
title: 'Instrukcje: Bezpośrednie wykonywanie zapytań SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 04353361f8356b1d2b2aa3b930bb9b5ab88b9c0b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583692"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="722c1-102">Instrukcje: Bezpośrednie wykonywanie zapytań SQL</span><span class="sxs-lookup"><span data-stu-id="722c1-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="722c1-103">przekłada zapytania, napisany w sparametryzowane zapytania SQL (w postaci tekstu), a następnie wysyła je do programu SQL server dla przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="722c1-103">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="722c1-104">SQL nie można wykonać różnych metod, które mogą być dostępne lokalnie na aplikację.</span><span class="sxs-lookup"><span data-stu-id="722c1-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="722c1-105">próbuje przekonwertować te metody lokalne równoważne operacje i funkcje, które są dostępne w środowisku SQL.</span><span class="sxs-lookup"><span data-stu-id="722c1-105">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="722c1-106">Większość metod i operatory na wbudowanych typów programu .NET Framework mają bezpośredni tłumaczenia poleceń SQL.</span><span class="sxs-lookup"><span data-stu-id="722c1-106">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="722c1-107">Niektóre można tworzyć z funkcji, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="722c1-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="722c1-108">Tymi, które nie wygenerowały generować wyjątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="722c1-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="722c1-109">Aby uzyskać więcej informacji, zobacz [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="722c1-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="722c1-110">W przypadkach, gdzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania jest niewystarczająca dla specjalne zadanie, można użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodę, aby wykonać zapytania SQL, a następnie przekonwertować wynik zapytania bezpośrednio do obiektów.</span><span class="sxs-lookup"><span data-stu-id="722c1-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="722c1-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="722c1-111">Example</span></span>  
 <span data-ttu-id="722c1-112">W poniższym przykładzie przyjęto założenie, że dane dla `Customer` klasy jest rozłożona się powyżej dwóch tabel (serwer customer1 i customer2).</span><span class="sxs-lookup"><span data-stu-id="722c1-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="722c1-113">Zapytanie zwraca sekwencję `Customer` obiektów.</span><span class="sxs-lookup"><span data-stu-id="722c1-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="722c1-114">Tak długo, jak nazwy kolumn w wyniki tabelaryczne dopasować kolumny właściwości swojej klasy jednostki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty z dowolnego zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="722c1-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="722c1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="722c1-115">Example</span></span>  
 <span data-ttu-id="722c1-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda umożliwia również parametry.</span><span class="sxs-lookup"><span data-stu-id="722c1-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="722c1-117">Użyj następujący kod, aby wykonać zapytanie parametryczne.</span><span class="sxs-lookup"><span data-stu-id="722c1-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="722c1-118">Parametry są wyrażone w tekst zapytania przy użyciu takiej samej notacji nawiasów posługują się `Console.WriteLine()` i `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="722c1-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="722c1-119">W rzeczywistości `String.Format()` faktycznie jest wywoływana w ciągu zapytania zostaną podane, zastępując nawiasów parametrów nawiasach z wygenerowanych takich jak nazwy parametrów @p0, @p1 ..., @p(n).</span><span class="sxs-lookup"><span data-stu-id="722c1-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722c1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="722c1-120">See also</span></span>

- [<span data-ttu-id="722c1-121">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="722c1-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="722c1-122">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="722c1-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
