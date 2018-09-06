---
title: Zdarzenia połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037740"
---
# <a name="connection-events"></a>Zdarzenia połączeń
Wszystkie dostawcy danych .NET Framework mają **połączenia** obiekty o dwa zdarzenia, które można pobrać komunikaty informacyjne ze źródła danych lub do określenia, czy stan **połączenia** ma zmienione. W poniższej tabeli opisano zdarzenia **połączenia** obiektu.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|**InfoMessage**|Występuje, gdy zwracany jest komunikat informacyjny ze źródła danych. Komunikaty informacyjne to komunikaty ze źródła danych, które nie powodują rzuceniem wyjątku.|  
|**StateChange**|Występuje, gdy stan **połączenia** zmiany.|  
  
## <a name="working-with-the-infomessage-event"></a>Praca ze zdarzeniem InfoMessage  
 Możesz pobrać ostrzeżenia i komunikaty informacyjne z programu SQL Server źródła danych przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia <xref:System.Data.SqlClient.SqlConnection> obiektu. Błędy zwrócone ze źródła danych z poziomem ważności 11 do 16 powodować zgłoszenie wyjątku. Jednak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń może służyć do uzyskania komunikatów ze źródła danych, które nie są skojarzone z powodu błędu. W przypadku programu Microsoft SQL Server, dowolnego błędu o o wadze 10 lub mniej jest uznawana za komunikat informacyjny i mogą zostać przechwycone przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń. Aby uzyskać więcej informacji, zobacz [ważności błąd aparatu bazy danych](/sql/relational-databases/errors-events/database-engine-error-severities) artykułu.
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Odbiera zdarzenia <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> zawierającą obiekt, jego **błędy** właściwość, kolekcję komunikatów ze źródła danych. Można tworzyć zapytania **błąd** obiektów w tej kolekcji tekst numer i komunikat błędu, a także źródła błędu. .NET Framework Data Provider for SQL Server zawiera także szczegółowe informacje o bazie danych, procedury składowanej i numer wiersza, którego wiadomość pochodzi z.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dodać obsługę zdarzeń dla <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.  
  
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
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Zdarzeń zwykle będą uruchamiane tylko w przypadku komunikaty informacyjne i ostrzeżenia, które są wysyłane z serwera. Jednak gdy rzeczywisty wystąpi błąd, wykonanie **ExecuteNonQuery** lub **ExecuteReader** metodą, która zainicjowała działanie serwera jest zatrzymywana i zgłaszany jest wyjątek.  
  
 Jeśli chcesz kontynuować przetwarzanie resztę instrukcji w poleceniu, niezależnie od tego, błędy generowane przez serwer, ustaw <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> do `true`. W ten sposób powoduje, że połączenie ognia <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia błędów zamiast zgłaszać wyjątek i przerywania przetwarzania. Aplikacja kliencka można obsługiwać to zdarzenie i reagować na błędy.  
  
> [!NOTE]
>  Błąd z poziomem ważności 17 lub nowszej, który powoduje, że serwer zatrzymać przetwarzanie, polecenie musi być obsługiwany jako wyjątek. W tym przypadku jest zgłaszany wyjątek, niezależnie od tego, jak obsługiwany jest błąd w <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.  
  
## <a name="working-with-the-statechange-event"></a>Praca ze zdarzeniem StateChange  
 **StateChange** zdarzenie występuje gdy stan **połączenia** zmiany. **StateChange** odbiera zdarzenia <xref:System.Data.StateChangeEventArgs> umożliwiające ustalić zmiany w stanie **połączenia** przy użyciu **OriginalState** i **CurrentState** właściwości. **OriginalState** właściwość <xref:System.Data.ConnectionState> wyliczenie, które wskazuje stan **połączenia** poprzedzających go zmienić. **CurrentState** jest <xref:System.Data.ConnectionState> wyliczenie, które wskazuje stan **połączenia** po jego zmianie.  
  
 Poniższy przykład kodu wykorzystuje **StateChange** zdarzenie, aby zapisać komunikat do konsoli po stan **połączenia** zmiany.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
