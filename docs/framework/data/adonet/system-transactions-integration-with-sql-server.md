---
title: Integracja System.Transactions z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 25b443d8234909a4d8525c2ce2b4e70c3baa337b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965223"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="164ab-102">Integracja System.Transactions z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="164ab-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="164ab-103">W .NET Framework w wersji 2,0 wprowadzono strukturę transakcji, do której można uzyskać dostęp <xref:System.Transactions> za pomocą przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="164ab-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="164ab-104">Ta struktura uwidacznia transakcje w sposób, który jest w pełni zintegrowany w .NET Framework, w tym ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="164ab-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="164ab-105">Oprócz ulepszeń programistycznych, <xref:System.Transactions> a ADO.NET może współdziałać w celu koordynowania optymalizacji podczas pracy z transakcjami.</span><span class="sxs-lookup"><span data-stu-id="164ab-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="164ab-106">Transakcja promocji to lekki (lokalny) transakcję, którą można automatycznie podwyższyć do w pełni rozproszonej transakcji.</span><span class="sxs-lookup"><span data-stu-id="164ab-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="164ab-107">Począwszy od ADO.NET 2,0, <xref:System.Data.SqlClient> obsługuje transakcje promocji podczas pracy z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="164ab-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="164ab-108">Transakcja promocji nie wywołuje dodanego nakładu transakcji rozproszonej, chyba że jest wymagane dodatkowe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="164ab-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="164ab-109">Transakcje promocji są automatyczne i nie wymagają żadnej interwencji z dewelopera.</span><span class="sxs-lookup"><span data-stu-id="164ab-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="164ab-110">Transakcje promocyjne są dostępne tylko wtedy, gdy używasz dostawca danych .NET Framework dla SQL Server (`SqlClient`) z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="164ab-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="164ab-111">Tworzenie transakcji promocji</span><span class="sxs-lookup"><span data-stu-id="164ab-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="164ab-112">Dostawca .NET Framework dla SQL Server zapewnia obsługę transakcji promocji, które są obsługiwane przez klasy w przestrzeni nazw .NET Framework <xref:System.Transactions> .</span><span class="sxs-lookup"><span data-stu-id="164ab-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="164ab-113">Transakcje promocyjne optymalizują transakcje rozproszone przez odroczenie tworzenia transakcji rozproszonej do momentu, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="164ab-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="164ab-114">Jeśli jest wymagany tylko jeden Menedżer zasobów, nie są wykonywane żadne transakcje rozproszone.</span><span class="sxs-lookup"><span data-stu-id="164ab-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="164ab-115">W częściowo zaufanym scenariuszu <xref:System.Transactions.DistributedTransactionPermission> jest to wymagane, gdy transakcja jest podwyższana do transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="164ab-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="164ab-116">Scenariusze transakcji promocji</span><span class="sxs-lookup"><span data-stu-id="164ab-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="164ab-117">Transakcje rozproszone zazwyczaj zużywają znaczne zasoby systemowe zarządzane przez firmę Microsoft Distributed Transaction Coordinator (MS DTC), które integrują wszystkich menedżerów zasobów, do których uzyskuje dostęp w transakcji.</span><span class="sxs-lookup"><span data-stu-id="164ab-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="164ab-118">Transakcja promocji to specjalna forma <xref:System.Transactions> transakcji, która efektywnie deleguje prace do prostej transakcji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="164ab-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="164ab-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>i SQL Server koordynuje pracy związanej z obsługą transakcji, promując ją do pełnej transakcji rozproszonej w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="164ab-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="164ab-120">Korzyści wynikające z korzystania z transakcji promocyjnych polegają na tym, że gdy połączenie jest otwierane przy użyciu aktywnej <xref:System.Transactions.TransactionScope> transakcji, a żadne inne połączenia nie są otwierane, transakcja zostaje zatwierdzona jako uproszczona transakcja, zamiast naliczać dodatkowe narzuty za pełną transakcję rozproszoną.</span><span class="sxs-lookup"><span data-stu-id="164ab-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="164ab-121">Słowa kluczowe parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="164ab-121">Connection String Keywords</span></span>  
 <span data-ttu-id="164ab-122">Właściwość obsługuje słowo kluczowe, `Enlist`które wskazuje, czy <xref:System.Data.SqlClient> program będzie wykrywał konteksty transakcyjne i automatycznie zarejestrowana w transakcji rozproszonej. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A></span><span class="sxs-lookup"><span data-stu-id="164ab-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="164ab-123">Jeśli `Enlist=true`połączenie zostanie automatycznie zarejestrowane w bieżącym kontekście transakcji otwarcia wątku.</span><span class="sxs-lookup"><span data-stu-id="164ab-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="164ab-124">Jeśli `Enlist=false`połączenieniedziała wprzypadkutransakcjirozproszonej.`SqlClient`</span><span class="sxs-lookup"><span data-stu-id="164ab-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="164ab-125">Wartość domyślna dla `Enlist` ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="164ab-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="164ab-126">Jeśli `Enlist` wartość nie jest określona w parametrach połączenia, połączenie zostanie automatycznie zarejestrowane w transakcji rozproszonej, jeśli zostanie wykryta po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="164ab-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="164ab-127">Słowa kluczowe w parametrach połączenia kontrolują skojarzenie połączenia z zarejestrowaną `System.Transactions` transakcją. <xref:System.Data.SqlClient.SqlConnection> `Transaction Binding`</span><span class="sxs-lookup"><span data-stu-id="164ab-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="164ab-128">Jest ona również dostępna za pomocą <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> właściwości. <xref:System.Data.SqlClient.SqlConnectionStringBuilder></span><span class="sxs-lookup"><span data-stu-id="164ab-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="164ab-129">W poniższej tabeli opisano możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="164ab-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="164ab-130">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="164ab-130">Keyword</span></span>|<span data-ttu-id="164ab-131">Opis</span><span class="sxs-lookup"><span data-stu-id="164ab-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="164ab-132">Niejawne powiązanie</span><span class="sxs-lookup"><span data-stu-id="164ab-132">Implicit Unbind</span></span>|<span data-ttu-id="164ab-133">Domyślnie.</span><span class="sxs-lookup"><span data-stu-id="164ab-133">The default.</span></span> <span data-ttu-id="164ab-134">Połączenie zostanie odłączone od transakcji po jej zakończeniu, przełączając z powrotem do trybu automatycznego zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="164ab-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="164ab-135">Jawne powiązanie powiązania</span><span class="sxs-lookup"><span data-stu-id="164ab-135">Explicit Unbind</span></span>|<span data-ttu-id="164ab-136">Połączenie pozostaje dołączone do transakcji do momentu zamknięcia transakcji.</span><span class="sxs-lookup"><span data-stu-id="164ab-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="164ab-137">Połączenie zakończy się niepowodzeniem, jeśli skojarzona transakcja nie jest aktywna lub <xref:System.Transactions.Transaction.Current%2A>nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="164ab-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="164ab-138">Używanie elementu TransactionScope</span><span class="sxs-lookup"><span data-stu-id="164ab-138">Using TransactionScope</span></span>  
 <span data-ttu-id="164ab-139"><xref:System.Transactions.TransactionScope> Klasa wywołuje kod transakcyjny przez niejawnie zarejestrowane połączenia w transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="164ab-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="164ab-140">Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metodę na końcu <xref:System.Transactions.TransactionScope> bloku przed opuszczeniem go.</span><span class="sxs-lookup"><span data-stu-id="164ab-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="164ab-141">Wyjście bloku wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="164ab-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="164ab-142">Jeśli wystąpił wyjątek, który powoduje, że kod opuszcza zakres, transakcja jest traktowana jako przerwana.</span><span class="sxs-lookup"><span data-stu-id="164ab-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="164ab-143">Zalecamy użycie `using` bloku, aby upewnić się, że <xref:System.Transactions.TransactionScope.Dispose%2A> jest wywoływana na <xref:System.Transactions.TransactionScope> obiekcie, gdy blok using zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="164ab-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="164ab-144">Nie można zatwierdzić lub wycofać oczekujących transakcji może znacząco spowodować uszkodzenie wydajności, ponieważ domyślny <xref:System.Transactions.TransactionScope> limit czasu wynosi minutę.</span><span class="sxs-lookup"><span data-stu-id="164ab-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="164ab-145">Jeśli nie używasz `using` instrukcji, musisz wykonać wszystkie czynności `Try` w <xref:System.Transactions.TransactionScope.Dispose%2A> bloku i jawnie `Finally` wywołać metodę w bloku.</span><span class="sxs-lookup"><span data-stu-id="164ab-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="164ab-146">Jeśli wystąpi wyjątek w <xref:System.Transactions.TransactionScope>, transakcja jest oznaczona jako niespójna i została porzucona.</span><span class="sxs-lookup"><span data-stu-id="164ab-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="164ab-147">Zostanie wycofany po <xref:System.Transactions.TransactionScope> usunięciu.</span><span class="sxs-lookup"><span data-stu-id="164ab-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="164ab-148">Jeśli żaden wyjątek nie wystąpi, uczestniczące transakcje są zatwierdzane.</span><span class="sxs-lookup"><span data-stu-id="164ab-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="164ab-149">Klasa tworzy transakcję <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` wartością domyślną. `TransactionScope`</span><span class="sxs-lookup"><span data-stu-id="164ab-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="164ab-150">W zależności od aplikacji warto rozważyć obniżenie poziomu izolacji, aby uniknąć dużej rywalizacji w aplikację.</span><span class="sxs-lookup"><span data-stu-id="164ab-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="164ab-151">Zalecamy wykonywanie tylko aktualizacji, wstawianych i usuwanych transakcji rozproszonych, ponieważ zużywają one znaczne zasoby bazy danych.</span><span class="sxs-lookup"><span data-stu-id="164ab-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="164ab-152">Instrukcje SELECT mogą niepotrzebnie blokować zasoby bazy danych, a w niektórych scenariuszach może być konieczne użycie transakcji do wyboru.</span><span class="sxs-lookup"><span data-stu-id="164ab-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="164ab-153">Wszelkie zadania poza bazą danych powinny być wykonywane spoza zakresu transakcji, o ile nie obejmuje ona innych menedżerów zasobów transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="164ab-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="164ab-154">Chociaż wyjątek w zakresie transakcji uniemożliwia zatwierdzenie transakcji, <xref:System.Transactions.TransactionScope> Klasa nie ma do wycofania żadnych zmian wprowadzonych w kodzie poza zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="164ab-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="164ab-155">Jeśli konieczne jest wykonanie pewnej akcji w przypadku wycofania transakcji, należy napisać własną implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu i jawnie zarejestrować się w transakcji.</span><span class="sxs-lookup"><span data-stu-id="164ab-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="164ab-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="164ab-156">Example</span></span>  
 <span data-ttu-id="164ab-157">Praca z <xref:System.Transactions> programem wymaga odwołania do elementu System. Transactions. dll.</span><span class="sxs-lookup"><span data-stu-id="164ab-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="164ab-158">Poniższa funkcja pokazuje, jak utworzyć transakcję promocji dla dwóch różnych wystąpień SQL Server, reprezentowanych przez dwa <xref:System.Data.SqlClient.SqlConnection> różne obiekty, które są opakowane <xref:System.Transactions.TransactionScope> w bloku.</span><span class="sxs-lookup"><span data-stu-id="164ab-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="164ab-159">Kod tworzy <xref:System.Transactions.TransactionScope> blok `using` z instrukcją i otwiera pierwsze połączenie, które jest automatycznie <xref:System.Transactions.TransactionScope>rejestrowane w.</span><span class="sxs-lookup"><span data-stu-id="164ab-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="164ab-160">Transakcja jest początkowo rejestrowana jako uproszczona transakcja, a nie pełna transakcja rozproszona.</span><span class="sxs-lookup"><span data-stu-id="164ab-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="164ab-161">Drugie połączenie jest rejestrowane w <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenie w pierwszym połączeniu nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="164ab-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="164ab-162">Po otwarciu drugiego połączenia transakcja zostanie automatycznie podzielona na pełną transakcję rozproszoną.</span><span class="sxs-lookup"><span data-stu-id="164ab-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="164ab-163">Wywoływana <xref:System.Transactions.TransactionScope.Complete%2A> jest metoda, która zatwierdza transakcję tylko wtedy, gdy nie zgłoszono żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="164ab-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="164ab-164">Jeśli wyjątek został zgłoszony w <xref:System.Transactions.TransactionScope> dowolnym momencie w bloku, `Complete` nie zostanie wywołany, a transakcja rozproszona <xref:System.Transactions.TransactionScope> zostanie wycofana, gdy zostanie usunięty na końcu jego `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="164ab-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="164ab-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="164ab-165">See also</span></span>

- [<span data-ttu-id="164ab-166">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="164ab-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="164ab-167">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="164ab-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
