---
title: Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 83450e6ace33e89ddd263a1514f74f4d4e231cf7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405806"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="3bb06-102">Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="3bb06-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="3bb06-103">Element <xref:System.Data.SqlClient.SqlCommand> można skonfigurować, aby wygenerować powiadomienie po zmianie danych, gdy zostaną pobrane z serwera i zestawu wyników będzie inna w przypadku zapytania były wykonywane ponownie.</span><span class="sxs-lookup"><span data-stu-id="3bb06-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="3bb06-104">Jest to przydatne w scenariuszach, w której chcesz używać kolejek niestandardowe powiadomienie, na serwerze lub nie chcesz zachować obiektów na żywo.</span><span class="sxs-lookup"><span data-stu-id="3bb06-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="3bb06-105">Tworzenie żądania powiadomienia</span><span class="sxs-lookup"><span data-stu-id="3bb06-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="3bb06-106">Możesz użyć <xref:System.Data.Sql.SqlNotificationRequest> obiektu do utworzenia żądania powiadomienia, tworząc powiązanie do `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3bb06-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="3bb06-107">Po utworzeniu żądania nie są już potrzebne `SqlNotificationRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3bb06-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="3bb06-108">Można wykonywać zapytania kolejki w celu powiadomienia i odpowiednio reagować.</span><span class="sxs-lookup"><span data-stu-id="3bb06-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="3bb06-109">Powiadomienia może wystąpić, nawet jeśli aplikacja jest zamknięta i uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="3bb06-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="3bb06-110">Po wykonaniu polecenia z powiadomieniem skojarzone zmiany wprowadzone w wyniku oryginalnego zestawu wyzwalacza wysyłania komunikatu do kolejki programu SQL Server, który został skonfigurowany w żądaniu powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="3bb06-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="3bb06-111">Jak wykonać sondowanie kolejki programu SQL Server i interpretować komunikat jest specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bb06-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="3bb06-112">Aplikacja jest odpowiedzialna za sondowania kolejki i reagowanie na podstawie zawartości komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3bb06-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bb06-113">Korzystając z programu SQL Server notification żądań z <xref:System.Data.SqlClient.SqlDependency>, Utwórz własną nazwę kolejki, a nie przy użyciu nazwy usługi domyślnego.</span><span class="sxs-lookup"><span data-stu-id="3bb06-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="3bb06-114">Nie ma elementów nowych zabezpieczeń po stronie klienta dla <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="3bb06-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="3bb06-115">Jest to głównie funkcji serwera, a serwer został utworzony specjalne uprawnienia, które użytkownicy muszą mieć żądania powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="3bb06-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3bb06-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3bb06-116">Example</span></span>  
 <span data-ttu-id="3bb06-117">Poniższy fragment kodu przedstawia sposób tworzenia <xref:System.Data.Sql.SqlNotificationRequest> i powiąż ją z <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="3bb06-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bb06-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bb06-118">See Also</span></span>  
 [<span data-ttu-id="3bb06-119">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="3bb06-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="3bb06-120">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="3bb06-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
