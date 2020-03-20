---
title: Integracja System.Transactions z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174241"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="b76dc-102">Integracja System.Transactions z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="b76dc-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="b76dc-103">Program .NET Framework w wersji 2.0 wprowadził strukturę <xref:System.Transactions> transakcji, do których można uzyskać dostęp za pośrednictwem obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="b76dc-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="b76dc-104">Ta struktura udostępnia transakcje w sposób, który jest w pełni zintegrowany z .NET Framework, w tym ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b76dc-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="b76dc-105">Oprócz ulepszeń programowalności <xref:System.Transactions> i ADO.NET mogą współpracować w celu koordynowania optymalizacji podczas pracy z transakcjami.</span><span class="sxs-lookup"><span data-stu-id="b76dc-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="b76dc-106">Transakcja z możliwością promowania to lekka (lokalna) transakcja, która może być automatycznie promowana do w pełni rozproszonej transakcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="b76dc-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="b76dc-107">Począwszy od ADO.NET 2.0, <xref:System.Data.SqlClient> obsługuje transakcje promowane podczas pracy z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b76dc-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="b76dc-108">Transakcja z domosywana nie wywołuje dodatkowego obciążenia transakcji rozproszonej, chyba że wymagane jest dodatkowe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="b76dc-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="b76dc-109">Transakcje, które można promować, są automatyczne i nie wymagają interwencji ze strony dewelopera.</span><span class="sxs-lookup"><span data-stu-id="b76dc-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="b76dc-110">Transakcje z których można promować są dostępne tylko wtedy, gdy`SqlClient`używasz dostawcy danych programu .NET Framework dla programu SQL Server ( ) z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b76dc-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="b76dc-111">Tworzenie transakcji promowanych</span><span class="sxs-lookup"><span data-stu-id="b76dc-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="b76dc-112">Dostawca programu .NET Framework dla programu SQL Server zapewnia obsługę transakcji, które można <xref:System.Transactions> promować, które są obsługiwane za pośrednictwem klas w obszarze nazw programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b76dc-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="b76dc-113">Transakcje promowane optymalizują transakcje rozproszone, odraczając tworzenie transakcji rozproszonej, dopóki nie jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="b76dc-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="b76dc-114">Jeśli wymagany jest tylko jeden menedżer zasobów, nie występuje żadna transakcja rozproszona.</span><span class="sxs-lookup"><span data-stu-id="b76dc-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b76dc-115">W scenariuszu częściowo zaufany <xref:System.Transactions.DistributedTransactionPermission> jest wymagane, gdy transakcja jest promowany do transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="b76dc-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="b76dc-116">Scenariusze transakcji promowanych</span><span class="sxs-lookup"><span data-stu-id="b76dc-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="b76dc-117">Transakcje rozproszone zazwyczaj zużywają znaczne zasoby systemowe, zarządzane przez koordynatora transakcji rozproszonych firmy Microsoft (MS DTC), który integruje wszystkich menedżerów zasobów dostępnych w transakcji.</span><span class="sxs-lookup"><span data-stu-id="b76dc-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="b76dc-118">Transakcja z do promowania jest <xref:System.Transactions> specjalną formą transakcji, która skutecznie deleguje pracę do prostej transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b76dc-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="b76dc-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>a SQL Server koordynują pracę związaną z obsługą transakcji, promując ją do pełnej transakcji rozproszonej w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="b76dc-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="b76dc-120">Zaletą korzystania z transakcji można promować jest to, że <xref:System.Transactions.TransactionScope> gdy połączenie jest otwierane przy użyciu aktywnej transakcji, a żadne inne połączenia są otwierane, transakcja zatwierdza jako lekka transakcja, zamiast ponosić dodatkowe obciążenie pełnej transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="b76dc-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="b76dc-121">Słowa kluczowe ciągu połączenia</span><span class="sxs-lookup"><span data-stu-id="b76dc-121">Connection String Keywords</span></span>  
 <span data-ttu-id="b76dc-122">Właściwość <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> obsługuje słowo `Enlist`kluczowe, co <xref:System.Data.SqlClient> wskazuje, czy wykryje konteksty transakcyjne i automatycznie zarejestrować połączenie w transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="b76dc-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="b76dc-123">Jeśli `Enlist=true`połączenie jest automatycznie rejestrowane w kontekście bieżącej transakcji wątku otwarcia.</span><span class="sxs-lookup"><span data-stu-id="b76dc-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="b76dc-124">Jeśli `Enlist=false`połączenie `SqlClient` nie wchodzi w interakcję z transakcją rozproszoną.</span><span class="sxs-lookup"><span data-stu-id="b76dc-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="b76dc-125">Wartość domyślna `Enlist` dla jest true.</span><span class="sxs-lookup"><span data-stu-id="b76dc-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="b76dc-126">Jeśli `Enlist` nie jest określony w ciągu połączenia, połączenie jest automatycznie łączony w transakcji rozproszonej, jeśli zostanie wykryty po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b76dc-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="b76dc-127">Słowa `Transaction Binding` kluczowe w <xref:System.Data.SqlClient.SqlConnection> ciągu połączenia kontrolują skojarzenia połączenia `System.Transactions` z zarejestrowaną transakcją.</span><span class="sxs-lookup"><span data-stu-id="b76dc-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="b76dc-128">Jest on również <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> dostępny za <xref:System.Data.SqlClient.SqlConnectionStringBuilder>pośrednictwem obiektu.</span><span class="sxs-lookup"><span data-stu-id="b76dc-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="b76dc-129">W poniższej tabeli opisano możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="b76dc-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="b76dc-130">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="b76dc-130">Keyword</span></span>|<span data-ttu-id="b76dc-131">Opis</span><span class="sxs-lookup"><span data-stu-id="b76dc-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b76dc-132">Niejawne unbind</span><span class="sxs-lookup"><span data-stu-id="b76dc-132">Implicit Unbind</span></span>|<span data-ttu-id="b76dc-133">Domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b76dc-133">The default.</span></span> <span data-ttu-id="b76dc-134">Połączenie odłącza się od transakcji po jej zakończeniu, przełączając się z powrotem do trybu automatycznego przywiązania.</span><span class="sxs-lookup"><span data-stu-id="b76dc-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="b76dc-135">Jawne unbind</span><span class="sxs-lookup"><span data-stu-id="b76dc-135">Explicit Unbind</span></span>|<span data-ttu-id="b76dc-136">Połączenie pozostaje dołączone do transakcji do momentu zamknięcia transakcji.</span><span class="sxs-lookup"><span data-stu-id="b76dc-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="b76dc-137">Połączenie zakończy się niepowodzeniem, jeśli skojarzona transakcja <xref:System.Transactions.Transaction.Current%2A>nie jest aktywna lub nie jest zgodna .</span><span class="sxs-lookup"><span data-stu-id="b76dc-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="b76dc-138">Korzystanie z transactionscope</span><span class="sxs-lookup"><span data-stu-id="b76dc-138">Using TransactionScope</span></span>  
 <span data-ttu-id="b76dc-139">Klasa <xref:System.Transactions.TransactionScope> sprawia, że blok kodu transakcyjnych przez niejawnie rejestracji połączeń w transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="b76dc-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="b76dc-140">Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metodę na końcu <xref:System.Transactions.TransactionScope> bloku przed opuszczeniem go.</span><span class="sxs-lookup"><span data-stu-id="b76dc-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="b76dc-141">Pozostawienie bloku wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="b76dc-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="b76dc-142">Jeśli został zgłoszony wyjątek, który powoduje, że kod do opuszczenia zakresu, transakcja jest uważany za przerwane.</span><span class="sxs-lookup"><span data-stu-id="b76dc-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="b76dc-143">Zaleca się użycie `using` bloku, aby <xref:System.Transactions.TransactionScope.Dispose%2A> upewnić się, że jest wywoływana na <xref:System.Transactions.TransactionScope> obiekcie, gdy using blok jest zamykany.</span><span class="sxs-lookup"><span data-stu-id="b76dc-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="b76dc-144">Niepowodzenie zatwierdzania lub wycofywania oczekujących transakcji może znacznie uszkodzić wydajność, ponieważ domyślny limit czasu dla <xref:System.Transactions.TransactionScope> tej wartości wynosi jedną minutę.</span><span class="sxs-lookup"><span data-stu-id="b76dc-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="b76dc-145">Jeśli nie używasz `using` instrukcji, należy wykonać całą `Try` pracę w bloku <xref:System.Transactions.TransactionScope.Dispose%2A> i `Finally` jawnie wywołać metodę w bloku.</span><span class="sxs-lookup"><span data-stu-id="b76dc-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="b76dc-146">Jeśli wystąpi wyjątek <xref:System.Transactions.TransactionScope>w , transakcja jest oznaczona jako niespójne i jest porzucona.</span><span class="sxs-lookup"><span data-stu-id="b76dc-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="b76dc-147">Zostanie wycofany, gdy <xref:System.Transactions.TransactionScope> jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="b76dc-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="b76dc-148">Jeśli nie wystąpi wyjątek, transakcje uczestniczące zatwierdzają.</span><span class="sxs-lookup"><span data-stu-id="b76dc-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b76dc-149">Klasa `TransactionScope` tworzy transakcję <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b76dc-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="b76dc-150">W zależności od aplikacji warto rozważyć obniżenie poziomu izolacji, aby uniknąć wysokiej rywalizacji w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b76dc-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b76dc-151">Zaleca się wykonywanie tylko aktualizacji, wstawia i usuwa w ramach transakcji rozproszonych, ponieważ zużywają one znaczne zasoby bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b76dc-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="b76dc-152">Wybierz instrukcje mogą niepotrzebnie blokować zasoby bazy danych, a w niektórych scenariuszach może być trzeba użyć transakcji dla wybranych.</span><span class="sxs-lookup"><span data-stu-id="b76dc-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="b76dc-153">Wszelkie prace spoza bazy danych powinny być wykonywane poza zakresem transakcji, chyba że obejmuje ona innych transakcyjnych menedżerów zasobów.</span><span class="sxs-lookup"><span data-stu-id="b76dc-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="b76dc-154">Chociaż wyjątek w zakresie transakcji uniemożliwia zatwierdzenie transakcji, <xref:System.Transactions.TransactionScope> klasa nie ma przepisu na wycofywanie wszelkich zmian wprowadzonych przez kod poza zakresem samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="b76dc-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="b76dc-155">Jeśli trzeba podjąć pewne działania, gdy transakcja jest przywracana, należy <xref:System.Transactions.IEnlistmentNotification> napisać własną implementację interfejsu i jawnie zarejestrować się w transakcji.</span><span class="sxs-lookup"><span data-stu-id="b76dc-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b76dc-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="b76dc-156">Example</span></span>  
 <span data-ttu-id="b76dc-157">Praca <xref:System.Transactions> z wymaga, aby masz odwołanie do System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="b76dc-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="b76dc-158">Poniższa funkcja pokazuje, jak utworzyć transakcję można promować względem dwóch różnych <xref:System.Data.SqlClient.SqlConnection> wystąpień programu SQL <xref:System.Transactions.TransactionScope> Server, reprezentowanych przez dwa różne obiekty, które są zawinięte w bloku.</span><span class="sxs-lookup"><span data-stu-id="b76dc-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="b76dc-159">Kod tworzy <xref:System.Transactions.TransactionScope> blok z `using` instrukcją i otwiera pierwsze połączenie, które <xref:System.Transactions.TransactionScope>automatycznie rejestruje go w pliku .</span><span class="sxs-lookup"><span data-stu-id="b76dc-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="b76dc-160">Transakcja jest początkowo rejestrowana jako lekka transakcja, a nie pełna transakcja rozproszona.</span><span class="sxs-lookup"><span data-stu-id="b76dc-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="b76dc-161">Drugie połączenie jest rejestrowane <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenie w pierwszym połączeniu nie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b76dc-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="b76dc-162">Po otwarciu drugiego połączenia transakcja jest automatycznie podyzowana do pełnej transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="b76dc-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="b76dc-163">Metoda <xref:System.Transactions.TransactionScope.Complete%2A> jest wywoływana, która zatwierdza transakcji tylko wtedy, gdy nie zostały odrzucone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b76dc-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="b76dc-164">Jeśli wyjątek został zgłoszony w <xref:System.Transactions.TransactionScope> dowolnym `Complete` momencie w bloku, nie zostanie wywołana, <xref:System.Transactions.TransactionScope> a transakcja rozproszona `using` zostanie wycofana, gdy jest usuwany na końcu jego bloku.</span><span class="sxs-lookup"><span data-stu-id="b76dc-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b76dc-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b76dc-165">See also</span></span>

- [<span data-ttu-id="b76dc-166">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="b76dc-166">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="b76dc-167">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b76dc-167">ADO.NET Overview</span></span>](ado-net-overview.md)
