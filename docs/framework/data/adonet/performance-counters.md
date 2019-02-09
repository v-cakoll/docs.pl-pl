---
title: Liczniki wydajności w ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: e60df2b576980ecd1ff92af78cef36f025b71417
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903792"
---
# <a name="performance-counters-in-adonet"></a>Liczniki wydajności w ADO.NET
ADO.NET w wersji 2.0 wprowadzono rozszerzonej pomocy technicznej dla liczników wydajności, która obejmuje zarówno obsługę <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient>. <xref:System.Data.SqlClient> Dostępne w poprzednich wersjach programu ADO.NET, liczniki wydajności zostały przestarzały i zastąpiony nowe liczniki wydajności omówione w tym temacie. Liczniki wydajności programu ADO.NET umożliwia monitorowanie stanu aplikacji i zasobów połączenia, z których korzysta. Liczniki wydajności mogą być monitorowane przez korzystanie z Monitora wydajności Windows lub jest możliwy programowo przy użyciu <xref:System.Diagnostics.PerformanceCounter> klasy w <xref:System.Diagnostics> przestrzeni nazw.  
  
## <a name="available-performance-counters"></a>Dostępne liczniki wydajności  
 Obecnie istnieją 14 różnych liczników wydajności dla <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient> zgodnie z opisem w poniższej tabeli. Należy zauważyć, że nazwy poszczególnych liczników nie są zlokalizowane w różnych wersjach regionalnych programu Microsoft .NET Framework.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Liczba połączeń na sekundę, wprowadzone do serwera bazy danych.|  
|`HardDisconnectsPerSecond`|Odłącza liczba na sekundę, gdy są wprowadzane do serwera bazy danych.|  
|`NumberOfActiveConnectionPoolGroups`|Liczba grup puli unikatowego połączenia, które są aktywne. Ten licznik jest kontrolowana przez liczbę unikatowych ciągów połączeń, które znajdują się w domenie aplikacji.|  
|`NumberOfActiveConnectionPools`|Całkowita liczba pul połączeń.|  
|`NumberOfActiveConnections`|Liczba aktywnych połączeń, które są obecnie używane. **Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Liczba połączeń dostępnych do użycia w puli połączeń. **Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Liczba grup puli unikatowego połączenia, które są oznaczone do oczyszczenia. Ten licznik jest kontrolowana przez liczbę unikatowych ciągów połączeń, które znajdują się w domenie aplikacji.|  
|`NumberOfInactiveConnectionPools`|Liczba nieaktywnych pul połączeń nie przypisano żadnych ostatnich działań, które oczekują na usunięte.|  
|`NumberOfNonPooledConnections`|Liczba aktywnych połączeń, które nie są grupowane w pulach.|  
|`NumberOfPooledConnections`|Liczba aktywnych połączeń, które są zarządzane przez infrastrukturę do buforowania połączeń.|  
|`NumberOfReclaimedConnections`|Liczba połączeń, które zostały odzyskane do wyrzucania elementów bezużytecznych gdzie `Close` lub `Dispose` nie została wywołana przez aplikację. Nie zostały jawnie zamykanie lub usuwanie połączeń dobrze jest wydajność.|  
|`NumberOfStasisConnections`|Liczba połączeń aktualnie oczekiwanie na ukończenie działania i które są dostępne do użycia przez aplikację.|  
|`SoftConnectsPerSecond`|Liczba aktywnych połączeń, które są pobierane z puli połączeń. **Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Liczba aktywnych połączeń, które zostały zwrócone do puli połączeń. **Uwaga:**  Ten licznik wydajności nie jest włączona domyślnie. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki wyłączone domyślnie](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Grupy w puli połączeń i pule połączeń  
 Korzystając z uwierzytelniania Windows (zabezpieczeń zintegrowanych), należy monitorować zarówno `NumberOfActiveConnectionPoolGroups` i `NumberOfActiveConnectionPools` liczników wydajności. Przyczyną jest mapowane grup puli połączeń na unikatowych ciągów połączeń. Stosowania zabezpieczenia zintegrowane pul połączeń mapowania parametrów połączenia, a ponadto utworzyć osobne pule dla indywidualnych tożsamości Windows. Na przykład, jeśli Fred i Julie, każde w tej samej domenie aplikacji, jednocześnie użyć parametrów połączenia `"Data Source=MySqlServer;Integrated Security=true"`grupy puli połączeń jest tworzony dla parametrów połączenia i dwie dodatkowe pule są tworzone, jeden dla Fred i jeden dla Julie. Jeśli Jan i Martę za pomocą parametrów połączenia identyczne nazwy logowania programu SQL Server `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, a następnie pojedynczej puli jest tworzony dla **lowPrivUser** tożsamości.  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>Aktywowanie wyłączone domyślnie liczników  
 Liczniki wydajności `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, i `SoftConnectsPerSecond` są domyślnie wyłączone. Do pliku konfiguracji aplikacji, aby je włączyć, należy dodać następujące informacje:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Podczas pobierania wartości licznika wydajności  
 Następująca aplikacja konsoli Pokazuje, jak można pobrać wartości licznika wydajności w aplikacji. Połączenia muszą być otwartą i aktywną, aby uzyskać informacje, które mają zostać zwrócone wszystkie liczniki wydajności programu ADO.NET.  
  
> [!NOTE]
>  W tym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server. Parametry połączenia, udostępniane w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym za pomocą nazwy wystąpienia programu SqlExpress i utworzono nazwy logowania programu SQL Server, które pasują do terminów dostarczone w parametrach połączenia. Może być konieczne Włączanie logowania programu SQL Server, jeśli serwer jest skonfigurowany przy użyciu domyślnych ustawień zabezpieczeń, które pozwalają tylko uwierzytelnianie Windows. Zmodyfikuj parametry połączenia, zgodnie z potrzebami, w zależności od środowiska.  
  
### <a name="example"></a>Przykład  
  
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
        ' you can retrieve it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
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
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a>Zobacz także
- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Buforowanie połączenia Oracle, OLE DB i ODBC](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [Liczniki wydajności dla programu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Profilowanie środowiska uruchomieniowego](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)
- [Wprowadzenie do monitorowania progów wydajności](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [Omówienie ADO.NET](ado-net-overview.md)
