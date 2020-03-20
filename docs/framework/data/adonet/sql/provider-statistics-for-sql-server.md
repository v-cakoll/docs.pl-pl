---
title: Statystyki dostawcy dla programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 5e37a04ff731a99664d636e0d4175f99214c2646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174514"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="87bb4-102">Statystyki dostawcy dla programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="87bb4-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="87bb4-103">Począwszy od programu .NET Framework w wersji 2.0, dostawca danych programu .NET Framework dla programu SQL Server obsługuje statystyki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="87bb4-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="87bb4-104">Statystyki należy włączyć, ustawiając <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> właściwość `True` <xref:System.Data.SqlClient.SqlConnection> obiektu po utworzeniu prawidłowego obiektu połączenia.</span><span class="sxs-lookup"><span data-stu-id="87bb4-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="87bb4-105">Po włączeniu statystyk można przejrzeć je jako "migawka w <xref:System.Collections.IDictionary> czasie", <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> pobierając <xref:System.Data.SqlClient.SqlConnection> odwołanie za pomocą metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="87bb4-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="87bb4-106">Wyliczyć za pośrednictwem listy jako zestaw wpisów słownika nazwa/wartość pary.</span><span class="sxs-lookup"><span data-stu-id="87bb4-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="87bb4-107">Te pary nazw/wartości są nieurządzone.</span><span class="sxs-lookup"><span data-stu-id="87bb4-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="87bb4-108">W dowolnym momencie można <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> wywołać <xref:System.Data.SqlClient.SqlConnection> metodę obiektu, aby zresetować liczniki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="87bb4-109">Jeśli zbieranie statystyk nie zostało włączone, wyjątek nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="87bb4-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="87bb4-110">Ponadto jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> wywoływane jako pierwsze, wartości pobrane są wartościami początkowymi dla każdego wpisu.</span><span class="sxs-lookup"><span data-stu-id="87bb4-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="87bb4-111">Jeśli włączysz statystyki, uruchom aplikację przez jakiś czas, a następnie wyłącz statystyki, pobrane wartości będą odzwierciedlać wartości zebrane do punktu, w którym statystyki zostały wyłączone.</span><span class="sxs-lookup"><span data-stu-id="87bb4-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="87bb4-112">Wszystkie zebrane wartości statystyczne są na podstawie połączenia.</span><span class="sxs-lookup"><span data-stu-id="87bb4-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="87bb4-113">Dostępne wartości statystyczne</span><span class="sxs-lookup"><span data-stu-id="87bb4-113">Statistical Values Available</span></span>  
 <span data-ttu-id="87bb4-114">Obecnie istnieje 18 różnych elementów dostępnych od dostawcy programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87bb4-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="87bb4-115">Liczba dostępnych elementów jest dostępna **Count** za pośrednictwem <xref:System.Collections.IDictionary> Count właściwości <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>odwołania interfejsu zwracane przez .</span><span class="sxs-lookup"><span data-stu-id="87bb4-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="87bb4-116">Wszystkie liczniki dla statystyk dostawcy używają wspólnego <xref:System.Int64> typu środowiska wykonawczego języka **(long** w języku C# i Visual Basic), który ma 64 bity szerokości.</span><span class="sxs-lookup"><span data-stu-id="87bb4-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="87bb4-117">Maksymalna wartość typu danych **int64,** zdefiniowana przez **int64. MaxValue,** jest ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="87bb4-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="87bb4-118">Gdy wartości liczników osiągną tę maksymalną wartość, nie powinny być już uważane za dokładne.</span><span class="sxs-lookup"><span data-stu-id="87bb4-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="87bb4-119">Oznacza to, że **int64. MaxValue**-1((2^63)-2) jest skutecznie największą prawidłową wartością dla każdej statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87bb4-120">Słownik jest używany do zwracania statystyk dostawcy, ponieważ liczba, nazwy i kolejność zwracanych statystyk mogą ulec zmianie w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="87bb4-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="87bb4-121">Aplikacje nie powinny polegać na określonej wartości znalezionej w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest tam i odpowiednio gałęzi.</span><span class="sxs-lookup"><span data-stu-id="87bb4-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="87bb4-122">W poniższej tabeli opisano bieżące dostępne wartości statystyczne.</span><span class="sxs-lookup"><span data-stu-id="87bb4-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="87bb4-123">Należy zauważyć, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w regionalnych wersjach programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87bb4-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="87bb4-124">Nazwa klucza</span><span class="sxs-lookup"><span data-stu-id="87bb4-124">Key Name</span></span>|<span data-ttu-id="87bb4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="87bb4-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="87bb4-126">Zwraca liczbę pakietów strumienia danych tabelaryczne (TDS) odebranych przez dostawcę z programu SQL Server po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="87bb4-127">Zwraca liczbę pakietów TDS wysyłanych do programu SQL Server przez dostawcę po włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="87bb4-128">Duże polecenia mogą wymagać wielu buforów.</span><span class="sxs-lookup"><span data-stu-id="87bb4-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="87bb4-129">Na przykład jeśli duże polecenie jest wysyłane do serwera i `ServerRoundtrips` wymaga sześciu pakietów, `BuffersSent` jest zwiększane o jeden i zwiększa się o sześć.</span><span class="sxs-lookup"><span data-stu-id="87bb4-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="87bb4-130">Zwraca liczbę bajtów danych w pakietach TDS odebranych przez dostawcę z programu SQL Server po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="87bb4-131">Zwraca liczbę bajtów danych wysyłanych do programu SQL Server w pakietach TDS po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="87bb4-132">Czas (w milisekundach), przez który połączenie zostało otwarte po włączeniu statystyk (całkowity czas połączenia, jeśli statystyki zostały włączone przed otwarciem połączenia).</span><span class="sxs-lookup"><span data-stu-id="87bb4-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="87bb4-133">Zwraca liczbę razy kursor został otwarty za pośrednictwem połączenia po aplikacji rozpoczął przy użyciu dostawcy i włączył statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="87bb4-134">Należy zauważyć, że wyniki tylko do odczytu/tylko do przodu zwracane przez instrukcje SELECT nie są uważane za kursory i dlatego nie mają wpływu na ten licznik.</span><span class="sxs-lookup"><span data-stu-id="87bb4-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="87bb4-135">Zwraca skumulowaną ilość czasu (w milisekundach), który dostawca spędził przetwarzania po włączeniu statystyk, w tym czas spędzony na oczekiwanie na odpowiedzi z serwera, a także czas spędzony na wykonywaniu kodu w samym dostawcy.</span><span class="sxs-lookup"><span data-stu-id="87bb4-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="87bb4-136">Klasy, które zawierają kod chronometrażu są:</span><span class="sxs-lookup"><span data-stu-id="87bb4-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="87bb4-137">Sqlconnection</span><span class="sxs-lookup"><span data-stu-id="87bb4-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="87bb4-138">Sqlcommand</span><span class="sxs-lookup"><span data-stu-id="87bb4-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="87bb4-139">Sqldatareader</span><span class="sxs-lookup"><span data-stu-id="87bb4-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="87bb4-140">Sqldataadapter</span><span class="sxs-lookup"><span data-stu-id="87bb4-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="87bb4-141">Sqltransaction</span><span class="sxs-lookup"><span data-stu-id="87bb4-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="87bb4-142">Sqlcommandbuilder</span><span class="sxs-lookup"><span data-stu-id="87bb4-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="87bb4-143">Aby elementy członkowskie o krytycznym znaczeniu dla wydajności były jak najmniejsze, następujące elementy członkowskie nie są czasowe:</span><span class="sxs-lookup"><span data-stu-id="87bb4-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="87bb4-144">Sqldatareader</span><span class="sxs-lookup"><span data-stu-id="87bb4-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="87bb4-145">ten[] operator (wszystkie przeciążenia)</span><span class="sxs-lookup"><span data-stu-id="87bb4-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="87bb4-146">Getboolean</span><span class="sxs-lookup"><span data-stu-id="87bb4-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="87bb4-147">Getchar</span><span class="sxs-lookup"><span data-stu-id="87bb4-147">GetChar</span></span><br /><br /> <span data-ttu-id="87bb4-148">GetDateTime (Czas 1lat</span><span class="sxs-lookup"><span data-stu-id="87bb4-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="87bb4-149">GetDecimal (GetDecimal)</span><span class="sxs-lookup"><span data-stu-id="87bb4-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="87bb4-150">Getdouble</span><span class="sxs-lookup"><span data-stu-id="87bb4-150">GetDouble</span></span><br /><br /> <span data-ttu-id="87bb4-151">GetFloat ( GetFloat )</span><span class="sxs-lookup"><span data-stu-id="87bb4-151">GetFloat</span></span><br /><br /> <span data-ttu-id="87bb4-152">GetGuid ( GetGuid )</span><span class="sxs-lookup"><span data-stu-id="87bb4-152">GetGuid</span></span><br /><br /> <span data-ttu-id="87bb4-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="87bb4-153">GetInt16</span></span><br /><br /> <span data-ttu-id="87bb4-154">GetInt32 (GetInt32)</span><span class="sxs-lookup"><span data-stu-id="87bb4-154">GetInt32</span></span><br /><br /> <span data-ttu-id="87bb4-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="87bb4-155">GetInt64</span></span><br /><br /> <span data-ttu-id="87bb4-156">GetName</span><span class="sxs-lookup"><span data-stu-id="87bb4-156">GetName</span></span><br /><br /> <span data-ttu-id="87bb4-157">Getordinal</span><span class="sxs-lookup"><span data-stu-id="87bb4-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="87bb4-158">GetSqlBinary (Łącze Łącze)</span><span class="sxs-lookup"><span data-stu-id="87bb4-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="87bb4-159">GetSqlBoolean (GetSqlBoolean)</span><span class="sxs-lookup"><span data-stu-id="87bb4-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="87bb4-160">GetSqlByte ( GetSqlByte )</span><span class="sxs-lookup"><span data-stu-id="87bb4-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="87bb4-161">Czas 100 000 000 000 000 0</span><span class="sxs-lookup"><span data-stu-id="87bb4-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="87bb4-162">GetSqlDecymal</span><span class="sxs-lookup"><span data-stu-id="87bb4-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="87bb4-163">GetSqlDouble (GetSqlDouble)</span><span class="sxs-lookup"><span data-stu-id="87bb4-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="87bb4-164">GetSqlGuid ( GetSqlGuid )</span><span class="sxs-lookup"><span data-stu-id="87bb4-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="87bb4-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="87bb4-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="87bb4-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="87bb4-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="87bb4-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="87bb4-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="87bb4-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="87bb4-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="87bb4-169">GetSqlSingle ( GetSqlSingle )</span><span class="sxs-lookup"><span data-stu-id="87bb4-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="87bb4-170">GetSqlString (wysiewu)</span><span class="sxs-lookup"><span data-stu-id="87bb4-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="87bb4-171">GetString</span><span class="sxs-lookup"><span data-stu-id="87bb4-171">GetString</span></span><br /><br /> <span data-ttu-id="87bb4-172">Isdbnull</span><span class="sxs-lookup"><span data-stu-id="87bb4-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="87bb4-173">Zwraca całkowitą liczbę instrukcji INSERT, DELETE i UPDATE wykonanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="87bb4-174">Zwraca całkowitą liczbę wierszy, których dotyczą instrukcje INSERT, DELETE i UPDATE wykonywane za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="87bb4-175">Zwraca skumulowaną ilość czasu (w milisekundach), który dostawca spędził na czekaniu na odpowiedzi z serwera po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="87bb4-176">Zwraca liczbę przygotowanych poleceń wykonywanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="87bb4-177">Zwraca liczbę instrukcji przygotowanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="87bb4-178">Zwraca liczbę instrukcji SELECT wykonanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="87bb4-179">Obejmuje to instrukcje FETCH, aby pobrać wiersze z kursorów, a liczba <xref:System.Data.SqlClient.SqlDataReader> instrukcji SELECT jest aktualizowana po osiągnięciu końca a.</span><span class="sxs-lookup"><span data-stu-id="87bb4-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="87bb4-180">Zwraca liczbę wierszy wybranych po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="87bb4-181">Ten licznik odzwierciedla wszystkie wiersze generowane przez instrukcje SQL, nawet te, które nie zostały faktycznie wykorzystane przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="87bb4-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="87bb4-182">Na przykład zamknięcie czytnika danych przed odczytaniem całego zestawu wyników nie wpłynie na liczbę.</span><span class="sxs-lookup"><span data-stu-id="87bb4-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="87bb4-183">Obejmuje to wiersze pobrane z kursorów za pośrednictwem instrukcji FETCH.</span><span class="sxs-lookup"><span data-stu-id="87bb4-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="87bb4-184">Zwraca liczbę razy połączenie wysłane polecenia do serwera i otrzymał odpowiedź z powrotem po aplikacji rozpoczął korzystanie z dostawcy i włączył statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="87bb4-185">Zwraca liczbę zestawów wyników, które zostały użyte po uruchomieniu aplikacji przy użyciu dostawcy i włączył statystyki.</span><span class="sxs-lookup"><span data-stu-id="87bb4-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="87bb4-186">Na przykład może to obejmować dowolny zestaw wyników zwrócony do klienta.</span><span class="sxs-lookup"><span data-stu-id="87bb4-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="87bb4-187">W przypadku kursorów każda operacja pobierania lub pobierania blokowego jest uważana za niezależny zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="87bb4-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="87bb4-188">Zwraca liczbę transakcji użytkownika rozpoczętych po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki, w tym wycofywanie.</span><span class="sxs-lookup"><span data-stu-id="87bb4-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="87bb4-189">Jeśli połączenie jest uruchomione z automatycznym zatwierdzaniem, każde polecenie jest uważane za transakcję.</span><span class="sxs-lookup"><span data-stu-id="87bb4-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="87bb4-190">Ten licznik zwiększa liczbę transakcji, gdy tylko instrukcja BEGIN TRAN jest wykonywana, niezależnie od tego, czy transakcja została zatwierdzona, czy wycofana później.</span><span class="sxs-lookup"><span data-stu-id="87bb4-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="87bb4-191">Zwraca liczbę nieprzygotowanych instrukcji wykonanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.</span><span class="sxs-lookup"><span data-stu-id="87bb4-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="87bb4-192">Pobieranie wartości</span><span class="sxs-lookup"><span data-stu-id="87bb4-192">Retrieving a Value</span></span>  
 <span data-ttu-id="87bb4-193">W poniższej aplikacji konsoli pokazano, jak włączyć statystyki połączenia, pobrać cztery poszczególne wartości statystyczne i zapisać je w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="87bb4-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87bb4-194">W poniższym przykładzie użyto przykładowej bazy danych **AdventureWorks** dołączonej do programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87bb4-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="87bb4-195">Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="87bb4-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="87bb4-196">Zmodyfikuj parametry połączenia zgodnie z oczekiwaniami środowiska.</span><span class="sxs-lookup"><span data-stu-id="87bb4-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
### <a name="retrieving-all-values"></a><span data-ttu-id="87bb4-197">Pobieranie wszystkich wartości</span><span class="sxs-lookup"><span data-stu-id="87bb4-197">Retrieving All Values</span></span>  
 <span data-ttu-id="87bb4-198">W poniższej aplikacji konsoli pokazano, jak włączyć statystyki połączenia, pobrać wszystkie dostępne wartości statystyczne przy użyciu wylicznika i zapisać je w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="87bb4-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87bb4-199">W poniższym przykładzie użyto przykładowej bazy danych **AdventureWorks** dołączonej do programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87bb4-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="87bb4-200">Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="87bb4-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="87bb4-201">Zmodyfikuj parametry połączenia zgodnie z oczekiwaniami środowiska.</span><span class="sxs-lookup"><span data-stu-id="87bb4-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87bb4-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87bb4-202">See also</span></span>

- [<span data-ttu-id="87bb4-203">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="87bb4-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="87bb4-204">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="87bb4-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
