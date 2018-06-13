---
title: Liczniki wydajności w ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 8696bf567d8f32fc3bc3f78e127631f488c551aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365119"
---
# <a name="performance-counters-in-adonet"></a>Liczniki wydajności w ADO.NET
Rozszerzona obsługa liczników wydajności, który zawiera obsługę zarówno wprowadzone ADO.NET 2.0 <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient>. <xref:System.Data.SqlClient> Dostępne w poprzednich wersjach programu ADO.NET liczniki wydajności zostały przestarzałe i zastępowane nowe liczniki wydajności omówione w tym temacie. Liczniki wydajności ADO.NET służy do monitorowania stanu aplikacji i zasobów połączenia, których używa. Liczniki wydajności można monitorować za pomocą Monitora wydajności systemu Windows lub mogą uzyskiwać programowo przy użyciu <xref:System.Diagnostics.PerformanceCounter> klasy w <xref:System.Diagnostics> przestrzeni nazw.  
  
## <a name="available-performance-counters"></a>Dostępnych liczników wydajności  
 Obecnie brak 14 liczników wydajności różnych dostępnych dla <xref:System.Data.SqlClient> i <xref:System.Data.OracleClient> zgodnie z opisem w poniższej tabeli. Należy pamiętać, że nazwy dla poszczególnych liczników nie są zlokalizowane w regionalnych wersji programu Microsoft .NET Framework.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Liczba połączeń na sekundę, które są nawiązywane z serwerem bazy danych.|  
|`HardDisconnectsPerSecond`|Liczba rozłącza na sekundę, które są nawiązywane z serwerem bazy danych.|  
|`NumberOfActiveConnectionPoolGroups`|Numer grupy puli połączeń, które są aktywne. Ten licznik jest kontrolowana przez liczbę unikatowych parametrów połączeń, które znajdują się w domenie aplikacji.|  
|`NumberOfActiveConnectionPools`|Całkowita liczba pul połączeń.|  
|`NumberOfActiveConnections`|Liczba aktywnych połączeń, które są obecnie używane. **Uwaga:** ten licznik wydajności nie jest domyślnie włączona. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki poza domyślnie](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Liczba połączeń można używać pul połączeń. **Uwaga:** ten licznik wydajności nie jest domyślnie włączona. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki poza domyślnie](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Liczba grup puli połączeń, które są oznaczone do oczyszczania. Ten licznik jest kontrolowana przez liczbę unikatowych parametrów połączeń, które znajdują się w domenie aplikacji.|  
|`NumberOfInactiveConnectionPools`|Liczba nieaktywnych pul połączeń nie przypisano żadnych ostatnią aktywność, które oczekują na usunięcie go.|  
|`NumberOfNonPooledConnections`|Liczba aktywnych połączeń, które nie są grupowane w pulach.|  
|`NumberOfPooledConnections`|Liczba aktywnych połączeń, które są zarządzane przez infrastrukturę do buforowania połączeń.|  
|`NumberOfReclaimedConnections`|Liczba połączeń, które odzyskano za pośrednictwem wyrzucanie elementów bezużytecznych gdzie `Close` lub `Dispose` nie została wywołana przez aplikację. Nie są jawnie zamknięcie lub usuwanie połączeń powinna wydajności.|  
|`NumberOfStasisConnections`|Liczba połączeń aktualnie oczekujących na ukończenie działania i które są niedostępne do użytku przez aplikację.|  
|`SoftConnectsPerSecond`|Liczba aktywnych połączeń pochodzi z puli połączeń. **Uwaga:** ten licznik wydajności nie jest domyślnie włączona. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki poza domyślnie](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Liczba aktywnych połączeń zwróconych do puli połączeń. **Uwaga:** ten licznik wydajności nie jest domyślnie włączona. Aby włączyć ten licznik wydajności, zobacz [aktywowanie liczniki poza domyślnie](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Grupy puli połączeń i pul połączeń  
 Podczas korzystania z uwierzytelniania systemu Windows (zintegrowanych zabezpieczeń), należy monitorować zarówno `NumberOfActiveConnectionPoolGroups` i `NumberOfActiveConnectionPools` liczników wydajności. Przyczyną jest mapowane grupy puli połączeń na unikatowych parametrów połączeń. Gdy używane są zabezpieczenia zintegrowane pul połączeń mapowania parametrów połączenia i ponadto utworzyć oddzielne pule dla indywidualnych tożsamości systemu Windows. Na przykład, jeśli Krzysztof i Julie, każde w tej samej domenie AppDomain jednocześnie użyć parametrów połączenia `"Data Source=MySqlServer;Integrated Security=true"`grupy puli połączeń jest tworzony dla parametrów połączenia i dwa dodatkowe pule są tworzone, jeden dla Krzysztof i jeden dla Julie. Jan i Marta używania ciągu połączenia z identycznymi logowania programu SQL Server, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, a następnie tylko jednej puli jest tworzona dla **lowPrivUser** tożsamości.  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>Aktywowanie poza domyślnie liczników  
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
 Następującej aplikacji konsoli Pokazuje, jak można pobrać wartości licznika wydajności w aplikacji. Połączenia muszą być otwarte i aktywne informacje mają być zwracane dla wszystkich liczników wydajności ADO.NET.  
  
> [!NOTE]
>  W tym przykładzie użyto przykładowej **AdventureWorks** bazy danych programu SQL Server. Parametry połączenia w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym za pomocą nazwy wystąpienia programu SqlExpress i utworzono logowania do programu SQL Server, które są zgodne z tymi dostarczone w parametrach połączenia. Może być konieczne włączenie logowania do programu SQL Server, jeśli serwer jest skonfigurowany przy użyciu domyślnych ustawień zabezpieczeń, które umożliwiają tylko uwierzytelnianie systemu Windows. Zmodyfikuj parametry połączenia, odpowiednio do potrzeb środowiska.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Buforowanie połączenia Oracle, OLE DB i ODBC](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [Liczniki wydajności dla programu ASP.NET](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [Profilowanie środowiska uruchomieniowego](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [Wprowadzenie do monitorowania wydajności progi](http://msdn.microsoft.com/library/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
