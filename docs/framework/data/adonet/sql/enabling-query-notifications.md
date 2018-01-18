---
title: "Włączanie powiadomień o zapytaniach"
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
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c7b02ba7959a5cfc2205222655460026847c3098
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="b4b6e-102">Włączanie powiadomień o zapytaniach</span><span class="sxs-lookup"><span data-stu-id="b4b6e-102">Enabling Query Notifications</span></span>
<span data-ttu-id="b4b6e-103">Aplikacje używające powiadomień o zapytaniach mają wspólny zbiór wymagań.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="b4b6e-104">Źródło danych musi być poprawnie skonfigurowany do obsługi powiadomień kwerendy SQL, a użytkownik musi mieć odpowiednie uprawnienia po stronie klienta i po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="b4b6e-105">Aby użyć powiadomień o zapytaniach się, że należy:</span><span class="sxs-lookup"><span data-stu-id="b4b6e-105">To use query notifications you must:</span></span>  
  
-   <span data-ttu-id="b4b6e-106">Włącz powiadomienia kwerendy dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-106">Enable query notifications for your database.</span></span>  
  
-   <span data-ttu-id="b4b6e-107">Upewnij się, że identyfikator użytkownika używane do łączenia z bazą danych ma odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
-   <span data-ttu-id="b4b6e-108">Użyj <xref:System.Data.SqlClient.SqlCommand> obiekt, aby wykonać poprawną instrukcją SELECT z obiektem skojarzony powiadomienia — albo <xref:System.Data.SqlClient.SqlDependency> lub <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
-   <span data-ttu-id="b4b6e-109">Podaj kod w celu przetworzenia powiadomienia, jeśli monitorowane dane zmian.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="b4b6e-110">Wymagania dotyczące powiadomień kwerendy</span><span class="sxs-lookup"><span data-stu-id="b4b6e-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="b4b6e-111">Liczba powiadomień o zapytaniach są obsługiwane tylko dla instrukcji SELECT, które spełniają określone wymagania.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="b4b6e-112">Poniższa tabela zawiera linki do dokumentacji programu Service Broker i powiadomień o zapytaniach w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="b4b6e-113">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="b4b6e-113">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="b4b6e-114">Tworzenie zapytania o powiadomienie</span><span class="sxs-lookup"><span data-stu-id="b4b6e-114">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="b4b6e-115">Zagadnienia dotyczące zabezpieczeń dla programu Service Broker</span><span class="sxs-lookup"><span data-stu-id="b4b6e-115">Security Considerations for Service Broker</span></span>](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [<span data-ttu-id="b4b6e-116">Zabezpieczenia i ochrona (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="b4b6e-116">Security and Protection (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [<span data-ttu-id="b4b6e-117">Zagadnienia dotyczące zabezpieczeń dla usług powiadomień</span><span class="sxs-lookup"><span data-stu-id="b4b6e-117">Security Considerations for Notifications Services</span></span>](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [<span data-ttu-id="b4b6e-118">Kwerenda powiadomienia uprawnień</span><span class="sxs-lookup"><span data-stu-id="b4b6e-118">Query Notification Permissions</span></span>](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [<span data-ttu-id="b4b6e-119">Międzynarodowe uwagi dotyczące programu Service Broker</span><span class="sxs-lookup"><span data-stu-id="b4b6e-119">International Considerations for Service Broker</span></span>](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [<span data-ttu-id="b4b6e-120">Zagadnienia dotyczące projektowania rozwiązania (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="b4b6e-120">Solution Design Considerations (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [<span data-ttu-id="b4b6e-121">Centrum usługi Broker Developer informacyjne</span><span class="sxs-lookup"><span data-stu-id="b4b6e-121">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="b4b6e-122">Przewodnik dewelopera usługi (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="b4b6e-122">Developer's Guide (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="b4b6e-123">Włączanie powiadomień kwerendy uruchamiać kod przykładowy</span><span class="sxs-lookup"><span data-stu-id="b4b6e-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="b4b6e-124">Aby włączyć brokera usługi na **AdventureWorks** bazy danych przy użyciu programu SQL Server Management Studio, należy wykonać następującą instrukcję Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="b4b6e-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="b4b6e-125">Dla przykładów powiadomień kwerendy do poprawnego działania należy wykonać następujące instrukcje języka Transact-SQL na serwerze bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="b4b6e-126">Kwerenda powiadomienia uprawnień</span><span class="sxs-lookup"><span data-stu-id="b4b6e-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="b4b6e-127">Użytkownicy, którzy wykonywania poleceń żąda powiadomienia musi mieć SUBSKRYPCJI powiadomień o ZAPYTANIACH bazy danych uprawnienia na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="b4b6e-128">Kod po stronie klienta, który jest uruchamiany w przypadku częściowej relacji zaufania wymaga <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="b4b6e-129">Poniższy kod tworzy <xref:System.Data.SqlClient.SqlClientPermission> obiektu ustawienie <xref:System.Security.Permissions.PermissionState> do <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="b4b6e-130"><xref:System.Security.CodeAccessPermission.Demand%2A> Wymusi <xref:System.Security.SecurityException> w czasie wykonywania, jeśli wszystkie obiekty wywołujące wyżej w stosie wywołań nie przyznano uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="b4b6e-131">Wybieranie obiektu powiadomienia</span><span class="sxs-lookup"><span data-stu-id="b4b6e-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="b4b6e-132">API powiadomienia kwerendy udostępnia dwa obiekty do przetworzenia powiadomienia: <xref:System.Data.SqlClient.SqlDependency> i <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="b4b6e-133">Ogólnie rzecz biorąc, należy użyć większości aplikacji ASP.NET z systemem innym niż <xref:System.Data.SqlClient.SqlDependency> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="b4b6e-134">Aplikacji ASP.NET należy używać wyższego poziomu <xref:System.Web.Caching.SqlCacheDependency>, który opakowuje <xref:System.Data.SqlClient.SqlDependency> i zapewnia platformę zarządzania obiektów powiadomień i pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="b4b6e-135">Korzystania z elementu SqlDependency</span><span class="sxs-lookup"><span data-stu-id="b4b6e-135">Using SqlDependency</span></span>  
 <span data-ttu-id="b4b6e-136">Aby użyć <xref:System.Data.SqlClient.SqlDependency>, Service Broker musi być włączona dla bazy danych programu SQL Server używany, a użytkownicy muszą mieć uprawnienia do odbierania powiadomień.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="b4b6e-137">Jest wstępnie zdefiniowanych obiektów brokera usług, takich jak kolejka powiadomień.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="b4b6e-138">Ponadto <xref:System.Data.SqlClient.SqlDependency> automatycznie spowoduje uruchomienie procesu roboczego wątku przetwarzania powiadomień ogłoszone do kolejki, a także analizuje komunikatów programu Service Broker, ujawnienia informacji jako dane argument zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="b4b6e-139"><xref:System.Data.SqlClient.SqlDependency>musi zostać zainicjowany przez wywołanie metody `Start` metodę ustanawiania zależności w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="b4b6e-140">To jest metodą statyczną, który musi zostać wywołana tylko raz podczas inicjowania aplikacji dla każdego połączenia bazy danych, wymagane.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="b4b6e-141">`Stop` Metoda powinna być wywoływana po zakończeniu aplikacji dla każdego połączenia zależności, która została wprowadzona.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="b4b6e-142">Przy użyciu SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="b4b6e-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="b4b6e-143">Z kolei <xref:System.Data.Sql.SqlNotificationRequest> wymaga wykonania całej infrastruktury nasłuchiwania samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="b4b6e-144">Ponadto muszą być zdefiniowane wszystkie pomocnicze obiektów brokera usług takich jak kolejki, usługi i typy obsługiwane przez kolejkę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="b4b6e-145">Ta metoda ręczna jest przydatne, jeśli aplikacja wymaga specjalnych powiadomień lub zachowania powiadomień, czy aplikacja jest częścią większej aplikacji programu Service Broker.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b6e-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4b6e-146">See Also</span></span>  
 [<span data-ttu-id="b4b6e-147">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4b6e-147">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="b4b6e-148">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b4b6e-148">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
