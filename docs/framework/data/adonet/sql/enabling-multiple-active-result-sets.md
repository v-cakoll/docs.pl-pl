---
title: "Włączanie wielu aktywnych zestawów wyników"
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
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b2b1e3ccfe162b6d4903aaf162673ba476296d8b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="bbe1b-102">Włączanie wielu aktywnych zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="bbe1b-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="bbe1b-103">Wiele aktywnych zestawów wyników (MARS) to funkcja, która współdziała z programem SQL Server, aby umożliwić wykonywanie wielu instancji na jedno połączenie.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="bbe1b-104">Po włączeniu MARS do użytku z programem SQL Server każdego obiektu polecenia używane dodaje sesji połączenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbe1b-105">Jednej sesji MARS otwiera jedno połączenie logiczne dla MARS do użycia, a następnie jedno połączenie logiczne dla każdego aktywnego polecenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="bbe1b-106">Włączanie i wyłączanie MARS w parametrach połączenia</span><span class="sxs-lookup"><span data-stu-id="bbe1b-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbe1b-107">Użyj następujących ciągów połączenia przykładu **AdventureWorks** bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="bbe1b-108">Podane parametry połączenia założono, że baza danych jest zainstalowana na serwerze o nazwie MSSQL1.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="bbe1b-109">Zmodyfikuj parametry połączenia w razie potrzeby dla danego środowiska.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="bbe1b-110">Funkcja MARS jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="bbe1b-111">Można ją włączyć przez dodanie "MultipleActiveResultSets = True" pary — słowo kluczowe parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="bbe1b-112">"Wartość prawda" jest jedyną poprawną wartością dla włączania elementu MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="bbe1b-113">W poniższym przykładzie pokazano sposób nawiązywania połączenia z wystąpieniem programu SQL Server i określić, że powinno być włączone MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="bbe1b-114">Można wyłączyć MARS, dodając "MultipleActiveResultSets = False" pary — słowo kluczowe parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="bbe1b-115">"Fałsz" jest jedyną poprawną wartością dla wyłączenie MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="bbe1b-116">Następujący ciąg połączenia pokazano, jak wyłączyć MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="bbe1b-117">Szczególne zagadnienia dotyczące używania MARS</span><span class="sxs-lookup"><span data-stu-id="bbe1b-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="bbe1b-118">Ogólnie rzecz biorąc istniejące aplikacje nie będą modyfikacji połączenie włączone MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="bbe1b-119">Jednak jeśli chcesz używać funkcji MARS w aplikacji, zapoznaj się następujące uwagi.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="bbe1b-120">Naprzemiennego wykonywania instrukcji</span><span class="sxs-lookup"><span data-stu-id="bbe1b-120">Statement Interleaving</span></span>  
 <span data-ttu-id="bbe1b-121">Operacje MARS synchronicznie wykonania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="bbe1b-122">Instrukcja naprzemiennego wykonywania instrukcji SELECT i BULK INSERT jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="bbe1b-123">Jednak język edycji danych (DML) i instrukcje (DDL) języka definicji danych wykonać automatycznie.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="bbe1b-124">Wszystkie instrukcje próby wykonania podczas wykonywania wsadowego atomic są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="bbe1b-125">Wykonywanie równoległe na serwerze nie jest funkcją MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="bbe1b-126">Jeśli dwie partie są przedstawiane w ramach połączenia MARS, jeden z nich zawierający instrukcję SELECT innych zawierająca instrukcję DML DML można rozpocząć wykonywania w ramach wykonywania instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="bbe1b-127">Jednak do ukończenia należy uruchomić instrukcji DML, przed instrukcją SELECT może postęp.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="bbe1b-128">Jeśli zarówno instrukcje działają w ramach jednej transakcji, zmiany wprowadzone przez instrukcję DML, po uruchomieniu wykonywania instrukcji SELECT nie są widoczne dla operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="bbe1b-129">Instrukcję WAITFOR wewnątrz instrukcji SELECT nie yield transakcji, gdy oczekuje, oznacza to, aż do pierwszego wiersza jest generowany.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="bbe1b-130">Oznacza to, że nie inne instancje może zostać uruchomiony w ramach tego samego połączenia, gdy oczekuje instrukcji WAITFOR.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="bbe1b-131">Pamięci podręcznej sesji MARS</span><span class="sxs-lookup"><span data-stu-id="bbe1b-131">MARS Session Cache</span></span>  
 <span data-ttu-id="bbe1b-132">Po otwarciu połączenia z włączoną MARS, tworzona jest logiczną sesji, która dodaje dodatkowe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="bbe1b-133">Aby zminimalizować koszty i zwiększyć wydajność, **SqlClient** buforuje sesji MARS w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="bbe1b-134">Pamięć podręczna zawiera maksymalnie 10 sesji MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="bbe1b-135">Ta wartość nie jest regulowany użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-135">This value is not user adjustable.</span></span> <span data-ttu-id="bbe1b-136">Po osiągnięciu limitu czasu sesji zostanie utworzona nowa sesja — nie zostanie wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="bbe1b-137">Pamięci podręcznej i zawarte w niej sesji są na połączenie. nie są współdzielone przez połączenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="bbe1b-138">Po zwolnieniu sesji, chyba że osiągnęła górny limit puli jest zwracana do puli.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="bbe1b-139">Jeśli w puli pamięci podręcznej jest pełna, sesja jest zamknięta.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="bbe1b-140">Sesji MARS nie wygasa.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-140">MARS sessions do not expire.</span></span> <span data-ttu-id="bbe1b-141">Obecny one tylko są czyszczone po usunięciu obiektu połączenia.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="bbe1b-142">Pamięci podręcznej sesji MARS nie jest załadowane.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="bbe1b-143">Jest on załadowany jako aplikacji wymaga więcej sesji.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="bbe1b-144">Bezpieczeństwo wątków</span><span class="sxs-lookup"><span data-stu-id="bbe1b-144">Thread Safety</span></span>  
 <span data-ttu-id="bbe1b-145">Operacje MARS nie są wątkowo.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="bbe1b-146">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="bbe1b-146">Connection Pooling</span></span>  
 <span data-ttu-id="bbe1b-147">Włączone MARS połączeń są grupowane w pulach podobnie jak inne połączenie.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="bbe1b-148">Jeśli aplikacja otwiera dwa połączenia, jeden z MARS włączone i jeden z MARS wyłączone, dwa połączenia są w osobnych pulach.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="bbe1b-149">Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="bbe1b-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="bbe1b-150">Środowiska wykonania programu SQL Server partii</span><span class="sxs-lookup"><span data-stu-id="bbe1b-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="bbe1b-151">Po otwarciu połączenia jest zdefiniowana domyślnego środowiska.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="bbe1b-152">To środowisko jest następnie skopiowana do logicznego sesji MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="bbe1b-153">Środowiska wykonawczego wsadowego obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="bbe1b-153">The batch execution environment includes the following components:</span></span>  
  
