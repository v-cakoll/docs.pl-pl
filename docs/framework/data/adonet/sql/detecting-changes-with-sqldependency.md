---
title: Wykrywanie zmian z elementu SqlDependency
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
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1d3fd662ace71d77a185cd996c05960d026ef691
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="17f91-102">Wykrywanie zmian z elementu SqlDependency</span><span class="sxs-lookup"><span data-stu-id="17f91-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="17f91-103">A <xref:System.Data.SqlClient.SqlDependency> obiekt może być skojarzony z <xref:System.Data.SqlClient.SqlCommand> w celu wykrycia, gdy wyniki zapytania różnią się od pierwotnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="17f91-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="17f91-104">Można także przypisać pełnomocnika, aby `OnChange` zdarzenie, które będą uruchamiane po zmianie wyniki dla skojarzone polecenie.</span><span class="sxs-lookup"><span data-stu-id="17f91-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="17f91-105">Musisz skojarzyć <xref:System.Data.SqlClient.SqlDependency> przy użyciu polecenia przed wykonaniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="17f91-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="17f91-106">`HasChanges` Właściwość <xref:System.Data.SqlClient.SqlDependency> można również określić, jeśli wyniki zapytania zostały zmienione od czasu najpierw pobrania danych.</span><span class="sxs-lookup"><span data-stu-id="17f91-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="17f91-107">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="17f91-107">Security Considerations</span></span>  
 <span data-ttu-id="17f91-108">Zależy od infrastruktury zależności <xref:System.Data.SqlClient.SqlConnection> otwieranego podczas <xref:System.Data.SqlClient.SqlDependency.Start%2A> jest wywoływana w celu odbierania powiadomień, które danych została zmieniona dla danego polecenia.</span><span class="sxs-lookup"><span data-stu-id="17f91-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="17f91-109">Możliwość przez klienta do zainicjowania wywołanie `SqlDependency.Start` jest kontrolowany za pośrednictwem <xref:System.Data.SqlClient.SqlClientPermission> i atrybuty zabezpieczeń dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="17f91-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="17f91-110">Aby uzyskać więcej informacji, zobacz [włączania powiadomień o zapytaniach](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) i [zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="17f91-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="17f91-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="17f91-111">Example</span></span>  
 <span data-ttu-id="17f91-112">Poniższe kroki przedstawiają sposób zadeklarować zależność, wykonaj polecenie i otrzymasz powiadomienie, gdy zestaw wyników zmiany:</span><span class="sxs-lookup"><span data-stu-id="17f91-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="17f91-113">Zainicjuj `SqlDependency` połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="17f91-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="17f91-114">Utwórz <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów do łączenia się z serwerem i zdefiniuj instrukcji języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="17f91-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="17f91-115">Utwórz nową `SqlDependency` obiekt, lub użyj istniejącej i powiązać `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="17f91-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="17f91-116">Wewnętrznie, spowoduje to utworzenie <xref:System.Data.Sql.SqlNotificationRequest> obiektu i wiąże go do obiektu command zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="17f91-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="17f91-117">To żądanie powiadomienia zawiera wewnętrzny identyfikator, który unikatowo identyfikuje to `SqlDependency` obiektu.</span><span class="sxs-lookup"><span data-stu-id="17f91-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="17f91-118">Uruchamia również odbiornik klienta, jeśli nie jest już aktywne.</span><span class="sxs-lookup"><span data-stu-id="17f91-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="17f91-119">Program obsługi zdarzeń do subskrybowania `OnChange` zdarzenie `SqlDependency` obiektu.</span><span class="sxs-lookup"><span data-stu-id="17f91-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="17f91-120">Wykonanie polecenia przy użyciu dowolnego `Execute` metody `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="17f91-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="17f91-121">Ponieważ polecenie jest powiązany z obiektem powiadomień, serwer uznaje, że należy wygenerować powiadomienie, informacji kolejki wskaże kolejki zależności.</span><span class="sxs-lookup"><span data-stu-id="17f91-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="17f91-122">Zatrzymaj `SqlDependency` połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="17f91-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="17f91-123">Jeśli dowolny użytkownik zmieni się następnie danych, programu Microsoft SQL Server wykryje, że nie znajduje się powiadomienie do czasu tej zmiany i zapisuje powiadomienie, które jest przetwarzane i przesyłane dalej do klienta za pośrednictwem podstawowych `SqlConnection` utworzony wywołując `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="17f91-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="17f91-124">Odbiornik klient odbiera komunikat unieważniania.</span><span class="sxs-lookup"><span data-stu-id="17f91-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="17f91-125">Odbiornik klient następnie klient zlokalizuje skojarzony `SqlDependency` obiekt i uruchamiany `OnChange` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17f91-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="17f91-126">Poniższy fragment kodu przedstawia wzorzec projektowania, który ma zostać użyty do tworzenia przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17f91-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
```vb  
Sub Initialization()  
    ' Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName)  
End Sub  
  
Sub SomeMethod()   
    ' Assume connection is an open SqlConnection.  
    ' Create a new SqlCommand object.  
    Using command As New SqlCommand( _  
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _  
      connection)  
  
        ' Create a dependency and associate it with the SqlCommand.  
        Dim dependency As New SqlDependency(command)  
        ' Maintain the refence in a class member.  
        ' Subscribe to the SqlDependency event.  
        AddHandler dependency.OnChange, AddressOf OnDependencyChange  
  
        ' Execute the command.  
        Using reader = command.ExecuteReader()  
            ' Process the DataReader.  
        End Using  
    End Using  
End Sub   
  
' Handler method  
Sub OnDependencyChange(ByVal sender As Object, _  
    ByVal e As SqlNotificationEventArgs)   
    ' Handle the event (for example, invalidate this cache entry).  
End Sub  
  
Sub Termination()  
    ' Release the dependency  
    SqlDependency.Stop(connectionString, queueName)  
End Sub  
```  
  
```csharp  
void Initialization()  
{  
    // Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName);  
}  
  
void SomeMethod()  
{  
    // Assume connection is an open SqlConnection.  
  
    // Create a new SqlCommand object.  
    using (SqlCommand command=new SqlCommand(  
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",   
        connection))  
    {  
  
        // Create a dependency and associate it with the SqlCommand.  
        SqlDependency dependency=new SqlDependency(command);  
        // Maintain the refence in a class member.  
  
        // Subscribe to the SqlDependency event.  
        dependency.OnChange+=new  
           OnChangeEventHandler(OnDependencyChange);  
  
        // Execute the command.  
        using (SqlDataReader reader = command.ExecuteReader())  
        {  
            // Process the DataReader.  
        }  
    }  
}  
  
// Handler method  
void OnDependencyChange(object sender,   
   SqlNotificationEventArgs e )  
{  
  // Handle the event (for example, invalidate this cache entry).  
}  
  
void Termination()  
{  
    // Release the dependency.  
    SqlDependency.Stop(connectionString, queueName);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="17f91-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17f91-127">See Also</span></span>  
 [<span data-ttu-id="17f91-128">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="17f91-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="17f91-129">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="17f91-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
