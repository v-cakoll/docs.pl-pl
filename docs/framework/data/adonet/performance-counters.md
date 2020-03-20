---
title: Liczniki wydajności
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: b68787980a8b64d9ee90ed8d834fab2c5c69006b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149339"
---
# <a name="performance-counters-in-adonet"></a>Liczniki wydajności w ADO.NET
ADO.NET 2.0 wprowadzono rozszerzoną obsługę liczników wydajności, <xref:System.Data.SqlClient> która <xref:System.Data.OracleClient>obejmuje obsługę obu i . Liczniki <xref:System.Data.SqlClient> wydajności dostępne w poprzednich wersjach ADO.NET zostały przestarzałe i zastąpione nowymi licznikami wydajności omówionymi w tym temacie. Liczniki wydajności ADO.NET można używać do monitorowania stanu aplikacji i zasobów połączenia, których używa. Liczniki wydajności mogą być monitorowane za pomocą Monitora wydajności systemu <xref:System.Diagnostics.PerformanceCounter> Windows <xref:System.Diagnostics> lub można uzyskać dostęp programowo przy użyciu klasy w obszarze nazw.  
  
## <a name="available-performance-counters"></a>Dostępne liczniki wydajności  
 Obecnie dostępnych jest 14 różnych liczników wydajności <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient> zgodnie z opisem w poniższej tabeli. Należy zauważyć, że nazwy poszczególnych liczników nie są zlokalizowane w regionalnych wersjach programu Microsoft .NET Framework.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Liczba połączeń na sekundę, które są wprowadzane do serwera bazy danych.|  
|`HardDisconnectsPerSecond`|Liczba rozłączenia na sekundę, które są wprowadzane do serwera bazy danych.|  
|`NumberOfActiveConnectionPoolGroups`|Liczba unikatowych grup puli połączeń, które są aktywne. Ten licznik jest kontrolowany przez liczbę unikatowych ciągów połączeń, które znajdują się w AppDomain.|  
|`NumberOfActiveConnectionPools`|Całkowita liczba pul połączeń.|  
|`NumberOfActiveConnections`|Liczba aktywnych połączeń, które są obecnie używane. **Uwaga:**  Ten licznik wydajności nie jest domyślnie włączony. Aby włączyć ten licznik wydajności, zobacz [Aktywowanie liczników domyślnych](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Liczba połączeń dostępnych do użycia w pulach połączeń. **Uwaga:**  Ten licznik wydajności nie jest domyślnie włączony. Aby włączyć ten licznik wydajności, zobacz [Aktywowanie liczników domyślnych](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Liczba unikatowych grup puli połączeń, które są oznaczone do przycinania. Ten licznik jest kontrolowany przez liczbę unikatowych ciągów połączeń, które znajdują się w AppDomain.|  
|`NumberOfInactiveConnectionPools`|Liczba nieaktywnych pul połączeń, które nie miały ostatnio aktywności i oczekują na usunięcie.|  
|`NumberOfNonPooledConnections`|Liczba aktywnych połączeń, które nie są połączone.|  
|`NumberOfPooledConnections`|Liczba aktywnych połączeń, które są zarządzane przez infrastrukturę buforowania połączeń.|  
|`NumberOfReclaimedConnections`|Liczba połączeń, które zostały odzyskane za pośrednictwem `Close` `Dispose` wyrzucania elementów bezużytecznych, gdzie lub nie został wywołany przez aplikację. Nie jawnie zamykanie lub usuwanie połączeń wpływa na wydajność.|  
|`NumberOfStasisConnections`|Liczba połączeń oczekujących obecnie oczekujących na zakończenie akcji i które w związku z tym są niedostępne do użycia przez aplikację.|  
|`SoftConnectsPerSecond`|Liczba aktywnych połączeń pobieranych z puli połączeń. **Uwaga:**  Ten licznik wydajności nie jest domyślnie włączony. Aby włączyć ten licznik wydajności, zobacz [Aktywowanie liczników domyślnych](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Liczba aktywnych połączeń, które są zwracane do puli połączeń. **Uwaga:**  Ten licznik wydajności nie jest domyślnie włączony. Aby włączyć ten licznik wydajności, zobacz [Aktywowanie liczników domyślnych](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Grupy puli połączeń i pule połączeń  
 Podczas korzystania z uwierzytelniania systemu Windows `NumberOfActiveConnectionPoolGroups` (zintegrowane zabezpieczenia), należy monitorować zarówno liczniki wydajności, jak i `NumberOfActiveConnectionPools` wydajności. Powodem jest to, że grupy puli połączeń mapują unikatowe parametry połączenia. Gdy używane są zintegrowane zabezpieczenia, pule połączeń mapują parametry połączenia i dodatkowo tworzą oddzielne pule dla poszczególnych tożsamości systemu Windows. Na przykład jeśli Fred i Julie, każdy w tej samej `"Data Source=MySqlServer;Integrated Security=true"`AppDomain, zarówno użyć ciągu połączenia, grupa puli połączeń jest tworzony dla ciągu połączenia i dwa dodatkowe pule są tworzone, jeden dla Fred i jeden dla Julie. Jeśli John i Martha używają ciągu połączenia z `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`identycznym logowaniem programu SQL Server, wówczas dla tożsamości **lowPrivUser** jest tworzona tylko pojedyncza pula.  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a>Aktywowanie liczników domyślnych  
 Liczniki `NumberOfFreeConnections`wydajności `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, `SoftConnectsPerSecond` i są domyślnie wyłączone. Dodaj następujące informacje do pliku konfiguracyjnego aplikacji, aby je włączyć:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Pobieranie wartości licznika wydajności  
 W poniższej aplikacji konsoli pokazano, jak pobrać wartości licznika wydajności w aplikacji. Połączenia muszą być otwarte i aktywne, aby informacje były zwracane dla wszystkich liczników wydajności ADO.NET.  
  
> [!NOTE]
> W tym przykładzie użyto przykładowej bazy danych **AdventureWorks** dołączonej do programu SQL Server. Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym o nazwie wystąpienia SqlExpress i że utworzono logowania programu SQL Server, które są zgodne z tymi dostarczonymi w ciągu połączenia. Może być konieczne włączenie logowania programu SQL Server, jeśli serwer jest skonfigurowany przy użyciu domyślnych ustawień zabezpieczeń, które zezwalają tylko na uwierzytelnianie systemu Windows. Zmodyfikuj parametry połączenia zgodnie z potrzebami, aby dostosować je do potrzeb środowiska.  
  
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

## <a name="see-also"></a>Zobacz też

- [Łączenie się ze źródłem danych](connecting-to-a-data-source.md)
- [Buforowanie połączenia Oracle, OLE DB i ODBC](ole-db-odbc-and-oracle-connection-pooling.md)
- [Liczniki wydajności dla ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Profilowanie środowiska uruchomieniowego](../../debug-trace-profile/runtime-profiling.md)
- [Wprowadzenie do progów wydajności monitorowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [Omówienie ADO.NET](ado-net-overview.md)
