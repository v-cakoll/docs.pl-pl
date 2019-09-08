---
title: Statystyki dostawcy dla programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b6fa4207531e86cbde8657d0c47596f22c886f89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791872"
---
# <a name="provider-statistics-for-sql-server"></a>Statystyki dostawcy dla programu SQL Server
Począwszy od .NET Framework w wersji 2,0, .NET Framework Dostawca danych dla SQL Server obsługuje statystyki czasu wykonywania. Aby włączyć statystykę, należy ustawić <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu na `True` po utworzeniu prawidłowego obiektu połączenia. Po włączeniu statystyk można je przejrzeć jako "migawkę w czasie", pobierając <xref:System.Collections.IDictionary> odwołanie <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> za pomocą metody <xref:System.Data.SqlClient.SqlConnection> obiektu. Wyliczasz listę jako zbiór wpisów słownika par nazwa/wartość. Te pary nazwa/wartość są nieuporządkowane. W dowolnym momencie można wywołać <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodę <xref:System.Data.SqlClient.SqlConnection> obiektu, aby zresetować liczniki. Jeśli zbieranie informacji statystycznych nie zostało włączone, wyjątek nie jest generowany. Ponadto, jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> uprzedniego wywołania, pobierane wartości są początkowymi wartościami dla każdego wpisu. W przypadku włączenia statystyk, uruchomienia aplikacji przez pewien czas, a następnie wyłączenia statystyk, pobrane wartości będą odzwierciedlać wartości zbierane do punktu, w którym statystyki zostały wyłączone. Wszystkie zebrane wartości statystyczne dotyczą poszczególnych połączeń.  
  
