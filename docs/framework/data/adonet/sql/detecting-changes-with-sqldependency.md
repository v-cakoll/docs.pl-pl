---
title: Wykrywanie zmian za pomocą elementu SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649949"
---
# <a name="detecting-changes-with-sqldependency"></a>Wykrywanie zmian za pomocą elementu SqlDependency
A <xref:System.Data.SqlClient.SqlDependency> obiekt może być skojarzony z <xref:System.Data.SqlClient.SqlCommand> w celu wykrycia, gdy wyniki zapytania różnią się od pierwotnie pobrany. Można także przypisać obiekt delegowany do `OnChange` zdarzenie, które będą uruchamiane, gdy zmienią się wyniki skojarzone polecenia. Musisz skojarzyć <xref:System.Data.SqlClient.SqlDependency> za pomocą polecenia przed wykonaniem polecenia. `HasChanges` Właściwość <xref:System.Data.SqlClient.SqlDependency> można również określić, czy wyniki zapytania uległy zmianie od czasu najpierw pobrania danych.  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Zależy od infrastruktury zależności <xref:System.Data.SqlClient.SqlConnection> otwieranego po <xref:System.Data.SqlClient.SqlDependency.Start%2A> jest wywoływana, aby otrzymywać powiadomienia o zmienionych danych bazowych dla podanego polecenia. Możliwości dla klientów zainicjować wywołanie `SqlDependency.Start` jest kontrolowany za pośrednictwem <xref:System.Data.SqlClient.SqlClientPermission> i atrybuty zabezpieczeń dostępu kodu. Aby uzyskać więcej informacji, zobacz [Włączanie kwerenda powiadomienia](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) i [zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Przykład  
 Poniższe kroki pokazują, jak zadeklarować zależność, należy wykonać polecenie i otrzymywanie powiadomienia w przypadku zmiany zestawu wyników:  
  
1.  Zainicjuj `SqlDependency` połączenie z serwerem.  
  
2.  Tworzenie <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów, aby połączyć się z serwerem i Zdefiniuj instrukcję Transact-SQL.  
  
3.  Utwórz nową `SqlDependency` obiektu lub użyć istniejącego i powiązać `SqlCommand` obiektu. Wewnętrznie, spowoduje to utworzenie <xref:System.Data.Sql.SqlNotificationRequest> obiektu i wiąże go obiekt polecenia zgodnie z potrzebami. To żądanie powiadomienie zawiera wewnętrzny identyfikator, który unikatowo identyfikuje to `SqlDependency` obiektu. Uruchamia również odbiornik klienta, jeśli nie jest już aktywny.  
  
4.  Subskrybuj program obsługi zdarzeń do `OnChange` zdarzenia `SqlDependency` obiektu.  
  
5.  Wykonanie polecenia przy użyciu dowolnej z `Execute` metody `SqlCommand` obiektu. Ponieważ polecenie jest powiązany z obiektem powiadomień, serwer rozpoznaje, że muszą być generowane powiadomienia i informacji o kolejki wskaże kolejki zależności.  
  
6.  Zatrzymaj `SqlDependency` połączenie z serwerem.  
  
 Jeśli każdy użytkownik zmieni później danych bazowych, programu Microsoft SQL Server wykryje, że nie jest oczekiwanie na powiadomienie dla tej zmiany i wysyła powiadomienie, które są przetwarzane i przesyłane dalej do klienta za pośrednictwem podstawowych `SqlConnection` utworzony przez wywołanie metody `SqlDependency.Start`. Odbiornik klient otrzymuje komunikat unieważniania. Odbiornik klient następnie klient zlokalizuje skojarzonego `SqlDependency` obiektu i generowane `OnChange` zdarzeń.  
  
 Poniższy fragment kodu przedstawia wzorzec projektowania, które są używane do tworzenia przykładowej aplikacji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienia zapytań w programie SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
