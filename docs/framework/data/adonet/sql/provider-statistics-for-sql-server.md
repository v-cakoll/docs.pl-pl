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
# <a name="provider-statistics-for-sql-server"></a>Statystyki dostawcy dla programu SQL Server
Począwszy od programu .NET Framework w wersji 2.0, dostawca danych programu .NET Framework dla programu SQL Server obsługuje statystyki w czasie wykonywania. Statystyki należy włączyć, ustawiając <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> właściwość `True` <xref:System.Data.SqlClient.SqlConnection> obiektu po utworzeniu prawidłowego obiektu połączenia. Po włączeniu statystyk można przejrzeć je jako "migawka w <xref:System.Collections.IDictionary> czasie", <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> pobierając <xref:System.Data.SqlClient.SqlConnection> odwołanie za pomocą metody obiektu. Wyliczyć za pośrednictwem listy jako zestaw wpisów słownika nazwa/wartość pary. Te pary nazw/wartości są nieurządzone. W dowolnym momencie można <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> wywołać <xref:System.Data.SqlClient.SqlConnection> metodę obiektu, aby zresetować liczniki. Jeśli zbieranie statystyk nie zostało włączone, wyjątek nie jest generowany. Ponadto jeśli <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> jest wywoływana bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> wywoływane jako pierwsze, wartości pobrane są wartościami początkowymi dla każdego wpisu. Jeśli włączysz statystyki, uruchom aplikację przez jakiś czas, a następnie wyłącz statystyki, pobrane wartości będą odzwierciedlać wartości zebrane do punktu, w którym statystyki zostały wyłączone. Wszystkie zebrane wartości statystyczne są na podstawie połączenia.  
  
