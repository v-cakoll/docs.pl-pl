---
title: Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 90ec7653f7de931bd8127263643b5467998325b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364470"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest

Element <xref:System.Data.SqlClient.SqlCommand> można skonfigurować, aby wygenerować powiadomienie po zmianie danych, gdy zostaną pobrane z serwera i zestawu wyników będzie inna w przypadku zapytania były wykonywane ponownie. Jest to przydatne w scenariuszach, w której chcesz używać kolejek niestandardowe powiadomienie, na serwerze lub nie chcesz zachować obiektów na żywo.

## <a name="creating-the-notification-request"></a>Tworzenie żądania powiadomienia

Możesz użyć <xref:System.Data.Sql.SqlNotificationRequest> obiektu do utworzenia żądania powiadomienia, tworząc powiązanie do `SqlCommand` obiektu. Po utworzeniu żądania nie są już potrzebne `SqlNotificationRequest` obiektu. Można wykonywać zapytania kolejki w celu powiadomienia i odpowiednio reagować. Powiadomienia może wystąpić, nawet jeśli aplikacja jest zamknięta i uruchomiony ponownie.

Po wykonaniu polecenia z powiadomieniem skojarzone zmiany wprowadzone w wyniku oryginalnego zestawu wyzwalacza wysyłania komunikatu do kolejki programu SQL Server, który został skonfigurowany w żądaniu powiadomienia.

Jak wykonać sondowanie kolejki programu SQL Server i interpretować komunikat jest specyficzne dla aplikacji. Aplikacja jest odpowiedzialna za sondowania kolejki i reagowanie na podstawie zawartości komunikatu.

> [!NOTE]
> Korzystając z programu SQL Server notification żądań z <xref:System.Data.SqlClient.SqlDependency>, Utwórz własną nazwę kolejki, a nie przy użyciu nazwy usługi domyślnego.

Nie ma elementów nowych zabezpieczeń po stronie klienta dla <xref:System.Data.Sql.SqlNotificationRequest>. Jest to głównie funkcji serwera, a serwer został utworzony specjalne uprawnienia, które użytkownicy muszą mieć żądania powiadomienia.

### <a name="example"></a>Przykład

Poniższy fragment kodu przedstawia sposób tworzenia <xref:System.Data.Sql.SqlNotificationRequest> i powiąż ją z <xref:System.Data.SqlClient.SqlCommand>.

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

- [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
