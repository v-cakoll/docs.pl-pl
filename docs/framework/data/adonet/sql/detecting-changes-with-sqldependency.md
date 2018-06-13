---
title: Wykrywanie zmian z elementu SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: a25afbe0124f7870df886a1e26e0df2a0716b205
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360193"
---
# <a name="detecting-changes-with-sqldependency"></a>Wykrywanie zmian z elementu SqlDependency
A <xref:System.Data.SqlClient.SqlDependency> obiekt może być skojarzony z <xref:System.Data.SqlClient.SqlCommand> w celu wykrycia, gdy wyniki zapytania różnią się od pierwotnie pobrany. Można także przypisać pełnomocnika, aby `OnChange` zdarzenie, które będą uruchamiane po zmianie wyniki dla skojarzone polecenie. Musisz skojarzyć <xref:System.Data.SqlClient.SqlDependency> przy użyciu polecenia przed wykonaniem polecenia. `HasChanges` Właściwość <xref:System.Data.SqlClient.SqlDependency> można również określić, jeśli wyniki zapytania zostały zmienione od czasu najpierw pobrania danych.  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Zależy od infrastruktury zależności <xref:System.Data.SqlClient.SqlConnection> otwieranego podczas <xref:System.Data.SqlClient.SqlDependency.Start%2A> jest wywoływana w celu odbierania powiadomień, które danych została zmieniona dla danego polecenia. Możliwość przez klienta do zainicjowania wywołanie `SqlDependency.Start` jest kontrolowany za pośrednictwem <xref:System.Data.SqlClient.SqlClientPermission> i atrybuty zabezpieczeń dostępu kodu. Aby uzyskać więcej informacji, zobacz [włączania powiadomień o zapytaniach](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) i [zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Przykład  
 Poniższe kroki przedstawiają sposób zadeklarować zależność, wykonaj polecenie i otrzymasz powiadomienie, gdy zestaw wyników zmiany:  
  
1.  Zainicjuj `SqlDependency` połączenie z serwerem.  
  
2.  Utwórz <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów do łączenia się z serwerem i zdefiniuj instrukcji języka Transact-SQL.  
  
3.  Utwórz nową `SqlDependency` obiekt, lub użyj istniejącej i powiązać `SqlCommand` obiektu. Wewnętrznie, spowoduje to utworzenie <xref:System.Data.Sql.SqlNotificationRequest> obiektu i wiąże go do obiektu command zgodnie z potrzebami. To żądanie powiadomienia zawiera wewnętrzny identyfikator, który unikatowo identyfikuje to `SqlDependency` obiektu. Uruchamia również odbiornik klienta, jeśli nie jest już aktywne.  
  
4.  Program obsługi zdarzeń do subskrybowania `OnChange` zdarzenie `SqlDependency` obiektu.  
  
5.  Wykonanie polecenia przy użyciu dowolnego `Execute` metody `SqlCommand` obiektu. Ponieważ polecenie jest powiązany z obiektem powiadomień, serwer uznaje, że należy wygenerować powiadomienie, informacji kolejki wskaże kolejki zależności.  
  
6.  Zatrzymaj `SqlDependency` połączenie z serwerem.  
  
 Jeśli dowolny użytkownik zmieni się następnie danych, programu Microsoft SQL Server wykryje, że nie znajduje się powiadomienie do czasu tej zmiany i zapisuje powiadomienie, które jest przetwarzane i przesyłane dalej do klienta za pośrednictwem podstawowych `SqlConnection` utworzony wywołując `SqlDependency.Start`. Odbiornik klient odbiera komunikat unieważniania. Odbiornik klient następnie klient zlokalizuje skojarzony `SqlDependency` obiekt i uruchamiany `OnChange` zdarzeń.  
  
 Poniższy fragment kodu przedstawia wzorzec projektowania, który ma zostać użyty do tworzenia przykładowej aplikacji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