## <a name="statistical-values-available"></a>Dostępne wartości statystyczne  
 Obecnie istnieje 18 różnych elementów dostępnych od dostawcy programu Microsoft SQL Server. Liczba dostępnych elementów jest dostępna **Count** za pośrednictwem <xref:System.Collections.IDictionary> Count właściwości <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>odwołania interfejsu zwracane przez . Wszystkie liczniki dla statystyk dostawcy używają wspólnego <xref:System.Int64> typu środowiska wykonawczego języka **(long** w języku C# i Visual Basic), który ma 64 bity szerokości. Maksymalna wartość typu danych **int64,** zdefiniowana przez **int64. MaxValue,** jest ((2^63)-1)). Gdy wartości liczników osiągną tę maksymalną wartość, nie powinny być już uważane za dokładne. Oznacza to, że **int64. MaxValue**-1((2^63)-2) jest skutecznie największą prawidłową wartością dla każdej statystyki.  
  
> [!NOTE]
> Słownik jest używany do zwracania statystyk dostawcy, ponieważ liczba, nazwy i kolejność zwracanych statystyk mogą ulec zmianie w przyszłości. Aplikacje nie powinny polegać na określonej wartości znalezionej w słowniku, ale zamiast tego należy sprawdzić, czy wartość jest tam i odpowiednio gałęzi.  
  
 W poniższej tabeli opisano bieżące dostępne wartości statystyczne. Należy zauważyć, że nazwy kluczy dla poszczególnych wartości nie są zlokalizowane w regionalnych wersjach programu Microsoft .NET Framework.  
  
|Nazwa klucza|Opis|  
|--------------|-----------------|  
|`BuffersReceived`|Zwraca liczbę pakietów strumienia danych tabelaryczne (TDS) odebranych przez dostawcę z programu SQL Server po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.|  
|`BuffersSent`|Zwraca liczbę pakietów TDS wysyłanych do programu SQL Server przez dostawcę po włączeniu statystyk. Duże polecenia mogą wymagać wielu buforów. Na przykład jeśli duże polecenie jest wysyłane do serwera i `ServerRoundtrips` wymaga sześciu pakietów, `BuffersSent` jest zwiększane o jeden i zwiększa się o sześć.|  
|`BytesReceived`|Zwraca liczbę bajtów danych w pakietach TDS odebranych przez dostawcę z programu SQL Server po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.|  
|`BytesSent`|Zwraca liczbę bajtów danych wysyłanych do programu SQL Server w pakietach TDS po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.|  
|`ConnectionTime`|Czas (w milisekundach), przez który połączenie zostało otwarte po włączeniu statystyk (całkowity czas połączenia, jeśli statystyki zostały włączone przed otwarciem połączenia).|  
|`CursorOpens`|Zwraca liczbę razy kursor został otwarty za pośrednictwem połączenia po aplikacji rozpoczął przy użyciu dostawcy i włączył statystyki.<br /><br /> Należy zauważyć, że wyniki tylko do odczytu/tylko do przodu zwracane przez instrukcje SELECT nie są uważane za kursory i dlatego nie mają wpływu na ten licznik.|  
|`ExecutionTime`|Zwraca skumulowaną ilość czasu (w milisekundach), który dostawca spędził przetwarzania po włączeniu statystyk, w tym czas spędzony na oczekiwanie na odpowiedzi z serwera, a także czas spędzony na wykonywaniu kodu w samym dostawcy.<br /><br /> Klasy, które zawierają kod chronometrażu są:<br /><br /> Sqlconnection<br /><br /> Sqlcommand<br /><br /> Sqldatareader<br /><br /> Sqldataadapter<br /><br /> Sqltransaction<br /><br /> Sqlcommandbuilder<br /><br /> Aby elementy członkowskie o krytycznym znaczeniu dla wydajności były jak najmniejsze, następujące elementy członkowskie nie są czasowe:<br /><br /> Sqldatareader<br /><br /> ten[] operator (wszystkie przeciążenia)<br /><br /> Getboolean<br /><br /> Getchar<br /><br /> GetDateTime (Czas 1lat<br /><br /> GetDecimal (GetDecimal)<br /><br /> Getdouble<br /><br /> GetFloat ( GetFloat )<br /><br /> GetGuid ( GetGuid )<br /><br /> GetInt16<br /><br /> GetInt32 (GetInt32)<br /><br /> GetInt64<br /><br /> GetName<br /><br /> Getordinal<br /><br /> GetSqlBinary (Łącze Łącze)<br /><br /> GetSqlBoolean (GetSqlBoolean)<br /><br /> GetSqlByte ( GetSqlByte )<br /><br /> Czas 100 000 000 000 000 0<br /><br /> GetSqlDecymal<br /><br /> GetSqlDouble (GetSqlDouble)<br /><br /> GetSqlGuid ( GetSqlGuid )<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle ( GetSqlSingle )<br /><br /> GetSqlString (wysiewu)<br /><br /> GetString<br /><br /> Isdbnull|  
|`IduCount`|Zwraca całkowitą liczbę instrukcji INSERT, DELETE i UPDATE wykonanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.|  
|`IduRows`|Zwraca całkowitą liczbę wierszy, których dotyczą instrukcje INSERT, DELETE i UPDATE wykonywane za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.|  
|`NetworkServerTime`|Zwraca skumulowaną ilość czasu (w milisekundach), który dostawca spędził na czekaniu na odpowiedzi z serwera po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.|  
|`PreparedExecs`|Zwraca liczbę przygotowanych poleceń wykonywanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.|  
|`Prepares`|Zwraca liczbę instrukcji przygotowanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki.|  
|`SelectCount`|Zwraca liczbę instrukcji SELECT wykonanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk. Obejmuje to instrukcje FETCH, aby pobrać wiersze z kursorów, a liczba <xref:System.Data.SqlClient.SqlDataReader> instrukcji SELECT jest aktualizowana po osiągnięciu końca a.|  
|`SelectRows`|Zwraca liczbę wierszy wybranych po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki. Ten licznik odzwierciedla wszystkie wiersze generowane przez instrukcje SQL, nawet te, które nie zostały faktycznie wykorzystane przez wywołującego. Na przykład zamknięcie czytnika danych przed odczytaniem całego zestawu wyników nie wpłynie na liczbę. Obejmuje to wiersze pobrane z kursorów za pośrednictwem instrukcji FETCH.|  
|`ServerRoundtrips`|Zwraca liczbę razy połączenie wysłane polecenia do serwera i otrzymał odpowiedź z powrotem po aplikacji rozpoczął korzystanie z dostawcy i włączył statystyki.|  
|`SumResultSets`|Zwraca liczbę zestawów wyników, które zostały użyte po uruchomieniu aplikacji przy użyciu dostawcy i włączył statystyki. Na przykład może to obejmować dowolny zestaw wyników zwrócony do klienta. W przypadku kursorów każda operacja pobierania lub pobierania blokowego jest uważana za niezależny zestaw wyników.|  
|`Transactions`|Zwraca liczbę transakcji użytkownika rozpoczętych po rozpoczęciu korzystania z dostawcy przez aplikację i włączono statystyki, w tym wycofywanie. Jeśli połączenie jest uruchomione z automatycznym zatwierdzaniem, każde polecenie jest uważane za transakcję.<br /><br /> Ten licznik zwiększa liczbę transakcji, gdy tylko instrukcja BEGIN TRAN jest wykonywana, niezależnie od tego, czy transakcja została zatwierdzona, czy wycofana później.|  
|`UnpreparedExecs`|Zwraca liczbę nieprzygotowanych instrukcji wykonanych za pośrednictwem połączenia po rozpoczęciu korzystania z dostawcy przez aplikację i włączeniu statystyk.|  
  
### <a name="retrieving-a-value"></a>Pobieranie wartości  
 W poniższej aplikacji konsoli pokazano, jak włączyć statystyki połączenia, pobrać cztery poszczególne wartości statystyczne i zapisać je w oknie konsoli.  
  
> [!NOTE]
> W poniższym przykładzie użyto przykładowej bazy danych **AdventureWorks** dołączonej do programu SQL Server. Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym. Zmodyfikuj parametry połączenia zgodnie z oczekiwaniami środowiska.  
  
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
 W poniższej aplikacji konsoli pokazano, jak włączyć statystyki połączenia, pobrać wszystkie dostępne wartości statystyczne przy użyciu wylicznika i zapisać je w oknie konsoli.  
  
> [!NOTE]
> W poniższym przykładzie użyto przykładowej bazy danych **AdventureWorks** dołączonej do programu SQL Server. Parametry połączenia podane w przykładowym kodzie zakładają, że baza danych jest zainstalowana i dostępna na komputerze lokalnym. Zmodyfikuj parametry połączenia zgodnie z oczekiwaniami środowiska.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
