---
title: Statystyki dostawcy dla programu SQL Server
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
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 87f3dfbb3af6e638207d68540217f7134b95c354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="provider-statistics-for-sql-server"></a>Statystyki dostawcy dla programu SQL Server
W programie .NET Framework w wersji 2.0, .NET Framework Data Provider for SQL Server obsługuje statystyk czasu wykonywania. Należy włączyć statystyki przez ustawienie <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> do obiektu `True` po poprawnego obiektu połączenia utworzone. Po włączeniu statystyki można przeglądać je jako "migawka w czasie" pobierając <xref:System.Collections.IDictionary> odwoływać się za pośrednictwem <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiektu. Wyliczanie za pośrednictwem listy jako zbiór wpisy słownika pary nazwa/wartość. Tych par nazwa/wartość są nieuporządkowane. W dowolnym momencie można wywołać <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiektu do resetowania liczników. Jeśli nie włączono zbieranie statystyk, wyjątek nie zostanie wygenerowany. Ponadto jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> o najpierw wywołuje, wartości pobierane są wartości początkowe dla każdego wpisu. Po włączeniu statystyki uruchomienie aplikacji przez pewien czas i Wyłącz statystyk, wartości pobierane odpowiada wartości zebranych do punktu wyłączonym statystyk. Wszystkie wartości statystyczne zebrane znajdują się na poszczególnych połączeń.  
  
