---
title: "Włączanie powiadomień o zapytaniach"
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
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 473f1ca54d54a1d852edaed424729778e5a7513d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-query-notifications"></a>Włączanie powiadomień o zapytaniach
Aplikacje używające powiadomień o zapytaniach mają wspólny zbiór wymagań. Źródło danych musi być poprawnie skonfigurowany do obsługi powiadomień kwerendy SQL, a użytkownik musi mieć odpowiednie uprawnienia po stronie klienta i po stronie serwera.  
  
 Aby użyć powiadomień o zapytaniach się, że należy:  
  
-   Włącz powiadomienia kwerendy dla bazy danych.  
  
-   Upewnij się, że identyfikator użytkownika używane do łączenia z bazą danych ma odpowiednie uprawnienia.  
  
-   Użyj <xref:System.Data.SqlClient.SqlCommand> obiekt, aby wykonać poprawną instrukcją SELECT z obiektem skojarzony powiadomienia — albo <xref:System.Data.SqlClient.SqlDependency> lub <xref:System.Data.Sql.SqlNotificationRequest>.  
  
-   Podaj kod w celu przetworzenia powiadomienia, jeśli monitorowane dane zmian.  
  
## <a name="query-notifications-requirements"></a>Wymagania dotyczące powiadomień kwerendy  
 Liczba powiadomień o zapytaniach są obsługiwane tylko dla instrukcji SELECT, które spełniają określone wymagania. Poniższa tabela zawiera linki do dokumentacji programu Service Broker i powiadomień o zapytaniach w dokumentacji SQL Server — książki Online.  
  
 **SQL Server — książki Online**  
  
-   [Tworzenie zapytania o powiadomienie](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Zagadnienia dotyczące zabezpieczeń dla programu Service Broker](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [Zabezpieczenia i ochrona (Service Broker)](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [Zagadnienia dotyczące zabezpieczeń dla usług powiadomień](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [Kwerenda powiadomienia uprawnień](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [Międzynarodowe uwagi dotyczące programu Service Broker](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [Zagadnienia dotyczące projektowania rozwiązania (Service Broker)](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [Centrum usługi Broker Developer informacyjne](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Przewodnik dewelopera usługi (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Włączanie powiadomień kwerendy uruchamiać kod przykładowy  
 Aby włączyć brokera usługi na **AdventureWorks** bazy danych przy użyciu programu SQL Server Management Studio, należy wykonać następującą instrukcję Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Dla przykładów powiadomień kwerendy do poprawnego działania należy wykonać następujące instrukcje języka Transact-SQL na serwerze bazy danych.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Kwerenda powiadomienia uprawnień  
 Użytkownicy, którzy wykonywania poleceń żąda powiadomienia musi mieć SUBSKRYPCJI powiadomień o ZAPYTANIACH bazy danych uprawnienia na serwerze.  
  
 Kod po stronie klienta, który jest uruchamiany w przypadku częściowej relacji zaufania wymaga <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Poniższy kod tworzy <xref:System.Data.SqlClient.SqlClientPermission> obiektu ustawienie <xref:System.Security.Permissions.PermissionState> do <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> Wymusi <xref:System.Security.SecurityException> w czasie wykonywania, jeśli wszystkie obiekty wywołujące wyżej w stosie wywołań nie przyznano uprawnienia.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Wybieranie obiektu powiadomienia  
 API powiadomienia kwerendy udostępnia dwa obiekty do przetworzenia powiadomienia: <xref:System.Data.SqlClient.SqlDependency> i <xref:System.Data.Sql.SqlNotificationRequest>. Ogólnie rzecz biorąc, należy użyć większości aplikacji ASP.NET z systemem innym niż <xref:System.Data.SqlClient.SqlDependency> obiektu. Aplikacji ASP.NET należy używać wyższego poziomu <xref:System.Web.Caching.SqlCacheDependency>, który opakowuje <xref:System.Data.SqlClient.SqlDependency> i zapewnia platformę zarządzania obiektów powiadomień i pamięci podręcznej.  
  
### <a name="using-sqldependency"></a>Korzystania z elementu SqlDependency  
 Aby użyć <xref:System.Data.SqlClient.SqlDependency>, Service Broker musi być włączona dla bazy danych programu SQL Server używany, a użytkownicy muszą mieć uprawnienia do odbierania powiadomień. Jest wstępnie zdefiniowanych obiektów brokera usług, takich jak kolejka powiadomień.  
  
 Ponadto <xref:System.Data.SqlClient.SqlDependency> automatycznie spowoduje uruchomienie procesu roboczego wątku przetwarzania powiadomień ogłoszone do kolejki, a także analizuje komunikatów programu Service Broker, ujawnienia informacji jako dane argument zdarzenia. <xref:System.Data.SqlClient.SqlDependency>musi zostać zainicjowany przez wywołanie metody `Start` metodę ustanawiania zależności w bazie danych. To jest metodą statyczną, który musi zostać wywołana tylko raz podczas inicjowania aplikacji dla każdego połączenia bazy danych, wymagane. `Stop` Metoda powinna być wywoływana po zakończeniu aplikacji dla każdego połączenia zależności, która została wprowadzona.  
  
### <a name="using-sqlnotificationrequest"></a>Przy użyciu SqlNotificationRequest  
 Z kolei <xref:System.Data.Sql.SqlNotificationRequest> wymaga wykonania całej infrastruktury nasłuchiwania samodzielnie. Ponadto muszą być zdefiniowane wszystkie pomocnicze obiektów brokera usług takich jak kolejki, usługi i typy obsługiwane przez kolejkę komunikatów. Ta metoda ręczna jest przydatne, jeśli aplikacja wymaga specjalnych powiadomień lub zachowania powiadomień, czy aplikacja jest częścią większej aplikacji programu Service Broker.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
