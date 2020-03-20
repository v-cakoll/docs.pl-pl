---
title: Integracja System.Transactions z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174241"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integracja System.Transactions z programem SQL Server
Program .NET Framework w wersji 2.0 wprowadził strukturę <xref:System.Transactions> transakcji, do których można uzyskać dostęp za pośrednictwem obszaru nazw. Ta struktura udostępnia transakcje w sposób, który jest w pełni zintegrowany z .NET Framework, w tym ADO.NET.  
  
 Oprócz ulepszeń programowalności <xref:System.Transactions> i ADO.NET mogą współpracować w celu koordynowania optymalizacji podczas pracy z transakcjami. Transakcja z możliwością promowania to lekka (lokalna) transakcja, która może być automatycznie promowana do w pełni rozproszonej transakcji zgodnie z potrzebami.  
  
 Począwszy od ADO.NET 2.0, <xref:System.Data.SqlClient> obsługuje transakcje promowane podczas pracy z programem SQL Server. Transakcja z domosywana nie wywołuje dodatkowego obciążenia transakcji rozproszonej, chyba że wymagane jest dodatkowe obciążenie. Transakcje, które można promować, są automatyczne i nie wymagają interwencji ze strony dewelopera.  
  
 Transakcje z których można promować są dostępne tylko wtedy, gdy`SqlClient`używasz dostawcy danych programu .NET Framework dla programu SQL Server ( ) z programem SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Tworzenie transakcji promowanych  
 Dostawca programu .NET Framework dla programu SQL Server zapewnia obsługę transakcji, które można <xref:System.Transactions> promować, które są obsługiwane za pośrednictwem klas w obszarze nazw programu .NET Framework. Transakcje promowane optymalizują transakcje rozproszone, odraczając tworzenie transakcji rozproszonej, dopóki nie jest potrzebna. Jeśli wymagany jest tylko jeden menedżer zasobów, nie występuje żadna transakcja rozproszona.  
  
> [!NOTE]
> W scenariuszu częściowo zaufany <xref:System.Transactions.DistributedTransactionPermission> jest wymagane, gdy transakcja jest promowany do transakcji rozproszonej.  
  
## <a name="promotable-transaction-scenarios"></a>Scenariusze transakcji promowanych  
 Transakcje rozproszone zazwyczaj zużywają znaczne zasoby systemowe, zarządzane przez koordynatora transakcji rozproszonych firmy Microsoft (MS DTC), który integruje wszystkich menedżerów zasobów dostępnych w transakcji. Transakcja z do promowania jest <xref:System.Transactions> specjalną formą transakcji, która skutecznie deleguje pracę do prostej transakcji programu SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>a SQL Server koordynują pracę związaną z obsługą transakcji, promując ją do pełnej transakcji rozproszonej w razie potrzeby.  
  
 Zaletą korzystania z transakcji można promować jest to, że <xref:System.Transactions.TransactionScope> gdy połączenie jest otwierane przy użyciu aktywnej transakcji, a żadne inne połączenia są otwierane, transakcja zatwierdza jako lekka transakcja, zamiast ponosić dodatkowe obciążenie pełnej transakcji rozproszonej.  
  
### <a name="connection-string-keywords"></a>Słowa kluczowe ciągu połączenia  
 Właściwość <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> obsługuje słowo `Enlist`kluczowe, co <xref:System.Data.SqlClient> wskazuje, czy wykryje konteksty transakcyjne i automatycznie zarejestrować połączenie w transakcji rozproszonej. Jeśli `Enlist=true`połączenie jest automatycznie rejestrowane w kontekście bieżącej transakcji wątku otwarcia. Jeśli `Enlist=false`połączenie `SqlClient` nie wchodzi w interakcję z transakcją rozproszoną. Wartość domyślna `Enlist` dla jest true. Jeśli `Enlist` nie jest określony w ciągu połączenia, połączenie jest automatycznie łączony w transakcji rozproszonej, jeśli zostanie wykryty po otwarciu połączenia.  
  
 Słowa `Transaction Binding` kluczowe w <xref:System.Data.SqlClient.SqlConnection> ciągu połączenia kontrolują skojarzenia połączenia `System.Transactions` z zarejestrowaną transakcją. Jest on również <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> dostępny za <xref:System.Data.SqlClient.SqlConnectionStringBuilder>pośrednictwem obiektu.  
  
 W poniższej tabeli opisano możliwe wartości.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|Niejawne unbind|Domyślnie. Połączenie odłącza się od transakcji po jej zakończeniu, przełączając się z powrotem do trybu automatycznego przywiązania.|  
