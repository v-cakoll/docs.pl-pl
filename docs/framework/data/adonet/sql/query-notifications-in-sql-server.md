---
title: Powiadomienia zapytań w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 94171c8dac59fc17b0dd699d87fc043651fa5b7a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791772"
---
# <a name="query-notifications-in-sql-server"></a>Powiadomienia zapytań w programie SQL Server
W oparciu o infrastrukturę Service Broker powiadomienia o zapytaniach umożliwiają powiadamianie aplikacji o zmianach danych. Ta funkcja jest szczególnie przydatna w przypadku aplikacji, które udostępniają pamięć podręczną informacji z bazy danych, takiej jak aplikacja sieci Web, i należy powiadamiać o zmianach danych źródłowych.  
  
 Istnieją trzy sposoby implementacji powiadomień o zapytaniach przy użyciu ADO.NET:  
  
1. Implementacja niskiego poziomu jest dostarczana przez `SqlNotificationRequest` klasę, która udostępnia funkcje po stronie serwera, co umożliwia wykonywanie poleceń z żądaniem powiadomienia.  
  
2. Implementacja wysokiego poziomu jest dostarczana przez `SqlDependency` klasę, która jest klasą, która zapewnia abstrakcję wysokiego poziomu funkcji powiadomień między aplikacją źródłową i SQL Server, umożliwiając użycie zależności do wykrywania zmian w Server. W większości przypadków jest to najprostszy i najbardziej efektywny sposób, aby wykorzystać możliwości SQL Server powiadomień przez zarządzane aplikacje klienckie przy użyciu Dostawca danych .NET Framework dla SQL Server.  
  
3. Ponadto aplikacje sieci Web skompilowane przy użyciu ASP.NET 2,0 lub nowszej mogą używać `SqlCacheDependency` klas pomocnika.  
  
 Powiadomienia o zapytaniach są używane w przypadku aplikacji, które wymagają odświeżenia wyświetlania lub buforowania w odpowiedzi na zmiany danych bazowych. Microsoft SQL Server umożliwia aplikacjom .NET Framework wysyłanie polecenia do SQL Server i żądanie powiadomienia, jeśli wykonanie tego samego polecenia spowoduje wygenerowanie zestawów wynikowych innych niż pobrane początkowo. Powiadomienia generowane na serwerze są wysyłane przez kolejki, aby można je było przetworzyć później.  
  
 Możesz skonfigurować powiadomienia dla instrukcji SELECT i EXECUTE. Przy użyciu instrukcji EXECUTE SQL Server rejestruje powiadomienie dla wykonywanego polecenia, a nie samą instrukcję EXECUTE. Polecenie musi spełniać wymagania i ograniczenia dotyczące instrukcji SELECT. Gdy polecenie rejestrujące powiadomienie zawiera więcej niż jedną instrukcję, aparat bazy danych tworzy powiadomienie dla każdej instrukcji w partii.  
  
 Jeśli tworzysz aplikację, w której potrzebujesz niezawodnych powiadomień podrzędnych w przypadku zmiany danych, zapoznaj się z sekcją **Planowanie wydajnej strategii powiadomień o zapytaniach** i **alternatywy do wysyłania zapytań dotyczących powiadomień** w [przypadku planowania Temat powiadomień](https://go.microsoft.com/fwlink/?LinkId=211984) w SQL Server książki online. Aby uzyskać więcej informacji na temat powiadomień o zapytaniach i SQL Server Service Broker, zobacz następujące linki do tematów w temacie SQL Server Books Online.  
  
 **Dokumentacja SQL Server**  
  
- [Korzystanie z powiadomień o zapytaniach](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Tworzenie zapytania dla powiadomienia](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Programowanie (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Przewodnik dewelopera (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Włączanie powiadomień o zapytaniach](enabling-query-notifications.md)  
 W tym artykule omówiono sposób używania powiadomień o zapytaniach, w tym wymagania dotyczące włączania i korzystania z nich.  
  
 [Element SqlDependency w aplikacji ASP.NET](sqldependency-in-an-aspnet-app.md)  
 Pokazuje, jak używać powiadomień o zapytaniach z aplikacji ASP.NET.  
  
 [Wykrywanie zmian za pomocą elementu SqlDependency](detecting-changes-with-sqldependency.md)  
 Pokazuje, w jaki sposób wykryć, kiedy wyniki zapytania będą inne niż te, które zostały pierwotnie odebrane.  
  
 [Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Demonstruje Konfigurowanie <xref:System.Data.SqlClient.SqlCommand> obiektu do pracy z powiadomieniem o zapytaniach.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <xref:System.Data.Sql.SqlNotificationRequest> Opisuje klasę i wszystkich jej członków.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <xref:System.Data.SqlClient.SqlDependency> Opisuje klasę i wszystkich jej członków.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <xref:System.Web.Caching.SqlCacheDependency> Opisuje klasę i wszystkich jej członków.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
