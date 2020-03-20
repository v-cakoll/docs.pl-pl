---
title: N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 6758ae23c25d8e7a4255d0a784cccd1eb404bfe7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174306"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL
Można tworzyć aplikacje n-warstwowe [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]lub wielowarstwowe, które używają . Zazwyczaj kontekst [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] danych, klasy jednostek i logika budowy zapytań znajdują się w warstwie środkowej jako warstwa dostępu do danych (DAL). Logika biznesowa i wszelkie dane nietrwałe mogą być całkowicie zaimplementowane w klasach częściowych i metodach jednostek i kontekstu danych lub mogą być implementowane w oddzielnych klasach.

 Warstwa klienta lub prezentacji wywołuje metody na interfejsie zdalnym warstwy środkowej, a warstwa DAL w <xref:System.Data.Linq.DataContext> tej warstwie będzie wykonywać kwerendy lub procedury przechowywane, które są mapowane na metody. Warstwa środkowa zwraca dane do klientów zazwyczaj jako reprezentacje XML jednostek lub obiektów serwera proxy.

 W warstwie środkowej jednostki są tworzone przez kontekst danych, który śledzi ich stan i zarządza odroczonym ładowaniem i przesyłaniem zmian do bazy danych. Te jednostki są "dołączone" `DataContext`do . Jednak po jednostek są wysyłane do innej warstwy za pośrednictwem `DataContext` serializacji, stają się odłączone, co oznacza, że nie jest już śledzenie ich stanu. Jednostki, które klient wysyła z powrotem do aktualizacji muszą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] być ponownie dołączone do kontekstu danych, zanim będzie można przesłać zmiany do bazy danych. Klient jest odpowiedzialny za dostarczanie oryginalnych wartości i/lub sygnatury czasowe z powrotem do warstwy środkowej, jeśli są to wymagane do optymistycznych kontroli współbieżności.

 W ASP.NET aplikacji <xref:System.Web.UI.WebControls.LinqDataSource> zarządza większość tej złożoności. Aby uzyskać więcej informacji, zobacz [Omówienie kontroli serwera sieci Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Dodatkowe zasoby
 Aby uzyskać więcej informacji na temat implementacji aplikacji n-warstwowych, które używają, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zobacz następujące tematy:

- [N-warstwowa LINQ to SQL z użyciem ASP.NET](linq-to-sql-n-tier-with-aspnet.md)

- [N-warstwowa LINQ to SQL z użyciem usług internetowych](linq-to-sql-n-tier-with-web-services.md)

- [Implementowanie N-warstwowej logiki biznesowej](implementing-business-logic-linq-to-sql.md)

- [Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Aby uzyskać więcej informacji na temat aplikacji n-warstwowych, które używają ADO.NET zestawy danych, zobacz [Praca z zestawami danych w aplikacjach n-warstwowych](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Zobacz też

- [Informacje uzupełniające](background-information.md)