-   <span data-ttu-id="bbe1b-154">Ustawianie opcji (na przykład ANSI_NULLS, DATE_FORMAT, języka, wartość parametru TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="bbe1b-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
-   <span data-ttu-id="bbe1b-155">Kontekst zabezpieczeń (rola użytkownika/aplikacji)</span><span class="sxs-lookup"><span data-stu-id="bbe1b-155">Security context (user/application role)</span></span>  
  
-   <span data-ttu-id="bbe1b-156">Kontekst bazy danych (bieżącej bazy danych)</span><span class="sxs-lookup"><span data-stu-id="bbe1b-156">Database context (current database)</span></span>  
  
-   <span data-ttu-id="bbe1b-157">Zmienne stanu wykonywania (na przykład @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="bbe1b-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
-   <span data-ttu-id="bbe1b-158">Tabele tymczasowe najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="bbe1b-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="bbe1b-159">Z MARS środowiska wykonawczego domyślny jest skojarzona z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="bbe1b-160">Co nowego zadania wsadowego, który rozpoczyna wykonywanie w ramach danego połączenia wysyłana kopia domyślnego środowiska.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="bbe1b-161">Zawsze, gdy kod jest wykonywane w ramach danej partii, wszystkie zmiany wprowadzone do środowiska dostosowanych do określonego zadania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="bbe1b-162">Po zakończeniu wykonywania, wykonanie ustawienia są kopiowane do domyślnego środowiska.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="bbe1b-163">W przypadku pojedynczej partii wystawiania kilka poleceń do wykonania po kolei w tej samej transakcji semantyki są takie same jak te udostępniane przez połączeń obejmujących starszych klientów lub serwerów.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="bbe1b-164">Wykonywanie równoległe</span><span class="sxs-lookup"><span data-stu-id="bbe1b-164">Parallel Execution</span></span>  
 <span data-ttu-id="bbe1b-165">MARS nie jest przeznaczony do usunięcia wszystkich wymagań dotyczących wiele połączeń w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="bbe1b-166">Jeśli aplikacja wymaga true równoległe wykonywanie polecenia na serwerze, należy używać wielu połączeń.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="bbe1b-167">Na przykład rozważmy następujący scenariusz.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-167">For example, consider the following scenario.</span></span> <span data-ttu-id="bbe1b-168">Dwa obiekty polecenia są tworzone, jeden dla przetwarzania zestawu wyników i drugi dla aktualizowania danych. mają wspólnego połączenia za pośrednictwem MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="bbe1b-169">W tym scenariuszu `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="bbe1b-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="bbe1b-170">kończy się niepowodzeniem przy aktualizacji do momentu odczytania wszystkich wyników na pierwszy obiekt polecenia reaguje następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="bbe1b-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="bbe1b-171">Komunikat o błędzie: Kontekst transakcji jest używany przez inną sesję.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="bbe1b-172">Źródło: Dostawca danych SqlClient programu .net</span><span class="sxs-lookup"><span data-stu-id="bbe1b-172">Source: .Net SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="bbe1b-173">Oczekiwano: (null)</span><span class="sxs-lookup"><span data-stu-id="bbe1b-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="bbe1b-174">Received: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="bbe1b-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="bbe1b-175">Dostępne są trzy opcje do obsługi tego scenariusza:</span><span class="sxs-lookup"><span data-stu-id="bbe1b-175">There are three options for handling this scenario:</span></span>  
  
1.  <span data-ttu-id="bbe1b-176">Uruchom transakcji po utworzeniu czytnik, dzięki czemu nie jest częścią transakcji.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="bbe1b-177">Każda aktualizacja staje się własną transakcji.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-177">Every update then becomes its own transaction.</span></span>  
  
2.  <span data-ttu-id="bbe1b-178">Zatwierdź wszystkie wykonywane po czytnik jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="bbe1b-179">To może potencjalnie znaczny pakietu aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-179">This has the potential for a substantial batch of updates.</span></span>  
  
3.  <span data-ttu-id="bbe1b-180">Nie używaj MARS; Zamiast tego użyć osobnego połączenia dla każdego obiektu polecenia, podobnie jak przed MARS.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="bbe1b-181">Wykrywanie MARS pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="bbe1b-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="bbe1b-182">Aplikację można sprawdzić MARS obsługuje odczytując `SqlConnection.ServerVersion` wartość.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="bbe1b-183">Główny numer powinna być 9 dla programu SQL Server 2005 i 10 dla programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="bbe1b-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe1b-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbe1b-184">See Also</span></span>  
 [<span data-ttu-id="bbe1b-185">Wiele aktywnych zestawów wyników (MARS)</span><span class="sxs-lookup"><span data-stu-id="bbe1b-185">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="bbe1b-186">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="bbe1b-186">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
