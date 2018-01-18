---
title: "Transakcje i współbieżność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e6dfa946313bb9d43077bad68b761e8f03c175c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="7437c-102">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="7437c-102">Transactions and Concurrency</span></span>
<span data-ttu-id="7437c-103">Transakcja składa się z jednego polecenia lub grupy poleceń, które są wykonywane w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7437c-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="7437c-104">Transakcje pozwalają połączyć wiele operacji w pojedynczą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="7437c-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="7437c-105">Jeśli wystąpi błąd w jednym punkcie w transakcji, wszystkie aktualizacje można go z powrotem obniżyć do stanu przed transakcji.</span><span class="sxs-lookup"><span data-stu-id="7437c-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="7437c-106">Transakcja musi być zgodna z właściwości ACID — niepodzielność, spójności, izolacji i odporność — w celu zagwarantowania spójności danych.</span><span class="sxs-lookup"><span data-stu-id="7437c-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="7437c-107">Większość systemów relacyjnej bazy danych, takich jak Microsoft SQL Server, Obsługa transakcji podając, blokowanie, rejestrowanie i transakcji zarządzania urządzeń zawsze, gdy aplikacja kliencka przeprowadzi aktualizację, Wstaw lub operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="7437c-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7437c-108">Transakcje, które obejmują wiele zasobów można obniżyć współbieżności, jeśli blokady są przechowywane zbyt długa.</span><span class="sxs-lookup"><span data-stu-id="7437c-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="7437c-109">W związku z tym należy możliwie krótki transakcji.</span><span class="sxs-lookup"><span data-stu-id="7437c-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="7437c-110">Jeśli transakcja obejmuje wiele tabel w tej samej bazy danych lub serwerze, następnie jawnych transakcji w procedurach składowanych często działać lepiej.</span><span class="sxs-lookup"><span data-stu-id="7437c-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="7437c-111">Można utworzyć transakcji w procedurach składowanych serwera SQL przy użyciu języka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, i `ROLLBACK TRANSACTION` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="7437c-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="7437c-112">Aby uzyskać więcej informacji zobacz dokumentację SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="7437c-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="7437c-113">Transakcje dotyczące menedżerów różnych zasobów, takich jak transakcji między [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] i Oracle, wymagają transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="7437c-113">Transactions involving different resource managers, such as a transaction between [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7437c-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7437c-114">In This Section</span></span>  
 [<span data-ttu-id="7437c-115">Transakcje lokalne</span><span class="sxs-lookup"><span data-stu-id="7437c-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="7437c-116">Pokazuje, jak wykonywać transakcje w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7437c-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="7437c-117">Transakcje rozproszone</span><span class="sxs-lookup"><span data-stu-id="7437c-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="7437c-118">Opisuje sposób wykonywania transakcji rozproszonych w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7437c-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="7437c-119">Integracja System.Transactions z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="7437c-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="7437c-120">W tym artykule opisano <xref:System.Transactions> integracji z [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] do pracy z transakcji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="7437c-120">Describes <xref:System.Transactions> integration with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="7437c-121">Optymistyczna współbieżność</span><span class="sxs-lookup"><span data-stu-id="7437c-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="7437c-122">Opisuje optymistycznej i pesymistyczne współbieżności i jak można sprawdzić naruszenia współbieżności.</span><span class="sxs-lookup"><span data-stu-id="7437c-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7437c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7437c-123">See Also</span></span>  
 [<span data-ttu-id="7437c-124">Podstawowe informacje dotyczące transakcji</span><span class="sxs-lookup"><span data-stu-id="7437c-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="7437c-125">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="7437c-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="7437c-126">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="7437c-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="7437c-127">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="7437c-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="7437c-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="7437c-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="7437c-129">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="7437c-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
