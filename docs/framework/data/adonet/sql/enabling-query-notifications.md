---
title: Włączanie powiadomień o zapytaniach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 84048a3fba2b32b1ae745160e2b405c04b738c65
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040225"
---
# <a name="enabling-query-notifications"></a>Włączanie powiadomień o zapytaniach
Aplikacje korzystające z powiadomień o zapytaniach mają wspólny zestaw wymagań. Źródło danych musi być poprawnie skonfigurowane do obsługi powiadomień zapytań SQL, a użytkownik musi mieć odpowiednie uprawnienia po stronie klienta i serwera.  
  
 Aby używać powiadomień o zapytaniach, musisz:  
  
- Włącz powiadomienia o zapytaniach dla bazy danych.  
  
- Upewnij się, że identyfikator użytkownika użyty do nawiązania połączenia z bazą danych ma wymagane uprawnienia.  
  
- Użyj obiektu <xref:System.Data.SqlClient.SqlCommand>, aby wykonać prawidłową instrukcję SELECT ze skojarzonym obiektem powiadomienia — <xref:System.Data.SqlClient.SqlDependency> lub <xref:System.Data.Sql.SqlNotificationRequest>.  
  
- Podaj kod, aby przetworzyć powiadomienie, jeśli monitorowane zmiany.  
  
## <a name="query-notifications-requirements"></a>Wymagania dotyczące powiadomień o zapytaniach  
 Powiadomienia o zapytaniach są obsługiwane tylko w przypadku instrukcji SELECT, które spełniają określone wymagania. Poniższa tabela zawiera linki do dokumentacji Service Broker i powiadomień o zapytaniach w temacie SQL Server Books Online.  
  
 **Dokumentacja SQL Server**  
  
- [Tworzenie zapytania dla powiadomienia](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Zagadnienia dotyczące zabezpieczeń Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Zabezpieczenia i ochrona (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Zagadnienia dotyczące zabezpieczeń dla usług powiadomień](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Uprawnienia do powiadomień o zapytaniach](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Zagadnienia międzynarodowe dotyczące Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Zagadnienia dotyczące projektowania rozwiązań (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Przewodnik dewelopera (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Włączanie powiadomień o zapytaniach w celu uruchomienia przykładowego kodu  
 Aby włączyć Service Broker w bazie danych **AdventureWorks** przy użyciu SQL Server Management Studio, wykonaj następującą instrukcję Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Aby przykłady powiadomień o zapytaniach działały prawidłowo, należy wykonać następujące instrukcje języka Transact-SQL na serwerze bazy danych.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Uprawnienia do wysyłania zapytań  
 Użytkownicy, którzy uruchamiają polecenia żądające powiadomienia, muszą mieć na serwerze uprawnienia do bazy danych powiadomień o zapytaniach dotyczących subskrypcji.  
  
 Kod po stronie klienta, który działa w ramach częściowej sytuacji zaufania, wymaga <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Poniższy kod tworzy obiekt <xref:System.Data.SqlClient.SqlClientPermission>, ustawiając <xref:System.Security.Permissions.PermissionState> do <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> wymusi <xref:System.Security.SecurityException> w czasie wykonywania, jeśli wszyscy wywołujący znajdujący się wyżej w stosie wywołań nie uzyskali uprawnienia.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Wybieranie obiektu powiadomienia  
 Interfejs API powiadomień o zapytaniach zawiera dwa obiekty do przetwarzania powiadomień: <xref:System.Data.SqlClient.SqlDependency> i <xref:System.Data.Sql.SqlNotificationRequest>. Ogólnie rzecz biorąc większość aplikacji non-ASP.NET powinna używać obiektu <xref:System.Data.SqlClient.SqlDependency>. Aplikacje ASP.NET powinny używać <xref:System.Web.Caching.SqlCacheDependency>wyższego poziomu, które zawijają <xref:System.Data.SqlClient.SqlDependency> i udostępniają strukturę służącą do administrowania obiektami powiadomień i pamięci podręcznej.  
  
### <a name="using-sqldependency"></a>Korzystanie z elementu SqlDependency  
 Aby można było używać <xref:System.Data.SqlClient.SqlDependency>, Service Broker musi być włączona dla używanej bazy danych SQL Server, a użytkownicy muszą mieć uprawnienia do odbierania powiadomień. Obiekty Service Broker, takie jak Kolejka powiadomień, są wstępnie zdefiniowane.  
  
 Ponadto <xref:System.Data.SqlClient.SqlDependency> automatycznie uruchamia wątek roboczy, aby przetwarzać powiadomienia w miarę ich ogłaszania w kolejce; analizuje również komunikat Service Broker, uwidaczniając informacje jako dane argumentu zdarzenia. należy zainicjować <xref:System.Data.SqlClient.SqlDependency>, wywołując metodę `Start` w celu ustanowienia zależności z bazą danych. Jest to metoda statyczna, która musi być wywoływana tylko raz podczas inicjowania aplikacji dla wszystkich wymaganych połączeń z bazą danych. Metoda `Stop` powinna być wywoływana podczas kończenia aplikacji dla każdego połączenia zależności, które zostało wykonane.  
  
### <a name="using-sqlnotificationrequest"></a>Korzystanie z SqlNotificationRequest  
 Z kolei <xref:System.Data.Sql.SqlNotificationRequest> wymaga zaimplementowania całej infrastruktury nasłuchiwania. Ponadto należy zdefiniować wszystkie pomocnicze obiekty Service Broker, takie jak kolejka, usługa i typy komunikatów obsługiwane przez kolejkę. To podejście ręczne jest przydatne, jeśli aplikacja wymaga specjalnych komunikatów powiadomień lub zachowań powiadomień lub jeśli aplikacja jest częścią aplikacji o większej Service Broker.  
  
## <a name="see-also"></a>Zobacz także

- [Powiadomienia zapytań w programie SQL Server](query-notifications-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
