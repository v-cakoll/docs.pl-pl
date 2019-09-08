---
title: Transakcje i współbieżność
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 837fe6c42d64f7416dbd895e56a38d1a409e567a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791320"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="6c45b-102">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="6c45b-102">Transactions and Concurrency</span></span>
<span data-ttu-id="6c45b-103">Transakcja składa się z jednego polecenia lub grupy poleceń, które są wykonywane jako pakiet.</span><span class="sxs-lookup"><span data-stu-id="6c45b-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="6c45b-104">Transakcje umożliwiają łączenie wielu operacji w pojedynczą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="6c45b-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="6c45b-105">Jeśli wystąpi awaria w jednym punkcie transakcji, wszystkie aktualizacje można przywrócić do stanu sprzed transakcji.</span><span class="sxs-lookup"><span data-stu-id="6c45b-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="6c45b-106">Transakcja musi być zgodna z właściwościami KWASu — niepodzielności, spójności, izolacji i trwałości — w celu zagwarantowania spójności danych.</span><span class="sxs-lookup"><span data-stu-id="6c45b-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="6c45b-107">Większość systemów relacyjnej bazy danych, takich jak Microsoft SQL Server, obsługa transakcji przez zapewnienie blokowania, rejestrowania i zarządzania transakcjami za każdym razem, gdy aplikacja kliencka wykonuje operację Update, INSERT lub DELETE.</span><span class="sxs-lookup"><span data-stu-id="6c45b-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c45b-108">Transakcje obejmujące wiele zasobów mogą obniżać współbieżność, jeśli blokady są zbyt długie.</span><span class="sxs-lookup"><span data-stu-id="6c45b-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="6c45b-109">W związku z tym Zachowaj transakcje tak krótkie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6c45b-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="6c45b-110">Jeśli transakcja obejmuje wiele tabel w tej samej bazie danych lub serwerze, to jawne transakcje w procedurach składowanych często działają lepiej.</span><span class="sxs-lookup"><span data-stu-id="6c45b-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="6c45b-111">Można tworzyć transakcje w SQL Server procedury składowane przy użyciu instrukcji Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`i `ROLLBACK TRANSACTION` .</span><span class="sxs-lookup"><span data-stu-id="6c45b-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="6c45b-112">Aby uzyskać więcej informacji, zobacz SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="6c45b-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6c45b-113">Transakcje dotyczące różnych menedżerów zasobów, takich jak transakcja między SQL Server i Oracle, wymagają transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="6c45b-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c45b-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6c45b-114">In This Section</span></span>  
 [<span data-ttu-id="6c45b-115">Transakcje lokalne</span><span class="sxs-lookup"><span data-stu-id="6c45b-115">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="6c45b-116">Pokazuje, jak wykonywać transakcje względem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6c45b-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="6c45b-117">Transakcje rozproszone</span><span class="sxs-lookup"><span data-stu-id="6c45b-117">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="6c45b-118">Opisuje sposób wykonywania transakcji rozproszonych w programie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6c45b-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="6c45b-119">Integracja System.Transactions z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="6c45b-119">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="6c45b-120">Opisuje <xref:System.Transactions> integrację z SQL Server do pracy z transakcjami rozproszonymi.</span><span class="sxs-lookup"><span data-stu-id="6c45b-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="6c45b-121">Optymistyczna współbieżność</span><span class="sxs-lookup"><span data-stu-id="6c45b-121">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="6c45b-122">Opisuje optymistyczne i pesymistyczne współbieżność oraz sposób testowania naruszeń współbieżności.</span><span class="sxs-lookup"><span data-stu-id="6c45b-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c45b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c45b-123">See also</span></span>

- [<span data-ttu-id="6c45b-124">Podstawowe informacje dotyczące transakcji</span><span class="sxs-lookup"><span data-stu-id="6c45b-124">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="6c45b-125">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="6c45b-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="6c45b-126">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="6c45b-126">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="6c45b-127">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="6c45b-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="6c45b-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="6c45b-128">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="6c45b-129">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c45b-129">ADO.NET Overview</span></span>](ado-net-overview.md)
