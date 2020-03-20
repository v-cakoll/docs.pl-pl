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
# <a name="connection-events"></a><span data-ttu-id="f77e9-102">Zdarzenia połączenia</span><span class="sxs-lookup"><span data-stu-id="f77e9-102">Connection Events</span></span>
<span data-ttu-id="f77e9-103">Wszyscy dostawcy danych programu .NET Framework mają obiekty **Połączenia** z dwoma zdarzeniami, których można użyć do pobierania komunikatów informacyjnych ze źródła danych lub do określenia, czy stan **połączenia** uległ zmianie.</span><span class="sxs-lookup"><span data-stu-id="f77e9-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="f77e9-104">W poniższej tabeli opisano zdarzenia **connection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="f77e9-105">Wydarzenie</span><span class="sxs-lookup"><span data-stu-id="f77e9-105">Event</span></span>|<span data-ttu-id="f77e9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f77e9-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f77e9-107">**Infomessage**</span><span class="sxs-lookup"><span data-stu-id="f77e9-107">**InfoMessage**</span></span>|<span data-ttu-id="f77e9-108">Występuje, gdy wiadomość informacyjna jest zwracana ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f77e9-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="f77e9-109">Komunikaty informacyjne są komunikaty ze źródła danych, które nie powodują wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f77e9-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="f77e9-110">**Statechange**</span><span class="sxs-lookup"><span data-stu-id="f77e9-110">**StateChange**</span></span>|<span data-ttu-id="f77e9-111">Występuje, gdy zmienia się stan **połączenia.**</span><span class="sxs-lookup"><span data-stu-id="f77e9-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="f77e9-112">Praca z wydarzeniem InfoMessage</span><span class="sxs-lookup"><span data-stu-id="f77e9-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="f77e9-113">Ostrzeżenia i komunikaty informacyjne można pobrać ze źródła <xref:System.Data.SqlClient.SqlConnection.InfoMessage> danych programu <xref:System.Data.SqlClient.SqlConnection> SQL Server przy użyciu zdarzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="f77e9-114">Błędy zwracane ze źródła danych o poziomie ważności od 11 do 16 powodują wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f77e9-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="f77e9-115">Jednak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zdarzenie może służyć do uzyskiwania wiadomości ze źródła danych, które nie są skojarzone z błędem.</span><span class="sxs-lookup"><span data-stu-id="f77e9-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="f77e9-116">W przypadku programu Microsoft SQL Server każdy błąd o ważności 10 lub mniejszej jest uważany za komunikat <xref:System.Data.SqlClient.SqlConnection.InfoMessage> informacyjny i może zostać przechwycony przy użyciu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f77e9-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="f77e9-117">Aby uzyskać więcej informacji, zobacz [ważność błędów aparatu bazy danych.](/sql/relational-databases/errors-events/database-engine-error-severities)</span><span class="sxs-lookup"><span data-stu-id="f77e9-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="f77e9-118">Zdarzenie <xref:System.Data.SqlClient.SqlConnection.InfoMessage> odbiera <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> obiekt zawierający, w jego **Errors** właściwości, zbiór komunikatów ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f77e9-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="f77e9-119">Można zbadać **Error** obiektów w tej kolekcji dla numeru błędu i tekst wiadomości, a także źródło błędu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="f77e9-120">Dostawca danych programu .NET Framework dla programu SQL Server zawiera również szczegółowe informacje na temat bazy danych, procedury składowanej i numeru wiersza, z których pochodzi wiadomość.</span><span class="sxs-lookup"><span data-stu-id="f77e9-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f77e9-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f77e9-121">Example</span></span>  
 <span data-ttu-id="f77e9-122">Poniższy przykład kodu pokazuje, jak dodać <xref:System.Data.SqlClient.SqlConnection.InfoMessage> program obsługi zdarzeń dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f77e9-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="f77e9-123">Obsługa błędów jako InfoMessages</span><span class="sxs-lookup"><span data-stu-id="f77e9-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="f77e9-124">Zdarzenie <xref:System.Data.SqlClient.SqlConnection.InfoMessage> będzie zwykle uruchamiane tylko dla komunikatów informacyjnych i ostrzegawczych, które są wysyłane z serwera.</span><span class="sxs-lookup"><span data-stu-id="f77e9-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="f77e9-125">Jednak gdy wystąpi rzeczywisty błąd, wykonanie **ExecuteNonQuery** lub **ExecuteReader** metody, która zainicjowała operację serwera jest zatrzymany i wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f77e9-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="f77e9-126">Jeśli chcesz kontynuować przetwarzanie pozostałych instrukcji w poleceniu, niezależnie od błędów <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> wywoływanych <xref:System.Data.SqlClient.SqlConnection> przez `true`serwer, ustaw właściwość na .</span><span class="sxs-lookup"><span data-stu-id="f77e9-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="f77e9-127">W ten sposób powoduje, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> że połączenie do wypalania zdarzenia dla błędów zamiast zgłaszania wyjątku i przerywania przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f77e9-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="f77e9-128">Aplikacja kliencka może następnie obsługiwać to zdarzenie i reagować na warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f77e9-129">Błąd o poziomie ważności 17 lub wyższym, który powoduje, że serwer do zatrzymania przetwarzania polecenia musi być obsługiwany jako wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f77e9-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="f77e9-130">W takim przypadku wyjątek jest zgłaszany niezależnie od sposobu <xref:System.Data.SqlClient.SqlConnection.InfoMessage> obsługi błędu w zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="f77e9-131">Praca ze zdarzeniem StateChange</span><span class="sxs-lookup"><span data-stu-id="f77e9-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="f77e9-132">**StateChange** zdarzenie występuje, gdy zmienia się stan **Połączenia.**</span><span class="sxs-lookup"><span data-stu-id="f77e9-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="f77e9-133"><xref:System.Data.StateChangeEventArgs> Odebrane zdarzenie **StateChange,** które umożliwia określenie zmiany stanu **połączenia** przy użyciu **originalstate** i **CurrentState** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f77e9-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="f77e9-134">**OriginalState** Właściwość <xref:System.Data.ConnectionState> jest wyliczenie, które wskazuje stan **połączenia** przed jego zmianą.</span><span class="sxs-lookup"><span data-stu-id="f77e9-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="f77e9-135">**CurrentState** jest <xref:System.Data.ConnectionState> wyliczeniem, które wskazuje stan **połączenia** po zmianie.</span><span class="sxs-lookup"><span data-stu-id="f77e9-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="f77e9-136">Poniższy przykład kodu używa **StateChange** zdarzenia do pisania wiadomości do konsoli, gdy zmienia się stan **połączenia.**</span><span class="sxs-lookup"><span data-stu-id="f77e9-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f77e9-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f77e9-137">See also</span></span>

- [<span data-ttu-id="f77e9-138">Łączenie się ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="f77e9-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="f77e9-139">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f77e9-139">ADO.NET Overview</span></span>](ado-net-overview.md)
