---
title: Wykrywanie zmian za pomocą elementu SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 3719188064388b00c756dd037d4a475ca6debd13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782422"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="0b7b6-102">Wykrywanie zmian za pomocą elementu SqlDependency</span><span class="sxs-lookup"><span data-stu-id="0b7b6-102">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="0b7b6-103">Obiekt może być skojarzony z w celu <xref:System.Data.SqlClient.SqlCommand> wykrycia, gdy wyniki zapytania różnią się od pierwotnych pobranych. <xref:System.Data.SqlClient.SqlDependency></span><span class="sxs-lookup"><span data-stu-id="0b7b6-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="0b7b6-104">Można również przypisać delegata do `OnChange` zdarzenia, które zostanie wywołane po zmianie wyników dla skojarzonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="0b7b6-105">Należy skojarzyć <xref:System.Data.SqlClient.SqlDependency> z poleceniem przed wykonaniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="0b7b6-106">`HasChanges` Właściwość<xref:System.Data.SqlClient.SqlDependency> może również służyć do określenia, czy wyniki zapytania uległy zmianie od momentu pierwszego pobrania danych.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="0b7b6-107">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0b7b6-107">Security Considerations</span></span>

<span data-ttu-id="0b7b6-108">Infrastruktura zależności opiera się na <xref:System.Data.SqlClient.SqlConnection> otwarciu, gdy <xref:System.Data.SqlClient.SqlDependency.Start%2A> jest wywoływana w celu otrzymywania powiadomień, że dane bazowe zostały zmienione dla danego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="0b7b6-109">Możliwość inicjowania wywołania `SqlDependency.Start` przez klienta jest kontrolowana za pomocą <xref:System.Data.SqlClient.SqlClientPermission> atrybutów zabezpieczeń dostępu do kodu i.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="0b7b6-110">Aby uzyskać więcej informacji, zobacz [Włączanie powiadomień o zapytaniach](enabling-query-notifications.md) i [zabezpieczenia dostępu kodu i ADO.NET](../code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="0b7b6-110">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="0b7b6-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b7b6-111">Example</span></span>

<span data-ttu-id="0b7b6-112">Poniższe kroki ilustrują sposób deklarowania zależności, wykonywania polecenia i odbierania powiadomienia po zmianie zestawu wyników:</span><span class="sxs-lookup"><span data-stu-id="0b7b6-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="0b7b6-113">Zainicjuj `SqlDependency` połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-113">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="0b7b6-114">Utwórz <xref:System.Data.SqlClient.SqlConnection> obiekty <xref:System.Data.SqlClient.SqlCommand> i Połącz się z serwerem i zdefiniuj instrukcję języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="0b7b6-115">Utwórz nowy `SqlDependency` obiekt lub Użyj istniejącego obiektu i powiąż go `SqlCommand` z obiektem.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="0b7b6-116">Wewnętrznie tworzy <xref:System.Data.Sql.SqlNotificationRequest> obiekt i wiąże go z obiektem Command w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="0b7b6-117">To żądanie powiadomienia zawiera identyfikator wewnętrzny, który jednoznacznie identyfikuje ten `SqlDependency` obiekt.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="0b7b6-118">Uruchamia również odbiornik klienta, jeśli nie jest jeszcze aktywny.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-118">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="0b7b6-119">Zasubskrybuj procedurę obsługi zdarzeń do `OnChange` zdarzenia `SqlDependency` obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="0b7b6-120">Wykonaj polecenie przy użyciu dowolnej `Execute` metody `SqlCommand` obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="0b7b6-121">Ponieważ polecenie jest powiązane z obiektem Notification, serwer rozpoznaje, że musi wygenerować powiadomienie, a informacje o kolejce wskazują na kolejkę zależności.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="0b7b6-122">`SqlDependency` Zatrzymaj połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-122">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="0b7b6-123">Jeśli dowolny użytkownik zmieni dane bazowe, Microsoft SQL Server wykryje, że istnieje powiadomienie oczekujące na taką zmianę, i opublikuje powiadomienie, które jest przetwarzane i przekazywane do klienta za pomocą programu `SqlConnection` , który został utworzony. przez wywołanie `SqlDependency.Start`metody.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="0b7b6-124">Odbiornik klienta odbiera komunikat informujący o unieważnieniu.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="0b7b6-125">Odbiornik klienta lokalizuje skojarzony `SqlDependency` obiekt i `OnChange` uruchamia zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="0b7b6-126">Poniższy fragment kodu przedstawia Wzorzec projektowy, który służy do tworzenia przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b7b6-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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
        ' Maintain the refernce in a class member.
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

## <a name="see-also"></a><span data-ttu-id="0b7b6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b7b6-127">See also</span></span>

- [<span data-ttu-id="0b7b6-128">Powiadomienia zapytań w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="0b7b6-128">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="0b7b6-129">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0b7b6-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
