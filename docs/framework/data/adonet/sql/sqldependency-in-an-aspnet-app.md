---
title: Element SqlDependency w aplikacji ASP.NET
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
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8c63118db5333158feb596a534e01f922473cd7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="526c9-102">Element SqlDependency w aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="526c9-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="526c9-103">W przykładzie w tej sekcji pokazano sposób użycia <xref:System.Data.SqlClient.SqlDependency> pośrednio, wykorzystując ASP.NET <xref:System.Web.Caching.SqlCacheDependency> obiektu.</span><span class="sxs-lookup"><span data-stu-id="526c9-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="526c9-104"><xref:System.Web.Caching.SqlCacheDependency> Obiekt używa <xref:System.Data.SqlClient.SqlDependency> do nasłuchiwania powiadomienia i poprawnie zaktualizować pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="526c9-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="526c9-105">W przykładowym kodzie przyjęto założenie, że włączono powiadomień o zapytaniach przez wykonywanie skryptów w [włączania powiadomień o zapytaniach](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="526c9-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="526c9-106">O przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="526c9-106">About the Sample Application</span></span>  
 <span data-ttu-id="526c9-107">Przykładowa aplikacja korzysta z pojedynczą stroną sieci Web ASP.NET do wyświetlenia informacji o produkcie z **AdventureWorks** bazy danych programu SQL Server w <xref:System.Web.UI.WebControls.GridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="526c9-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="526c9-108">Podczas ładowania strony kod zapisuje bieżący czas na <xref:System.Web.UI.WebControls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="526c9-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="526c9-109">Następnie definiuje <xref:System.Web.Caching.SqlCacheDependency> obiektu i ustawia właściwości <xref:System.Web.Caching.Cache> obiekt, aby przechowywać dane pamięci podręcznej przez maksymalnie trzy minuty.</span><span class="sxs-lookup"><span data-stu-id="526c9-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="526c9-110">Następnie kod nawiązuje połączenie z bazą danych i pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="526c9-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="526c9-111">Po załadowaniu strony i działa aplikacja ASP.NET będzie pobierać dane z pamięci podręcznej, który można zweryfikować, biorąc pod uwagę czas na stronie nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="526c9-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="526c9-112">Jeśli monitorowana zmieniają się dane, ASP.NET unieważnia pamięci podręcznej i ponownie wypełnij `GridView` formantu o nowe dane, aktualizowanie godziny wyświetlanych w `Label` formantu.</span><span class="sxs-lookup"><span data-stu-id="526c9-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="526c9-113">Tworzenie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="526c9-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="526c9-114">Wykonaj następujące kroki, aby utworzyć i uruchomić przykładową aplikację:</span><span class="sxs-lookup"><span data-stu-id="526c9-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="526c9-115">Utwórz nową witrynę sieci Web programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="526c9-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="526c9-116">Dodaj <xref:System.Web.UI.WebControls.Label> i <xref:System.Web.UI.WebControls.GridView> formantu do strony Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="526c9-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="526c9-117">Otwórz moduł klasy strony i dodaj następujące dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="526c9-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="526c9-118">Dodaj następujący kod na stronie `Page_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="526c9-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="526c9-119">Dodaj dwie metody pomocnika `GetConnectionString` i `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="526c9-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="526c9-120">Określone parametry połączenia używane zintegrowane zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="526c9-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="526c9-121">Należy sprawdzić, czy używane konto ma uprawnienia niezbędne bazy danych oraz że przykładowa baza danych, **AdventureWorks**, ma włączone powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="526c9-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span> <span data-ttu-id="526c9-122">Aby uzyskać więcej informacji, zobacz [specjalne uwagi dotyczące podczas za pomocą powiadomień o zapytaniach](http://msdn.microsoft.com/en-us/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span><span class="sxs-lookup"><span data-stu-id="526c9-122">For more information, see [Special Considerations When Using Query Notifications](http://msdn.microsoft.com/en-us/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="526c9-123">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="526c9-123">Testing the Application</span></span>  
 <span data-ttu-id="526c9-124">Aplikacja przechowuje dane wyświetlane w formularzu sieci Web i odświeża go co trzy minuty, jeśli nic się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="526c9-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="526c9-125">Jeśli nastąpi zmiana w bazie danych, natychmiast odświeżania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="526c9-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="526c9-126">Uruchom aplikację w programie Visual Studio, który wyświetla stronę w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="526c9-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="526c9-127">Czas odświeżania pamięci podręcznej wyświetlany wskazuje, kiedy ostatniego odświeżania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="526c9-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="526c9-128">Odczekaj trzy minut, a następnie odśwież stronę, co powoduje wystąpienie zdarzenia odświeżania strony.</span><span class="sxs-lookup"><span data-stu-id="526c9-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="526c9-129">Należy pamiętać, że czas wyświetlany na stronie uległ zmianie.</span><span class="sxs-lookup"><span data-stu-id="526c9-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="526c9-130">Po odświeżeniu strony w mniej niż trzy minuty, godziny widocznej na stronie jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="526c9-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="526c9-131">Teraz zaktualizować dane w bazie danych, za pomocą polecenia AKTUALIZUJ języka Transact-SQL i Odśwież stronę.</span><span class="sxs-lookup"><span data-stu-id="526c9-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="526c9-132">Teraz wyświetlany czas wskazuje, że pamięć podręczna została odświeżona przy użyciu nowych danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="526c9-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="526c9-133">Należy pamiętać, że chociaż pamięci podręcznej jest aktualizowany, wyświetlany na stronie czas nie zmienia się, dopóki nie wystąpi zdarzenie ogłaszania zwrotnego strony.</span><span class="sxs-lookup"><span data-stu-id="526c9-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526c9-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="526c9-134">See Also</span></span>  
 [<span data-ttu-id="526c9-135">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="526c9-135">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="526c9-136">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="526c9-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