## <a name="statistical-values-available"></a>Dostępne wartości statystycznych  
 Aktualnie brak dostępnych 18 różnych elementów od dostawcy programu Microsoft SQL Server. Liczba dostępnych elementów jest możliwy za pośrednictwem **liczba** właściwość <xref:System.Collections.IDictionary> interfejsu Odwołanie zwrócone przez <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Wszystkie liczniki dla dostawcy statystyk użycia środowisko uruchomieniowe języka wspólnego <xref:System.Int64> typu (**długi** w języku C# i Visual Basic), która jest 64 bity. Maksymalna wartość **int64** typu danych, zgodnie z definicją **int64. MaxValue** pola, ((2^63)-1)). Gdy ta wartość maksymalna, wartości liczników one już nie należy traktować jako dokładne. Oznacza to, że **int64. MaxValue**-1((2^63)-2) skutecznie jest największy poprawną wartością wszystkie statystyki.  
  
> [!NOTE]
>  Słownik służy do zwracania statystyki dostawcy, ponieważ numer, nazwy i kolejność zwracane statystyki mogą ulec zmianie w przyszłości. Aplikacje nie należy polegać na określoną wartość zostanie znaleziony w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest istnieje i odpowiednio gałęzi.  
  
 W poniższej tabeli opisano bieżące wartości statystyczne dostępne. Należy pamiętać, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w regionalnych wersji programu Microsoft .NET Framework.  
  
|Nazwa klucza|Opis|  
|--------------|-----------------|  
|`BuffersReceived`|Zwraca liczbę strumienia danych tabelarycznych (TDS) pakietów odebranych przez dostawcę z programu SQL Server po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`BuffersSent`|Zwraca liczbę pakietów TDS wysyłanych do serwera SQL przez dostawcę po włączeniu statystyk. Duże polecenia może wymagać wielu buforów. Na przykład, jeśli dużych polecenia są wysyłane do serwera i wymaga sześciu pakietów `ServerRoundtrips` jest zwiększany o jeden i `BuffersSent` jest zwiększany o sześciu.|  
|`BytesReceived`|Zwraca liczbę bajtów danych odebranych przez dostawcę z programu SQL Server, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki pakietów TDS.|  
|`BytesSent`|Zwraca liczbę bajtów danych wysłanych do programu SQL Server w pakietach TDS po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki.|  
|`ConnectionTime`|Czas (w milisekundach), że połączenie zostało otwarte po włączeniu statystyki (całkowity czas połączenia, jeśli umożliwiono statystyki przed otwarciem połączenie).|  
|`CursorOpens`|Zwraca liczbę powtórzeń kursora był otwarty przez połączenie, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.<br /><br /> Należy pamiętać, że tylko/do przodu — tylko do odczytu wyniki zwrócone przez instrukcje SELECT nie są uznawane za kursory i w związku z tym nie wpływają na wartość tego licznika.|  
|`ExecutionTime`|Zwraca zbiorczą ilość czasu (w milisekundach), czy dostawca jest poświęcony na przetwarzanie włączenie statystyk, tym czas oczekiwania na odpowiedzi z serwera, a także czas poświęcony na wykonywanie kodu w samej dostawcy.<br /><br /> Klasy, które zawierają kod chronometrażu są:<br /><br /> Element SqlConnection<br /><br /> Klasy SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Aby zachować możliwie najmniejsze członków wydajności o znaczeniu krytycznym, nie jest mierzony następujące elementy:<br /><br /> SqlDataReader<br /><br /> Ten operator [] (wszystkie przeciążenia)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Zwraca sumę instrukcje INSERT, usuwania i aktualizacji, które są wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`IduRows`|Zwraca całkowitą liczbę wierszy, wpływ instrukcje INSERT, usuwania i aktualizacji, które są wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`NetworkServerTime`|Zwraca zbiorczą ilość czasu (w milisekundach) dostawcy oczekujących na odpowiedzi z serwera po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`PreparedExecs`|Zwraca liczbę przygotowanego polecenia wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`Prepares`|Zwraca liczbę instrukcji przygotowane przez połączenie, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`SelectCount`|Zwraca liczbę instrukcji "SELECT" wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk. Zawiera instrukcje pobierania, aby pobierać wiersze z kursorami oraz liczbę elementów w instrukcji "SELECT" jest aktualizowany po zakończeniu <xref:System.Data.SqlClient.SqlDataReader> zostanie osiągnięty.|  
|`SelectRows`|Zwraca liczbę wierszy zaznaczone, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk. Ten licznik wskazuje wszystkie wiersze, które są generowane przez instrukcje SQL, nawet te, które nie zostały faktycznie używane przez obiekt wywołujący. Na przykład zamknięcia czytnika danych przed odczytaniem cały zestaw wyników nie wpłynie na wartość licznika. W tym wiersze, pobierane z kursorami za pomocą instrukcji pobierania.|  
|`ServerRoundtrips`|Zwraca liczbę razy połączenia wysłane do serwera poleceń i otrzymano odpowiedzi, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk.|  
|`SumResultSets`|Zwraca liczbę wyników zestawów, które były używane po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyk. Na przykład obejmuje to każdego zestawu wyników zwróconego do klienta. Kursory każdej operacji pobierania lub fetch bloku jest traktowany jako zestaw wyników niezależne.|  
|`Transactions`|Zwraca liczbę uruchomione po aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki, w tym wycofywania transakcji użytkownika. Jeśli połączenie jest uruchamiana za pomocą automatycznego zatwierdzania na, każde polecenie jest uważany za transakcji.<br /><br /> Ten licznik zwiększa liczbę transakcji, jak najszybciej po wykonaniu instrukcji BEGIN TRAN, niezależnie od tego, czy transakcja jest zatwierdzenia lub wycofania później.|  
|`UnpreparedExecs`|Zwraca liczbę nieprzygotowany instrukcje wykonywane za pośrednictwem połączenia, gdy aplikacja została uruchomiona przy użyciu dostawcy i włączył statystyki.|  
  
### <a name="retrieving-a-value"></a>Pobieranie wartości  
 Następującej aplikacji konsoli pokazano, jak włączyć statystyki dotyczące połączenia, pobrać cztery wartości poszczególnych statystyk i zapisać je w oknie konsoli.  
  
> [!NOTE]
>  W poniższym przykładzie użyto przykładowej **AdventureWorks** baza danych dołączona [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. W przykładowym kodzie w podanym ciągu połączenia przyjęto założenie, że baza danych jest zainstalowany i dostępny na komputerze lokalnym. Zmodyfikuj parametry połączenia w razie potrzeby dla danego środowiska.  
  
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
 Następującej aplikacji konsoli Pokazuje, jak włączyć statystyki dotyczące połączenia, pobrać wszystkich wartości dostępne statystyki przy użyciu modułu wyliczającego i zapisywać je w oknie konsoli.  
  
> [!NOTE]
>  W poniższym przykładzie użyto przykładowej **AdventureWorks** baza danych dołączona [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. W przykładowym kodzie w podanym ciągu połączenia przyjęto założenie, że baza danych jest zainstalowany i dostępny na komputerze lokalnym. Zmodyfikuj parametry połączenia w razie potrzeby dla danego środowiska.  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
