---
title: Nawiązywanie połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: b4a61306cd9b61f84eff16ffaac302317b6dfe44
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959189"
---
# <a name="establishing-the-connection"></a>Nawiązywanie połączenia
Aby nawiązać połączenie z Microsoft SQL Server, <xref:System.Data.SqlClient.SqlConnection> Użyj obiektu dostawca danych .NET Framework SQL Server. Aby nawiązać połączenie ze źródłem danych OLE DB, użyj <xref:System.Data.OleDb.OleDbConnection> obiektu .NET Framework dostawca danych dla OLE DB. Aby nawiązać połączenie ze źródłem danych ODBC, użyj <xref:System.Data.Odbc.OdbcConnection> obiektu dostawca danych .NET Framework dla ODBC. Aby nawiązać połączenie ze źródłem danych Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu dostawca danych .NET Framework dla programu Oracle. Aby bezpiecznie przechowywać i pobierać parametry połączenia, zobacz [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Zamykanie połączeń  
 Zalecane jest, aby zawsze zamykać połączenie po zakończeniu korzystania z niego, aby można było zwrócić połączenie do puli. Blok w Visual Basic lub C# automatycznie usuwa połączenie, gdy kod opuszcza blok, nawet w przypadku nieobsługiwanego wyjątku. `Using` Aby uzyskać więcej informacji, zobacz [używanie instrukcji using](../../../csharp/language-reference/keywords/using-statement.md) i [instrukcji using](../../../visual-basic/language-reference/statements/using-statement.md) .  
  
 Można również użyć `Close` metod lub `Dispose` obiektu połączenia dla dostawcy, którego używasz. Połączenia, które nie zostały jawnie zamknięte, mogą nie zostać dodane lub zwrócone do puli. Na przykład połączenie, które zostało utracone poza zakresem, ale nie zostało jawnie zamknięte, zostanie zwrócone do puli połączeń tylko wtedy, gdy Osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważne. Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i pule połączeń Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> Nie należy `Close` wywoływać `Dispose` ani nawiązać **połączenia**, elementu **DataReader**ani innego obiektu zarządzanego w `Finalize` metodzie klasy. W finalizatorze zwalniane są tylko niezarządzane zasoby, które są własnością klasy bezpośrednio. Jeśli Klasa nie jest własnością żadnych niezarządzanych zasobów, nie Uwzględniaj `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Zdarzenia logowania i wylogowywania nie będą zgłaszane na serwerze, gdy połączenie zostanie pobrane z lub zwrócone do puli połączeń, ponieważ połączenie nie jest faktycznie zamknięte, gdy zostanie zwrócone do puli połączeń. Aby uzyskać więcej informacji, zobacz SQL Servering pooling [(ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Nawiązywanie połączenia z SQL Server  
 Dostawca danych .NET Framework dla SQL Server obsługuje format parametrów połączenia, który jest podobny do formatu parametrów połączenia OLE DB (ADO). W przypadku prawidłowych nazw i wartości formatu ciągu zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu. Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasy do tworzenia składniowo prawidłowych parametrów połączenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [konstruktory parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie z bazą danych SQL Server.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a>Zintegrowane zabezpieczenia i ASP.NET  
 SQL Server zintegrowane zabezpieczenia (znane także jako zaufane połączenia) pomagają zapewnić ochronę podczas nawiązywania połączenia z SQL Server, ponieważ nie uwidacznia identyfikatora użytkownika i hasła w parametrach połączenia i jest zalecaną metodą uwierzytelniania połączenia. Zabezpieczenia zintegrowane korzystają z bieżącej tożsamości lub tokenu procesu wykonywania. W przypadku aplikacji klasycznych zwykle jest to tożsamość aktualnie zalogowanego użytkownika.  
  
 Tożsamość zabezpieczeń dla aplikacji ASP.NET można ustawić na jedną z kilku różnych opcji. Aby lepiej zrozumieć tożsamość zabezpieczeń używaną przez aplikację ASP.NET podczas nawiązywania połączenia z SQL Server, zobacz [personifikacja ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [uwierzytelnianie ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))i [instrukcje: Dostęp SQL Server przy użyciu zintegrowanych](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))zabezpieczeń systemu Windows.  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Nawiązywanie połączenia ze źródłem danych OLE DB  
 Dostawca danych .NET Framework dla OLE DB zapewnia łączność ze źródłami danych ujawnionymi przy użyciu OLE DB (za pośrednictwem SQLOLEDB, dostawcy OLE DB dla SQL Server) przy użyciu obiektu **OleDbConnection** .  
  
 W przypadku .NET Framework Dostawca danych dla OLE DB format parametrów połączenia jest identyczny z formatem parametrów połączenia używanym w ADO, z następującymi wyjątkami:  
  
- Słowo kluczowe **Provider** jest wymagane.  
  
- **Adresy URL**, **dostawcy zdalnego**i słowa kluczowe **serwera zdalnego** nie są obsługiwane.  
  
 Aby uzyskać więcej informacji na temat OLE DB parametrów połączenia, <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Zobacz temat. Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> do tworzenia parametrów połączenia w czasie wykonywania.  
  
> [!NOTE]
> Obiekt **OleDbConnection** nie obsługuje ustawiania ani pobierania właściwości dynamicznych specyficznych dla dostawcy OLE DB. Obsługiwane są tylko właściwości, które można przekazywać w parametrach połączenia dla dostawcy OLE DB.  
  
 Poniższy przykład kodu demonstruje sposób tworzenia i otwierania połączenia ze źródłem danych OLE DB.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a>Nie używaj plików Universal Data Link  
 Możliwe jest podanie informacji o połączeniu dla **OleDbConnection** w pliku Universal Data Link (UDL); należy jednak unikać tego. Pliki UDL nie są szyfrowane i ujawniają informacje o parametrach połączenia w postaci zwykłego tekstu. Ponieważ plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji, nie może być zabezpieczony przy użyciu .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Nawiązywanie połączenia ze źródłem danych ODBC  
 Dostawca danych .NET Framework dla ODBC zapewnia łączność ze źródłami danych, które są udostępniane za pomocą ODBC przy użyciu obiektu **OdbcConnection** .  
  
 W przypadku .NET Framework Dostawca danych dla ODBC, format parametrów połączenia jest zaprojektowana tak, aby pasował do formatu parametrów połączenia ODBC tak blisko, jak to możliwe. Możesz również podać nazwę źródła danych ODBC (DSN). Aby uzyskać więcej szczegółów na temat **OdbcConnection** , zobacz <xref:System.Data.Odbc.OdbcConnection>.  
  
 Poniższy przykład kodu demonstruje sposób tworzenia i otwierania połączenia ze źródłem danych ODBC.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a>Nawiązywanie połączenia ze źródłem danych Oracle  
 .NET Framework Dostawca danych dla programu Oracle zapewnia łączność ze źródłami danych Oracle przy użyciu obiektu **OracleConnection** .  
  
 W przypadku .NET Framework Dostawca danych dla programu Oracle format parametrów połączenia jest zaprojektowany tak, aby był zgodny z formatem parametrów połączenia dostawcy OLE DB dla programu Oracle (MSDAORA I). Aby uzyskać więcej szczegółów na temat **OracleConnection**, zobacz <xref:System.Data.OracleClient.OracleConnection>.  
  
 Poniższy przykład kodu demonstruje sposób tworzenia i otwierania połączenia ze źródłem danych Oracle.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)
- [Buforowanie połączenia Oracle, OLE DB i ODBC](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
