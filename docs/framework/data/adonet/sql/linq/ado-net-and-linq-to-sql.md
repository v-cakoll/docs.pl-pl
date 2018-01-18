---
title: ADO.NET i LINQ do SQL
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
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c95a84bafcb32861e299135feb0b89b931d11165
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="2ff00-102">ADO.NET i LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="2ff00-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2ff00-103">wchodzi w skład [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodziny technologii.</span><span class="sxs-lookup"><span data-stu-id="2ff00-103"> is part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies.</span></span> <span data-ttu-id="2ff00-104">Jest on oparty na usług świadczonych przez [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] dostawcy modelu.</span><span class="sxs-lookup"><span data-stu-id="2ff00-104">It is based on services provided by the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] provider model.</span></span> <span data-ttu-id="2ff00-105">W związku z tym można łączyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu z istniejącym [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplikacji i przeprowadzić migrację bieżącego [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rozwiązania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2ff00-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] applications and migrate current [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2ff00-106">Poniższa ilustracja przedstawia ogólny widok relacji.</span><span class="sxs-lookup"><span data-stu-id="2ff00-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="2ff00-107">![LINQ do SQL i ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="2ff00-107">![LINQ to SQL and ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="2ff00-108">Połączenia</span><span class="sxs-lookup"><span data-stu-id="2ff00-108">Connections</span></span>  
 <span data-ttu-id="2ff00-109">Możesz podać istniejące [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] połączenia podczas tworzenia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="2ff00-109">You can supply an existing [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="2ff00-110">Wszystkie operacje przed <xref:System.Data.Linq.DataContext> (w tym zapytań) Użyj tej podane połączenie.</span><span class="sxs-lookup"><span data-stu-id="2ff00-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="2ff00-111">Jeśli połączenie jest już otwarty, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozostawia go jako jest po zakończeniu pracy z nim.</span><span class="sxs-lookup"><span data-stu-id="2ff00-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="2ff00-112">Zawsze możesz uzyskiwać dostęp do połączenia i zamknij je samodzielnie przy użyciu <xref:System.Data.Linq.DataContext.Connection%2A> właściwości, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="2ff00-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="2ff00-113">Transakcje</span><span class="sxs-lookup"><span data-stu-id="2ff00-113">Transactions</span></span>  
 <span data-ttu-id="2ff00-114">Możesz podać Twoje <xref:System.Data.Linq.DataContext> przy użyciu własnego transakcji bazy danych w przypadku aplikacji zainicjował już transakcji użytkownika <xref:System.Data.Linq.DataContext> zaangażować.</span><span class="sxs-lookup"><span data-stu-id="2ff00-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="2ff00-115">Preferowaną metodą prowadzenia transakcji z [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] jest użycie <xref:System.Transactions.TransactionScope> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ff00-115">The preferred method of doing transactions with the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="2ff00-116">Przy użyciu tej metody, możesz wprowadzić transakcji rozproszonych, obsługiwanych przez baz danych i menedżerów innych rezydentny zasobów.</span><span class="sxs-lookup"><span data-stu-id="2ff00-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="2ff00-117">Zakresy transakcji wymaga niewielkiej ilości zasobów, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="2ff00-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="2ff00-118">One przełącza się do transakcji rozproszonych tylko wtedy, gdy wiele połączeń w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="2ff00-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="2ff00-119">Nie można użyć tej metody dla wszystkich baz danych.</span><span class="sxs-lookup"><span data-stu-id="2ff00-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="2ff00-120">Na przykład połączenie SqlClient nie można podwyższyć poziomu transakcji systemu podczas działania przed [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] serwera.</span><span class="sxs-lookup"><span data-stu-id="2ff00-120">For example, the SqlClient connection cannot promote system transactions when it works against a [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] server.</span></span> <span data-ttu-id="2ff00-121">Zamiast tego automatycznie współdziała on do pełnego transakcji rozproszonej przy każdym stwierdzeniu zakresu transakcji używany.</span><span class="sxs-lookup"><span data-stu-id="2ff00-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="2ff00-122">Poleceń SQL bezpośredniego</span><span class="sxs-lookup"><span data-stu-id="2ff00-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="2ff00-123">Czasami może wystąpić sytuacje gdzie zdolność <xref:System.Data.Linq.DataContext> do wykonywania kwerend lub przesyłania zmian jest niewystarczający dla specjalne zadanie, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="2ff00-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="2ff00-124">W takiej sytuacji można użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metody w celu wydawania polecenia SQL z bazą danych i przekonwertować na obiekty wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="2ff00-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="2ff00-125">Załóżmy na przykład, że dane dla `Customer` klasy jest rozkładu ponad dwie tabele (customer1 i customer2).</span><span class="sxs-lookup"><span data-stu-id="2ff00-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="2ff00-126">Następujące zapytanie zwraca sekwencji `Customer` obiektów:</span><span class="sxs-lookup"><span data-stu-id="2ff00-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="2ff00-127">Tak długo, jak nazwy kolumn w wynikach tabelarycznym odpowiada właściwości kolumny klasy jednostki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty poza każde zapytanie SQL.</span><span class="sxs-lookup"><span data-stu-id="2ff00-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="2ff00-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff00-128">Parameters</span></span>  
 <span data-ttu-id="2ff00-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda przyjmuje parametry.</span><span class="sxs-lookup"><span data-stu-id="2ff00-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="2ff00-130">Poniższy kod wykonuje zapytania parametrycznego:</span><span class="sxs-lookup"><span data-stu-id="2ff00-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="2ff00-131">Parametry są wyrażane w tekst zapytania przy użyciu tego samego notacji klamrowych używanych przez `Console.WriteLine()` i `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="2ff00-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="2ff00-132">`String.Format()`pobiera ciąg zapytania, podaj i zastępuje takich jak parametry nawiasach klamrowych z nazwy parametru wygenerowanego `@p0`, `@p1` ..., `@p(n)`.</span><span class="sxs-lookup"><span data-stu-id="2ff00-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff00-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff00-133">See Also</span></span>  
 [<span data-ttu-id="2ff00-134">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="2ff00-134">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="2ff00-135">Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext</span><span class="sxs-lookup"><span data-stu-id="2ff00-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
