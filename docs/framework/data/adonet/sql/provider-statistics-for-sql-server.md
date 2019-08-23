---
title: Statystyki dostawcy dla programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: e13c4df87909629a45830e3b7950551434ed5ab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946587"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="6a3a2-102">Statystyki dostawcy dla programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a3a2-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="6a3a2-103">Począwszy od .NET Framework w wersji 2,0, .NET Framework Dostawca danych dla SQL Server obsługuje statystyki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="6a3a2-104">Aby włączyć statystykę, należy ustawić <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu na `True` po utworzeniu prawidłowego obiektu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="6a3a2-105">Po włączeniu statystyk można je przejrzeć jako "migawkę w czasie", pobierając <xref:System.Collections.IDictionary> odwołanie <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> za pomocą metody <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="6a3a2-106">Wyliczasz listę jako zbiór wpisów słownika par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="6a3a2-107">Te pary nazwa/wartość są nieuporządkowane.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="6a3a2-108">W dowolnym momencie można wywołać <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodę <xref:System.Data.SqlClient.SqlConnection> obiektu, aby zresetować liczniki.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="6a3a2-109">Jeśli zbieranie informacji statystycznych nie zostało włączone, wyjątek nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="6a3a2-110">Ponadto, jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> uprzedniego wywołania, pobierane wartości są początkowymi wartościami dla każdego wpisu.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="6a3a2-111">W przypadku włączenia statystyk, uruchomienia aplikacji przez pewien czas, a następnie wyłączenia statystyk, pobrane wartości będą odzwierciedlać wartości zbierane do punktu, w którym statystyki zostały wyłączone.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="6a3a2-112">Wszystkie zebrane wartości statystyczne dotyczą poszczególnych połączeń.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="6a3a2-113">Dostępne wartości statystyczne</span><span class="sxs-lookup"><span data-stu-id="6a3a2-113">Statistical Values Available</span></span>  
 <span data-ttu-id="6a3a2-114">Obecnie dla dostawcy Microsoft SQL Server dostępne są 18 różnych elementów.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="6a3a2-115">Dostępną liczbę elementów można uzyskać za pomocą właściwości **Count** odwołania do <xref:System.Collections.IDictionary> interfejsu zwróconego przez. <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A></span><span class="sxs-lookup"><span data-stu-id="6a3a2-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="6a3a2-116">We wszystkich licznikach statystyk dostawcy używany jest typ środowiska uruchomieniowego <xref:System.Int64> języka wspólnego (Long C# in i Visual Basic), który jest 64 bitów.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="6a3a2-117">Wartość maksymalna typu **Int64** , zgodnie z definicją podaną przez **Int64. MaxValue** pole jest ((2 ^ 63)-1)).</span><span class="sxs-lookup"><span data-stu-id="6a3a2-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="6a3a2-118">Gdy wartości liczników docierają do tej wartości maksymalnej, nie powinny być już dokładnie traktowane jako dokładne.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="6a3a2-119">Oznacza to, że **Int64. MaxValue**-1 ((2 ^ 63)-2) jest efektywnie największą prawidłową wartością dla każdej statystyki.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a3a2-120">Słownik jest używany do zwracania statystyk dostawcy, ponieważ liczba, nazwy i kolejność zwróconych statystyk mogą ulec zmianie w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="6a3a2-121">Aplikacje nie powinny polegać na określonej wartości znalezionej w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest odpowiednio i rozgałęzienia.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="6a3a2-122">W poniższej tabeli opisano bieżące dostępne wartości statystyczne.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="6a3a2-123">Należy zauważyć, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w regionalnych wersjach środowiska Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="6a3a2-124">Nazwa klucza</span><span class="sxs-lookup"><span data-stu-id="6a3a2-124">Key Name</span></span>|<span data-ttu-id="6a3a2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="6a3a2-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="6a3a2-126">Zwraca liczbę pakietów strumienia danych tabelarycznych (TDS) odebranych przez dostawcę z SQL Server po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="6a3a2-127">Zwraca liczbę pakietów TDS wysłanych do SQL Server przez dostawcę po włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="6a3a2-128">Duże polecenia mogą wymagać wielu buforów.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="6a3a2-129">Na przykład, jeśli do serwera jest wysyłane duże polecenie, które wymaga sześciu pakietów, `ServerRoundtrips` zwiększa się o jeden i `BuffersSent` zwiększa się o sześć.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="6a3a2-130">Zwraca liczbę bajtów danych w pakietach TDS odbieranych przez dostawcę z SQL Server po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="6a3a2-131">Zwraca liczbę bajtów danych wysyłanych do SQL Server w pakietach TDS po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="6a3a2-132">Czas (w milisekundach), przez jaki połączenie zostało otwarte po włączeniu statystyk (łączny czas połączenia, jeśli Statystyka została włączona przed otwarciem połączenia).</span><span class="sxs-lookup"><span data-stu-id="6a3a2-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="6a3a2-133">Zwraca liczbę przypadków otwarcia kursora przez połączenie po rozpoczęciu pracy aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="6a3a2-134">Zwróć uwagę, że wyniki tylko do odczytu/do przodu zwracane przez instrukcje SELECT nie są uważane za kursory i w ten sposób nie wpływają na ten licznik.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="6a3a2-135">Zwraca łączny czas (w milisekundach), przez jaki dostawca spędził przetwarzanie po włączeniu statystyk, w tym czas oczekiwania na odpowiedzi z serwera, a także czas poświęcony na wykonanie kodu w samym dostawcy.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="6a3a2-136">Klasy, które zawierają kod chronometrażu są:</span><span class="sxs-lookup"><span data-stu-id="6a3a2-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="6a3a2-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="6a3a2-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="6a3a2-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="6a3a2-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="6a3a2-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="6a3a2-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="6a3a2-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="6a3a2-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="6a3a2-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="6a3a2-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="6a3a2-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="6a3a2-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="6a3a2-143">Aby zapewnić możliwie najmniejszą wydajność krytycznych elementów członkowskich, następujące elementy członkowskie nie przekroczą czasu:</span><span class="sxs-lookup"><span data-stu-id="6a3a2-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="6a3a2-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="6a3a2-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="6a3a2-145">This [] — operator (wszystkie przeciążenia)</span><span class="sxs-lookup"><span data-stu-id="6a3a2-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="6a3a2-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="6a3a2-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="6a3a2-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="6a3a2-147">GetChar</span></span><br /><br /> <span data-ttu-id="6a3a2-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="6a3a2-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="6a3a2-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="6a3a2-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="6a3a2-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="6a3a2-150">GetDouble</span></span><br /><br /> <span data-ttu-id="6a3a2-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="6a3a2-151">GetFloat</span></span><br /><br /> <span data-ttu-id="6a3a2-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="6a3a2-152">GetGuid</span></span><br /><br /> <span data-ttu-id="6a3a2-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="6a3a2-153">GetInt16</span></span><br /><br /> <span data-ttu-id="6a3a2-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="6a3a2-154">GetInt32</span></span><br /><br /> <span data-ttu-id="6a3a2-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="6a3a2-155">GetInt64</span></span><br /><br /> <span data-ttu-id="6a3a2-156">GetName —</span><span class="sxs-lookup"><span data-stu-id="6a3a2-156">GetName</span></span><br /><br /> <span data-ttu-id="6a3a2-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="6a3a2-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="6a3a2-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="6a3a2-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="6a3a2-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="6a3a2-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="6a3a2-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="6a3a2-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="6a3a2-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="6a3a2-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="6a3a2-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="6a3a2-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="6a3a2-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="6a3a2-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="6a3a2-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="6a3a2-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="6a3a2-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="6a3a2-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="6a3a2-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="6a3a2-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="6a3a2-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="6a3a2-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="6a3a2-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="6a3a2-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="6a3a2-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="6a3a2-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="6a3a2-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="6a3a2-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="6a3a2-171">GetString</span><span class="sxs-lookup"><span data-stu-id="6a3a2-171">GetString</span></span><br /><br /> <span data-ttu-id="6a3a2-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="6a3a2-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="6a3a2-173">Zwraca łączną liczbę instrukcji INSERT, DELETE i UPDATE wykonywanych przez połączenie po rozpoczęciu uruchamiania aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="6a3a2-174">Zwraca łączną liczbę wierszy, na które mają wpływ instrukcje INSERT, DELETE i UPDATE wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystyki.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="6a3a2-175">Zwraca łączny czas (w milisekundach), przez jaki dostawca poświęca na odpowiedzi z serwera po rozpoczęciu pracy przez aplikację przy użyciu dostawcy i włączył statystykę.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="6a3a2-176">Zwraca liczbę przygotowanych poleceń wykonywanych przez połączenie po rozpoczęciu uruchamiania aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="6a3a2-177">Zwraca liczbę instrukcji przygotowanych przez połączenie po rozpoczęciu uruchamiania aplikacji przy użyciu dostawcy i włączonych statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="6a3a2-178">Zwraca liczbę instrukcji SELECT wykonywanych za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystyki.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="6a3a2-179">Obejmuje to instrukcje pobierania do pobrania wierszy z kursorów, a liczba instrukcji SELECT jest aktualizowana po osiągnięciu końca elementu <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="6a3a2-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="6a3a2-180">Zwraca liczbę wierszy wybranych po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączonych statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="6a3a2-181">Ten licznik odzwierciedla wszystkie wiersze wygenerowane przez instrukcje SQL, nawet te, które nie zostały faktycznie wykorzystane przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="6a3a2-182">Na przykład zamknięcie czytnika danych przed odczytaniem całego zestawu wyników nie wpłynie na liczbę.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="6a3a2-183">Obejmuje to wiersze pobierane z kursorów za pomocą instrukcji FETCH.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="6a3a2-184">Zwraca liczbę poleceń wysłanych przez połączenie do serwera i odebranie odpowiedzi z powrotem po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="6a3a2-185">Zwraca liczbę zestawów wyników, które były używane po uruchomieniu aplikacji przy użyciu dostawcy i włączonych statystyk.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="6a3a2-186">Na przykład może to obejmować dowolny zestaw wyników zwrócony klientowi.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="6a3a2-187">W przypadku kursorów każda operacja pobierania lub pobierania bloku jest uznawana za niezależny zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="6a3a2-188">Zwraca liczbę transakcji użytkownika rozpoczętych, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystykę, włącznie z wycofywaniem.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="6a3a2-189">Jeśli połączenie jest uruchomione z funkcją automatycznego zatwierdzania, każde polecenie jest uznawane za transakcję.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="6a3a2-190">Ten licznik zwiększa liczbę transakcji zaraz po wykonaniu instrukcji BEGIN przeładunku, niezależnie od tego, czy transakcja została zatwierdzona czy wycofana później.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="6a3a2-191">Zwraca liczbę nieprzygotowanych instrukcji wykonywanych za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystyki.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="6a3a2-192">Pobieranie wartości</span><span class="sxs-lookup"><span data-stu-id="6a3a2-192">Retrieving a Value</span></span>  
 <span data-ttu-id="6a3a2-193">W poniższej aplikacji konsolowej pokazano, jak włączyć statystykę połączenia, pobrać cztery poszczególne wartości statystyczne i zapisać je w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a3a2-194">Poniższy przykład używa przykładowej bazy danych **AdventureWorks** dołączonej do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="6a3a2-195">Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="6a3a2-196">Zmodyfikuj parametry połączenia jako niezbędne dla danego środowiska.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="6a3a2-197">Pobieranie wszystkich wartości</span><span class="sxs-lookup"><span data-stu-id="6a3a2-197">Retrieving All Values</span></span>  
 <span data-ttu-id="6a3a2-198">W poniższej aplikacji konsolowej pokazano, jak włączyć statystykę połączenia, pobrać wszystkie dostępne wartości statystyczne przy użyciu modułu wyliczającego i zapisać je w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a3a2-199">Poniższy przykład używa przykładowej bazy danych **AdventureWorks** dołączonej do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="6a3a2-200">Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="6a3a2-201">Zmodyfikuj parametry połączenia jako niezbędne dla danego środowiska.</span><span class="sxs-lookup"><span data-stu-id="6a3a2-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a3a2-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a3a2-202">See also</span></span>

- [<span data-ttu-id="6a3a2-203">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a3a2-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="6a3a2-204">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6a3a2-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
