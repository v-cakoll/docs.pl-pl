---
title: Wykrywanie zmian za pomocą elementu SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871153"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="d279f-102">Wykrywanie zmian za pomocą elementu SqlDependency</span><span class="sxs-lookup"><span data-stu-id="d279f-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="d279f-103">A <xref:System.Data.SqlClient.SqlDependency> obiekt może być skojarzony z <xref:System.Data.SqlClient.SqlCommand> w celu wykrycia, gdy wyniki zapytania różnią się od pierwotnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="d279f-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="d279f-104">Można także przypisać obiekt delegowany do `OnChange` zdarzenie, które będą uruchamiane, gdy zmienią się wyniki skojarzone polecenia.</span><span class="sxs-lookup"><span data-stu-id="d279f-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="d279f-105">Musisz skojarzyć <xref:System.Data.SqlClient.SqlDependency> za pomocą polecenia przed wykonaniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="d279f-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="d279f-106">`HasChanges` Właściwość <xref:System.Data.SqlClient.SqlDependency> można również określić, czy wyniki zapytania uległy zmianie od czasu najpierw pobrania danych.</span><span class="sxs-lookup"><span data-stu-id="d279f-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="d279f-107">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d279f-107">Security Considerations</span></span>  
 <span data-ttu-id="d279f-108">Zależy od infrastruktury zależności <xref:System.Data.SqlClient.SqlConnection> otwieranego po <xref:System.Data.SqlClient.SqlDependency.Start%2A> jest wywoływana, aby otrzymywać powiadomienia o zmienionych danych bazowych dla podanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d279f-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="d279f-109">Możliwości dla klientów zainicjować wywołanie `SqlDependency.Start` jest kontrolowany za pośrednictwem <xref:System.Data.SqlClient.SqlClientPermission> i atrybuty zabezpieczeń dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="d279f-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="d279f-110">Aby uzyskać więcej informacji, zobacz [Włączanie kwerenda powiadomienia](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) i [zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="d279f-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="d279f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d279f-111">Example</span></span>  
 <span data-ttu-id="d279f-112">Poniższe kroki pokazują, jak zadeklarować zależność, należy wykonać polecenie i otrzymywanie powiadomienia w przypadku zmiany zestawu wyników:</span><span class="sxs-lookup"><span data-stu-id="d279f-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="d279f-113">Zainicjuj `SqlDependency` połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="d279f-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="d279f-114">Tworzenie <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów, aby połączyć się z serwerem i Zdefiniuj instrukcję Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="d279f-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="d279f-115">Utwórz nową `SqlDependency` obiektu lub użyć istniejącego i powiązać `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d279f-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="d279f-116">Wewnętrznie, spowoduje to utworzenie <xref:System.Data.Sql.SqlNotificationRequest> obiektu i wiąże go obiekt polecenia zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d279f-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="d279f-117">To żądanie powiadomienie zawiera wewnętrzny identyfikator, który unikatowo identyfikuje to `SqlDependency` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d279f-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="d279f-118">Uruchamia również odbiornik klienta, jeśli nie jest już aktywny.</span><span class="sxs-lookup"><span data-stu-id="d279f-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="d279f-119">Subskrybuj program obsługi zdarzeń do `OnChange` zdarzenia `SqlDependency` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d279f-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="d279f-120">Wykonanie polecenia przy użyciu dowolnej z `Execute` metody `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d279f-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="d279f-121">Ponieważ polecenie jest powiązany z obiektem powiadomień, serwer rozpoznaje, że muszą być generowane powiadomienia i informacji o kolejki wskaże kolejki zależności.</span><span class="sxs-lookup"><span data-stu-id="d279f-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="d279f-122">Zatrzymaj `SqlDependency` połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="d279f-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="d279f-123">Jeśli każdy użytkownik zmieni później danych bazowych, programu Microsoft SQL Server wykryje, że nie jest oczekiwanie na powiadomienie dla tej zmiany i wysyła powiadomienie, które są przetwarzane i przesyłane dalej do klienta za pośrednictwem podstawowych `SqlConnection` utworzony przez wywołanie metody `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="d279f-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="d279f-124">Odbiornik klient otrzymuje komunikat unieważniania.</span><span class="sxs-lookup"><span data-stu-id="d279f-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="d279f-125">Odbiornik klient następnie klient zlokalizuje skojarzonego `SqlDependency` obiektu i generowane `OnChange` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d279f-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="d279f-126">Poniższy fragment kodu przedstawia wzorzec projektowania, które są używane do tworzenia przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d279f-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
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
        // Maintain the reference in a class member.  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d279f-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d279f-127">See Also</span></span>  
 [<span data-ttu-id="d279f-128">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="d279f-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="d279f-129">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d279f-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
