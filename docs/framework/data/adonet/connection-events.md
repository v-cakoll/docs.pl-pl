---
title: Zdarzenia połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a71758781511f18ddf5451feaf0d308af1b4a652
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879934"
---
# <a name="connection-events"></a><span data-ttu-id="997ff-102">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="997ff-102">Connection Events</span></span>
<span data-ttu-id="997ff-103">Wszystkie dostawcy danych .NET Framework mają **połączenia** obiekty o dwa zdarzenia, które można pobrać komunikaty informacyjne ze źródła danych lub do określenia, czy stan **połączenia** ma zmienione.</span><span class="sxs-lookup"><span data-stu-id="997ff-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="997ff-104">W poniższej tabeli opisano zdarzenia **połączenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="997ff-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="997ff-105">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="997ff-105">Event</span></span>|<span data-ttu-id="997ff-106">Opis</span><span class="sxs-lookup"><span data-stu-id="997ff-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="997ff-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="997ff-107">**InfoMessage**</span></span>|<span data-ttu-id="997ff-108">Występuje, gdy zwracany jest komunikat informacyjny ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="997ff-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="997ff-109">Komunikaty informacyjne to komunikaty ze źródła danych, które nie powodują rzuceniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="997ff-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="997ff-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="997ff-110">**StateChange**</span></span>|<span data-ttu-id="997ff-111">Występuje, gdy stan **połączenia** zmiany.</span><span class="sxs-lookup"><span data-stu-id="997ff-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="997ff-112">Praca ze zdarzeniem InfoMessage</span><span class="sxs-lookup"><span data-stu-id="997ff-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="997ff-113">Możesz pobrać ostrzeżenia i komunikaty informacyjne z programu SQL Server źródła danych przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="997ff-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="997ff-114">Błędy zwrócone ze źródła danych z poziomem ważności 11 do 16 powodować zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="997ff-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="997ff-115">Jednak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń może służyć do uzyskania komunikatów ze źródła danych, które nie są skojarzone z powodu błędu.</span><span class="sxs-lookup"><span data-stu-id="997ff-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="997ff-116">W przypadku programu Microsoft SQL Server, dowolnego błędu o o wadze 10 lub mniej jest uznawana za komunikat informacyjny i mogą zostać przechwycone przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="997ff-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="997ff-117">Aby uzyskać więcej informacji, zobacz [ważności błąd aparatu bazy danych](/sql/relational-databases/errors-events/database-engine-error-severities) artykułu.</span><span class="sxs-lookup"><span data-stu-id="997ff-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="997ff-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Odbiera zdarzenia <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> zawierającą obiekt, jego **błędy** właściwość, kolekcję komunikatów ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="997ff-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="997ff-119">Można tworzyć zapytania **błąd** obiektów w tej kolekcji tekst numer i komunikat błędu, a także źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="997ff-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="997ff-120">.NET Framework Data Provider for SQL Server zawiera także szczegółowe informacje o bazie danych, procedury składowanej i numer wiersza, którego wiadomość pochodzi z.</span><span class="sxs-lookup"><span data-stu-id="997ff-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="997ff-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="997ff-121">Example</span></span>  
 <span data-ttu-id="997ff-122">Poniższy przykład kodu pokazuje, jak dodać obsługę zdarzeń dla <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="997ff-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="997ff-123">Obsługa błędów jako InfoMessages</span><span class="sxs-lookup"><span data-stu-id="997ff-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="997ff-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Zdarzeń zwykle będą uruchamiane tylko w przypadku komunikaty informacyjne i ostrzeżenia, które są wysyłane z serwera.</span><span class="sxs-lookup"><span data-stu-id="997ff-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="997ff-125">Jednak gdy rzeczywisty wystąpi błąd, wykonanie **ExecuteNonQuery** lub **ExecuteReader** metodą, która zainicjowała działanie serwera jest zatrzymywana i zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="997ff-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="997ff-126">Jeśli chcesz kontynuować przetwarzanie resztę instrukcji w poleceniu, niezależnie od tego, błędy generowane przez serwer, ustaw <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> do `true`.</span><span class="sxs-lookup"><span data-stu-id="997ff-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="997ff-127">W ten sposób powoduje, że połączenie ognia <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia błędów zamiast zgłaszać wyjątek i przerywania przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="997ff-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="997ff-128">Aplikacja kliencka można obsługiwać to zdarzenie i reagować na błędy.</span><span class="sxs-lookup"><span data-stu-id="997ff-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="997ff-129">Błąd z poziomem ważności 17 lub nowszej, który powoduje, że serwer zatrzymać przetwarzanie, polecenie musi być obsługiwany jako wyjątek.</span><span class="sxs-lookup"><span data-stu-id="997ff-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="997ff-130">W tym przypadku jest zgłaszany wyjątek, niezależnie od tego, jak obsługiwany jest błąd w <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="997ff-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="997ff-131">Praca ze zdarzeniem StateChange</span><span class="sxs-lookup"><span data-stu-id="997ff-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="997ff-132">**StateChange** zdarzenie występuje gdy stan **połączenia** zmiany.</span><span class="sxs-lookup"><span data-stu-id="997ff-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="997ff-133">**StateChange** odbiera zdarzenia <xref:System.Data.StateChangeEventArgs> umożliwiające ustalić zmiany w stanie **połączenia** przy użyciu **OriginalState** i **CurrentState** właściwości.</span><span class="sxs-lookup"><span data-stu-id="997ff-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="997ff-134">**OriginalState** właściwość <xref:System.Data.ConnectionState> wyliczenie, które wskazuje stan **połączenia** poprzedzających go zmienić.</span><span class="sxs-lookup"><span data-stu-id="997ff-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="997ff-135">**CurrentState** jest <xref:System.Data.ConnectionState> wyliczenie, które wskazuje stan **połączenia** po jego zmianie.</span><span class="sxs-lookup"><span data-stu-id="997ff-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="997ff-136">Poniższy przykład kodu wykorzystuje **StateChange** zdarzenie, aby zapisać komunikat do konsoli po stan **połączenia** zmiany.</span><span class="sxs-lookup"><span data-stu-id="997ff-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="997ff-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="997ff-137">See also</span></span>

- [<span data-ttu-id="997ff-138">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="997ff-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="997ff-139">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="997ff-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
