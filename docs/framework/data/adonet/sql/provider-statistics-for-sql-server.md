---
title: Statystyki dostawcy dla programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: d52c6bfdadf0a53ac4c5f62c37f1056c6702a82c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970217"
---
# <a name="provider-statistics-for-sql-server"></a>Statystyki dostawcy dla programu SQL Server
Począwszy od programu .NET Framework w wersji 2.0, .NET Framework Data Provider for SQL Server obsługuje statystyki czasu wykonywania. Należy włączyć statystyki, ustawiając <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiekt `True` po poprawnego obiektu połączenia utworzone. Po statystyki są włączone, można przejrzeć je jako "migawki w czasie" pobierając <xref:System.Collections.IDictionary> odwoływać się za pośrednictwem <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiektu. Wyliczanie za pośrednictwem listy jako zbiór wpisy słownika par nazwa/wartość. Tych par nazwa/wartość są nieuporządkowane. W dowolnym momencie możesz wywołać <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiekt, aby zresetować liczniki. Jeśli zbieranie wartości licznika statystyka nie została włączona, wyjątek nie zostanie wygenerowany. Ponadto jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> o najpierw wywołuje, są wartościami pobranymi początkowe wartości dla każdego wpisu. Jeśli włączysz statystyki, uruchomienie aplikacji przez jakiś czas i następnie wyłącz statystyki, wartościami pobranymi będą odzwierciedlać wartości, które są zbierane aż do momentu, gdy statystyki zostały wyłączone. Wszystkie wartości statystyczne zebrane znajdują się na poszczególnych połączeń.  
  
