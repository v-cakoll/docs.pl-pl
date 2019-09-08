---
title: Integracja System.Transactions z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 075eea42c65a822fc46ca14f820599567c35d231
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791366"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integracja System.Transactions z programem SQL Server
W .NET Framework w wersji 2,0 wprowadzono strukturę transakcji, do której można uzyskać dostęp <xref:System.Transactions> za pomocą przestrzeni nazw. Ta struktura uwidacznia transakcje w sposób, który jest w pełni zintegrowany w .NET Framework, w tym ADO.NET.  
  
 Oprócz ulepszeń programistycznych, <xref:System.Transactions> a ADO.NET może współdziałać w celu koordynowania optymalizacji podczas pracy z transakcjami. Transakcja promocji to lekki (lokalny) transakcję, którą można automatycznie podwyższyć do w pełni rozproszonej transakcji.  
  
 Począwszy od ADO.NET 2,0, <xref:System.Data.SqlClient> obsługuje transakcje promocji podczas pracy z SQL Server. Transakcja promocji nie wywołuje dodanego nakładu transakcji rozproszonej, chyba że jest wymagane dodatkowe obciążenie. Transakcje promocji są automatyczne i nie wymagają żadnej interwencji z dewelopera.  
  
 Transakcje promocyjne są dostępne tylko wtedy, gdy używasz dostawca danych .NET Framework dla SQL Server (`SqlClient`) z SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Tworzenie transakcji promocji  
 Dostawca .NET Framework dla SQL Server zapewnia obsługę transakcji promocji, które są obsługiwane przez klasy w przestrzeni nazw .NET Framework <xref:System.Transactions> . Transakcje promocyjne optymalizują transakcje rozproszone przez odroczenie tworzenia transakcji rozproszonej do momentu, gdy jest to konieczne. Jeśli jest wymagany tylko jeden Menedżer zasobów, nie są wykonywane żadne transakcje rozproszone.  
  
> [!NOTE]
> W częściowo zaufanym scenariuszu <xref:System.Transactions.DistributedTransactionPermission> jest to wymagane, gdy transakcja jest podwyższana do transakcji rozproszonej.  
  
## <a name="promotable-transaction-scenarios"></a>Scenariusze transakcji promocji  
 Transakcje rozproszone zazwyczaj zużywają znaczne zasoby systemowe zarządzane przez firmę Microsoft Distributed Transaction Coordinator (MS DTC), które integrują wszystkich menedżerów zasobów, do których uzyskuje dostęp w transakcji. Transakcja promocji to specjalna forma <xref:System.Transactions> transakcji, która efektywnie deleguje prace do prostej transakcji SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>i SQL Server koordynuje pracy związanej z obsługą transakcji, promując ją do pełnej transakcji rozproszonej w razie potrzeby.  
  
 Korzyści wynikające z korzystania z transakcji promocyjnych polegają na tym, że gdy połączenie jest otwierane przy użyciu aktywnej <xref:System.Transactions.TransactionScope> transakcji, a żadne inne połączenia nie są otwierane, transakcja zostaje zatwierdzona jako uproszczona transakcja, zamiast naliczać dodatkowe narzuty za pełną transakcję rozproszoną.  
  
### <a name="connection-string-keywords"></a>Słowa kluczowe parametrów połączenia  
 Właściwość obsługuje słowo kluczowe, `Enlist`które wskazuje, czy <xref:System.Data.SqlClient> program będzie wykrywał konteksty transakcyjne i automatycznie zarejestrowana w transakcji rozproszonej. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Jeśli `Enlist=true`połączenie zostanie automatycznie zarejestrowane w bieżącym kontekście transakcji otwarcia wątku. Jeśli `Enlist=false`połączenieniedziała wprzypadkutransakcjirozproszonej.`SqlClient` Wartość domyślna dla `Enlist` ma wartość true. Jeśli `Enlist` wartość nie jest określona w parametrach połączenia, połączenie zostanie automatycznie zarejestrowane w transakcji rozproszonej, jeśli zostanie wykryta po otwarciu połączenia.  
  
 Słowa kluczowe w parametrach połączenia kontrolują skojarzenie połączenia z zarejestrowaną `System.Transactions` transakcją. <xref:System.Data.SqlClient.SqlConnection> `Transaction Binding` Jest ona również dostępna za pomocą <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> właściwości. <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
 W poniższej tabeli opisano możliwe wartości.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|Niejawne powiązanie|Domyślnie. Połączenie zostanie odłączone od transakcji po jej zakończeniu, przełączając z powrotem do trybu automatycznego zatwierdzania.|  
