---
title: Element SqlDependency w aplikacji ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 5465238e4b9deaa13c76cb35122fcaded7acd7f7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736662"
---
# <a name="sqldependency-in-an-aspnet-application"></a>Element SqlDependency w aplikacji ASP.NET
W przykładzie w tej sekcji pokazano sposób użycia <xref:System.Data.SqlClient.SqlDependency> pośrednio, wykorzystując platformę ASP.NET <xref:System.Web.Caching.SqlCacheDependency> obiektu. <xref:System.Web.Caching.SqlCacheDependency> Obiektu używa <xref:System.Data.SqlClient.SqlDependency> do nasłuchiwania powiadomień i poprawnie zaktualizować pamięci podręcznej.  
  
> [!NOTE]
>  W przykładowym kodzie założono, że włączono powiadomienia o zapytaniach przez wykonywanie skryptów w [Włączanie kwerenda powiadomienia](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Temat przykładowej aplikacji  
 Przykładowa aplikacja korzysta z pojedynczej strony sieci Web platformy ASP.NET do wyświetlania informacji o produktach z **AdventureWorks** bazy danych programu SQL Server w <xref:System.Web.UI.WebControls.GridView> kontroli. Po załadowaniu strony kodu zapisuje bieżący czas na <xref:System.Web.UI.WebControls.Label> kontroli. Następnie definiuje <xref:System.Web.Caching.SqlCacheDependency> obiektu i ustawia właściwości <xref:System.Web.Caching.Cache> obiektu do przechowywania danych w pamięci podręcznej dla maksymalnie trzy minuty. Kod następnie nawiązuje połączenie z bazą danych i pobierania danych. Po załadowaniu strony i której działa aplikacja ASP.NET będzie pobierać dane z pamięci podręcznej, można sprawdzić, biorąc pod uwagę, że czas na stronie nie zmienia. Jeśli monitorowana zmieniają się dane, ASP.NET unieważnia zawartość pamięci podręcznej i ponownie wypełnić `GridView` sterowania za pomocą najnowszych danych, aktualizowanie godziny widocznej w `Label` kontroli.  
  
## <a name="creating-the-sample-application"></a>Tworzenie przykładowej aplikacji  
 Wykonaj następujące kroki, aby utworzyć i uruchamianie przykładowej aplikacji:  
  
1.  Utwórz nową witrynę sieci Web platformy ASP.NET.  
  
2.  Dodaj <xref:System.Web.UI.WebControls.Label> i <xref:System.Web.UI.WebControls.GridView> formantu do strony Default.aspx.  
  
3.  Otwórz moduł klasy strony i dodaj następujące dyrektywy:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  Dodaj następujący kod na stronie `Page_Load` zdarzeń:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  Dodaj dwie metody pomocnika, `GetConnectionString` i `GetSQL`. Parametry połączenia, definicja używa zintegrowanych zabezpieczeń. Należy sprawdzić, czy konto, którego używasz, ma uprawnienia niezbędne bazy danych oraz że przykładowej bazy danych, **AdventureWorks**, ma włączone powiadomienia. Aby uzyskać więcej informacji, zobacz [specjalne zagadnienia dotyczące podczas przy użyciu powiadomienia o zapytaniach](https://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testowanie aplikacji  
 Aplikacja przechowuje dane wyświetlane w formularzu sieci Web i odświeża jej co trzy minuty, jeśli nic się nie dzieje. W przypadku zmiany w bazie danych, pamięci podręcznej są natychmiast odświeżane. Uruchom aplikację w programie Visual Studio, który wyświetla stronę w przeglądarce. Czas odświeżania pamięci podręcznej, które są wyświetlane wskazuje, kiedy ostatniego odświeżania pamięci podręcznej. Poczekaj trzy minuty, a następnie odśwież stronę, co powoduje wystąpienie zwrotu zdarzenia. Należy pamiętać, że została zmieniona podczas wyświetlania na stronie. Po odświeżeniu strony w mniej niż trzy minuty, godziny widocznej na stronie pozostaną takie same.  
  
 Teraz zaktualizować dane w bazie danych, za pomocą polecenia języka Transact-SQL, aktualizacji i Odśwież stronę. Teraz wyświetlany czas wskazuje, że pamięć podręczna została odświeżona przy użyciu nowych danych z bazy danych. Pamiętaj, że mimo, że pamięć podręczna jest aktualizowany, podczas wyświetlania na stronie nie zmienia się, dopóki nie wystąpi zdarzenie ogłaszania wstecznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
