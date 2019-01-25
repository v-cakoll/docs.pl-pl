---
title: Transakcje i współbieżność
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: f5efa8f25e3cd4dedec9e5a9c99db28320a4d93e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494057"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="db4fe-102">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="db4fe-102">Transactions and Concurrency</span></span>
<span data-ttu-id="db4fe-103">Transakcja składa się z jednego polecenia lub grupy poleceń, które są wykonywane w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="db4fe-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="db4fe-104">Transakcje pozwala połączyć wiele operacji w pojedynczą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="db4fe-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="db4fe-105">Jeśli wystąpi awaria w jednym punkcie w transakcji, wszystkie aktualizacje można wycofać do stanu wstępnego transakcji.</span><span class="sxs-lookup"><span data-stu-id="db4fe-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="db4fe-106">Transakcji musi odpowiadać właściwości ACID — niepodzielności, spójności, izolacji i trwałości — w celu zagwarantowania spójności danych.</span><span class="sxs-lookup"><span data-stu-id="db4fe-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="db4fe-107">Większość systemy relacyjnych baz danych, takich jak Microsoft SQL Server, transakcje pomocy technicznej, podając, blokowanie, rejestrowanie i transakcji Zarządzanie usługą zawsze wtedy, gdy aplikacja kliencka przeprowadzi aktualizację, wstawiania lub usuwania operacji.</span><span class="sxs-lookup"><span data-stu-id="db4fe-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db4fe-108">Transakcje obejmujące wiele zasobów można zmniejszyć współbieżność, jeśli blokady są przechowywane za długa.</span><span class="sxs-lookup"><span data-stu-id="db4fe-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="db4fe-109">W związku z tym Zachowaj możliwie krótkie transakcji.</span><span class="sxs-lookup"><span data-stu-id="db4fe-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="db4fe-110">Jeśli transakcja wiąże się z wielu tabel w tej samej bazy danych lub serwerze, następnie jawnego transakcji w procedurach składowanych często działać lepiej.</span><span class="sxs-lookup"><span data-stu-id="db4fe-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="db4fe-111">Można utworzyć transakcji w procedurach składowanych serwera SQL Server przy użyciu języka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, i `ROLLBACK TRANSACTION` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="db4fe-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="db4fe-112">Aby uzyskać więcej informacji zobacz dokumentację SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="db4fe-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="db4fe-113">Transakcje dotyczące inny zasób menedżerów, takich jak transakcji między programu SQL Server i Oracle, wymagają transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="db4fe-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db4fe-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="db4fe-114">In This Section</span></span>  
 [<span data-ttu-id="db4fe-115">Transakcje lokalne</span><span class="sxs-lookup"><span data-stu-id="db4fe-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="db4fe-116">Pokazuje, jak wykonywać transakcje w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="db4fe-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="db4fe-117">Transakcje rozproszone</span><span class="sxs-lookup"><span data-stu-id="db4fe-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="db4fe-118">W tym artykule opisano, jak wykonywać transakcje rozproszone w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="db4fe-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="db4fe-119">Integracja System.Transactions z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="db4fe-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="db4fe-120">W tym artykule opisano <xref:System.Transactions> integracji z programem SQL Server do pracy z transakcje rozproszone.</span><span class="sxs-lookup"><span data-stu-id="db4fe-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="db4fe-121">Optymistyczna współbieżność</span><span class="sxs-lookup"><span data-stu-id="db4fe-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="db4fe-122">W tym artykule opisano optymistyczne i pesymistycznej współbieżności i jak można sprawdzić, naruszenia współbieżności.</span><span class="sxs-lookup"><span data-stu-id="db4fe-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db4fe-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db4fe-123">See also</span></span>
- [<span data-ttu-id="db4fe-124">Podstawowe informacje dotyczące transakcji</span><span class="sxs-lookup"><span data-stu-id="db4fe-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [<span data-ttu-id="db4fe-125">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="db4fe-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="db4fe-126">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="db4fe-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="db4fe-127">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="db4fe-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="db4fe-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="db4fe-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="db4fe-129">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="db4fe-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