|Jawne powiązanie powiązania|Połączenie pozostaje dołączone do transakcji do momentu zamknięcia transakcji. Połączenie zakończy się niepowodzeniem, jeśli skojarzona transakcja nie jest aktywna lub <xref:System.Transactions.Transaction.Current%2A>nie jest zgodna.|  
  
## <a name="using-transactionscope"></a>Używanie elementu TransactionScope  
 <xref:System.Transactions.TransactionScope> Klasa wywołuje kod transakcyjny przez niejawnie zarejestrowane połączenia w transakcji rozproszonej. Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metodę na końcu <xref:System.Transactions.TransactionScope> bloku przed opuszczeniem go. Wyjście bloku wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metodę. Jeśli wystąpił wyjątek, który powoduje, że kod opuszcza zakres, transakcja jest traktowana jako przerwana.  
  
 Zalecamy użycie `using` bloku, aby upewnić się, że <xref:System.Transactions.TransactionScope.Dispose%2A> jest wywoływana na <xref:System.Transactions.TransactionScope> obiekcie, gdy blok using zostanie zakończony. Nie można zatwierdzić lub wycofać oczekujących transakcji może znacząco spowodować uszkodzenie wydajności, ponieważ domyślny <xref:System.Transactions.TransactionScope> limit czasu wynosi minutę. Jeśli nie używasz `using` instrukcji, musisz wykonać wszystkie czynności `Try` w <xref:System.Transactions.TransactionScope.Dispose%2A> bloku i jawnie `Finally` wywołać metodę w bloku.  
  
 Jeśli wystąpi wyjątek w <xref:System.Transactions.TransactionScope>, transakcja jest oznaczona jako niespójna i została porzucona. Zostanie wycofany po <xref:System.Transactions.TransactionScope> usunięciu. Jeśli żaden wyjątek nie wystąpi, uczestniczące transakcje są zatwierdzane.  
  
> [!NOTE]
> Klasa tworzy transakcję <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` wartością domyślną. `TransactionScope` W zależności od aplikacji warto rozważyć obniżenie poziomu izolacji, aby uniknąć dużej rywalizacji w aplikację.  
  
> [!NOTE]
> Zalecamy wykonywanie tylko aktualizacji, wstawianych i usuwanych transakcji rozproszonych, ponieważ zużywają one znaczne zasoby bazy danych. Instrukcje SELECT mogą niepotrzebnie blokować zasoby bazy danych, a w niektórych scenariuszach może być konieczne użycie transakcji do wyboru. Wszelkie zadania poza bazą danych powinny być wykonywane spoza zakresu transakcji, o ile nie obejmuje ona innych menedżerów zasobów transakcyjnych. Chociaż wyjątek w zakresie transakcji uniemożliwia zatwierdzenie transakcji, <xref:System.Transactions.TransactionScope> Klasa nie ma do wycofania żadnych zmian wprowadzonych w kodzie poza zakres transakcji. Jeśli konieczne jest wykonanie pewnej akcji w przypadku wycofania transakcji, należy napisać własną implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu i jawnie zarejestrować się w transakcji.  
  
## <a name="example"></a>Przykład  
 Praca z <xref:System.Transactions> programem wymaga odwołania do elementu System. Transactions. dll.  
  
 Poniższa funkcja pokazuje, jak utworzyć transakcję promocji dla dwóch różnych wystąpień SQL Server, reprezentowanych przez dwa <xref:System.Data.SqlClient.SqlConnection> różne obiekty, które są opakowane <xref:System.Transactions.TransactionScope> w bloku. Kod tworzy <xref:System.Transactions.TransactionScope> blok `using` z instrukcją i otwiera pierwsze połączenie, które jest automatycznie <xref:System.Transactions.TransactionScope>rejestrowane w. Transakcja jest początkowo rejestrowana jako uproszczona transakcja, a nie pełna transakcja rozproszona. Drugie połączenie jest rejestrowane w <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenie w pierwszym połączeniu nie zgłasza wyjątku. Po otwarciu drugiego połączenia transakcja zostanie automatycznie podzielona na pełną transakcję rozproszoną. Wywoływana <xref:System.Transactions.TransactionScope.Complete%2A> jest metoda, która zatwierdza transakcję tylko wtedy, gdy nie zgłoszono żadnych wyjątków. Jeśli wyjątek został zgłoszony w <xref:System.Transactions.TransactionScope> dowolnym momencie w bloku, `Complete` nie zostanie wywołany, a transakcja rozproszona <xref:System.Transactions.TransactionScope> zostanie wycofana, gdy zostanie usunięty na końcu jego `using` bloku.  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a>Zobacz także

- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Omówienie ADO.NET](ado-net-overview.md)
