---
title: N-warstwowe i zdalne aplikacje za pomocą LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 614adf9e00f912e0dddb6674fe4c4ab329f652c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734545"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-warstwowe i zdalne aplikacje za pomocą LINQ to SQL
Można utworzyć aplikacji n warstwowa lub wielowarstwowa, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Zazwyczaj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontekst danych, klas jednostek i logiki budowa zapytania znajdują się w warstwie środkowej jako warstwa dostępu do danych (DAL). Logika biznesowa i trwałe dane mogą być implementowane całkowicie w klasy częściowe i metody jednostek i kontekst danych, lub może być implementowana w osobnych klas.

 Warstwa prezentacji lub klient wywołuje metody na interfejsie zdalnego warstwy środkowej i warstwy DAL w danej warstwie wykona zapytań lub procedur przechowywanych, które są mapowane do <xref:System.Data.Linq.DataContext> metody. Warstwa środkowa zwraca dane do klientów zwykle jako XML reprezentacje obiektów lub obiekty serwerów proxy.

 W środkowej warstwie jednostki są tworzone przez kontekst danych, który śledzi ich stan i zarządza odroczone ładowanie z i przesyłanie zmian do bazy danych. Te jednostki są "dołączone" do `DataContext`. Jednak po jednostki są wysyłane do innej warstwy za pomocą serializacji, stają się one odłączone, co oznacza, że `DataContext` już służy do śledzenia stanu. Jednostki, które klient wysyła aktualizacje musi być ponownie dołączyć do kontekstu danych przed [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można przesłać zmian w bazie danych. Klient jest odpowiedzialny za zapewnienie oryginalnych wartości i/lub sygnatury czasowe z powrotem do warstwy środkowej, jeśli są wymagane w celu pomyślnych kontroli współbieżności.

 W aplikacjach ASP.NET <xref:System.Web.UI.WebControls.LinqDataSource> zarządza większość tę złożoność. Aby uzyskać więcej informacji, zobacz [NIB: Omówienie kontrolki serwera sieci Web LinqDataSource](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).

## <a name="additional-resources"></a>Dodatkowe zasoby
 Aby uzyskać więcej informacji o sposobie wdrażania aplikacji n warstwowej, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zobacz następujące tematy:

-   [N-warstwowa LINQ to SQL z użyciem ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)

-   [N-warstwowa LINQ to SQL z użyciem usług internetowych](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md) 

-   [Implementowanie N-warstwowej logiki biznesowej](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)

-   [Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Aby uzyskać więcej informacji na temat aplikacji n warstwowych, które używają zestawów danych ADO.NET, zobacz [Praca z zestawami danych w aplikacjach n warstwowych](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Zobacz także
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
