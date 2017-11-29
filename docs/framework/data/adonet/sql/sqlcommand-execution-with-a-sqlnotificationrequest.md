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
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Wykonywanie SqlCommand SqlNotificationRequest
A <xref:System.Data.SqlClient.SqlCommand> można skonfigurować, aby wygenerować powiadomienie o zmianie danych po zostaną pobrane z serwera i zestawu wyników będzie inny, jeśli zostały ponownie wykonać zapytanie. Jest to przydatne w scenariuszach, w której chcesz użyć niestandardowych powiadomień kolejek na serwerze lub nie chcesz zachować obiektów na żywo.  
  
## <a name="creating-the-notification-request"></a>Tworzenie żądania powiadomienia  
 Można użyć <xref:System.Data.Sql.SqlNotificationRequest> obiektu do utworzenia żądania powiadomienia przez to powiązanie `SqlCommand` obiektu. Po utworzeniu żądania nie są już potrzebne `SqlNotificationRequest` obiektu. Można zapytania do kolejki w celu powiadomienia i reagowania. Powiadomienia może wystąpić, nawet jeśli aplikacja jest zamknięta i uruchomiony ponownie.  
  
 Po wykonaniu polecenia skojarzone powiadomienia zmiany wprowadzone w wyniku oryginalnego ustawić wyzwalacz wysyłanie wiadomości do kolejki programu SQL Server, który został skonfigurowany w żądaniu powiadomienia.  
  
 Sposób sondowania kolejki programu SQL Server i interpretować wiadomość jest specyficzne dla aplikacji. Aplikacja jest odpowiedzialny za sondowania kolejki i reagowania na podstawie zawartości wiadomości.  
  
> [!NOTE]
>  Korzystając z programu SQL Server żądania powiadomień o <xref:System.Data.SqlClient.SqlDependency>, utworzyć własną nazwę kolejki, zamiast domyślnej nazwy usługi.  
  
 Istnieją żadne nowe elementy zabezpieczeń po stronie klienta dla <xref:System.Data.Sql.SqlNotificationRequest>. To przede wszystkim funkcję serwera, a serwer został utworzony specjalne uprawnienia, które użytkownicy muszą mieć żądania powiadomienie.  
  
### <a name="example"></a>Przykład  
 Poniższy fragment kodu przedstawia sposób tworzenia <xref:System.Data.Sql.SqlNotificationRequest> i skojarz ją z <xref:System.Data.SqlClient.SqlCommand>.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
