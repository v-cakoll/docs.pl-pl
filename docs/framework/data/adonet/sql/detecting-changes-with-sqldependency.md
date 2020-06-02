---
title: Wykrywanie zmian za pomocą elementu SqlDependency
description: Skojarz obiekt SqlDependency z elementem SqlCommand w celu wykrycia, kiedy wyniki zapytania różnią się od pierwotnych pobranych w ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: b196d42477e1778c45df64b1390502645fdd649d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286471"
---
# <a name="detecting-changes-with-sqldependency"></a>Wykrywanie zmian za pomocą elementu SqlDependency

<xref:System.Data.SqlClient.SqlDependency>Obiekt może być skojarzony z <xref:System.Data.SqlClient.SqlCommand> w celu wykrycia, gdy wyniki zapytania różnią się od pierwotnych pobranych. Można również przypisać delegata do `OnChange` zdarzenia, które zostanie wywołane po zmianie wyników dla skojarzonego polecenia. Należy skojarzyć <xref:System.Data.SqlClient.SqlDependency> z poleceniem przed wykonaniem polecenia. `HasChanges`Właściwość <xref:System.Data.SqlClient.SqlDependency> może również służyć do określenia, czy wyniki zapytania uległy zmianie od momentu pierwszego pobrania danych.

## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami

Infrastruktura zależności opiera się na <xref:System.Data.SqlClient.SqlConnection> otwarciu, gdy <xref:System.Data.SqlClient.SqlDependency.Start%2A> jest wywoływana w celu otrzymywania powiadomień, że dane bazowe zostały zmienione dla danego polecenia. Możliwość inicjowania wywołania przez klienta `SqlDependency.Start` jest kontrolowana za pomocą <xref:System.Data.SqlClient.SqlClientPermission> atrybutów zabezpieczeń dostępu do kodu i. Aby uzyskać więcej informacji, zobacz [Włączanie powiadomień o zapytaniach](enabling-query-notifications.md) i [zabezpieczenia dostępu kodu i ADO.NET](../code-access-security.md).

### <a name="example"></a>Przykład

Poniższe kroki ilustrują sposób deklarowania zależności, wykonywania polecenia i odbierania powiadomienia po zmianie zestawu wyników:

1. Zainicjuj `SqlDependency` połączenie z serwerem.

2. Utwórz <xref:System.Data.SqlClient.SqlConnection> obiekty i Połącz się z <xref:System.Data.SqlClient.SqlCommand> serwerem i zdefiniuj instrukcję języka Transact-SQL.

3. Utwórz nowy `SqlDependency` obiekt lub Użyj istniejącego obiektu i powiąż go z `SqlCommand` obiektem. Wewnętrznie tworzy <xref:System.Data.Sql.SqlNotificationRequest> obiekt i wiąże go z obiektem Command w razie potrzeby. To żądanie powiadomienia zawiera identyfikator wewnętrzny, który jednoznacznie identyfikuje ten `SqlDependency` obiekt. Uruchamia również odbiornik klienta, jeśli nie jest jeszcze aktywny.

4. Zasubskrybuj procedurę obsługi zdarzeń do `OnChange` zdarzenia `SqlDependency` obiektu.

5. Wykonaj polecenie przy użyciu dowolnej `Execute` metody `SqlCommand` obiektu. Ponieważ polecenie jest powiązane z obiektem Notification, serwer rozpoznaje, że musi wygenerować powiadomienie, a informacje o kolejce wskazują na kolejkę zależności.

6. Zatrzymaj `SqlDependency` połączenie z serwerem.

Jeśli dowolny użytkownik zmieni dane bazowe, Microsoft SQL Server wykryje, że istnieje powiadomienie oczekujące na taką zmianę, i opublikuje powiadomienie, które jest przetwarzane i przekazywane do klienta za pomocą elementu `SqlConnection` , który został utworzony przez wywołanie `SqlDependency.Start` . Odbiornik klienta odbiera komunikat informujący o unieważnieniu. Odbiornik klienta lokalizuje skojarzony `SqlDependency` obiekt i uruchamia `OnChange` zdarzenie.

Poniższy fragment kodu przedstawia Wzorzec projektowy, który służy do tworzenia przykładowej aplikacji.

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

## <a name="see-also"></a>Zobacz także

- [Powiadomienia zapytań w programie SQL Server](query-notifications-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