## <a name="statistical-values-available"></a>Dostępne wartości statystyczne  
 Obecnie istnieją 18 różnych elementów od dostawcy programu Microsoft SQL Server. Liczba elementów jest możliwy za pośrednictwem **liczba** właściwość <xref:System.Collections.IDictionary> Odwołanie zwrócone przez interfejs <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Wszystkie liczniki dla statystyki dostawcy używać środowiska uruchomieniowego języka wspólnego <xref:System.Int64> typu (**długie** w języku C# i Visual Basic), który jest 64-bitowy szeroki. Maksymalna wartość **int64** typu danych, zgodnie z definicją **int64. MaxValue** pola, ((2^63) 1)). Jeśli wartości liczników osiągnąć tę wartość maksymalna, są już należy rozważyć dokładne. Oznacza to, że **int64. MaxValue**-1((2^63)-2) jest faktycznie największy prawidłową wartość wszystkie statystyki.  
  
> [!NOTE]
>  Słownik służy do zwracania statystyki dostawcy, ponieważ numer, nazwy i kolejność zwracane statystyki może ulec zmianie w przyszłości. Aplikacje nie należy polegać na określoną wartość, zostanie on znaleziony w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest i odpowiednio gałęzi.  
  
 W poniższej tabeli opisano bieżące wartości statystyczne dostępne. Należy zauważyć, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w różnych wersjach regionalnych programu Microsoft .NET Framework.  
  
|Nazwa klucza|Opis|  
|--------------|-----------------|  
|`BuffersReceived`|Zwraca liczbę strumienia danych tabelarycznych (TDS) odebrane pakiety przez dostawcę z programu SQL Server po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`BuffersSent`|Zwraca liczbę TDS pakiety wysyłane do programu SQL Server przez dostawcę po włączeniu statystyk. Duże poleceń może wymagać wielu buforów. Na przykład, jeśli polecenie dużych są wysyłane do serwera i wymaga sześć pakietów `ServerRoundtrips` jest zwiększany o jeden i `BuffersSent` jest zwiększany o sześciu.|  
|`BytesReceived`|Zwraca liczbę bajtów danych w pakietach TDS odebrane przez dostawcę z programu SQL Server, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`BytesSent`|Zwraca liczbę bajtów danych wysyłanych do serwera SQL w pakietach TDS po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`ConnectionTime`|Ilość czasu (w milisekundach), że połączenie zostało otwarte po włączeniu statystyki (całkowity czas połączenia, jeśli statystyki zostały włączone przed otwarciem połączenie).|  
|`CursorOpens`|Zwraca liczbę przypadków, gdy kursor był otwarty za pośrednictwem połączenia w przypadku, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.<br /><br /> Pamiętaj, że tylko/do przodu — tylko do odczytu wyników zwróconych przez instrukcji "SELECT" nie są uważane za kursorów, a zatem nie wpływają na wartość tego licznika.|  
|`ExecutionTime`|Zwraca wartość łącznego czasu (w milisekundach), czy dostawca jest poświęcony na przetwarzanie po włączeniu statystyki, w tym czas oczekiwania na odpowiedzi z serwera, a także czas poświęcony na wykonywanie kodu w samej dostawcy.<br /><br /> Klasy, które zawierają kod chronometrażu są:<br /><br /> Element SqlConnection<br /><br /> Klasy SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Aby zachować wydajność krytycznych członków tak małej, jak to możliwe, następujące elementy członkowskie są nie upłynął limit czasu:<br /><br /> SqlDataReader<br /><br /> Ten operator [] (wszystkie przeciążenia)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> Getguid —<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> Getname —<br /><br /> Getordinal —<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString —<br /><br /> IsDBNull|  
|`IduCount`|Zwraca sumę instrukcje INSERT, usuwania i aktualizacji, które są wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`IduRows`|Zwraca łączną liczbę wierszy, o których wpływ instrukcje INSERT, usuwania i aktualizacji, które są wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`NetworkServerTime`|Zwraca łącznego czasu (w milisekundach), dostawca poświęcony oczekiwania na odpowiedzi z serwera, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki.|  
|`PreparedExecs`|Zwraca liczbę przygotowanego polecenia wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`Prepares`|Zwraca liczbę instrukcji przygotowane przez połączenie, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`SelectCount`|Zwraca liczbę instrukcji "SELECT" wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk. Dotyczy to również instrukcje pobierania, aby pobierać wiersze z kursorami i liczbę elementów w instrukcji "SELECT" jest aktualizowana po końcu <xref:System.Data.SqlClient.SqlDataReader> zostanie osiągnięty.|  
|`SelectRows`|Zwraca liczbę wierszy wybrany, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk. Ten licznik wskazuje wszystkie wiersze, które są generowane przez instrukcje SQL, nawet te, które faktycznie nie były używane przez obiekt wywołujący. Na przykład zamknięcia czytnika danych przed odczytaniem cały zestaw wyników nie wpłynie na liczbę. W tym wiersze, pobierane z kursorami za pomocą instrukcji pobierania.|  
|`ServerRoundtrips`|Zwraca liczbę połączeń wysyłanych poleceń do serwera i otrzymano odpowiedź, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki.|  
|`SumResultSets`|Zwraca liczbę wyników zestawów, które były używane w taki sposób, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk. Na przykład to dotyczy wszelkich zestaw wyników, zwracany do klienta. Kursory każdej operacji pobierania lub fetch bloku są uznawane za zestawu wyników niezależnych.|  
|`Transactions`|Zwraca liczbę pracę, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki, w tym funkcji wycofywania transakcji. Jeśli połączenie jest uruchomiony przy użyciu automatycznego zatwierdzenia na, każde polecenie jest traktowany jako jedna transakcja.<br /><br /> Ten licznik zwiększa się liczba transakcji zaraz po wykonaniu instrukcji BEGIN TRAN, niezależnie od tego, czy transakcja jest przekazana lub wycofana później.|  
|`UnpreparedExecs`|Zwraca liczbę instrukcji nieprzygotowane wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
  
### <a name="retrieving-a-value"></a>Pobieranie wartości  
 Następująca aplikacja konsoli Pokazuje, jak włączyć statystyki dotyczące połączenia, pobrać cztery wartości poszczególnych statystyk i zapisać je w oknie konsoli.  
  
> [!NOTE]
>  W poniższym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server. Parametry połączenia, udostępniane w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym. Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.  
  
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
  
### <a name="retrieving-all-values"></a>Pobieranie wszystkich wartości  
 Następująca aplikacja konsoli Pokazuje, jak włączyć statystyki dotyczące połączenia, pobrać wszystkie dostępne statystyki wartości, przy użyciu modułu wyliczającego i zapisanie ich w oknie konsoli.  
  
> [!NOTE]
>  W poniższym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server. Parametry połączenia, udostępniane w przykładowym kodzie założono, że baza danych jest zainstalowany i dostępny na komputerze lokalnym. Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
