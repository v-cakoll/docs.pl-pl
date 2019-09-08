---
title: N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 94ca057da10c3570e85e17b5caec2d86154d8a3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781408"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL
Można tworzyć aplikacje warstwy n lub wielowarstwowe korzystające [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]z programu. Zazwyczaj kontekst danych, klasy jednostek i logika konstruowania zapytania znajdują się w warstwie środkowej jako warstwa dostępu do danych (dal). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Logika biznesowa i wszystkie nietrwałe dane można całkowicie zaimplementować w klasach częściowych i metodach jednostek i kontekście danych albo można je zaimplementować w oddzielnych klasach.

 Klient lub warstwa prezentacji wywołuje metody w interfejsie zdalnym warstwy środkowej, a dal w tej warstwie wykona zapytania lub procedury składowane, które są mapowane na <xref:System.Data.Linq.DataContext> metody. Warstwa środkowa zwraca dane do klientów zazwyczaj jako reprezentacje XML jednostek lub obiektów proxy.

 W warstwie środkowej jednostki są tworzone przez kontekst danych, który śledzi ich stan i zarządza odroczonym ładowaniem z i przesyłaniem zmian do bazy danych. Te jednostki są "dołączone" do `DataContext`. Jednak po wysłaniu jednostek do innej warstwy przy użyciu serializacji stają się one odłączane, co oznacza, `DataContext` że nie śledzi już stanu. Jednostki wysyłane przez klienta z powrotem do aktualizacji muszą zostać ponownie dołączone do kontekstu danych, zanim [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] będą mogły przesłać zmiany do bazy danych. Klient jest odpowiedzialny za dostarczanie oryginalnych wartości i/lub sygnatur czasowych do warstwy środkowej, jeśli są one wymagane do optymistycznych kontroli współbieżności.

 W aplikacjach <xref:System.Web.UI.WebControls.LinqDataSource> ASP.NET zarządza największą z tych złożoności. Aby uzyskać więcej informacji, zobacz [Omówienie kontrolki serwera sieci Web programu LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Dodatkowe zasoby
 Aby uzyskać więcej informacji na temat implementowania aplikacji n-warstwowych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], które korzystają z programu, zobacz następujące tematy:

- [N-warstwowa LINQ to SQL z użyciem ASP.NET](linq-to-sql-n-tier-with-aspnet.md)

- [N-warstwowa LINQ to SQL z użyciem usług internetowych](linq-to-sql-n-tier-with-web-services.md) 

- [Implementowanie N-warstwowej logiki biznesowej](implementing-business-logic-linq-to-sql.md)

- [Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Aby uzyskać więcej informacji na temat aplikacji n-warstwowych, które używają zestawów danych ADO.NET, zobacz [Work with datasetss in aplikacje n-warstwowe](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
