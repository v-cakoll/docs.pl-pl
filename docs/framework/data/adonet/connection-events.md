---
title: Zdarzenia połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: e958c96e304962dace72e90b9266b57943f01ac9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785738"
---
# <a name="connection-events"></a>Zdarzenia połączenia
Wszyscy dostawcy danych .NET Framework są obiektami **połączeń** z dwoma zdarzeniami, których można użyć do pobierania komunikatów informacyjnych ze źródła danych lub w celu ustalenia, czy stan **połączenia** został zmieniony. W poniższej tabeli opisano zdarzenia obiektu **Connection** .  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|**InfoMessage**|Występuje, gdy zostanie zwrócony komunikat informacyjny ze źródła danych. Komunikaty informacyjne to komunikaty ze źródła danych, które nie powodują zgłaszania wyjątku.|  
|**StateChange**|Występuje, gdy zmienia się stan **połączenia** .|  
  
## <a name="working-with-the-infomessage-event"></a>Praca ze zdarzeniem InfoMessage  
 Można pobrać ostrzeżenia i komunikaty informacyjne ze źródła danych SQL Server przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia <xref:System.Data.SqlClient.SqlConnection> obiektu. Błędy zwrócone ze źródła danych o poziomie ważności 11 do 16 powodują zgłoszenie wyjątku. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Jednak zdarzenie może służyć do uzyskiwania komunikatów ze źródła danych, które nie są skojarzone z błędem. W przypadku Microsoft SQL Server każdy błąd o ważności 10 lub mniejszej jest traktowany jako komunikat informacyjny i może być przechwytywany przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia. Aby uzyskać więcej informacji, zobacz artykuł [dotyczący ilości błędów aparatu bazy danych](/sql/relational-databases/errors-events/database-engine-error-severities) .
  
 Zdarzenie odbiera obiekt zawierający, w jego właściwości Errors, kolekcję komunikatów ze źródła danych. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> Można wysyłać zapytania dotyczące obiektów **błędów** w tej kolekcji dla numeru błędu i tekstu komunikatu, jak również źródła błędu. Dostawca danych .NET Framework dla SQL Server zawiera również szczegółowe informacje o bazie danych, procedurze składowanej i numerze wiersza, z którego pochodzi wiadomość.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dodać program obsługi zdarzeń dla <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia.  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>Obsługa błędów jako InfoMessages  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Zdarzenie będzie zazwyczaj wyzwalane tylko w przypadku komunikatów informacyjnych i ostrzeżeń wysyłanych z serwera. Jednak w przypadku wystąpienia rzeczywistego błędu wykonywanie metody **ExecuteNonQuery** lub **ExecuteReader** , która zainicjowała operację serwera, jest zatrzymane i zgłaszany jest wyjątek.  
  
 Jeśli chcesz kontynuować przetwarzanie reszt instrukcji w poleceniu, niezależnie od błędów wygenerowanych przez serwer, ustaw <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> na `true`. Powoduje to, że połączenie wyzwala <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenie w poszukiwaniu błędów zamiast zgłaszania wyjątku i przerywania przetwarzania. Aplikacja kliencka może następnie obsłużyć to zdarzenie i odpowiedzieć na błędy.  
  
> [!NOTE]
> Wystąpił błąd o poziomie ważności wynoszącym 17 lub wyższym, który powoduje, że serwer zatrzymania przetwarzania polecenia musi być obsłużony jako wyjątek. W takim przypadku wyjątek jest zgłaszany niezależnie od tego, jak błąd jest obsługiwany w <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeniu.  
  
## <a name="working-with-the-statechange-event"></a>Praca ze zdarzeniem StateChange  
 Zdarzenie **StateChange** występuje, gdy zmienia się stan **połączenia** . Zostanie odebrane <xref:System.Data.StateChangeEventArgs> zdarzenie stateChange, które umożliwia określenie zmiany stanu **połączenia** przy użyciu właściwości **OriginalState** i **CurrentState** . Właściwość **OriginalState** jest <xref:System.Data.ConnectionState> wyliczeniem wskazującym stan **połączenia** przed jego zmianą. **CurrentState** to <xref:System.Data.ConnectionState> Wyliczenie, które wskazuje stan **połączenia** po jego zmianie.  
  
 Poniższy przykład kodu używa zdarzenia **StateChange** , aby napisać komunikat do konsoli w przypadku zmiany stanu **połączenia** .  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)
- [Omówienie ADO.NET](ado-net-overview.md)
