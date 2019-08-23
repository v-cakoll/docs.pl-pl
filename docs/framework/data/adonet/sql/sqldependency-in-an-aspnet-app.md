---
title: Element SqlDependency w aplikacji ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: a93cb9da44985fa29a4975875564b384117ce76f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938454"
---
# <a name="sqldependency-in-an-aspnet-application"></a>Element SqlDependency w aplikacji ASP.NET
W przykładzie w tej sekcji pokazano, jak używać <xref:System.Data.SqlClient.SqlDependency> pośrednio, wykorzystując obiekt ASP.NET <xref:System.Web.Caching.SqlCacheDependency> . <xref:System.Web.Caching.SqlCacheDependency> Obiekt używaobiektudonasłuchiwaniapowiadomieńipoprawnie<xref:System.Data.SqlClient.SqlDependency> zaktualizować pamięć podręczną.  
  
> [!NOTE]
> Przykładowy kod założono, że włączono powiadomienia o zapytaniach przez wykonanie skryptów w temacie [Włączanie powiadomień o](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)zapytaniach.  
  
## <a name="about-the-sample-application"></a>Informacje o aplikacji przykładowej  
 Aplikacja Przykładowa używa pojedynczej strony sieci Web ASP.NET do wyświetlania informacji o produkcie z bazy danych SQL Server AdventureWorks <xref:System.Web.UI.WebControls.GridView> w kontrolce. Po załadowaniu strony kod zapisuje bieżący czas do <xref:System.Web.UI.WebControls.Label> kontrolki. Następnie definiuje <xref:System.Web.Caching.SqlCacheDependency> obiekt i ustawia właściwości <xref:System.Web.Caching.Cache> dla obiektu w celu przechowywania danych w pamięci podręcznej przez maksymalnie trzy minuty. Kod następnie łączy się z bazą danych i pobiera dane. Po załadowaniu strony i uruchomieniu aplikacji ASP.NET pobierze dane z pamięci podręcznej, którą można zweryfikować, zwracając uwagę, że czas na stronie nie ulegnie zmianie. Jeśli monitorowane dane zmieniają się, ASP.NET unieważnia pamięć podręczną i ponownie wypełnia `GridView` kontrolę przy użyciu nowych danych, aktualizując czas wyświetlany `Label` w kontrolce.  
  
## <a name="creating-the-sample-application"></a>Tworzenie przykładowej aplikacji  
 Wykonaj następujące kroki, aby utworzyć i uruchomić przykładową aplikację:  
  
1. Utwórz nową witrynę sieci Web ASP.NET.  
  
2. Dodaj kontrolkę <xref:System.Web.UI.WebControls.Label> <xref:System.Web.UI.WebControls.GridView> i do domyślnej strony. aspx.  
  
3. Otwórz moduł klasy strony i Dodaj następujące dyrektywy:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Dodaj następujący kod do `Page_Load` zdarzenia strony:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. Dodaj dwie metody `GetConnectionString` pomocnika i `GetSQL`. Zdefiniowane parametry połączenia korzystają ze zintegrowanych zabezpieczeń. Musisz sprawdzić, czy konto, którego używasz, ma wymagane uprawnienia do bazy danych i czy Przykładowa baza danych, **AdventureWorks**ma włączone powiadomienia.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testowanie aplikacji  
 Aplikacja buforuje dane wyświetlane w formularzu sieci Web i odświeża je co trzy minuty w przypadku braku aktywności. Jeśli nastąpi zmiana do bazy danych, pamięć podręczna jest odświeżana natychmiast. Uruchom aplikację z programu Visual Studio, która ładuje stronę do przeglądarki. Wyświetlany czas odświeżania pamięci podręcznej wskazuje, kiedy ostatnio odświeżono pamięć podręczną. Odczekaj trzy minuty, a następnie Odśwież stronę, powodując wystąpienie zdarzenia ogłaszania zwrotnego. Zauważ, że czas wyświetlany na stronie został zmieniony. Po odświeżeniu strony w czasie krótszym niż trzy minuty godzina wyświetlana na stronie pozostanie taka sama.  
  
 Teraz zaktualizuj dane w bazie danych przy użyciu polecenia Transact-SQL UPDATE i Odśwież stronę. Czas wyświetlania teraz wskazuje, że pamięć podręczna została odświeżona przy użyciu nowych danych z bazy danych. Należy pamiętać, że mimo że pamięć podręczna jest aktualizowana, czas wyświetlania na stronie nie zmienia się, dopóki nie wystąpi zdarzenie ogłaszania zwrotnego.  
  
## <a name="see-also"></a>Zobacz także

- [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
