---
title: Włączanie powiadomień o zapytaniach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: be9cae6f702b72306875246e874b99e7c79eb113
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743039"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="97728-102">Włączanie powiadomień o zapytaniach</span><span class="sxs-lookup"><span data-stu-id="97728-102">Enabling Query Notifications</span></span>
<span data-ttu-id="97728-103">Aplikacje używające powiadomienia o zapytaniach mają wspólny zbiór wymagań.</span><span class="sxs-lookup"><span data-stu-id="97728-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="97728-104">Źródła danych muszą być prawidłowo skonfigurowane do obsługi powiadomień kwerendy SQL, a użytkownik musi mieć odpowiednie uprawnienia po stronie klienta i po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="97728-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="97728-105">Aby użyć powiadomienia o zapytaniach, należy:</span><span class="sxs-lookup"><span data-stu-id="97728-105">To use query notifications you must:</span></span>  
  
-   <span data-ttu-id="97728-106">Włącz powiadomienia kwerendy dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="97728-106">Enable query notifications for your database.</span></span>  
  
-   <span data-ttu-id="97728-107">Upewnij się, że identyfikator użytkownika, używany do łączenia z bazą danych ma odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="97728-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
-   <span data-ttu-id="97728-108">Użyj <xref:System.Data.SqlClient.SqlCommand> obiekt, aby wykonać poprawną instrukcją SELECT z obiektem skojarzone powiadomień — albo <xref:System.Data.SqlClient.SqlDependency> lub <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="97728-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
-   <span data-ttu-id="97728-109">Podaj kod, aby przetworzyć powiadomienia, jeśli monitorowane dane zmian.</span><span class="sxs-lookup"><span data-stu-id="97728-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="97728-110">Wymagania dotyczące powiadomień kwerendy</span><span class="sxs-lookup"><span data-stu-id="97728-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="97728-111">Powiadomienia o zapytaniach są obsługiwane tylko w przypadku instrukcji SELECT, spełniających określone wymagania.</span><span class="sxs-lookup"><span data-stu-id="97728-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="97728-112">Poniższa tabela zawiera linki do dokumentacji programu Service Broker i powiadomienia o zapytaniach w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="97728-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="97728-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="97728-113">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="97728-114">Tworzenie zapytania o powiadomienie</span><span class="sxs-lookup"><span data-stu-id="97728-114">Creating a Query for Notification</span></span>](https://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="97728-115">Zagadnienia dotyczące zabezpieczeń dla programu Service Broker</span><span class="sxs-lookup"><span data-stu-id="97728-115">Security Considerations for Service Broker</span></span>](https://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [<span data-ttu-id="97728-116">Zabezpieczenia i ochrona (programu Service Broker)</span><span class="sxs-lookup"><span data-stu-id="97728-116">Security and Protection (Service Broker)</span></span>](https://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [<span data-ttu-id="97728-117">Zagadnienia dotyczące zabezpieczeń dla usługi powiadomień</span><span class="sxs-lookup"><span data-stu-id="97728-117">Security Considerations for Notifications Services</span></span>](https://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [<span data-ttu-id="97728-118">Uprawnienia do zapytań powiadomień</span><span class="sxs-lookup"><span data-stu-id="97728-118">Query Notification Permissions</span></span>](https://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [<span data-ttu-id="97728-119">Międzynarodowe uwagi dotyczące programu Service Broker</span><span class="sxs-lookup"><span data-stu-id="97728-119">International Considerations for Service Broker</span></span>](https://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [<span data-ttu-id="97728-120">Solution Design Considerations (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="97728-120">Solution Design Considerations (Service Broker)</span></span>](https://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [<span data-ttu-id="97728-121">Service Broker Developer InfoCenter</span><span class="sxs-lookup"><span data-stu-id="97728-121">Service Broker Developer InfoCenter</span></span>](https://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="97728-122">Przewodnik dewelopera usługi (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="97728-122">Developer's Guide (Service Broker)</span></span>](https://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="97728-123">Włączanie powiadomień kwerendy do uruchomienia przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="97728-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="97728-124">Aby włączyć brokera usługi na **AdventureWorks** bazy danych przy użyciu programu SQL Server Management Studio, wykonaj następującą instrukcję języka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="97728-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="97728-125">Przykłady powiadomień kwerendy by działała poprawnie należy wykonać następujące instrukcje języka Transact-SQL na serwerze bazy danych.</span><span class="sxs-lookup"><span data-stu-id="97728-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="97728-126">Uprawnienia do zapytań powiadomienia</span><span class="sxs-lookup"><span data-stu-id="97728-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="97728-127">Użytkownicy, którzy wykonaj polecenia żądania powiadomienia musi mieć SUBSKRYBOWANIA powiadomienia o ZAPYTANIACH bazy danych, uprawnienia na serwerze.</span><span class="sxs-lookup"><span data-stu-id="97728-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="97728-128">Kod po stronie klienta, która działa w sytuacji, w częściowej relacji zaufania wymaga <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="97728-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="97728-129">Poniższy kod tworzy <xref:System.Data.SqlClient.SqlClientPermission> obiektu, ustawienie <xref:System.Security.Permissions.PermissionState> do <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="97728-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="97728-130"><xref:System.Security.CodeAccessPermission.Demand%2A> Wymusi <xref:System.Security.SecurityException> w czasie wykonywania, jeśli wszystkie obiekty wywołujące wyżej w stosie wywołań nie przyznano uprawnień.</span><span class="sxs-lookup"><span data-stu-id="97728-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="97728-131">Wybieranie obiektu powiadomienia</span><span class="sxs-lookup"><span data-stu-id="97728-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="97728-132">Interfejs API powiadomień zapytania udostępnia dwa obiekty można przetworzyć powiadomień: <xref:System.Data.SqlClient.SqlDependency> i <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="97728-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="97728-133">Ogólnie rzecz biorąc, należy użyć większości aplikacji niedotyczący środowiska ASP.NET <xref:System.Data.SqlClient.SqlDependency> obiektu.</span><span class="sxs-lookup"><span data-stu-id="97728-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="97728-134">Aplikacje ASP.NET należy używać wyższego poziomu <xref:System.Web.Caching.SqlCacheDependency>, który opakowuje <xref:System.Data.SqlClient.SqlDependency> i zapewnia platformę do administrowania obiektów powiadomień i pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="97728-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="97728-135">Za pomocą elementu SqlDependency</span><span class="sxs-lookup"><span data-stu-id="97728-135">Using SqlDependency</span></span>  
 <span data-ttu-id="97728-136">Aby użyć <xref:System.Data.SqlClient.SqlDependency>, programu Service Broker musi być włączona dla bazy danych SQL Server używany, a użytkownicy muszą mieć uprawnienia do odbierania powiadomień.</span><span class="sxs-lookup"><span data-stu-id="97728-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="97728-137">Obiekty programu Service Broker, takie jak kolejka powiadomień są wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="97728-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="97728-138">Ponadto <xref:System.Data.SqlClient.SqlDependency> automatycznie powoduje uruchomienie procesu roboczego wątku można przetworzyć powiadomień, ponieważ są one opublikowane w kolejce; również analizuje komunikatów programu Service Broker, ujawnienia informacji jako dane argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="97728-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="97728-139"><xref:System.Data.SqlClient.SqlDependency> musi zostać zainicjowany przez wywołanie metody `Start` metodę ustanawiania zależności z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="97728-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="97728-140">Jest to metoda statyczna, musi być wywołana tylko raz podczas inicjowania aplikacji, dla każdego połączenia z bazą danych wymagane.</span><span class="sxs-lookup"><span data-stu-id="97728-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="97728-141">`Stop` Metoda powinna być wywoływana po zakończeniu aplikacji dla każdego połączenia zależności, który został wykonany.</span><span class="sxs-lookup"><span data-stu-id="97728-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="97728-142">Za pomocą SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="97728-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="97728-143">Z kolei <xref:System.Data.Sql.SqlNotificationRequest> wymaga implementacji całej infrastruktury nasłuchiwania samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="97728-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="97728-144">Ponadto muszą być zdefiniowane wszystkie pomocnicze obiektów brokera usług takich jak kolejki, usług i typy obsługiwane przez kolejkę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="97728-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="97728-145">To podejście ręcznego jest przydatne, jeśli aplikacja wymaga specjalnych powiadomienia lub zachowania powiadomień, czy aplikacja jest częścią większej aplikacji brokera usług.</span><span class="sxs-lookup"><span data-stu-id="97728-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97728-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97728-146">See also</span></span>
- [<span data-ttu-id="97728-147">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="97728-147">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="97728-148">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="97728-148">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
