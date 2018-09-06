---
title: Integracja System.Transactions z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 31edbc8f4cbb09f8720b373780f1b0646a985b20
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884185"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="ef045-102">Integracja System.Transactions z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="ef045-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="ef045-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Wersji 2.0 wprowadzono framework transakcji, który jest możliwy za pośrednictwem <xref:System.Transactions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ef045-103">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="ef045-104">Ta platforma udostępnia transakcji w taki sposób, że jest w pełni zintegrowana w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], w tym [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef045-104">This framework exposes transactions in a way that is fully integrated in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], including [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="ef045-105">Oprócz rozszerzenia programowania <xref:System.Transactions> i [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mogą współpracować ze sobą do koordynowania optymalizacje podczas pracy z transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef045-105">In addition to the programmability enhancements, <xref:System.Transactions> and [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="ef045-106">Awansowanie transakcja jest uproszczone transakcji (local), która może być automatycznie podwyższony do transakcji rozproszonej pełni na zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="ef045-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="ef045-107">Począwszy od [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> obsługuje transakcje awansowanie, podczas pracy z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef045-107">Starting with [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="ef045-108">Awansowanie transakcji nie jest wywoływany dodano obciążenie z transakcji rozproszonych, chyba że dodany obciążenie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="ef045-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="ef045-109">Awansowanie transakcje są automatyczne i wymagają interwencji od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="ef045-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="ef045-110">Awansowanie transakcje są dostępne tylko, gdy używasz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef045-110">Promotable transactions are only available when you use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="ef045-111">Tworzenie awansowanie transakcji</span><span class="sxs-lookup"><span data-stu-id="ef045-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="ef045-112">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server zapewnia obsługę awansowanie transakcji, które są obsługiwane za pośrednictwem klasy w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ef045-112">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="ef045-113">Transakcje awansowanie Optymalizowanie transakcji rozproszonych opóźnienie tworzenia transakcji rozproszonej, dopóki nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="ef045-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="ef045-114">Jeśli jeden usługi resource manager jest wymagany tylko, występuje nie transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef045-115">W przypadku częściowo zaufanych <xref:System.Transactions.DistributedTransactionPermission> jest wymagana, gdy transakcja zostanie podwyższony do poziomu transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="ef045-116">Scenariusze awansowanie transakcji</span><span class="sxs-lookup"><span data-stu-id="ef045-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="ef045-117">Transakcje rozproszone zwykle używanie zasobów systemowych znaczące, są zarządzane przez program Microsoft Distributed Transaction Coordinator (MS DTC), którą można zintegrować z wszystkich menedżerów zasobów dostępne w ramach transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef045-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="ef045-118">Awansowanie transakcja jest specjalną postać <xref:System.Transactions> transakcji, które skutecznie deleguje pracy proste transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef045-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="ef045-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, i programu SQL Server koordynować pracę niezbędną do obsługi transakcji, promowania go do pełnego transakcji rozproszonej, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="ef045-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="ef045-120">Zaletą używania awansowanie transakcji jest fakt, że połączenie jest otwarte przy użyciu aktywnego <xref:System.Transactions.TransactionScope> transakcji, a żadne inne połączenia są otwarte, zatwierdzeń transakcji jako lekkie transakcje, zamiast ponoszenia dodatkowych koszty pełną transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="ef045-121">Słowa kluczowe parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="ef045-121">Connection String Keywords</span></span>  
 <span data-ttu-id="ef045-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Właściwość obsługuje słowem kluczowym `Enlist`, wskazuje, czy <xref:System.Data.SqlClient> wykryje kontekstów transakcyjne i automatycznie zarejestrować połączenia w ramach transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="ef045-123">Jeśli `Enlist=true`, połączenie jest automatycznie zarejestrowany w wątku otwierania bieżący kontekst transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef045-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="ef045-124">Jeśli `Enlist=false`, `SqlClient` połączenia nie wchodzi w interakcję z transakcji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="ef045-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="ef045-125">Wartością domyślną dla `Enlist` ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="ef045-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="ef045-126">Jeśli `Enlist` nie określono w parametrach połączenia, połączenie jest automatycznie zarejestrowany w transakcji rozproszonej, po wykryciu jednego po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ef045-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="ef045-127">`Transaction Binding` Słów kluczowych w <xref:System.Data.SqlClient.SqlConnection> parametry połączenia kontrolować połączenia do skojarzenia z zobowiązaniom `System.Transactions` transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef045-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="ef045-128">Jest również dostępna za pośrednictwem <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="ef045-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="ef045-129">W poniższej tabeli opisano możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="ef045-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="ef045-130">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="ef045-130">Keyword</span></span>|<span data-ttu-id="ef045-131">Opis</span><span class="sxs-lookup"><span data-stu-id="ef045-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef045-132">Niejawne Unbind</span><span class="sxs-lookup"><span data-stu-id="ef045-132">Implicit Unbind</span></span>|<span data-ttu-id="ef045-133">Domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ef045-133">The default.</span></span> <span data-ttu-id="ef045-134">Połączenie odłącza się od transakcji po jej zakończeniu, przełączanie do trybu automatycznego zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="ef045-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="ef045-135">Jawne usuwanie powiązania</span><span class="sxs-lookup"><span data-stu-id="ef045-135">Explicit Unbind</span></span>|<span data-ttu-id="ef045-136">Połączenie nadal jest dołączony do transakcji przed zamknięciem transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef045-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="ef045-137">Połączenie zakończy się niepowodzeniem, jeśli skojarzone transakcji jest nieaktywny lub nie jest zgodny <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef045-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="ef045-138">Za pomocą elementu TransactionScope</span><span class="sxs-lookup"><span data-stu-id="ef045-138">Using TransactionScope</span></span>  
 <span data-ttu-id="ef045-139"><xref:System.Transactions.TransactionScope> Klasy sprawia, że blok kodu transakcyjnych przez niejawnie wywołanie tej metody połączenia, w ramach transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="ef045-140">Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metody na końcu <xref:System.Transactions.TransactionScope> blok przed opuszczeniem go.</span><span class="sxs-lookup"><span data-stu-id="ef045-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="ef045-141">Pozostawiając blok wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef045-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="ef045-142">Jeśli został zgłoszony wyjątek, powoduje, że kod, aby pozostawić zakresu transakcji jest traktowane jak zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="ef045-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="ef045-143">Zaleca się, że używasz `using` bloku, aby upewnić się, że <xref:System.Transactions.TransactionScope.Dispose%2A> jest wywoływana w <xref:System.Transactions.TransactionScope> obiektów modułu za pomocą polecenia w przypadku bloku jest został zakończony.</span><span class="sxs-lookup"><span data-stu-id="ef045-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="ef045-144">Nie można przekazać ani wycofać oczekujące transakcje mogą znacznie pogorszyć wydajność, ponieważ domyślny limit czasu dla <xref:System.Transactions.TransactionScope> jest jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="ef045-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="ef045-145">Jeśli nie używasz `using` instrukcji, należy wykonać całą pracę w `Try` blokowania i jawnie wywołać <xref:System.Transactions.TransactionScope.Dispose%2A> method in Class metoda `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ef045-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="ef045-146">Jeśli wystąpi wyjątek w <xref:System.Transactions.TransactionScope>, transakcja jest oznaczone jako niespójne i zostanie porzucony.</span><span class="sxs-lookup"><span data-stu-id="ef045-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="ef045-147">Zostanie wycofana ponownie po <xref:System.Transactions.TransactionScope> zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="ef045-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="ef045-148">Jeśli nie wystąpi wyjątek, zatwierdzania transakcji uczestniczących w programie.</span><span class="sxs-lookup"><span data-stu-id="ef045-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef045-149">`TransactionScope` Klasy tworzy transakcji z <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ef045-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="ef045-150">W zależności od aplikacji warto wziąć pod uwagę obniżenia poziomu izolacji, aby uniknąć rywalizacji o wysokiej w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef045-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef045-151">Zaleca się, wykonaj tylko aktualizacji, wstawiania, i usuwa w transakcje rozproszone, ponieważ korzystają z zasobów znaczących bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ef045-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="ef045-152">Instrukcji "Select" może zablokować niepotrzebnie zasobów bazy danych, a w niektórych scenariuszach może być konieczne użycie transakcji do wybiera.</span><span class="sxs-lookup"><span data-stu-id="ef045-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="ef045-153">Wszelkie prace bez bazy danych powinna być podejmowana poza zakres transakcji, o ile nie dotyczy innych menedżerów zasobów transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="ef045-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="ef045-154">Mimo że wyjątek w zakresie transakcji zapobiega transakcji z zatwierdzeniem, <xref:System.Transactions.TransactionScope> klasa nie ma możliwości obsługi dla wycofywania zmian kodu podejścia biznesowego uczyniło poza zakresem transakcja.</span><span class="sxs-lookup"><span data-stu-id="ef045-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="ef045-155">Jeśli zachodzi potrzeba wykonania określonego działania, gdy transakcja zostanie wycofana, należy napisać własną implementację <xref:System.Transactions.IEnlistmentNotification> interfejs i jawnie zarejestrować transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef045-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef045-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef045-156">Example</span></span>  
 <span data-ttu-id="ef045-157">Praca z <xref:System.Transactions> wymaga odwołania do System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="ef045-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="ef045-158">Następująca funkcja przedstawia sposób tworzenia awansowanie transakcji dla dwóch różnych wystąpień programu SQL Server, reprezentowany przez dwa różne <xref:System.Data.SqlClient.SqlConnection> obiektów, które są opakowane w <xref:System.Transactions.TransactionScope> bloku.</span><span class="sxs-lookup"><span data-stu-id="ef045-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="ef045-159">Ten kod tworzy <xref:System.Transactions.TransactionScope> blokowania z `using` instrukcji i otwiera pierwszego połączenia, które automatycznie powoduje zarejestrowanie go w <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="ef045-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="ef045-160">Transakcja jest początkowo zarejestrowany jako uproszczone transakcji, a nie pełne transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="ef045-161">Drugie połączenie jest zarejestrowany w <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenia w pierwszym połączeniu nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ef045-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="ef045-162">Po otwarciu drugie połączenie transakcji jest automatycznie podwyższony do pełnego transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="ef045-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="ef045-163"><xref:System.Transactions.TransactionScope.Complete%2A> Wywołaniu metody, które zatwierdzeń transakcji, tylko wtedy, gdy żadne wyjątki nie były zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="ef045-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="ef045-164">Jeśli w dowolnym momencie został zgłoszony wyjątek <xref:System.Transactions.TransactionScope> bloku, `Complete` będą nie należy wywoływać i będzie transakcji rozproszonej, Przywróć ponownie po <xref:System.Transactions.TransactionScope> zostanie usunięty po zakończeniu jego `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="ef045-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef045-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef045-165">See Also</span></span>  
 [<span data-ttu-id="ef045-166">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="ef045-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="ef045-167">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ef045-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
