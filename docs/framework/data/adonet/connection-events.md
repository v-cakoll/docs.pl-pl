---
title: Zdarzenia połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a7ad0d4d950da71db0aebca872949fa82669c5c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151705"
---
# <a name="connection-events"></a>Zdarzenia połączenia
Wszyscy dostawcy danych programu .NET Framework mają obiekty **Połączenia** z dwoma zdarzeniami, których można użyć do pobierania komunikatów informacyjnych ze źródła danych lub do określenia, czy stan **połączenia** uległ zmianie. W poniższej tabeli opisano zdarzenia **connection** obiektu.  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|**Infomessage**|Występuje, gdy wiadomość informacyjna jest zwracana ze źródła danych. Komunikaty informacyjne są komunikaty ze źródła danych, które nie powodują wyjątek.|  
|**Statechange**|Występuje, gdy zmienia się stan **połączenia.**|  
  
## <a name="working-with-the-infomessage-event"></a>Praca z wydarzeniem InfoMessage  
 Ostrzeżenia i komunikaty informacyjne można pobrać ze źródła <xref:System.Data.SqlClient.SqlConnection.InfoMessage> danych programu <xref:System.Data.SqlClient.SqlConnection> SQL Server przy użyciu zdarzenia obiektu. Błędy zwracane ze źródła danych o poziomie ważności od 11 do 16 powodują wyjątek. Jednak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenie może służyć do uzyskiwania wiadomości ze źródła danych, które nie są skojarzone z błędem. W przypadku programu Microsoft SQL Server każdy błąd o ważności 10 lub mniejszej jest uważany za komunikat <xref:System.Data.SqlClient.SqlConnection.InfoMessage> informacyjny i może zostać przechwycony przy użyciu zdarzenia. Aby uzyskać więcej informacji, zobacz [ważność błędów aparatu bazy danych.](/sql/relational-databases/errors-events/database-engine-error-severities)
  
 Zdarzenie <xref:System.Data.SqlClient.SqlConnection.InfoMessage> odbiera <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> obiekt zawierający, w jego **Errors** właściwości, zbiór komunikatów ze źródła danych. Można zbadać **Error** obiektów w tej kolekcji dla numeru błędu i tekst wiadomości, a także źródło błędu. Dostawca danych programu .NET Framework dla programu SQL Server zawiera również szczegółowe informacje na temat bazy danych, procedury składowanej i numeru wiersza, z których pochodzi wiadomość.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dodać <xref:System.Data.SqlClient.SqlConnection.InfoMessage> program obsługi zdarzeń dla zdarzenia.  
  
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
 Zdarzenie <xref:System.Data.SqlClient.SqlConnection.InfoMessage> będzie zwykle uruchamiane tylko dla komunikatów informacyjnych i ostrzegawczych, które są wysyłane z serwera. Jednak gdy wystąpi rzeczywisty błąd, wykonanie **ExecuteNonQuery** lub **ExecuteReader** metody, która zainicjowała operację serwera jest zatrzymany i wyjątek.  
  
 Jeśli chcesz kontynuować przetwarzanie pozostałych instrukcji w poleceniu, niezależnie od błędów <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> wywoływanych <xref:System.Data.SqlClient.SqlConnection> przez `true`serwer, ustaw właściwość na . W ten sposób powoduje, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> że połączenie do wypalania zdarzenia dla błędów zamiast zgłaszania wyjątku i przerywania przetwarzania. Aplikacja kliencka może następnie obsługiwać to zdarzenie i reagować na warunki błędu.  
  
> [!NOTE]
> Błąd o poziomie ważności 17 lub wyższym, który powoduje, że serwer do zatrzymania przetwarzania polecenia musi być obsługiwany jako wyjątek. W takim przypadku wyjątek jest zgłaszany niezależnie od sposobu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> obsługi błędu w zdarzeniu.  
  
## <a name="working-with-the-statechange-event"></a>Praca ze zdarzeniem StateChange  
 **StateChange** zdarzenie występuje, gdy zmienia się stan **Połączenia.** <xref:System.Data.StateChangeEventArgs> Odebrane zdarzenie **StateChange,** które umożliwia określenie zmiany stanu **połączenia** przy użyciu **originalstate** i **CurrentState** właściwości. **OriginalState** Właściwość <xref:System.Data.ConnectionState> jest wyliczenie, które wskazuje stan **połączenia** przed jego zmianą. **CurrentState** jest <xref:System.Data.ConnectionState> wyliczeniem, które wskazuje stan **połączenia** po zmianie.  
  
 Poniższy przykład kodu używa **StateChange** zdarzenia do pisania wiadomości do konsoli, gdy zmienia się stan **połączenia.**  
  
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

- [Łączenie się ze źródłem danych](connecting-to-a-data-source.md)
- [Omówienie ADO.NET](ado-net-overview.md)
