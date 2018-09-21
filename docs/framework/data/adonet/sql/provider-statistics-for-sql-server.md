---
title: Statystyki dostawcy dla programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: d52c6bfdadf0a53ac4c5f62c37f1056c6702a82c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471823"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="144c4-102">Statystyki dostawcy dla programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="144c4-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="144c4-103">Począwszy od programu .NET Framework w wersji 2.0, .NET Framework Data Provider for SQL Server obsługuje statystyki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="144c4-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="144c4-104">Należy włączyć statystyki, ustawiając <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiekt `True` po poprawnego obiektu połączenia utworzone.</span><span class="sxs-lookup"><span data-stu-id="144c4-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="144c4-105">Po statystyki są włączone, można przejrzeć je jako "migawki w czasie" pobierając <xref:System.Collections.IDictionary> odwoływać się za pośrednictwem <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="144c4-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="144c4-106">Wyliczanie za pośrednictwem listy jako zbiór wpisy słownika par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="144c4-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="144c4-107">Tych par nazwa/wartość są nieuporządkowane.</span><span class="sxs-lookup"><span data-stu-id="144c4-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="144c4-108">W dowolnym momencie możesz wywołać <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiekt, aby zresetować liczniki.</span><span class="sxs-lookup"><span data-stu-id="144c4-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="144c4-109">Jeśli zbieranie wartości licznika statystyka nie została włączona, wyjątek nie zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="144c4-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="144c4-110">Ponadto jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> o najpierw wywołuje, są wartościami pobranymi początkowe wartości dla każdego wpisu.</span><span class="sxs-lookup"><span data-stu-id="144c4-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="144c4-111">Jeśli włączysz statystyki, uruchomienie aplikacji przez jakiś czas i następnie wyłącz statystyki, wartościami pobranymi będą odzwierciedlać wartości, które są zbierane aż do momentu, gdy statystyki zostały wyłączone.</span><span class="sxs-lookup"><span data-stu-id="144c4-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="144c4-112">Wszystkie wartości statystyczne zebrane znajdują się na poszczególnych połączeń.</span><span class="sxs-lookup"><span data-stu-id="144c4-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="144c4-113">Dostępne wartości statystyczne</span><span class="sxs-lookup"><span data-stu-id="144c4-113">Statistical Values Available</span></span>  
 <span data-ttu-id="144c4-114">Obecnie istnieją 18 różnych elementów od dostawcy programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="144c4-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="144c4-115">Liczba elementów jest możliwy za pośrednictwem **liczba** właściwość <xref:System.Collections.IDictionary> Odwołanie zwrócone przez interfejs <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="144c4-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="144c4-116">Wszystkie liczniki dla statystyki dostawcy używać środowiska uruchomieniowego języka wspólnego <xref:System.Int64> typu (**długie** w języku C# i Visual Basic), który jest 64-bitowy szeroki.</span><span class="sxs-lookup"><span data-stu-id="144c4-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="144c4-117">Maksymalna wartość **int64** typu danych, zgodnie z definicją **int64. MaxValue** pola, ((2^63) 1)).</span><span class="sxs-lookup"><span data-stu-id="144c4-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="144c4-118">Jeśli wartości liczników osiągnąć tę wartość maksymalna, są już należy rozważyć dokładne.</span><span class="sxs-lookup"><span data-stu-id="144c4-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="144c4-119">Oznacza to, że **int64. MaxValue**-1((2^63)-2) jest faktycznie największy prawidłową wartość wszystkie statystyki.</span><span class="sxs-lookup"><span data-stu-id="144c4-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="144c4-120">Słownik służy do zwracania statystyki dostawcy, ponieważ numer, nazwy i kolejność zwracane statystyki może ulec zmianie w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="144c4-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="144c4-121">Aplikacje nie należy polegać na określoną wartość, zostanie on znaleziony w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest i odpowiednio gałęzi.</span><span class="sxs-lookup"><span data-stu-id="144c4-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="144c4-122">W poniższej tabeli opisano bieżące wartości statystyczne dostępne.</span><span class="sxs-lookup"><span data-stu-id="144c4-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="144c4-123">Należy zauważyć, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w różnych wersjach regionalnych programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="144c4-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="144c4-124">Nazwa klucza</span><span class="sxs-lookup"><span data-stu-id="144c4-124">Key Name</span></span>|<span data-ttu-id="144c4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="144c4-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="144c4-126">Zwraca liczbę strumienia danych tabelarycznych (TDS) odebrane pakiety przez dostawcę z programu SQL Server po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="144c4-127">Zwraca liczbę TDS pakiety wysyłane do programu SQL Server przez dostawcę po włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="144c4-128">Duże poleceń może wymagać wielu buforów.</span><span class="sxs-lookup"><span data-stu-id="144c4-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="144c4-129">Na przykład, jeśli polecenie dużych są wysyłane do serwera i wymaga sześć pakietów `ServerRoundtrips` jest zwiększany o jeden i `BuffersSent` jest zwiększany o sześciu.</span><span class="sxs-lookup"><span data-stu-id="144c4-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="144c4-130">Zwraca liczbę bajtów danych w pakietach TDS odebrane przez dostawcę z programu SQL Server, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="144c4-131">Zwraca liczbę bajtów danych wysyłanych do serwera SQL w pakietach TDS po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="144c4-132">Ilość czasu (w milisekundach), że połączenie zostało otwarte po włączeniu statystyki (całkowity czas połączenia, jeśli statystyki zostały włączone przed otwarciem połączenie).</span><span class="sxs-lookup"><span data-stu-id="144c4-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="144c4-133">Zwraca liczbę przypadków, gdy kursor był otwarty za pośrednictwem połączenia w przypadku, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="144c4-134">Pamiętaj, że tylko/do przodu — tylko do odczytu wyników zwróconych przez instrukcji "SELECT" nie są uważane za kursorów, a zatem nie wpływają na wartość tego licznika.</span><span class="sxs-lookup"><span data-stu-id="144c4-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="144c4-135">Zwraca wartość łącznego czasu (w milisekundach), czy dostawca jest poświęcony na przetwarzanie po włączeniu statystyki, w tym czas oczekiwania na odpowiedzi z serwera, a także czas poświęcony na wykonywanie kodu w samej dostawcy.</span><span class="sxs-lookup"><span data-stu-id="144c4-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="144c4-136">Klasy, które zawierają kod chronometrażu są:</span><span class="sxs-lookup"><span data-stu-id="144c4-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="144c4-137">Element SqlConnection</span><span class="sxs-lookup"><span data-stu-id="144c4-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="144c4-138">Klasy SqlCommand</span><span class="sxs-lookup"><span data-stu-id="144c4-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="144c4-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="144c4-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="144c4-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="144c4-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="144c4-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="144c4-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="144c4-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="144c4-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="144c4-143">Aby zachować wydajność krytycznych członków tak małej, jak to możliwe, następujące elementy członkowskie są nie upłynął limit czasu:</span><span class="sxs-lookup"><span data-stu-id="144c4-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="144c4-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="144c4-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="144c4-145">Ten operator [] (wszystkie przeciążenia)</span><span class="sxs-lookup"><span data-stu-id="144c4-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="144c4-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="144c4-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="144c4-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="144c4-147">GetChar</span></span><br /><br /> <span data-ttu-id="144c4-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="144c4-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="144c4-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="144c4-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="144c4-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="144c4-150">GetDouble</span></span><br /><br /> <span data-ttu-id="144c4-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="144c4-151">GetFloat</span></span><br /><br /> <span data-ttu-id="144c4-152">Getguid —</span><span class="sxs-lookup"><span data-stu-id="144c4-152">GetGuid</span></span><br /><br /> <span data-ttu-id="144c4-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="144c4-153">GetInt16</span></span><br /><br /> <span data-ttu-id="144c4-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="144c4-154">GetInt32</span></span><br /><br /> <span data-ttu-id="144c4-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="144c4-155">GetInt64</span></span><br /><br /> <span data-ttu-id="144c4-156">Getname —</span><span class="sxs-lookup"><span data-stu-id="144c4-156">GetName</span></span><br /><br /> <span data-ttu-id="144c4-157">Getordinal —</span><span class="sxs-lookup"><span data-stu-id="144c4-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="144c4-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="144c4-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="144c4-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="144c4-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="144c4-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="144c4-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="144c4-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="144c4-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="144c4-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="144c4-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="144c4-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="144c4-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="144c4-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="144c4-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="144c4-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="144c4-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="144c4-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="144c4-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="144c4-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="144c4-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="144c4-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="144c4-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="144c4-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="144c4-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="144c4-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="144c4-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="144c4-171">GetString —</span><span class="sxs-lookup"><span data-stu-id="144c4-171">GetString</span></span><br /><br /> <span data-ttu-id="144c4-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="144c4-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="144c4-173">Zwraca sumę instrukcje INSERT, usuwania i aktualizacji, które są wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="144c4-174">Zwraca łączną liczbę wierszy, o których wpływ instrukcje INSERT, usuwania i aktualizacji, które są wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="144c4-175">Zwraca łącznego czasu (w milisekundach), dostawca poświęcony oczekiwania na odpowiedzi z serwera, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki.</span><span class="sxs-lookup"><span data-stu-id="144c4-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="144c4-176">Zwraca liczbę przygotowanego polecenia wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="144c4-177">Zwraca liczbę instrukcji przygotowane przez połączenie, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="144c4-178">Zwraca liczbę instrukcji "SELECT" wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="144c4-179">Dotyczy to również instrukcje pobierania, aby pobierać wiersze z kursorami i liczbę elementów w instrukcji "SELECT" jest aktualizowana po końcu <xref:System.Data.SqlClient.SqlDataReader> zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="144c4-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="144c4-180">Zwraca liczbę wierszy wybrany, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="144c4-181">Ten licznik wskazuje wszystkie wiersze, które są generowane przez instrukcje SQL, nawet te, które faktycznie nie były używane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="144c4-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="144c4-182">Na przykład zamknięcia czytnika danych przed odczytaniem cały zestaw wyników nie wpłynie na liczbę.</span><span class="sxs-lookup"><span data-stu-id="144c4-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="144c4-183">W tym wiersze, pobierane z kursorami za pomocą instrukcji pobierania.</span><span class="sxs-lookup"><span data-stu-id="144c4-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="144c4-184">Zwraca liczbę połączeń wysyłanych poleceń do serwera i otrzymano odpowiedź, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki.</span><span class="sxs-lookup"><span data-stu-id="144c4-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="144c4-185">Zwraca liczbę wyników zestawów, które były używane w taki sposób, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="144c4-186">Na przykład to dotyczy wszelkich zestaw wyników, zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="144c4-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="144c4-187">Kursory każdej operacji pobierania lub fetch bloku są uznawane za zestawu wyników niezależnych.</span><span class="sxs-lookup"><span data-stu-id="144c4-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="144c4-188">Zwraca liczbę pracę, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki, w tym funkcji wycofywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="144c4-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="144c4-189">Jeśli połączenie jest uruchomiony przy użyciu automatycznego zatwierdzenia na, każde polecenie jest traktowany jako jedna transakcja.</span><span class="sxs-lookup"><span data-stu-id="144c4-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="144c4-190">Ten licznik zwiększa się liczba transakcji zaraz po wykonaniu instrukcji BEGIN TRAN, niezależnie od tego, czy transakcja jest przekazana lub wycofana później.</span><span class="sxs-lookup"><span data-stu-id="144c4-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="144c4-191">Zwraca liczbę instrukcji nieprzygotowane wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.</span><span class="sxs-lookup"><span data-stu-id="144c4-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="144c4-192">Pobieranie wartości</span><span class="sxs-lookup"><span data-stu-id="144c4-192">Retrieving a Value</span></span>  
 <span data-ttu-id="144c4-193">Następująca aplikacja konsoli Pokazuje, jak włączyć statystyki dotyczące połączenia, pobrać cztery wartości poszczególnych statystyk i zapisać je w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="144c4-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="144c4-194">W poniższym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="144c4-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="144c4-195">Parametry połączenia, udostępniane w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="144c4-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="144c4-196">Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="144c4-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="144c4-197">Pobieranie wszystkich wartości</span><span class="sxs-lookup"><span data-stu-id="144c4-197">Retrieving All Values</span></span>  
 <span data-ttu-id="144c4-198">Następująca aplikacja konsoli Pokazuje, jak włączyć statystyki dotyczące połączenia, pobrać wszystkie dostępne statystyki wartości, przy użyciu modułu wyliczającego i zapisanie ich w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="144c4-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="144c4-199">W poniższym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="144c4-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="144c4-200">Parametry połączenia, udostępniane w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="144c4-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="144c4-201">Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="144c4-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="144c4-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="144c4-202">See Also</span></span>  
 [<span data-ttu-id="144c4-203">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="144c4-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="144c4-204">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="144c4-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
