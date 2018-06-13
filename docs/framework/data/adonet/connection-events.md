---
title: Zdarzenia połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 719e529c7813679f1e927b66e7db0e110714e438
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758164"
---
# <a name="connection-events"></a><span data-ttu-id="764d3-102">Zdarzenia połączeń</span><span class="sxs-lookup"><span data-stu-id="764d3-102">Connection Events</span></span>
<span data-ttu-id="764d3-103">Wszystkich dostawców danych .NET Framework jest **połączenia** obiekty o dwa zdarzenia, których można pobrać komunikaty informacyjne ze źródła danych lub można określić, czy stan **połączenia** ma zmienić.</span><span class="sxs-lookup"><span data-stu-id="764d3-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="764d3-104">W poniższej tabeli opisano zdarzenia **połączenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="764d3-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="764d3-105">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="764d3-105">Event</span></span>|<span data-ttu-id="764d3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="764d3-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="764d3-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="764d3-107">**InfoMessage**</span></span>|<span data-ttu-id="764d3-108">Występuje, gdy zwracany jest komunikat informacyjny ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="764d3-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="764d3-109">Komunikaty informacyjne są komunikatów ze źródła danych, które nie powodują wyjątek.</span><span class="sxs-lookup"><span data-stu-id="764d3-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="764d3-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="764d3-110">**StateChange**</span></span>|<span data-ttu-id="764d3-111">Występuje, gdy stan **połączenia** zmiany.</span><span class="sxs-lookup"><span data-stu-id="764d3-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="764d3-112">Praca z InfoMessage zdarzeń</span><span class="sxs-lookup"><span data-stu-id="764d3-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="764d3-113">Ostrzeżenia i komunikaty informacyjne można pobrać z serwera SQL źródła danych przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenie <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="764d3-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="764d3-114">Błędy zwrócone ze źródła danych na poziomie ważność 11 do 16 spowodować wyjątków.</span><span class="sxs-lookup"><span data-stu-id="764d3-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="764d3-115">Jednak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń może służyć do uzyskiwania wiadomości ze źródła danych, które nie są skojarzone z powodu błędu.</span><span class="sxs-lookup"><span data-stu-id="764d3-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="764d3-116">W przypadku programu Microsoft SQL Server jest uważany za komunikat informacyjny błędu z o wadze 10 lub mniej, a można przechwycić przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="764d3-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="764d3-117">Aby uzyskać więcej informacji zobacz temat "Poziomy ważności komunikat błędu" w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="764d3-117">For more information, see the "Error Message Severity Levels" topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="764d3-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Odbiera zdarzenia <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> zawierający obiekt, jego **błędy** właściwości, kolekcję komunikatów ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="764d3-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="764d3-119">Można zbadać **błąd** obiektów w tej kolekcji tekst numer i komunikat błędu, a także źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="764d3-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="764d3-120">.NET Framework Data Provider for SQL Server zawiera także szczegółowe informacje o bazie danych, procedur składowanych i numer wiersza, którego wiadomość pochodzi z.</span><span class="sxs-lookup"><span data-stu-id="764d3-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="764d3-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="764d3-121">Example</span></span>  
 <span data-ttu-id="764d3-122">W poniższym przykładzie przedstawiono sposób dodawania obsługi zdarzenia <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="764d3-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="764d3-123">Obsługa błędów jako InfoMessages</span><span class="sxs-lookup"><span data-stu-id="764d3-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="764d3-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Zdarzeń zwykle zostanie zastosowana tylko do komunikaty informacyjne i ostrzeżenia, które są wysyłane z serwera.</span><span class="sxs-lookup"><span data-stu-id="764d3-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="764d3-125">Jednak gdy rzeczywista wystąpi błąd, wykonanie **ExecuteNonQuery** lub **ExecuteReader** metody, który zainicjował operację serwera jest zatrzymywany i jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="764d3-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="764d3-126">Jeśli chcesz kontynuować przetwarzania pozostałe instrukcje w polecenia, bez względu na błędy generowane przez serwer, ustaw <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> do `true`.</span><span class="sxs-lookup"><span data-stu-id="764d3-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="764d3-127">W ten sposób spowoduje, że połączenie uruchomienie <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia błędów zamiast generowania wyjątku i przerywania przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="764d3-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="764d3-128">Aplikacja kliencka można obsłużyć tego zdarzenia i odpowiadanie na błędy.</span><span class="sxs-lookup"><span data-stu-id="764d3-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="764d3-129">Błąd poziomu ważności 17 lub nowszym, który powoduje, że serwer zatrzymania przetwarzania polecenia musi być obsługiwane jako wyjątek.</span><span class="sxs-lookup"><span data-stu-id="764d3-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="764d3-130">W takim przypadku jest zwracany wyjątek, niezależnie od sposobu obsługi błędu w <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="764d3-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="764d3-131">Praca z zdarzenie StateChange</span><span class="sxs-lookup"><span data-stu-id="764d3-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="764d3-132">**StateChange** zdarzenie po stan **połączenia** zmiany.</span><span class="sxs-lookup"><span data-stu-id="764d3-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="764d3-133">**StateChange** odbiera zdarzenia <xref:System.Data.StateChangeEventArgs> umożliwiające ustalenie, jaka zmiana w stanie **połączenia** za pomocą **OriginalState** i **CurrentState** właściwości.</span><span class="sxs-lookup"><span data-stu-id="764d3-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="764d3-134">**OriginalState** właściwość jest <xref:System.Data.ConnectionState> wyliczenia, które wskazuje stan **połączenia** przed go zmienić.</span><span class="sxs-lookup"><span data-stu-id="764d3-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="764d3-135">**CurrentState** jest <xref:System.Data.ConnectionState> wyliczenia, które wskazuje stan **połączenia** po zmianie go.</span><span class="sxs-lookup"><span data-stu-id="764d3-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="764d3-136">Poniższy przykład kodu wykorzystuje **StateChange** zdarzeń można zapisać komunikatu w konsoli po stan **połączenia** zmiany.</span><span class="sxs-lookup"><span data-stu-id="764d3-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="764d3-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="764d3-137">See Also</span></span>  
 [<span data-ttu-id="764d3-138">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="764d3-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="764d3-139">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="764d3-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
