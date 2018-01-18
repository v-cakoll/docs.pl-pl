---
title: System.Transactions integracji z programem SQL Server
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
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21924441c091c53a79d4b7bf8a683f8a7c74bd07
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="systemtransactions-integration-with-sql-server"></a>System.Transactions integracji z programem SQL Server
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 2.0 wprowadzono framework transakcji, które mogą być udostępniane za pośrednictwem <xref:System.Transactions> przestrzeni nazw. Ta struktura przedstawia transakcji w taki sposób, który jest w pełni zintegrowana z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], takie jak [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 Oprócz rozszerzenia programowania <xref:System.Transactions> i [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mogą współdziałać ze sobą do koordynowania optymalizacje podczas pracy z transakcji. Awansowanie transakcji to lekkie transakcja (local), która może być automatycznie podwyższony do transakcji rozproszonej pełni na zgodnie z potrzebami.  
  
 Począwszy od [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> obsługuje awansowanie transakcji podczas pracy z [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Awansowanie transakcji nie jest wywoływany dodany narzutów transakcji rozproszonej, chyba że dodany jest wymagana. Awansowanie transakcje są automatyczne i wymagają interwencji od dewelopera.  
  
 Awansowanie transakcje są dostępne tylko, gdy używasz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server (`SqlClient`) z [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].  
  
## <a name="creating-promotable-transactions"></a>Tworzenie awansowanie transakcji  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server zapewnia obsługę awansowanie transakcji, które są obsługiwane za pośrednictwem klas w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> przestrzeni nazw. Transakcje awansowanie zoptymalizować transakcje rozproszone odkładanie Tworzenie transakcji rozproszonej, dopóki nie jest wymagana. Jeśli tylko jeden Menedżera zasobów jest wymagana, występuje nie transakcji rozproszonej.  
  
> [!NOTE]
>  W scenariuszu z częściowo zaufanego <xref:System.Transactions.DistributedTransactionPermission> jest wymagany, gdy transakcja jest podwyższany do transakcji rozproszonej.  
  
## <a name="promotable-transaction-scenarios"></a>Scenariusze awansowanie transakcji  
 Transakcje rozproszone zwykle użycie zasobów systemu znaczące, zarządzana przez program Microsoft Distributed Transaction Coordinator (MS DTC), która integruje się menedżerowie zasobów dostępne w ramach transakcji. Awansowanie transakcji jest specjalny rodzaj <xref:System.Transactions> transakcji, które skutecznie deleguje pracy prostą [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] transakcji. <xref:System.Transactions>, <xref:System.Data.SqlClient>, i [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] koordynować pracę niezbędną do obsługi transakcji, promowania go do pełnego transakcji rozproszonej, zgodnie z potrzebami.  
  
 Zaletą używania awansowanie transakcji jest fakt, że połączenie jest otwarte przy użyciu aktywnego <xref:System.Transactions.TransactionScope> transakcji, a żadne inne połączenia są otwarte, zatwierdzenia transakcji jako lekkich transakcji, zamiast ponoszenia dodatkowych koszty pełne transakcji rozproszonej.  
  
### <a name="connection-string-keywords"></a>Słowa kluczowe parametrów połączenia  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Właściwość obsługuje słowem kluczowym `Enlist`, co oznacza, czy <xref:System.Data.SqlClient> wykryje transakcyjne konteksty i automatycznie zarejestrować połączenie w transakcji rozproszonej. Jeśli `Enlist=true`, połączenie jest automatycznie zarejestrowane w wątku otwarcia bieżącego kontekstu transakcji. Jeśli `Enlist=false`, `SqlClient` połączenia nie współdziała z transakcji rozproszonych. Wartość domyślna dla `Enlist` ma wartość true. Jeśli `Enlist` nie określono w parametrach połączenia, połączenie jest automatycznie zarejestrowane w transakcji rozproszonej, po wykryciu jednego po otwarciu połączenia.  
  
 `Transaction Binding` Słów kluczowych w <xref:System.Data.SqlClient.SqlConnection> ciąg połączenia kontroli skojarzenie tego połączenia z zarejestrowane `System.Transactions` transakcji. Jest również dostępna za pośrednictwem <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 W poniższej tabeli opisano możliwe wartości.  
  
|Keyword|Opis|  
|-------------|-----------------|  
|Niejawne usunięcia powiązania|Domyślnie. Połączenie odłącza transakcji po jej zakończeniu przełączania do trybu autozatwierdzania.|  
|Jawne usuwanie powiązania|Połączenie pozostaje przyłączona do transakcji do czasu zamknięcia transakcji. Połączenia zakończy się niepowodzeniem, jeśli skojarzonej transakcji jest nieaktywny lub nie odpowiada <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>Przy użyciu elementu TransactionScope  
 <xref:System.Transactions.TransactionScope> Klasy powoduje, że blok kodu transakcyjnego przez niejawnie rejestrowanie połączenia w transakcji rozproszonej. Należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metody na końcu <xref:System.Transactions.TransactionScope> blok przed opuszczeniem go. Pozostawienie bloku wywołuje <xref:System.Transactions.TransactionScope.Dispose%2A> metody. Jeśli wyjątek czy przyczyny, który jest uznawany za kod, aby pozostawić zakresu, transakcja została przerwana.  
  
 Firma Microsoft zaleca użycie `using` bloku, aby upewnić się, że <xref:System.Transactions.TransactionScope.Dispose%2A> jest wywoływana na <xref:System.Transactions.TransactionScope> obiektu po użyciu zablokować zostanie zakończone. Nie można przekazać ani wycofać transakcje oczekujące znacznie może uszkodzić wydajności, ponieważ domyślny limit czasu dla <xref:System.Transactions.TransactionScope> jest jedna minuta. Jeśli nie używasz `using` instrukcji, należy wykonać całą pracę w `Try` zablokować, a następnie jawnie wywołać <xref:System.Transactions.TransactionScope.Dispose%2A> metoda `Finally` bloku.  
  
 Jeśli wystąpi wyjątek w <xref:System.Transactions.TransactionScope>, transakcja jest oznaczone jako niespójne i zostanie zaniechana. Zostanie wycofana Wstecz, gdy <xref:System.Transactions.TransactionScope> został usunięty. Jeśli wystąpi żaden wyjątek, Zatwierdź uczestniczących transakcji.  
  
> [!NOTE]
>  `TransactionScope` Klasy tworzy transakcję o <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` domyślnie. W zależności od aplikacji warto rozważyć obniżenia poziomu izolacji, aby uniknąć rywalizacji wysokiej w aplikacji.  
  
> [!NOTE]
>  Zaleca się wykonywać tylko aktualizacje, wstawiania i usuwa w transakcje rozproszone, ponieważ zużywają zasoby znaczących bazy danych. Instrukcji "Select" może zablokować niepotrzebnie zasobów bazy danych, a w niektórych scenariuszach może być konieczne wybiera należy używać transakcji. Pracę bez bazy danych powinno być wykonywane poza zakresem transakcji, chyba że obejmuje ono inne menedżerowie zasobów transakcyjne. Mimo że wyjątek w zakresie transakcji uniemożliwia transakcji z zatwierdzania, <xref:System.Transactions.TransactionScope> klasa nie ma możliwości obsługi dla wycofywanie zmian kodu dokonał poza zakresem jest transakcja. Jeśli należy wykonać niektóre akcje, gdy transakcja zostanie wycofana, należy napisać własne implementacja <xref:System.Transactions.IEnlistmentNotification> interfejsu i jawnie zarejestrować transakcji.  
  
## <a name="example"></a>Przykład  
 Praca z <xref:System.Transactions> wymaga odwołania do Biblioteka System.Transactions.dll.  
  
 Następująca funkcja pokazano, jak utworzyć awansowanie transakcji dla dwóch różnych wystąpieniach programu SQL Server, reprezentowany przez dwa różne <xref:System.Data.SqlClient.SqlConnection> obiektów, które są ujęte w <xref:System.Transactions.TransactionScope> bloku. Kod tworzy <xref:System.Transactions.TransactionScope> zablokować z `using` instrukcji i otwiera pierwszego połączenia, które automatycznie rejestruje w <xref:System.Transactions.TransactionScope>. Transakcja jest początkowo zarejestrowane jako lekkie transakcji, a nie pełny transakcji rozproszonej. Drugie połączenie jest zarejestrowany w <xref:System.Transactions.TransactionScope> tylko wtedy, gdy polecenie w pierwszym połączeniu nie zgłasza wyjątek. Po otwarciu drugiego połączenia transakcji zostanie automatycznie podwyższony do pełnego transakcji rozproszonej. <xref:System.Transactions.TransactionScope.Complete%2A> Wywołaniu metody, które zatwierdza transakcję tylko wtedy, gdy żadne wyjątki nie były zgłaszane. Jeśli w dowolnym momencie zgłosił wyjątek <xref:System.Transactions.TransactionScope> bloku, `Complete` zostanie nie można wywołać i będzie transakcji rozproszonej, Przywróć Wstecz, gdy <xref:System.Transactions.TransactionScope> zostanie usunięty po zakończeniu jego `using` bloku.  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
