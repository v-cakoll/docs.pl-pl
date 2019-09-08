---
title: Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791532"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="875c5-102">Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="875c5-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="875c5-103">Program <xref:System.Data.SqlClient.SqlCommand> można skonfigurować tak, aby generował powiadomienie, gdy zmiany danych po ich pobraniu z serwera, a zestaw wynikowy będzie inny, jeśli zapytanie zostało wykonane ponownie.</span><span class="sxs-lookup"><span data-stu-id="875c5-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="875c5-104">Jest to przydatne w scenariuszach, w których chcesz użyć niestandardowych kolejek powiadomień na serwerze lub gdy nie chcesz obsługiwać obiektów na żywo.</span><span class="sxs-lookup"><span data-stu-id="875c5-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="875c5-105">Tworzenie żądania powiadomienia</span><span class="sxs-lookup"><span data-stu-id="875c5-105">Creating the Notification Request</span></span>

<span data-ttu-id="875c5-106">Za pomocą <xref:System.Data.Sql.SqlNotificationRequest> obiektu można utworzyć żądanie powiadomienia przez powiązanie go `SqlCommand` z obiektem.</span><span class="sxs-lookup"><span data-stu-id="875c5-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="875c5-107">Po utworzeniu żądania nie jest już potrzebny `SqlNotificationRequest` obiekt.</span><span class="sxs-lookup"><span data-stu-id="875c5-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="875c5-108">Możesz wysyłać zapytania do kolejki, aby otrzymywać powiadomienia i odpowiednio reagować.</span><span class="sxs-lookup"><span data-stu-id="875c5-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="875c5-109">Powiadomienia mogą wystąpić nawet wtedy, gdy aplikacja zostanie wyłączona, a następnie ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="875c5-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="875c5-110">Gdy wykonywane jest polecenie skojarzone z powiadomieniem, wszelkie zmiany w oryginalnym zestawie wyników będą wysyłać komunikat do kolejki SQL Server, która została skonfigurowana w żądaniu powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="875c5-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="875c5-111">Jak sondować kolejkę SQL Server i interpretować komunikat charakterystyczny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="875c5-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="875c5-112">Aplikacja odpowiada za sondowanie kolejki i reaguje na podstawie zawartości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="875c5-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="875c5-113">W przypadku korzystania z SQL Server żądań <xref:System.Data.SqlClient.SqlDependency>powiadomień w programie należy utworzyć własną nazwę kolejki zamiast korzystać z domyślnej nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="875c5-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="875c5-114">Nie ma nowych elementów zabezpieczeń po stronie klienta dla programu <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="875c5-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="875c5-115">Jest to przede wszystkim funkcja serwera, a serwer utworzył specjalne uprawnienia wymagane przez użytkowników do żądania powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="875c5-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="875c5-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="875c5-116">Example</span></span>

<span data-ttu-id="875c5-117">Poniższy fragment kodu ilustruje sposób tworzenia <xref:System.Data.Sql.SqlNotificationRequest> i kojarzenia go <xref:System.Data.SqlClient.SqlCommand>z.</span><span class="sxs-lookup"><span data-stu-id="875c5-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
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
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="875c5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="875c5-118">See also</span></span>

- [<span data-ttu-id="875c5-119">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="875c5-119">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="875c5-120">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="875c5-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
