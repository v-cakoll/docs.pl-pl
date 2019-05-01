---
title: Włączanie powiadomień o zapytaniach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: a2227b33c7caacdd04c7bf50082bb0cfab7f3302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877620"
---
# <a name="enabling-query-notifications"></a>Włączanie powiadomień o zapytaniach
Aplikacje używające powiadomienia o zapytaniach mają wspólny zbiór wymagań. Źródła danych muszą być prawidłowo skonfigurowane do obsługi powiadomień kwerendy SQL, a użytkownik musi mieć odpowiednie uprawnienia po stronie klienta i po stronie serwera.  
  
 Aby użyć powiadomienia o zapytaniach, należy:  
  
- Włącz powiadomienia kwerendy dla bazy danych.  
  
- Upewnij się, że identyfikator użytkownika, używany do łączenia z bazą danych ma odpowiednie uprawnienia.  
  
- Użyj <xref:System.Data.SqlClient.SqlCommand> obiekt, aby wykonać poprawną instrukcją SELECT z obiektem skojarzone powiadomień — albo <xref:System.Data.SqlClient.SqlDependency> lub <xref:System.Data.Sql.SqlNotificationRequest>.  
  
- Podaj kod, aby przetworzyć powiadomienia, jeśli monitorowane dane zmian.  
  
## <a name="query-notifications-requirements"></a>Wymagania dotyczące powiadomień kwerendy  
 Powiadomienia o zapytaniach są obsługiwane tylko w przypadku instrukcji SELECT, spełniających określone wymagania. Poniższa tabela zawiera linki do dokumentacji programu Service Broker i powiadomienia o zapytaniach w dokumentacji SQL Server — książki Online.  
  
 **Dokumentacja programu SQL Server**  
  
- [Tworzenie zapytania o powiadomienie](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Zagadnienia dotyczące zabezpieczeń dla programu Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Zabezpieczenia i ochrona (programu Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Zagadnienia dotyczące zabezpieczeń dla usługi powiadomień](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Uprawnienia do zapytań powiadomień](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Międzynarodowe uwagi dotyczące programu Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Przewodnik dewelopera usługi (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Włączanie powiadomień kwerendy do uruchomienia przykładowego kodu  
 Aby włączyć brokera usługi na **AdventureWorks** bazy danych przy użyciu programu SQL Server Management Studio, wykonaj następującą instrukcję języka Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Przykłady powiadomień kwerendy by działała poprawnie należy wykonać następujące instrukcje języka Transact-SQL na serwerze bazy danych.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Uprawnienia do zapytań powiadomienia  
 Użytkownicy, którzy wykonaj polecenia żądania powiadomienia musi mieć SUBSKRYBOWANIA powiadomienia o ZAPYTANIACH bazy danych, uprawnienia na serwerze.  
  
 Kod po stronie klienta, która działa w sytuacji, w częściowej relacji zaufania wymaga <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Poniższy kod tworzy <xref:System.Data.SqlClient.SqlClientPermission> obiektu, ustawienie <xref:System.Security.Permissions.PermissionState> do <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> Wymusi <xref:System.Security.SecurityException> w czasie wykonywania, jeśli wszystkie obiekty wywołujące wyżej w stosie wywołań nie przyznano uprawnień.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Wybieranie obiektu powiadomienia  
 Interfejs API powiadomień zapytania udostępnia dwa obiekty można przetworzyć powiadomień: <xref:System.Data.SqlClient.SqlDependency> i <xref:System.Data.Sql.SqlNotificationRequest>. Ogólnie rzecz biorąc, należy użyć większości aplikacji niedotyczący środowiska ASP.NET <xref:System.Data.SqlClient.SqlDependency> obiektu. Aplikacje ASP.NET należy używać wyższego poziomu <xref:System.Web.Caching.SqlCacheDependency>, który opakowuje <xref:System.Data.SqlClient.SqlDependency> i zapewnia platformę do administrowania obiektów powiadomień i pamięci podręcznej.  
  
### <a name="using-sqldependency"></a>Za pomocą elementu SqlDependency  
 Aby użyć <xref:System.Data.SqlClient.SqlDependency>, programu Service Broker musi być włączona dla bazy danych SQL Server używany, a użytkownicy muszą mieć uprawnienia do odbierania powiadomień. Obiekty programu Service Broker, takie jak kolejka powiadomień są wstępnie zdefiniowane.  
  
 Ponadto <xref:System.Data.SqlClient.SqlDependency> automatycznie powoduje uruchomienie procesu roboczego wątku można przetworzyć powiadomień, ponieważ są one opublikowane w kolejce; również analizuje komunikatów programu Service Broker, ujawnienia informacji jako dane argumentu zdarzenia. <xref:System.Data.SqlClient.SqlDependency> musi zostać zainicjowany przez wywołanie metody `Start` metodę ustanawiania zależności z bazą danych. Jest to metoda statyczna, musi być wywołana tylko raz podczas inicjowania aplikacji, dla każdego połączenia z bazą danych wymagane. `Stop` Metoda powinna być wywoływana po zakończeniu aplikacji dla każdego połączenia zależności, który został wykonany.  
  
### <a name="using-sqlnotificationrequest"></a>Za pomocą SqlNotificationRequest  
 Z kolei <xref:System.Data.Sql.SqlNotificationRequest> wymaga implementacji całej infrastruktury nasłuchiwania samodzielnie. Ponadto muszą być zdefiniowane wszystkie pomocnicze obiektów brokera usług takich jak kolejki, usług i typy obsługiwane przez kolejkę komunikatów. To podejście ręcznego jest przydatne, jeśli aplikacja wymaga specjalnych powiadomienia lub zachowania powiadomień, czy aplikacja jest częścią większej aplikacji brokera usług.  
  
## <a name="see-also"></a>Zobacz także

- [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
