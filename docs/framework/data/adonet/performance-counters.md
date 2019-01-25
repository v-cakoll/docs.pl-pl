---
title: Liczniki wydajności w ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: a17d0b2382f105bb6299386e45a6746e05c39feb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539067"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="d0e5b-102">Liczniki wydajności w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0e5b-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="d0e5b-103">ADO.NET w wersji 2.0 wprowadzono rozszerzonej pomocy technicznej dla liczników wydajności, która obejmuje zarówno obsługę <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="d0e5b-104"><xref:System.Data.SqlClient> Dostępne w poprzednich wersjach programu ADO.NET, liczniki wydajności zostały przestarzały i zastąpiony nowe liczniki wydajności omówione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="d0e5b-105">Liczniki wydajności programu ADO.NET umożliwia monitorowanie stanu aplikacji i zasobów połączenia, z których korzysta.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="d0e5b-106">Liczniki wydajności mogą być monitorowane przez korzystanie z Monitora wydajności Windows lub jest możliwy programowo przy użyciu <xref:System.Diagnostics.PerformanceCounter> klasy w <xref:System.Diagnostics> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="d0e5b-107">Dostępne liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="d0e5b-107">Available Performance Counters</span></span>  
 <span data-ttu-id="d0e5b-108">Obecnie istnieją 14 różnych liczników wydajności dla <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient> zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="d0e5b-109">Należy zauważyć, że nazwy poszczególnych liczników nie są zlokalizowane w różnych wersjach regionalnych programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="d0e5b-110">Licznik wydajności</span><span class="sxs-lookup"><span data-stu-id="d0e5b-110">Performance counter</span></span>|<span data-ttu-id="d0e5b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d0e5b-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="d0e5b-112">Liczba połączeń na sekundę, wprowadzone do serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="d0e5b-113">Odłącza liczba na sekundę, gdy są wprowadzane do serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="d0e5b-114">Liczba grup puli unikatowego połączenia, które są aktywne.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="d0e5b-115">Ten licznik jest kontrolowana przez liczbę unikatowych ciągów połączeń, które znajdują się w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="d0e5b-116">Całkowita liczba pul połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="d0e5b-117">Liczba aktywnych połączeń, które są obecnie używane.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="d0e5b-118">**Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="d0e5b-119">Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="d0e5b-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="d0e5b-120">Liczba połączeń dostępnych do użycia w puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="d0e5b-121">**Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="d0e5b-122">Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="d0e5b-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="d0e5b-123">Liczba grup puli unikatowego połączenia, które są oznaczone do oczyszczenia.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="d0e5b-124">Ten licznik jest kontrolowana przez liczbę unikatowych ciągów połączeń, które znajdują się w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="d0e5b-125">Liczba nieaktywnych pul połączeń nie przypisano żadnych ostatnich działań, które oczekują na usunięte.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="d0e5b-126">Liczba aktywnych połączeń, które nie są grupowane w pulach.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="d0e5b-127">Liczba aktywnych połączeń, które są zarządzane przez infrastrukturę do buforowania połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="d0e5b-128">Liczba połączeń, które zostały odzyskane do wyrzucania elementów bezużytecznych gdzie `Close` lub `Dispose` nie została wywołana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="d0e5b-129">Nie zostały jawnie zamykanie lub usuwanie połączeń dobrze jest wydajność.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="d0e5b-130">Liczba połączeń aktualnie oczekiwanie na ukończenie działania i które są dostępne do użycia przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="d0e5b-131">Liczba aktywnych połączeń, które są pobierane z puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="d0e5b-132">**Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="d0e5b-133">Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="d0e5b-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="d0e5b-134">Liczba aktywnych połączeń, które zostały zwrócone do puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="d0e5b-135">**Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="d0e5b-136">Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="d0e5b-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="d0e5b-137">Grupy w puli połączeń i pule połączeń</span><span class="sxs-lookup"><span data-stu-id="d0e5b-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="d0e5b-138">Korzystając z uwierzytelniania Windows (zabezpieczeń zintegrowanych), należy monitorować zarówno `NumberOfActiveConnectionPoolGroups` i `NumberOfActiveConnectionPools` liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="d0e5b-139">Przyczyną jest mapowane grup puli połączeń na unikatowych ciągów połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="d0e5b-140">Stosowania zabezpieczenia zintegrowane pul połączeń mapowania parametrów połączenia, a ponadto utworzyć osobne pule dla indywidualnych tożsamości Windows.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="d0e5b-141">Na przykład, jeśli Fred i Julie, każde w tej samej domenie aplikacji, jednocześnie użyć parametrów połączenia `"Data Source=MySqlServer;Integrated Security=true"`grupy puli połączeń jest tworzony dla parametrów połączenia i dwie dodatkowe pule są tworzone, jeden dla Fred i jeden dla Julie.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="d0e5b-142">Jeśli Jan i Martę za pomocą parametrów połączenia identyczne nazwy logowania programu SQL Server `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, a następnie pojedynczej puli jest tworzony dla **lowPrivUser** tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="d0e5b-143">Aktywowanie wyłączone domyślnie liczników</span><span class="sxs-lookup"><span data-stu-id="d0e5b-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="d0e5b-144">Liczniki wydajności `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, i `SoftConnectsPerSecond` są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="d0e5b-145">Do pliku konfiguracji aplikacji, aby je włączyć, należy dodać następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="d0e5b-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="d0e5b-146">Podczas pobierania wartości licznika wydajności</span><span class="sxs-lookup"><span data-stu-id="d0e5b-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="d0e5b-147">Następująca aplikacja konsoli Pokazuje, jak można pobrać wartości licznika wydajności w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="d0e5b-148">Połączenia muszą być otwartą i aktywną, aby uzyskać informacje, które mają zostać zwrócone wszystkie liczniki wydajności programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0e5b-149">W tym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-149">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="d0e5b-150">Parametry połączenia, udostępniane w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym za pomocą nazwy wystąpienia programu SqlExpress i utworzono nazwy logowania programu SQL Server, które pasują do terminów dostarczone w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="d0e5b-151">Może być konieczne Włączanie logowania programu SQL Server, jeśli serwer jest skonfigurowany przy użyciu domyślnych ustawień zabezpieczeń, które pozwalają tylko uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="d0e5b-152">Zmodyfikuj parametry połączenia, zgodnie z potrzebami, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="d0e5b-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0e5b-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0e5b-153">Example</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.   
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.   
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\   
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's   
        'FriendlyName. Replace the line above that sets the instanceName with this:   
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's   
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
        //  "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0e5b-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0e5b-154">See also</span></span>
- [<span data-ttu-id="d0e5b-155">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="d0e5b-155">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="d0e5b-156">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="d0e5b-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="d0e5b-157">Liczniki wydajności dla programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d0e5b-157">Performance Counters for ASP.NET</span></span>](https://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)
- [<span data-ttu-id="d0e5b-158">Profilowanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d0e5b-158">Runtime Profiling</span></span>](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)
- [<span data-ttu-id="d0e5b-159">Wprowadzenie do monitorowania progów wydajności</span><span class="sxs-lookup"><span data-stu-id="d0e5b-159">Introduction to Monitoring Performance Thresholds</span></span>](https://msdn.microsoft.com/library/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)
- [<span data-ttu-id="d0e5b-160">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d0e5b-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
