---
title: "N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 293ebf52b6179ec02f65c81112ee24c9b6322eae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL
Można utworzyć n warstwowa lub wielowarstwowej aplikacji, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Zazwyczaj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontekstu danych, klas jednostek i logiki konstrukcji zapytania znajdują się na warstwę środkową jako warstwa dostępu do danych (DAL). Logika biznesowa i trwałe dane może być całkowicie wdrożonych w klasy częściowe i metody jednostki oraz kontekst danych lub można ją wdrożyć w osobnych klas.  
  
 Warstwa prezentacji lub klienta wywołuje metody interfejsu zdalnego warstwy środkowej i warstwy DAL w tej warstwie wykona zapytania lub procedur składowanych, które są mapowane na <xref:System.Data.Linq.DataContext> metody. Warstwy środkowej zwraca dane do klientów zwykle jako jednostek lub obiektów pośredniczących reprezentacji XML.  
  
 W warstwie środkowej jednostki są tworzone przez kontekst danych, który śledzi ich stan i zarządza ładowanie odłożone z i przesłanie zmian w bazie danych. Te jednostki "dołączonych" do `DataContext`. Jednak po jednostek są wysyłane do innej warstwy za pomocą serializacji, stają się one odłączony, co oznacza, że `DataContext` już służy do śledzenia stanu. Jednostki, które klient wysyła ponownie dla aktualizacji musi zostać ponownie nałożona kontekst danych przed [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można przesłać zmian w bazie danych. Klient jest odpowiedzialny za zapewnienie oryginalnych wartości i/lub sygnatury czasowe z powrotem do warstwy środkowej, jeśli są wymagane dla sprawdzenie optymistycznej współbieżności.  
  
 W aplikacjach ASP.NET <xref:System.Web.UI.WebControls.LinqDataSource> zarządza większość tego złożoności. Aby uzyskać więcej informacji, zobacz [NIB: omówienie kontrolki serwera sieci Web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
 Aby uzyskać więcej informacji na temat sposobu wdrażania aplikacje warstwowe, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zobacz następujące tematy:  
  
-   [N-warstwowa LINQ to SQL z użyciem ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [N-warstwowa LINQ to SQL z użyciem usług internetowych](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [LINQ to SQL ze ściśle powiązanymi aplikacjami klient serwer](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [Implementowanie N-warstwowej logiki biznesowej](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 Aby uzyskać więcej informacji o aplikacjach warstwowych, które używają danych ADO.NET, zobacz [Praca z zestawami danych w aplikacjach warstwowych](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
