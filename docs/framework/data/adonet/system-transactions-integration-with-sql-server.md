---
title: Integracja System.Transactions z programem SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 31edbc8f4cbb09f8720b373780f1b0646a985b20
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481686"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integracja System.Transactions z programem SQL Server
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Wersji 2.0 wprowadzono framework transakcji, który jest możliwy za pośrednictwem <xref:System.Transactions> przestrzeni nazw. Ta platforma udostępnia transakcji w taki sposób, że jest w pełni zintegrowana w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], w tym [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 Oprócz rozszerzenia programowania <xref:System.Transactions> i [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mogą współpracować ze sobą do koordynowania optymalizacje podczas pracy z transakcji. Awansowanie transakcja jest uproszczone transakcji (local), która może być automatycznie podwyższony do transakcji rozproszonej pełni na zgodnie z potrzebami.  
  
 Począwszy od [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> obsługuje transakcje awansowanie, podczas pracy z programem SQL Server. Awansowanie transakcji nie jest wywoływany dodano obciążenie z transakcji rozproszonych, chyba że dodany obciążenie jest wymagana. Awansowanie transakcje są automatyczne i wymagają interwencji od dewelopera.  
  
 Awansowanie transakcje są dostępne tylko, gdy używasz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) z programem SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Tworzenie awansowanie transakcji  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server zapewnia obsługę awansowanie transakcji, które są obsługiwane za pośrednictwem klasy w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> przestrzeni nazw. Transakcje awansowanie Optymalizowanie transakcji rozproszonych opóźnienie tworzenia transakcji rozproszonej, dopóki nie jest to konieczne. Jeśli jeden usługi resource manager jest wymagany tylko, występuje nie transakcji rozproszonej.  
  
> [!NOTE]
>  W przypadku częściowo zaufanych <xref:System.Transactions.DistributedTransactionPermission> jest wymagana, gdy transakcja zostanie podwyższony do poziomu transakcji rozproszonej.  
  
## <a name="promotable-transaction-scenarios"></a>Scenariusze awansowanie transakcji  
 Transakcje rozproszone zwykle używanie zasobów systemowych znaczące, są zarządzane przez program Microsoft Distributed Transaction Coordinator (MS DTC), którą można zintegrować z wszystkich menedżerów zasobów dostępne w ramach transakcji. Awansowanie transakcja jest specjalną postać <xref:System.Transactions> transakcji, które skutecznie deleguje pracy proste transakcji programu SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>, i programu SQL Server koordynować pracę niezbędną do obsługi transakcji, promowania go do pełnego transakcji rozproszonej, zgodnie z potrzebami.  
  
 Zaletą używania awansowanie transakcji jest fakt, że połączenie jest otwarte przy użyciu aktywnego <xref:System.Transactions.TransactionScope> transakcji, a żadne inne połączenia są otwarte, zatwierdzeń transakcji jako lekkie transakcje, zamiast ponoszenia dodatkowych koszty pełną transakcji rozproszonej.  
  
### <a name="connection-string-keywords"></a>Słowa kluczowe parametrów połączenia  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Właściwość obsługuje słowem kluczowym `Enlist`, wskazuje, czy <xref:System.Data.SqlClient> wykryje kontekstów transakcyjne i automatycznie zarejestrować połączenia w ramach transakcji rozproszonej. Jeśli `Enlist=true`, połączenie jest automatycznie zarejestrowany w wątku otwierania bieżący kontekst transakcji. Jeśli `Enlist=false`, `SqlClient` połączenia nie wchodzi w interakcję z transakcji rozproszonych. Wartością domyślną dla `Enlist` ma wartość true. Jeśli `Enlist` nie określono w parametrach połączenia, połączenie jest automatycznie zarejestrowany w transakcji rozproszonej, po wykryciu jednego po otwarciu połączenia.  
  
 `Transaction Binding` Słów kluczowych w <xref:System.Data.SqlClient.SqlConnection> parametry połączenia kontrolować połączenia do skojarzenia z zobowiązaniom `System.Transactions` transakcji. Jest również dostępna za pośrednictwem <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 W poniższej tabeli opisano możliwe wartości.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|Niejawne Unbind|Domyślnie. Połączenie odłącza się od transakcji po jej zakończeniu, przełączanie do trybu automatycznego zatwierdzania.|  
|Jawne usuwanie powiązania|Połączenie nadal jest dołączony do transakcji przed zamknięciem transakcji. Połączenie zakończy się niepowodzeniem, jeśli skojarzone transakcji jest nieaktywny lub nie jest zgodny <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>Za pomocą elementu TransactionScope  
 <xref:System.Transactions.TransactionScope> Klasy sprawia, że blok kodu transakcyjnych przez niejawnie wywołanie tej metody połączenia, w ramach transakcji rozproszonej. Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metody na końcu <xref:System.Transactions.TransactionScope> blok przed opuszczeniem go. Pozostawiając blok wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metody. Jeśli został zgłoszony wyjątek, powoduje, że kod, aby pozostawić zakresu transakcji jest traktowane jak zostało przerwane.  
  
 Zaleca się, że używasz `using` bloku, aby upewnić się, że <xref:System.Transactions.TransactionScope.Dispose%2A> jest wywoływana w <xref:System.Transactions.TransactionScope> obiektów modułu za pomocą polecenia w przypadku bloku jest został zakończony. Nie można przekazać ani wycofać oczekujące transakcje mogą znacznie pogorszyć wydajność, ponieważ domyślny limit czasu dla <xref:System.Transactions.TransactionScope> jest jedna minuta. Jeśli nie używasz `using` instrukcji, należy wykonać całą pracę w `Try` blokowania i jawnie wywołać <xref:System.Transactions.TransactionScope.Dispose%2A> method in Class metoda `Finally` bloku.  
  
 Jeśli wystąpi wyjątek w <xref:System.Transactions.TransactionScope>, transakcja jest oznaczone jako niespójne i zostanie porzucony. Zostanie wycofana ponownie po <xref:System.Transactions.TransactionScope> zostanie usunięty. Jeśli nie wystąpi wyjątek, zatwierdzania transakcji uczestniczących w programie.  
  
> [!NOTE]
>  `TransactionScope` Klasy tworzy transakcji z <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` domyślnie. W zależności od aplikacji warto wziąć pod uwagę obniżenia poziomu izolacji, aby uniknąć rywalizacji o wysokiej w aplikacji.  
  
> [!NOTE]
>  Zaleca się, wykonaj tylko aktualizacji, wstawiania, i usuwa w transakcje rozproszone, ponieważ korzystają z zasobów znaczących bazy danych. Instrukcji "Select" może zablokować niepotrzebnie zasobów bazy danych, a w niektórych scenariuszach może być konieczne użycie transakcji do wybiera. Wszelkie prace bez bazy danych powinna być podejmowana poza zakres transakcji, o ile nie dotyczy innych menedżerów zasobów transakcyjne. Mimo że wyjątek w zakresie transakcji zapobiega transakcji z zatwierdzeniem, <xref:System.Transactions.TransactionScope> klasa nie ma możliwości obsługi dla wycofywania zmian kodu podejścia biznesowego uczyniło poza zakresem transakcja. Jeśli zachodzi potrzeba wykonania określonego działania, gdy transakcja zostanie wycofana, należy napisać własną implementację <xref:System.Transactions.IEnlistmentNotification> interfejs i jawnie zarejestrować transakcji.  
  
## <a name="example"></a>Przykład  
 Praca z <xref:System.Transactions> wymaga odwołania do System.Transactions.dll.  
  
 Następująca funkcja przedstawia sposób tworzenia awansowanie transakcji dla dwóch różnych wystąpień programu SQL Server, reprezentowany przez dwa różne <xref:System.Data.SqlClient.SqlConnection> obiektów, które są opakowane w <xref:System.Transactions.TransactionScope> bloku. Ten kod tworzy <xref:System.Transactions.TransactionScope> blokowania z `using` instrukcji i otwiera pierwszego połączenia, które automatycznie powoduje zarejestrowanie go w <xref:System.Transactions.TransactionScope>. Transakcja jest początkowo zarejestrowany jako uproszczone transakcji, a nie pełne transakcji rozproszonej. Drugie połączenie jest zarejestrowany w <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenia w pierwszym połączeniu nie zgłasza wyjątku. Po otwarciu drugie połączenie transakcji jest automatycznie podwyższony do pełnego transakcji rozproszonej. <xref:System.Transactions.TransactionScope.Complete%2A> Wywołaniu metody, które zatwierdzeń transakcji, tylko wtedy, gdy żadne wyjątki nie były zgłaszane. Jeśli w dowolnym momencie został zgłoszony wyjątek <xref:System.Transactions.TransactionScope> bloku, `Complete` będą nie należy wywoływać i będzie transakcji rozproszonej, Przywróć ponownie po <xref:System.Transactions.TransactionScope> zostanie usunięty po zakończeniu jego `using` bloku.  
  
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
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
