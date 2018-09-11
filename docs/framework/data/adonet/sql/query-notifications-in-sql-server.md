---
title: Powiadomienia zapytań w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: c4e58a3eecc18fb5693e9850163533b0a1a6a574
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275291"
---
# <a name="query-notifications-in-sql-server"></a>Powiadomienia zapytań w programie SQL Server
Powiadomienia o zapytaniach utworzonych na podstawie infrastruktury programu Service Broker, Zezwalaj na aplikacje otrzymywać powiadomienia, gdy dane zostały zmienione. Ta funkcja jest szczególnie użyteczna w przypadku aplikacji, które zapewniają pamięci podręcznej informacje z bazy danych, takich jak aplikacji sieci Web i musi być zgłoszone po zmianie źródła danych.  
  
 Istnieją trzy sposoby, które można wdrożyć za pomocą platformy ADO.NET powiadomienia o zapytaniach:  
  
1.  Implementacja niskiego poziomu są dostarczane przez `SqlNotificationRequest` klasę, która udostępnia funkcje po stronie serwera, dzięki któremu można wykonać polecenia z żądaniem powiadomienia.  
  
2.  Wdrożenia wysokiego poziomu są dostarczane przez `SqlDependency` klasy, która jest klasą, która zawiera Abstrakcja wysokiego poziomu funkcjonalności powiadomień od źródłowej aplikacji i programu SQL Server, dzięki czemu można na potrzeby wykrywania zmian w zależności serwer. W większości przypadków jest to najprostszy i najbardziej efektywnym sposobem wykorzystać możliwości powiadomienia programu SQL Server, aplikacji klienckich zarządzanych za pomocą dostawcy danych .NET Framework dla programu SQL Server.  
  
3.  Ponadto sieci Web aplikacji utworzonych za pomocą programu ASP.NET 2.0 lub później za pomocą `SqlCacheDependency` klas pomocniczych.  
  
 Powiadomienia o zapytaniach są używane dla aplikacji, które trzeba odświeżyć Wyświetla lub zapisuje w pamięci podręcznej, w odpowiedzi na zmiany w danych bazowych. Microsoft SQL Server umożliwia aplikacji .NET Framework wysyłać polecenia do programu SQL Server i powiadomień żądania, jeśli wykonywane to samo polecenie dałby w efekcie inne niż pobierana początkowo zestawów wyników. Powiadomienia generowane na serwerze są wysyłane za pośrednictwem kolejki do przetworzenia później.  
  
 Można skonfigurować powiadomienia wybierz pozycję i instrukcjach EXECUTE. Korzystając z instrukcji EXECUTE, programu SQL Server rejestruje powiadomienie wykonano zamiast instrukcji EXECUTE samego polecenia. Polecenie musi spełniać wymagania i ograniczenia dotyczące instrukcji SELECT. Gdy polecenia, który rejestruje powiadomienie zawiera więcej niż jedną instrukcję, aparat bazy danych tworzy powiadomień dla każdej instrukcji w partii.  
  
 Jeśli tworzysz aplikację, gdzie potrzebujesz niezawodnej sekundy powiadomienia po zmianie danych, zapoznaj się z sekcji **planowania strategii wydajne powiadomienia kwerendy** i **alternatywy dla zapytania Powiadomienia** w [planowanie powiadomień](https://go.microsoft.com/fwlink/?LinkId=211984) temat w dokumentacji SQL Server — książki Online. Aby uzyskać więcej informacji na temat powiadomienia o zapytaniach i SQL Server Service Broker zobacz poniższe linki do tematów, w dokumentacji SQL Server — książki Online.  
  
 **SQL Server — książki Online**  
  
-   [Przy użyciu powiadomienia o zapytaniach](https://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Tworzenie zapytania o powiadomienie](https://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Usługa Service Broker](https://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Centrum informacyjne do programu Service Broker dla deweloperów](https://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Programowanie (programu Service Broker)](https://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Włączanie powiadomień o zapytaniach](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 W tym artykule omówiono sposób używania powiadomień kwerendy, w tym wymagania dotyczące włączania i używania ich.  
  
 [Element SqlDependency w aplikacji ASP.NET](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Pokazuje sposób użycia kwerendy powiadomienia z aplikacji ASP.NET.  
  
 [Wykrywanie zmian za pomocą elementu SqlDependency](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Pokazuje, jak wykryć, kiedy wyniki zapytania będą inne niż pierwotnie otrzymały.  
  
 [Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Pokazuje Konfigurowanie <xref:System.Data.SqlClient.SqlCommand> obiektu do pracy z powiadomień o zapytaniach.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 W tym artykule opisano <xref:System.Data.Sql.SqlNotificationRequest> klasy i wszystkich jego składowych.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 W tym artykule opisano <xref:System.Data.SqlClient.SqlDependency> klasy i wszystkich jego składowych.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 W tym artykule opisano <xref:System.Web.Caching.SqlCacheDependency> klasy i wszystkich jego składowych.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
