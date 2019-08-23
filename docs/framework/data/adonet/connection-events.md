---
title: Zdarzenia połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 8ed62d0193639b434d66c446e3b9d0c184577a80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949562"
---
# <a name="connection-events"></a><span data-ttu-id="51c12-102">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="51c12-102">Connection Events</span></span>
<span data-ttu-id="51c12-103">Wszyscy dostawcy danych .NET Framework są obiektami **połączeń** z dwoma zdarzeniami, których można użyć do pobierania komunikatów informacyjnych ze źródła danych lub w celu ustalenia, czy stan **połączenia** został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="51c12-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="51c12-104">W poniższej tabeli opisano zdarzenia obiektu **Connection** .</span><span class="sxs-lookup"><span data-stu-id="51c12-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="51c12-105">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="51c12-105">Event</span></span>|<span data-ttu-id="51c12-106">Opis</span><span class="sxs-lookup"><span data-stu-id="51c12-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="51c12-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="51c12-107">**InfoMessage**</span></span>|<span data-ttu-id="51c12-108">Występuje, gdy zostanie zwrócony komunikat informacyjny ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="51c12-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="51c12-109">Komunikaty informacyjne to komunikaty ze źródła danych, które nie powodują zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="51c12-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="51c12-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="51c12-110">**StateChange**</span></span>|<span data-ttu-id="51c12-111">Występuje, gdy zmienia się stan **połączenia** .</span><span class="sxs-lookup"><span data-stu-id="51c12-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="51c12-112">Praca ze zdarzeniem InfoMessage</span><span class="sxs-lookup"><span data-stu-id="51c12-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="51c12-113">Można pobrać ostrzeżenia i komunikaty informacyjne ze źródła danych SQL Server przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="51c12-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="51c12-114">Błędy zwrócone ze źródła danych o poziomie ważności 11 do 16 powodują zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="51c12-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="51c12-115"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Jednak zdarzenie może służyć do uzyskiwania komunikatów ze źródła danych, które nie są skojarzone z błędem.</span><span class="sxs-lookup"><span data-stu-id="51c12-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="51c12-116">W przypadku Microsoft SQL Server każdy błąd o ważności 10 lub mniejszej jest traktowany jako komunikat informacyjny i może być przechwytywany przy użyciu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51c12-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="51c12-117">Aby uzyskać więcej informacji, zobacz artykuł dotyczący ilości [błędów aparatu bazy danych](/sql/relational-databases/errors-events/database-engine-error-severities) .</span><span class="sxs-lookup"><span data-stu-id="51c12-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="51c12-118">Zdarzenie odbiera obiekt zawierający, w jego właściwości Errors, kolekcję komunikatów ze źródła danych. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs></span><span class="sxs-lookup"><span data-stu-id="51c12-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="51c12-119">Można wysyłać zapytania dotyczące obiektów **błędów** w tej kolekcji dla numeru błędu i tekstu komunikatu, jak również źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="51c12-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="51c12-120">Dostawca danych .NET Framework dla SQL Server zawiera również szczegółowe informacje o bazie danych, procedurze składowanej i numerze wiersza, z którego pochodzi wiadomość.</span><span class="sxs-lookup"><span data-stu-id="51c12-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="51c12-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="51c12-121">Example</span></span>  
 <span data-ttu-id="51c12-122">Poniższy przykład kodu pokazuje, jak dodać program obsługi zdarzeń dla <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51c12-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="51c12-123">Obsługa błędów jako InfoMessages</span><span class="sxs-lookup"><span data-stu-id="51c12-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="51c12-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Zdarzenie będzie zazwyczaj wyzwalane tylko w przypadku komunikatów informacyjnych i ostrzeżeń wysyłanych z serwera.</span><span class="sxs-lookup"><span data-stu-id="51c12-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="51c12-125">Jednak w przypadku wystąpienia rzeczywistego błędu wykonywanie metody **ExecuteNonQuery** lub **ExecuteReader** , która zainicjowała operację serwera, jest zatrzymane i zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="51c12-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="51c12-126">Jeśli chcesz kontynuować przetwarzanie reszt instrukcji w poleceniu, niezależnie od błędów wygenerowanych przez serwer, ustaw <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> na `true`.</span><span class="sxs-lookup"><span data-stu-id="51c12-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="51c12-127">Powoduje to, że połączenie wyzwala <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenie w poszukiwaniu błędów zamiast zgłaszania wyjątku i przerywania przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="51c12-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="51c12-128">Aplikacja kliencka może następnie obsłużyć to zdarzenie i odpowiedzieć na błędy.</span><span class="sxs-lookup"><span data-stu-id="51c12-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51c12-129">Wystąpił błąd o poziomie ważności wynoszącym 17 lub wyższym, który powoduje, że serwer zatrzymania przetwarzania polecenia musi być obsłużony jako wyjątek.</span><span class="sxs-lookup"><span data-stu-id="51c12-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="51c12-130">W takim przypadku wyjątek jest zgłaszany niezależnie od tego, jak błąd jest obsługiwany w <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="51c12-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="51c12-131">Praca ze zdarzeniem StateChange</span><span class="sxs-lookup"><span data-stu-id="51c12-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="51c12-132">Zdarzenie **StateChange** występuje, gdy zmienia się stan **połączenia** .</span><span class="sxs-lookup"><span data-stu-id="51c12-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="51c12-133">Zostanie odebrane <xref:System.Data.StateChangeEventArgs> zdarzenie stateChange, które umożliwia określenie zmiany stanu **połączenia** przy użyciu właściwości **OriginalState** i **CurrentState** .</span><span class="sxs-lookup"><span data-stu-id="51c12-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="51c12-134">Właściwość **OriginalState** jest <xref:System.Data.ConnectionState> wyliczeniem wskazującym stan **połączenia** przed jego zmianą.</span><span class="sxs-lookup"><span data-stu-id="51c12-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="51c12-135">**CurrentState** to <xref:System.Data.ConnectionState> Wyliczenie, które wskazuje stan **połączenia** po jego zmianie.</span><span class="sxs-lookup"><span data-stu-id="51c12-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="51c12-136">Poniższy przykład kodu używa zdarzenia **StateChange** , aby napisać komunikat do konsoli w przypadku zmiany stanu **połączenia** .</span><span class="sxs-lookup"><span data-stu-id="51c12-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51c12-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51c12-137">See also</span></span>

- [<span data-ttu-id="51c12-138">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="51c12-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="51c12-139">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="51c12-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
