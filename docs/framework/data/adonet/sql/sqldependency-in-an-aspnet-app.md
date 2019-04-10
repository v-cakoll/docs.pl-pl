---
title: Element SqlDependency w aplikacji ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 67c1307bb18b3e86e05b56f4853a39f6831ab9cc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313596"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="3b21c-102">Element SqlDependency w aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3b21c-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="3b21c-103">W przykładzie w tej sekcji pokazano sposób użycia <xref:System.Data.SqlClient.SqlDependency> pośrednio, wykorzystując platformę ASP.NET <xref:System.Web.Caching.SqlCacheDependency> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b21c-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="3b21c-104"><xref:System.Web.Caching.SqlCacheDependency> Obiektu używa <xref:System.Data.SqlClient.SqlDependency> do nasłuchiwania powiadomień i poprawnie zaktualizować pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3b21c-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b21c-105">W przykładowym kodzie założono, że włączono powiadomienia o zapytaniach przez wykonywanie skryptów w [Włączanie kwerenda powiadomienia](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="3b21c-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="3b21c-106">Temat przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="3b21c-106">About the Sample Application</span></span>  
 <span data-ttu-id="3b21c-107">Przykładowa aplikacja korzysta z pojedynczej strony sieci Web platformy ASP.NET do wyświetlania informacji o produktach z **AdventureWorks** bazy danych programu SQL Server w <xref:System.Web.UI.WebControls.GridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3b21c-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="3b21c-108">Po załadowaniu strony kodu zapisuje bieżący czas na <xref:System.Web.UI.WebControls.Label> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3b21c-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="3b21c-109">Następnie definiuje <xref:System.Web.Caching.SqlCacheDependency> obiektu i ustawia właściwości <xref:System.Web.Caching.Cache> obiektu do przechowywania danych w pamięci podręcznej dla maksymalnie trzy minuty.</span><span class="sxs-lookup"><span data-stu-id="3b21c-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="3b21c-110">Kod następnie nawiązuje połączenie z bazą danych i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="3b21c-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="3b21c-111">Po załadowaniu strony i której działa aplikacja ASP.NET będzie pobierać dane z pamięci podręcznej, można sprawdzić, biorąc pod uwagę, że czas na stronie nie zmienia.</span><span class="sxs-lookup"><span data-stu-id="3b21c-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="3b21c-112">Jeśli monitorowana zmieniają się dane, ASP.NET unieważnia zawartość pamięci podręcznej i ponownie wypełnić `GridView` sterowania za pomocą najnowszych danych, aktualizowanie godziny widocznej w `Label` kontroli.</span><span class="sxs-lookup"><span data-stu-id="3b21c-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="3b21c-113">Tworzenie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="3b21c-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="3b21c-114">Wykonaj następujące kroki, aby utworzyć i uruchamianie przykładowej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3b21c-114">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="3b21c-115">Utwórz nową witrynę sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3b21c-115">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="3b21c-116">Dodaj <xref:System.Web.UI.WebControls.Label> i <xref:System.Web.UI.WebControls.GridView> formantu do strony Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="3b21c-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="3b21c-117">Otwórz moduł klasy strony i dodaj następujące dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="3b21c-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="3b21c-118">Dodaj następujący kod na stronie `Page_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="3b21c-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="3b21c-119">Dodaj dwie metody pomocnika, `GetConnectionString` i `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="3b21c-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="3b21c-120">Parametry połączenia, definicja używa zintegrowanych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3b21c-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="3b21c-121">Należy sprawdzić, czy konto, którego używasz, ma uprawnienia niezbędne bazy danych oraz że przykładowej bazy danych, **AdventureWorks**, ma włączone powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="3b21c-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="3b21c-122">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3b21c-122">Testing the Application</span></span>  
 <span data-ttu-id="3b21c-123">Aplikacja przechowuje dane wyświetlane w formularzu sieci Web i odświeża jej co trzy minuty, jeśli nic się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="3b21c-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="3b21c-124">W przypadku zmiany w bazie danych, pamięci podręcznej są natychmiast odświeżane.</span><span class="sxs-lookup"><span data-stu-id="3b21c-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="3b21c-125">Uruchom aplikację w programie Visual Studio, który wyświetla stronę w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="3b21c-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="3b21c-126">Czas odświeżania pamięci podręcznej, które są wyświetlane wskazuje, kiedy ostatniego odświeżania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3b21c-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="3b21c-127">Poczekaj trzy minuty, a następnie odśwież stronę, co powoduje wystąpienie zwrotu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3b21c-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="3b21c-128">Należy pamiętać, że została zmieniona podczas wyświetlania na stronie.</span><span class="sxs-lookup"><span data-stu-id="3b21c-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="3b21c-129">Po odświeżeniu strony w mniej niż trzy minuty, godziny widocznej na stronie pozostaną takie same.</span><span class="sxs-lookup"><span data-stu-id="3b21c-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="3b21c-130">Teraz zaktualizować dane w bazie danych, za pomocą polecenia języka Transact-SQL, aktualizacji i Odśwież stronę.</span><span class="sxs-lookup"><span data-stu-id="3b21c-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="3b21c-131">Teraz wyświetlany czas wskazuje, że pamięć podręczna została odświeżona przy użyciu nowych danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3b21c-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="3b21c-132">Pamiętaj, że mimo, że pamięć podręczna jest aktualizowany, podczas wyświetlania na stronie nie zmienia się, dopóki nie wystąpi zdarzenie ogłaszania wstecznego.</span><span class="sxs-lookup"><span data-stu-id="3b21c-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b21c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b21c-133">See also</span></span>

- [<span data-ttu-id="3b21c-134">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="3b21c-134">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="3b21c-135">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="3b21c-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
