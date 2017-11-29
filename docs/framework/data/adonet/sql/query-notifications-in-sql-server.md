---
title: "Powiadomienia zapytań w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 854407d2e6d1341d5917cc78664c1f653e55fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="9d91f-102">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d91f-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="9d91f-103">Wbudowane w system infrastruktury programu Service Broker, powiadomień o zapytaniach umożliwiają aplikacjom otrzymać powiadomienie, gdy dane zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="9d91f-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="9d91f-104">Ta funkcja jest szczególnie przydatne w przypadku aplikacji, które zapewniają pamięci podręcznej informacje z bazy danych, takich jak aplikacji sieci Web i musi być zgłoszone, gdy źródło danych zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="9d91f-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="9d91f-105">Istnieją trzy sposoby, które można wdrożyć za pomocą ADO.NET powiadomień o zapytaniach:</span><span class="sxs-lookup"><span data-stu-id="9d91f-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="9d91f-106">Niskiego poziomu implementacji jest zapewniana przez `SqlNotificationRequest` klasy, która udostępnia funkcje po stronie serwera, dzięki któremu można wykonać polecenia z żądaniem powiadomień.</span><span class="sxs-lookup"><span data-stu-id="9d91f-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="9d91f-107">Wdrożenia wysokiego poziomu są dostarczane przez `SqlDependency` klasy, która jest klasa, która zapewnia Abstrakcja wysokiego poziomu funkcjonalności powiadomień od źródłowej aplikacji i programu SQL Server, dzięki któremu można użyć do wykrycia zmian w zależności serwer.</span><span class="sxs-lookup"><span data-stu-id="9d91f-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="9d91f-108">W większości przypadków jest to najprostsza i najbardziej efektywny sposób wykorzystać możliwości powiadomienia programu SQL Server przez aplikacje klienckie zarządzane za pomocą dostawcy .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9d91f-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="9d91f-109">Ponadto aplikacje sieci Web w utworzonym przy użyciu składnika ASP.NET 2.0 lub później za pomocą `SqlCacheDependency` klasy pomocy.</span><span class="sxs-lookup"><span data-stu-id="9d91f-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="9d91f-110">Liczba powiadomień o zapytaniach są używane dla aplikacji, które trzeba odświeżyć Wyświetla lub buforuje w odpowiedzi na zmiany w danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9d91f-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="9d91f-111">Microsoft SQL Server umożliwia aplikacji .NET Framework wysyłania polecenia programu SQL Server i powiadomień żądania, jeśli wykonywanie tego samego polecenia wywołałoby inny niż początkowo pobranych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="9d91f-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="9d91f-112">Powiadomień generowanych na serwerze są wysyłane za pośrednictwem kolejek na przetworzenie później.</span><span class="sxs-lookup"><span data-stu-id="9d91f-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="9d91f-113">Można skonfigurować powiadomienia dla wybierz i WYKONAJ instrukcje.</span><span class="sxs-lookup"><span data-stu-id="9d91f-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="9d91f-114">Korzystając z instrukcji EXECUTE, SQL Server rejestruje powiadomień dla polecenia wykonywane zamiast instrukcji EXECUTE sam.</span><span class="sxs-lookup"><span data-stu-id="9d91f-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="9d91f-115">Polecenie musi spełniać wymagania i ograniczenia dotyczące instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d91f-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="9d91f-116">Jeśli polecenie, które rejestruje powiadomienie zawiera więcej niż jedną instrukcję, aparatu bazy danych tworzy powiadomień dla każdej instrukcji w partii.</span><span class="sxs-lookup"><span data-stu-id="9d91f-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="9d91f-117">Jeśli tworzysz aplikację, konieczne niezawodnej sekundę podrzędne powiadomienia po zmianie danych, należy przejrzeć sekcje **planowania strategii wydajne powiadomienia kwerendy** i **alternatywy dla zapytania Powiadomienia** w [planowanie powiadomienia](http://go.microsoft.com/fwlink/?LinkId=211984) tematu w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="9d91f-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="9d91f-118">Aby uzyskać więcej informacji na temat powiadomień o zapytaniach i brokera usług serwera SQL zobacz następujące linki do tematów w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="9d91f-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="9d91f-119">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="9d91f-119">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="9d91f-120">Za pomocą powiadomień o zapytaniach</span><span class="sxs-lookup"><span data-stu-id="9d91f-120">Using Query Notifications</span></span>](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [<span data-ttu-id="9d91f-121">Tworzenie zapytania o powiadomienie</span><span class="sxs-lookup"><span data-stu-id="9d91f-121">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="9d91f-122">Usługa Service Broker</span><span class="sxs-lookup"><span data-stu-id="9d91f-122">Service Broker</span></span>](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [<span data-ttu-id="9d91f-123">Centrum usługi Broker Developer informacyjne</span><span class="sxs-lookup"><span data-stu-id="9d91f-123">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="9d91f-124">Programowanie (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="9d91f-124">Development (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a><span data-ttu-id="9d91f-125">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9d91f-125">In This Section</span></span>  
 [<span data-ttu-id="9d91f-126">Włączanie powiadomień o zapytaniach</span><span class="sxs-lookup"><span data-stu-id="9d91f-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="9d91f-127">W tym artykule omówiono sposób używania powiadomień kwerendy, w tym wymagania dotyczące włączania i używania ich.</span><span class="sxs-lookup"><span data-stu-id="9d91f-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="9d91f-128">Element SqlDependency w aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9d91f-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="9d91f-129">Pokazuje, jak korzystać z zapytania powiadomień w aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9d91f-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="9d91f-130">Wykrywanie zmian z elementu SqlDependency</span><span class="sxs-lookup"><span data-stu-id="9d91f-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="9d91f-131">Demonstracja Wykryj, kiedy wyniki zapytania będą inne niż pierwotnie odebrane.</span><span class="sxs-lookup"><span data-stu-id="9d91f-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="9d91f-132">Wykonywanie SqlCommand SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="9d91f-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="9d91f-133">Pokazuje Konfigurowanie <xref:System.Data.SqlClient.SqlCommand> obiekt do pracy z powiadomienia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9d91f-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d91f-134">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9d91f-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="9d91f-135">W tym artykule opisano <xref:System.Data.Sql.SqlNotificationRequest> klasy i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9d91f-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="9d91f-136">W tym artykule opisano <xref:System.Data.SqlClient.SqlDependency> klasy i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9d91f-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="9d91f-137">W tym artykule opisano <xref:System.Web.Caching.SqlCacheDependency> klasy i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9d91f-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d91f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d91f-138">See Also</span></span>  
 [<span data-ttu-id="9d91f-139">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9d91f-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="9d91f-140">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="9d91f-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
