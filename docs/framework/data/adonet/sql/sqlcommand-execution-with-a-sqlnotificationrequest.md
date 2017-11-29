---
title: Wykonywanie SqlCommand SqlNotificationRequest
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
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fdd76820ee0758492fab1364c7561920c549a412
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="a4c3f-102">Wykonywanie SqlCommand SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="a4c3f-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="a4c3f-103">A <xref:System.Data.SqlClient.SqlCommand> można skonfigurować, aby wygenerować powiadomienie o zmianie danych po zostaną pobrane z serwera i zestawu wyników będzie inny, jeśli zostały ponownie wykonać zapytanie.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="a4c3f-104">Jest to przydatne w scenariuszach, w której chcesz użyć niestandardowych powiadomień kolejek na serwerze lub nie chcesz zachować obiektów na żywo.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="a4c3f-105">Tworzenie żądania powiadomienia</span><span class="sxs-lookup"><span data-stu-id="a4c3f-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="a4c3f-106">Można użyć <xref:System.Data.Sql.SqlNotificationRequest> obiektu do utworzenia żądania powiadomienia przez to powiązanie `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="a4c3f-107">Po utworzeniu żądania nie są już potrzebne `SqlNotificationRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="a4c3f-108">Można zapytania do kolejki w celu powiadomienia i reagowania.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="a4c3f-109">Powiadomienia może wystąpić, nawet jeśli aplikacja jest zamknięta i uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="a4c3f-110">Po wykonaniu polecenia skojarzone powiadomienia zmiany wprowadzone w wyniku oryginalnego ustawić wyzwalacz wysyłanie wiadomości do kolejki programu SQL Server, który został skonfigurowany w żądaniu powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="a4c3f-111">Sposób sondowania kolejki programu SQL Server i interpretować wiadomość jest specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="a4c3f-112">Aplikacja jest odpowiedzialny za sondowania kolejki i reagowania na podstawie zawartości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4c3f-113">Korzystając z programu SQL Server żądania powiadomień o <xref:System.Data.SqlClient.SqlDependency>, utworzyć własną nazwę kolejki, zamiast domyślnej nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="a4c3f-114">Istnieją żadne nowe elementy zabezpieczeń po stronie klienta dla <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="a4c3f-115">To przede wszystkim funkcję serwera, a serwer został utworzony specjalne uprawnienia, które użytkownicy muszą mieć żądania powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a4c3f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4c3f-116">Example</span></span>  
 <span data-ttu-id="a4c3f-117">Poniższy fragment kodu przedstawia sposób tworzenia <xref:System.Data.Sql.SqlNotificationRequest> i skojarz ją z <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="a4c3f-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4c3f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4c3f-118">See Also</span></span>  
 [<span data-ttu-id="a4c3f-119">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="a4c3f-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="a4c3f-120">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="a4c3f-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