## <a name="statistical-values-available"></a>Dostępne wartości statystyczne  
 Obecnie dla dostawcy Microsoft SQL Server dostępne są 18 różnych elementów. Dostępną liczbę elementów można uzyskać za pomocą właściwości **Count** odwołania do <xref:System.Collections.IDictionary> interfejsu zwróconego przez. <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> We wszystkich licznikach statystyk dostawcy używany jest typ środowiska uruchomieniowego <xref:System.Int64> języka wspólnego (Long C# in i Visual Basic), który jest 64 bitów. Wartość maksymalna typu **Int64** , zgodnie z definicją podaną przez **Int64. MaxValue** pole jest ((2 ^ 63)-1)). Gdy wartości liczników docierają do tej wartości maksymalnej, nie powinny być już dokładnie traktowane jako dokładne. Oznacza to, że **Int64. MaxValue**-1 ((2 ^ 63)-2) jest efektywnie największą prawidłową wartością dla każdej statystyki.  
  
> [!NOTE]
> Słownik jest używany do zwracania statystyk dostawcy, ponieważ liczba, nazwy i kolejność zwróconych statystyk mogą ulec zmianie w przyszłości. Aplikacje nie powinny polegać na określonej wartości znalezionej w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest odpowiednio i rozgałęzienia.  
  
 W poniższej tabeli opisano bieżące dostępne wartości statystyczne. Należy zauważyć, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w regionalnych wersjach środowiska Microsoft .NET Framework.  
  
|Nazwa klucza|Opis|  
|--------------|-----------------|  
|`BuffersReceived`|Zwraca liczbę pakietów strumienia danych tabelarycznych (TDS) odebranych przez dostawcę z SQL Server po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.|  
|`BuffersSent`|Zwraca liczbę pakietów TDS wysłanych do SQL Server przez dostawcę po włączeniu statystyk. Duże polecenia mogą wymagać wielu buforów. Na przykład, jeśli do serwera jest wysyłane duże polecenie, które wymaga sześciu pakietów, `ServerRoundtrips` zwiększa się o jeden i `BuffersSent` zwiększa się o sześć.|  
|`BytesReceived`|Zwraca liczbę bajtów danych w pakietach TDS odbieranych przez dostawcę z SQL Server po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.|  
|`BytesSent`|Zwraca liczbę bajtów danych wysyłanych do SQL Server w pakietach TDS po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.|  
|`ConnectionTime`|Czas (w milisekundach), przez jaki połączenie zostało otwarte po włączeniu statystyk (łączny czas połączenia, jeśli Statystyka została włączona przed otwarciem połączenia).|  
|`CursorOpens`|Zwraca liczbę przypadków otwarcia kursora przez połączenie po rozpoczęciu pracy aplikacji przy użyciu dostawcy i włączeniu statystyk.<br /><br /> Zwróć uwagę, że wyniki tylko do odczytu/do przodu zwracane przez instrukcje SELECT nie są uważane za kursory i w ten sposób nie wpływają na ten licznik.|  
|`ExecutionTime`|Zwraca łączny czas (w milisekundach), przez jaki dostawca spędził przetwarzanie po włączeniu statystyk, w tym czas oczekiwania na odpowiedzi z serwera, a także czas poświęcony na wykonanie kodu w samym dostawcy.<br /><br /> Klasy, które zawierają kod chronometrażu są:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Aby zapewnić możliwie najmniejszą wydajność krytycznych elementów członkowskich, następujące elementy członkowskie nie przekroczą czasu:<br /><br /> SqlDataReader<br /><br /> This [] — operator (wszystkie przeciążenia)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName —<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Zwraca łączną liczbę instrukcji INSERT, DELETE i UPDATE wykonywanych przez połączenie po rozpoczęciu uruchamiania aplikacji przy użyciu dostawcy i włączeniu statystyk.|  
|`IduRows`|Zwraca łączną liczbę wierszy, na które mają wpływ instrukcje INSERT, DELETE i UPDATE wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystyki.|  
|`NetworkServerTime`|Zwraca łączny czas (w milisekundach), przez jaki dostawca poświęca na odpowiedzi z serwera po rozpoczęciu pracy przez aplikację przy użyciu dostawcy i włączył statystykę.|  
|`PreparedExecs`|Zwraca liczbę przygotowanych poleceń wykonywanych przez połączenie po rozpoczęciu uruchamiania aplikacji przy użyciu dostawcy i włączeniu statystyk.|  
|`Prepares`|Zwraca liczbę instrukcji przygotowanych przez połączenie po rozpoczęciu uruchamiania aplikacji przy użyciu dostawcy i włączonych statystyk.|  
|`SelectCount`|Zwraca liczbę instrukcji SELECT wykonywanych za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystyki. Obejmuje to instrukcje pobierania do pobrania wierszy z kursorów, a liczba instrukcji SELECT jest aktualizowana po osiągnięciu końca elementu <xref:System.Data.SqlClient.SqlDataReader> .|  
|`SelectRows`|Zwraca liczbę wierszy wybranych po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączonych statystyk. Ten licznik odzwierciedla wszystkie wiersze wygenerowane przez instrukcje SQL, nawet te, które nie zostały faktycznie wykorzystane przez wywołującego. Na przykład zamknięcie czytnika danych przed odczytaniem całego zestawu wyników nie wpłynie na liczbę. Obejmuje to wiersze pobierane z kursorów za pomocą instrukcji FETCH.|  
|`ServerRoundtrips`|Zwraca liczbę poleceń wysłanych przez połączenie do serwera i odebranie odpowiedzi z powrotem po rozpoczęciu działania aplikacji przy użyciu dostawcy i włączeniu statystyk.|  
|`SumResultSets`|Zwraca liczbę zestawów wyników, które były używane po uruchomieniu aplikacji przy użyciu dostawcy i włączonych statystyk. Na przykład może to obejmować dowolny zestaw wyników zwrócony klientowi. W przypadku kursorów każda operacja pobierania lub pobierania bloku jest uznawana za niezależny zestaw wyników.|  
|`Transactions`|Zwraca liczbę transakcji użytkownika rozpoczętych, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystykę, włącznie z wycofywaniem. Jeśli połączenie jest uruchomione z funkcją automatycznego zatwierdzania, każde polecenie jest uznawane za transakcję.<br /><br /> Ten licznik zwiększa liczbę transakcji zaraz po wykonaniu instrukcji BEGIN przeładunku, niezależnie od tego, czy transakcja została zatwierdzona czy wycofana później.|  
|`UnpreparedExecs`|Zwraca liczbę nieprzygotowanych instrukcji wykonywanych za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączyła statystyki.|  
  
### <a name="retrieving-a-value"></a>Pobieranie wartości  
 W poniższej aplikacji konsolowej pokazano, jak włączyć statystykę połączenia, pobrać cztery poszczególne wartości statystyczne i zapisać je w oknie konsoli.  
  
> [!NOTE]
> Poniższy przykład używa przykładowej bazy danych **AdventureWorks** dołączonej do SQL Server. Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym. Zmodyfikuj parametry połączenia jako niezbędne dla danego środowiska.  
  
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
  
### <a name="retrieving-all-values"></a>Pobieranie wszystkich wartości  
 W poniższej aplikacji konsolowej pokazano, jak włączyć statystykę połączenia, pobrać wszystkie dostępne wartości statystyczne przy użyciu modułu wyliczającego i zapisać je w oknie konsoli.  
  
> [!NOTE]
> Poniższy przykład używa przykładowej bazy danych **AdventureWorks** dołączonej do SQL Server. Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym. Zmodyfikuj parametry połączenia jako niezbędne dla danego środowiska.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