|Jawne unbind|Połączenie pozostaje dołączone do transakcji do momentu zamknięcia transakcji. Połączenie zakończy się niepowodzeniem, jeśli skojarzona transakcja <xref:System.Transactions.Transaction.Current%2A>nie jest aktywna lub nie jest zgodna .|  
  
## <a name="using-transactionscope"></a>Korzystanie z transactionscope  
 Klasa <xref:System.Transactions.TransactionScope> sprawia, że blok kodu transakcyjnych przez niejawnie rejestracji połączeń w transakcji rozproszonej. Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metodę na końcu <xref:System.Transactions.TransactionScope> bloku przed opuszczeniem go. Pozostawienie bloku wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metodę. Jeśli został zgłoszony wyjątek, który powoduje, że kod do opuszczenia zakresu, transakcja jest uważany za przerwane.  
  
 Zaleca się użycie `using` bloku, aby <xref:System.Transactions.TransactionScope.Dispose%2A> upewnić się, że jest wywoływana na <xref:System.Transactions.TransactionScope> obiekcie, gdy using blok jest zamykany. Niepowodzenie zatwierdzania lub wycofywania oczekujących transakcji może znacznie uszkodzić wydajność, ponieważ domyślny limit czasu dla <xref:System.Transactions.TransactionScope> tej wartości wynosi jedną minutę. Jeśli nie używasz `using` instrukcji, należy wykonać całą `Try` pracę w bloku <xref:System.Transactions.TransactionScope.Dispose%2A> i `Finally` jawnie wywołać metodę w bloku.  
  
 Jeśli wystąpi wyjątek <xref:System.Transactions.TransactionScope>w , transakcja jest oznaczona jako niespójne i jest porzucona. Zostanie wycofany, gdy <xref:System.Transactions.TransactionScope> jest usuwany. Jeśli nie wystąpi wyjątek, transakcje uczestniczące zatwierdzają.  
  
> [!NOTE]
> Klasa `TransactionScope` tworzy transakcję <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` domyślnie. W zależności od aplikacji warto rozważyć obniżenie poziomu izolacji, aby uniknąć wysokiej rywalizacji w aplikacji.  
  
> [!NOTE]
> Zaleca się wykonywanie tylko aktualizacji, wstawia i usuwa w ramach transakcji rozproszonych, ponieważ zużywają one znaczne zasoby bazy danych. Wybierz instrukcje mogą niepotrzebnie blokować zasoby bazy danych, a w niektórych scenariuszach może być trzeba użyć transakcji dla wybranych. Wszelkie prace spoza bazy danych powinny być wykonywane poza zakresem transakcji, chyba że obejmuje ona innych transakcyjnych menedżerów zasobów. Chociaż wyjątek w zakresie transakcji uniemożliwia zatwierdzenie transakcji, <xref:System.Transactions.TransactionScope> klasa nie ma przepisu na wycofywanie wszelkich zmian wprowadzonych przez kod poza zakresem samej transakcji. Jeśli trzeba podjąć pewne działania, gdy transakcja jest przywracana, należy <xref:System.Transactions.IEnlistmentNotification> napisać własną implementację interfejsu i jawnie zarejestrować się w transakcji.  
  
## <a name="example"></a>Przykład  
 Praca <xref:System.Transactions> z wymaga, aby masz odwołanie do System.Transactions.dll.  
  
 Poniższa funkcja pokazuje, jak utworzyć transakcję można promować względem dwóch różnych <xref:System.Data.SqlClient.SqlConnection> wystąpień programu SQL <xref:System.Transactions.TransactionScope> Server, reprezentowanych przez dwa różne obiekty, które są zawinięte w bloku. Kod tworzy <xref:System.Transactions.TransactionScope> blok z `using` instrukcją i otwiera pierwsze połączenie, które <xref:System.Transactions.TransactionScope>automatycznie rejestruje go w pliku . Transakcja jest początkowo rejestrowana jako lekka transakcja, a nie pełna transakcja rozproszona. Drugie połączenie jest rejestrowane <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenie w pierwszym połączeniu nie zgłasza wyjątek. Po otwarciu drugiego połączenia transakcja jest automatycznie podyzowana do pełnej transakcji rozproszonej. Metoda <xref:System.Transactions.TransactionScope.Complete%2A> jest wywoływana, która zatwierdza transakcji tylko wtedy, gdy nie zostały odrzucone wyjątki. Jeśli wyjątek został zgłoszony w <xref:System.Transactions.TransactionScope> dowolnym `Complete` momencie w bloku, nie zostanie wywołana, <xref:System.Transactions.TransactionScope> a transakcja rozproszona `using` zostanie wycofana, gdy jest usuwany na końcu jego bloku.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Omówienie ADO.NET](ado-net-overview.md)
