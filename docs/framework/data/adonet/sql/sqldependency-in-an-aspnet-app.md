---
title: Element SqlDependency w aplikacji ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 51df8ad695b3e59b368499d35ac76cc7ac0cd6e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363367"
---
# <a name="sqldependency-in-an-aspnet-application"></a>Element SqlDependency w aplikacji ASP.NET
W przykładzie w tej sekcji pokazano sposób użycia <xref:System.Data.SqlClient.SqlDependency> pośrednio, wykorzystując ASP.NET <xref:System.Web.Caching.SqlCacheDependency> obiektu. <xref:System.Web.Caching.SqlCacheDependency> Obiekt używa <xref:System.Data.SqlClient.SqlDependency> do nasłuchiwania powiadomienia i poprawnie zaktualizować pamięci podręcznej.  
  
> [!NOTE]
>  W przykładowym kodzie przyjęto założenie, że włączono powiadomień o zapytaniach przez wykonywanie skryptów w [włączania powiadomień o zapytaniach](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>O przykładowej aplikacji  
 Przykładowa aplikacja korzysta z pojedynczą stroną sieci Web ASP.NET do wyświetlenia informacji o produkcie z **AdventureWorks** bazy danych programu SQL Server w <xref:System.Web.UI.WebControls.GridView> formantu. Podczas ładowania strony kod zapisuje bieżący czas na <xref:System.Web.UI.WebControls.Label> formantu. Następnie definiuje <xref:System.Web.Caching.SqlCacheDependency> obiektu i ustawia właściwości <xref:System.Web.Caching.Cache> obiekt, aby przechowywać dane pamięci podręcznej przez maksymalnie trzy minuty. Następnie kod nawiązuje połączenie z bazą danych i pobiera dane. Po załadowaniu strony i działa aplikacja ASP.NET będzie pobierać dane z pamięci podręcznej, który można zweryfikować, biorąc pod uwagę czas na stronie nie ulega zmianie. Jeśli monitorowana zmieniają się dane, ASP.NET unieważnia pamięci podręcznej i ponownie wypełnij `GridView` formantu o nowe dane, aktualizowanie godziny wyświetlanych w `Label` formantu.  
  
## <a name="creating-the-sample-application"></a>Tworzenie przykładowej aplikacji  
 Wykonaj następujące kroki, aby utworzyć i uruchomić przykładową aplikację:  
  
1.  Utwórz nową witrynę sieci Web programu ASP.NET.  
  
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
  
5.  Dodaj dwie metody pomocnika `GetConnectionString` i `GetSQL`. Określone parametry połączenia używane zintegrowane zabezpieczenia. Należy sprawdzić, czy używane konto ma uprawnienia niezbędne bazy danych oraz że przykładowa baza danych, **AdventureWorks**, ma włączone powiadomienia. Aby uzyskać więcej informacji, zobacz [specjalne uwagi dotyczące podczas za pomocą powiadomień o zapytaniach](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testowanie aplikacji  
 Aplikacja przechowuje dane wyświetlane w formularzu sieci Web i odświeża go co trzy minuty, jeśli nic się nie dzieje. Jeśli nastąpi zmiana w bazie danych, natychmiast odświeżania pamięci podręcznej. Uruchom aplikację w programie Visual Studio, który wyświetla stronę w przeglądarce. Czas odświeżania pamięci podręcznej wyświetlany wskazuje, kiedy ostatniego odświeżania pamięci podręcznej. Odczekaj trzy minut, a następnie odśwież stronę, co powoduje wystąpienie zdarzenia odświeżania strony. Należy pamiętać, że czas wyświetlany na stronie uległ zmianie. Po odświeżeniu strony w mniej niż trzy minuty, godziny widocznej na stronie jest taka sama.  
  
 Teraz zaktualizować dane w bazie danych, za pomocą polecenia AKTUALIZUJ języka Transact-SQL i Odśwież stronę. Teraz wyświetlany czas wskazuje, że pamięć podręczna została odświeżona przy użyciu nowych danych z bazy danych. Należy pamiętać, że chociaż pamięci podręcznej jest aktualizowany, wyświetlany na stronie czas nie zmienia się, dopóki nie wystąpi zdarzenie ogłaszania zwrotnego strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
