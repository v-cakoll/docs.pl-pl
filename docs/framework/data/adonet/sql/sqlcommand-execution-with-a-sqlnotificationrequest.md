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
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest

Program <xref:System.Data.SqlClient.SqlCommand> można skonfigurować tak, aby generował powiadomienie, gdy zmiany danych po ich pobraniu z serwera, a zestaw wynikowy będzie inny, jeśli zapytanie zostało wykonane ponownie. Jest to przydatne w scenariuszach, w których chcesz użyć niestandardowych kolejek powiadomień na serwerze lub gdy nie chcesz obsługiwać obiektów na żywo.

## <a name="creating-the-notification-request"></a>Tworzenie żądania powiadomienia

Za pomocą <xref:System.Data.Sql.SqlNotificationRequest> obiektu można utworzyć żądanie powiadomienia przez powiązanie go `SqlCommand` z obiektem. Po utworzeniu żądania nie jest już potrzebny `SqlNotificationRequest` obiekt. Możesz wysyłać zapytania do kolejki, aby otrzymywać powiadomienia i odpowiednio reagować. Powiadomienia mogą wystąpić nawet wtedy, gdy aplikacja zostanie wyłączona, a następnie ponownie uruchomiona.

Gdy wykonywane jest polecenie skojarzone z powiadomieniem, wszelkie zmiany w oryginalnym zestawie wyników będą wysyłać komunikat do kolejki SQL Server, która została skonfigurowana w żądaniu powiadomienia.

Jak sondować kolejkę SQL Server i interpretować komunikat charakterystyczny dla aplikacji. Aplikacja odpowiada za sondowanie kolejki i reaguje na podstawie zawartości wiadomości.

> [!NOTE]
> W przypadku korzystania z SQL Server żądań <xref:System.Data.SqlClient.SqlDependency>powiadomień w programie należy utworzyć własną nazwę kolejki zamiast korzystać z domyślnej nazwy usługi.

Nie ma nowych elementów zabezpieczeń po stronie klienta dla programu <xref:System.Data.Sql.SqlNotificationRequest>. Jest to przede wszystkim funkcja serwera, a serwer utworzył specjalne uprawnienia wymagane przez użytkowników do żądania powiadomienia.

### <a name="example"></a>Przykład

Poniższy fragment kodu ilustruje sposób tworzenia <xref:System.Data.Sql.SqlNotificationRequest> i kojarzenia go <xref:System.Data.SqlClient.SqlCommand>z.

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

## <a name="see-also"></a>Zobacz także

- [Powiadomienia zapytań w programie SQL Server](query-notifications-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
