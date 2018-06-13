---
title: System.Transactions integracji z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 219a806441e0f6ce501dc691f4c965168a250aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365751"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="d330c-102">System.Transactions integracji z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="d330c-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="d330c-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 2.0 wprowadzono framework transakcji, które mogą być udostępniane za pośrednictwem <xref:System.Transactions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d330c-103">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="d330c-104">Ta struktura przedstawia transakcji w taki sposób, który jest w pełni zintegrowana z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], takie jak [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d330c-104">This framework exposes transactions in a way that is fully integrated in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], including [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="d330c-105">Oprócz rozszerzenia programowania <xref:System.Transactions> i [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mogą współdziałać ze sobą do koordynowania optymalizacje podczas pracy z transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-105">In addition to the programmability enhancements, <xref:System.Transactions> and [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="d330c-106">Awansowanie transakcji to lekkie transakcja (local), która może być automatycznie podwyższony do transakcji rozproszonej pełni na zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d330c-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="d330c-107">Począwszy od [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> obsługuje awansowanie transakcji podczas pracy z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d330c-107">Starting with [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="d330c-108">Awansowanie transakcji nie jest wywoływany dodany narzutów transakcji rozproszonej, chyba że dodany jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d330c-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="d330c-109">Awansowanie transakcje są automatyczne i wymagają interwencji od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="d330c-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="d330c-110">Awansowanie transakcje są dostępne tylko, gdy używasz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server (`SqlClient`) z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d330c-110">Promotable transactions are only available when you use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="d330c-111">Tworzenie awansowanie transakcji</span><span class="sxs-lookup"><span data-stu-id="d330c-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="d330c-112">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server zapewnia obsługę awansowanie transakcji, które są obsługiwane za pośrednictwem klas w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d330c-112">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="d330c-113">Transakcje awansowanie zoptymalizować transakcje rozproszone odkładanie Tworzenie transakcji rozproszonej, dopóki nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d330c-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="d330c-114">Jeśli tylko jeden Menedżera zasobów jest wymagana, występuje nie transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d330c-115">W scenariuszu z częściowo zaufanego <xref:System.Transactions.DistributedTransactionPermission> jest wymagany, gdy transakcja jest podwyższany do transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="d330c-116">Scenariusze awansowanie transakcji</span><span class="sxs-lookup"><span data-stu-id="d330c-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="d330c-117">Transakcje rozproszone zwykle użycie zasobów systemu znaczące, zarządzana przez program Microsoft Distributed Transaction Coordinator (MS DTC), która integruje się menedżerowie zasobów dostępne w ramach transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="d330c-118">Awansowanie transakcji jest specjalny rodzaj <xref:System.Transactions> transakcji, które skutecznie deleguje pracy proste transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d330c-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="d330c-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, oraz programu SQL Server koordynować pracę niezbędną do obsługi transakcji, promowania go do pełnego transakcji rozproszonej, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d330c-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="d330c-120">Zaletą używania awansowanie transakcji jest fakt, że połączenie jest otwarte przy użyciu aktywnego <xref:System.Transactions.TransactionScope> transakcji, a żadne inne połączenia są otwarte, zatwierdzenia transakcji jako lekkich transakcji, zamiast ponoszenia dodatkowych koszty pełne transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="d330c-121">Słowa kluczowe parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="d330c-121">Connection String Keywords</span></span>  
 <span data-ttu-id="d330c-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Właściwość obsługuje słowem kluczowym `Enlist`, co oznacza, czy <xref:System.Data.SqlClient> wykryje transakcyjne konteksty i automatycznie zarejestrować połączenie w transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="d330c-123">Jeśli `Enlist=true`, połączenie jest automatycznie zarejestrowane w wątku otwarcia bieżącego kontekstu transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="d330c-124">Jeśli `Enlist=false`, `SqlClient` połączenia nie współdziała z transakcji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="d330c-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="d330c-125">Wartość domyślna dla `Enlist` ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="d330c-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="d330c-126">Jeśli `Enlist` nie określono w parametrach połączenia, połączenie jest automatycznie zarejestrowane w transakcji rozproszonej, po wykryciu jednego po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="d330c-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="d330c-127">`Transaction Binding` Słów kluczowych w <xref:System.Data.SqlClient.SqlConnection> ciąg połączenia kontroli skojarzenie tego połączenia z zarejestrowane `System.Transactions` transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="d330c-128">Jest również dostępna za pośrednictwem <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="d330c-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="d330c-129">W poniższej tabeli opisano możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="d330c-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="d330c-130">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="d330c-130">Keyword</span></span>|<span data-ttu-id="d330c-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d330c-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d330c-132">Niejawne usunięcia powiązania</span><span class="sxs-lookup"><span data-stu-id="d330c-132">Implicit Unbind</span></span>|<span data-ttu-id="d330c-133">Domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d330c-133">The default.</span></span> <span data-ttu-id="d330c-134">Połączenie odłącza transakcji po jej zakończeniu przełączania do trybu autozatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="d330c-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="d330c-135">Jawne usuwanie powiązania</span><span class="sxs-lookup"><span data-stu-id="d330c-135">Explicit Unbind</span></span>|<span data-ttu-id="d330c-136">Połączenie pozostaje przyłączona do transakcji do czasu zamknięcia transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="d330c-137">Połączenia zakończy się niepowodzeniem, jeśli skojarzonej transakcji jest nieaktywny lub nie odpowiada <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="d330c-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="d330c-138">Przy użyciu elementu TransactionScope</span><span class="sxs-lookup"><span data-stu-id="d330c-138">Using TransactionScope</span></span>  
 <span data-ttu-id="d330c-139"><xref:System.Transactions.TransactionScope> Klasy powoduje, że blok kodu transakcyjnego przez niejawnie rejestrowanie połączenia w transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="d330c-140">Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metody na końcu <xref:System.Transactions.TransactionScope> blok przed opuszczeniem go.</span><span class="sxs-lookup"><span data-stu-id="d330c-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="d330c-141">Pozostawienie bloku wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d330c-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="d330c-142">Jeśli wyjątek czy przyczyny, który jest uznawany za kod, aby pozostawić zakresu, transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="d330c-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="d330c-143">Firma Microsoft zaleca użycie `using` bloku, aby upewnić się, że <xref:System.Transactions.TransactionScope.Dispose%2A> jest wywoływana na <xref:System.Transactions.TransactionScope> obiektu po użyciu zablokować zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="d330c-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="d330c-144">Nie można przekazać ani wycofać transakcje oczekujące znacznie może uszkodzić wydajności, ponieważ domyślny limit czasu dla <xref:System.Transactions.TransactionScope> jest jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="d330c-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="d330c-145">Jeśli nie używasz `using` instrukcji, należy wykonać całą pracę w `Try` zablokować, a następnie jawnie wywołać <xref:System.Transactions.TransactionScope.Dispose%2A> metoda `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="d330c-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="d330c-146">Jeśli wystąpi wyjątek w <xref:System.Transactions.TransactionScope>, transakcja jest oznaczone jako niespójne i zostanie zaniechana.</span><span class="sxs-lookup"><span data-stu-id="d330c-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="d330c-147">Zostanie wycofana Wstecz, gdy <xref:System.Transactions.TransactionScope> został usunięty.</span><span class="sxs-lookup"><span data-stu-id="d330c-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="d330c-148">Jeśli wystąpi żaden wyjątek, Zatwierdź uczestniczących transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d330c-149">`TransactionScope` Klasy tworzy transakcję o <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d330c-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="d330c-150">W zależności od aplikacji warto rozważyć obniżenia poziomu izolacji, aby uniknąć rywalizacji wysokiej w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d330c-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d330c-151">Zaleca się wykonywać tylko aktualizacje, wstawiania i usuwa w transakcje rozproszone, ponieważ zużywają zasoby znaczących bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d330c-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="d330c-152">Instrukcji "Select" może zablokować niepotrzebnie zasobów bazy danych, a w niektórych scenariuszach może być konieczne wybiera należy używać transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="d330c-153">Pracę bez bazy danych powinno być wykonywane poza zakresem transakcji, chyba że obejmuje ono inne menedżerowie zasobów transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="d330c-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="d330c-154">Mimo że wyjątek w zakresie transakcji uniemożliwia transakcji z zatwierdzania, <xref:System.Transactions.TransactionScope> klasa nie ma możliwości obsługi dla wycofywanie zmian kodu dokonał poza zakresem jest transakcja.</span><span class="sxs-lookup"><span data-stu-id="d330c-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="d330c-155">Jeśli należy wykonać niektóre akcje, gdy transakcja zostanie wycofana, należy napisać własne implementacja <xref:System.Transactions.IEnlistmentNotification> interfejsu i jawnie zarejestrować transakcji.</span><span class="sxs-lookup"><span data-stu-id="d330c-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d330c-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="d330c-156">Example</span></span>  
 <span data-ttu-id="d330c-157">Praca z <xref:System.Transactions> wymaga odwołania do Biblioteka System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="d330c-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="d330c-158">Następująca funkcja pokazano, jak utworzyć awansowanie transakcji dla dwóch różnych wystąpieniach programu SQL Server, reprezentowany przez dwa różne <xref:System.Data.SqlClient.SqlConnection> obiektów, które są ujęte w <xref:System.Transactions.TransactionScope> bloku.</span><span class="sxs-lookup"><span data-stu-id="d330c-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="d330c-159">Kod tworzy <xref:System.Transactions.TransactionScope> zablokować z `using` instrukcji i otwiera pierwszego połączenia, które automatycznie rejestruje w <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="d330c-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="d330c-160">Transakcja jest początkowo zarejestrowane jako lekkie transakcji, a nie pełny transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="d330c-161">Drugie połączenie jest zarejestrowany w <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenie w pierwszym połączeniu nie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d330c-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="d330c-162">Po otwarciu drugiego połączenia transakcji zostanie automatycznie podwyższony do pełnego transakcji rozproszonej.</span><span class="sxs-lookup"><span data-stu-id="d330c-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="d330c-163"><xref:System.Transactions.TransactionScope.Complete%2A> Wywołaniu metody, które zatwierdza transakcję tylko wtedy, gdy żadne wyjątki nie były zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="d330c-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="d330c-164">Jeśli w dowolnym momencie zgłosił wyjątek <xref:System.Transactions.TransactionScope> bloku, `Complete` zostanie nie można wywołać i będzie transakcji rozproszonej, Przywróć Wstecz, gdy <xref:System.Transactions.TransactionScope> zostanie usunięty po zakończeniu jego `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="d330c-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d330c-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d330c-165">See Also</span></span>  
 [<span data-ttu-id="d330c-166">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="d330c-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="d330c-167">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="d330c-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
