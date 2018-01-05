---
title: "Zdarzenia połączeń"
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
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e0eb38eb764faa51524565e57826db17311fc5dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="connection-events"></a>Zdarzenia połączeń
Wszystkich dostawców danych .NET Framework jest **połączenia** obiekty o dwa zdarzenia, których można pobrać komunikaty informacyjne ze źródła danych lub można określić, czy stan **połączenia** ma zmienić. W poniższej tabeli opisano zdarzenia **połączenia** obiektu.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|**InfoMessage**|Występuje, gdy zwracany jest komunikat informacyjny ze źródła danych. Komunikaty informacyjne są komunikatów ze źródła danych, które nie powodują wyjątek.|  
|**StateChange**|Występuje, gdy stan **połączenia** zmiany.|  
  
## <a name="working-with-the-infomessage-event"></a>Praca z InfoMessage zdarzeń  
 Ostrzeżenia i komunikaty informacyjne można pobrać z serwera SQL źródła danych przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenie <xref:System.Data.SqlClient.SqlConnection> obiektu. Błędy zwrócone ze źródła danych na poziomie ważność 11 do 16 spowodować wyjątków. Jednak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń może służyć do uzyskiwania wiadomości ze źródła danych, które nie są skojarzone z powodu błędu. W przypadku programu Microsoft SQL Server jest uważany za komunikat informacyjny błędu z o wadze 10 lub mniej, a można przechwycić przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń. Aby uzyskać więcej informacji zobacz temat "Poziomy ważności komunikat błędu" w dokumentacji SQL Server — książki Online.  
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Odbiera zdarzenia <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> zawierający obiekt, jego **błędy** właściwości, kolekcję komunikatów ze źródła danych. Można zbadać **błąd** obiektów w tej kolekcji tekst numer i komunikat błędu, a także źródła błędu. .NET Framework Data Provider for SQL Server zawiera także szczegółowe informacje o bazie danych, procedur składowanych i numer wiersza, którego wiadomość pochodzi z.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób dodawania obsługi zdarzenia <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.  
  
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
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Zdarzeń zwykle zostanie zastosowana tylko do komunikaty informacyjne i ostrzeżenia, które są wysyłane z serwera. Jednak gdy rzeczywista wystąpi błąd, wykonanie **ExecuteNonQuery** lub **ExecuteReader** metody, który zainicjował operację serwera jest zatrzymywany i jest zgłaszany wyjątek.  
  
 Jeśli chcesz kontynuować przetwarzania pozostałe instrukcje w polecenia, bez względu na błędy generowane przez serwer, ustaw <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> do `true`. W ten sposób spowoduje, że połączenie uruchomienie <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia błędów zamiast generowania wyjątku i przerywania przetwarzania. Aplikacja kliencka można obsłużyć tego zdarzenia i odpowiadanie na błędy.  
  
> [!NOTE]
>  Błąd poziomu ważności 17 lub nowszym, który powoduje, że serwer zatrzymania przetwarzania polecenia musi być obsługiwane jako wyjątek. W takim przypadku jest zwracany wyjątek, niezależnie od sposobu obsługi błędu w <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.  
  
## <a name="working-with-the-statechange-event"></a>Praca z zdarzenie StateChange  
 **StateChange** zdarzenie po stan **połączenia** zmiany. **StateChange** odbiera zdarzenia <xref:System.Data.StateChangeEventArgs> umożliwiające ustalenie, jaka zmiana w stanie **połączenia** za pomocą **OriginalState** i **CurrentState** właściwości. **OriginalState** właściwość jest <xref:System.Data.ConnectionState> wyliczenia, które wskazuje stan **połączenia** przed go zmienić. **CurrentState** jest <xref:System.Data.ConnectionState> wyliczenia, które wskazuje stan **połączenia** po zmianie go.  
  
 Poniższy przykład kodu wykorzystuje **StateChange** zdarzeń można zapisać komunikatu w konsoli po stan **połączenia** zmiany.  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
